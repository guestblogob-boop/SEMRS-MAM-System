# WhatsApp Cloud API (Direct) Setup — Technical Reference

**Internal/technical — not client-facing, and scoped narrower than the
steps below suggest.** This is SEMRS's own engineering runbook for
standing up a WhatsApp Business Cloud API connection — but per CLAUDE.md,
"Conversion & Lead Generation Pricing Model," SEMRS never messages a
client's leads and never touches the client's own WhatsApp Business
Account. **Every phone number and WABA set up using this guide belongs
to SEMRS itself**, used for exactly one purpose: sending the client an
instant, low-volume "you have a new lead" notification (WhatsApp and/or
email — see agents/qualification-sales-agent.md) the moment the
Qualification + AI Sales Agent scores a lead. It is not used to message
end leads at any volume, which is why most of the scale-oriented
sections below (messaging tiers, App Review for consumer-facing
volume) will likely never be reached in practice — SEMRS is sending a
handful of Utility-category alerts per client, not marketing messages
to thousands of end users. Kept here in full because the setup
mechanics (permanent tokens, webhooks, templates, security) are the
same regardless of scale, and because a future feature might need the
higher tiers — not because this system is expected to hit them.

A client never sees or performs any of this directly. Compare against
`prompts/client-help-meta-ads-integration.md`, which *is* client-facing,
for the difference in audience/tone this document deliberately does
not follow.

## Prerequisites
- A Facebook account.
- A Meta Business Manager Account (business.facebook.com) — create one
  if you don't have it.
- A phone number that is NOT currently registered on the WhatsApp
  consumer or Business app. If it is, delete that account first and
  wait 15 minutes.
- A website for verification later.

## 1. Create a Meta App
1. Go to developers.facebook.com → My Apps → Create App.
2. Use case: Other. Type: Business.
3. Name it, link it to your Business Manager account.
4. In the app dashboard, find WhatsApp → Set up.
5. Meta auto-creates a test phone number and a WhatsApp Business
   Account (WABA).

You now have:
- Phone number ID — identifies the sending number
- WABA ID — the business account
- A temporary access token (24 hours, testing only)

## 2. Get a Permanent Access Token (Production)
1. business.facebook.com → Business Settings → Users → System Users
2. Add — name it (e.g. `whatsapp-backend`) — role Admin
3. Add Assets — select your WhatsApp account — grant Full control
4. Generate New Token — select your app, check these scopes:
   - `whatsapp_business_messaging` (send/receive)
   - `whatsapp_business_management` (templates, phone numbers)
5. Set expiry to Never. Copy the token — it's shown once.
6. Store it in your secrets manager (SEMRS's own — this is SEMRS's own
   token on SEMRS's own number, not a client credential). Never commit
   it, never expose it client-side. Still worth the same
   encrypted-at-rest, never-displayed-again discipline this system
   already applies to every stored client credential (see
   `lib/credentialEncryption.ts`) — a real secret is a real secret
   regardless of whose account it belongs to.

## 3. Add Your Real Phone Number
1. WhatsApp → API Setup → Add phone number.
2. Provide display name, category, description.
3. Verify via SMS or voice call.
4. Meta reviews the display name (can be rejected if it doesn't match
   your actual business name — avoid generic terms, emojis, or
   promotional text in the display name).

## 4. Business Verification
Business Settings → Business Info → Start Verification. Submit:
- Legal business name, address, phone
- A business document (registration certificate, utility bill, bank
  statement)
- Website with a matching domain

**Not the same verification CLAUDE.md's pricing model gates onboarding
on.** That gate is about the CLIENT's own WhatsApp Business number
(the one they use to message their leads — see prompts/client-brief.md,
"WhatsApp Business number"), which SEMRS has no access to and doesn't
verify. This section's verification is for SEMRS's own sending number
above, needed only if SEMRS's own notification volume ever needs to
scale past Tier 1 (see Section 7, below) — unlikely at "one alert per
captured lead" volume, but the mechanics are the same either way.

## 5. Set Up Webhooks (required to receive anything)
Sending messages works without this, but you cannot receive delivery
receipts, read receipts, template status updates, or a client's reply
to a notification without a webhook. Since SEMRS's number only ever
talks to clients (never leads — see the framing note at the top of
this document), there's no "did the lead reply" case to handle here;
this is purely about confirming a lead alert actually reached the
client.
1. Stand up an HTTPS endpoint on your backend (must be publicly
   reachable, valid SSL — self-signed certs are rejected).
2. In the app dashboard: WhatsApp → Configuration → Webhook.
3. Enter your callback URL and a Verify Token (a string you choose —
   Meta sends it back on the initial handshake so you can confirm the
   request is really from Meta).
4. Subscribe to these webhook fields at minimum:
   - `messages` — incoming messages and message status
     (sent/delivered/read/failed)
   - `message_template_status_update` — tells you when a submitted
     template is approved/rejected
5. On every incoming webhook call, verify the `X-Hub-Signature-256`
   header against your app secret before trusting the payload — this
   is the concrete mechanism behind CLAUDE.md's existing "Lead-capture
   webhook security" guardrail ("every inbound lead-capture endpoint
   must validate the sender's signature before trusting the payload"),
   not a new rule.

## 6. Create & Submit Message Templates (required before you can message a lead first)
Any business-initiated message to someone who hasn't messaged you in
the last 24 hours must use a pre-approved template — this is the same
24-hour free-form window already documented in CLAUDE.md's Email/
WhatsApp compliance requirements, and it applies to the very first
"instant lead alert" message, so templates need to exist before
go-live, not after.
1. WhatsApp Manager → Message Templates → Create Template.
2. Choose a category: Marketing, Utility, or Authentication — pick the
   one that actually matches the content (a lead-alert to your own
   client counts as Utility; a promo/discount to an end lead is
   Marketing). Mislabeling categories is a common cause of rejection or
   unexpected billing.
3. Write the template with `{{1}}`, `{{2}}` style variables for
   dynamic content (name, lead source, etc.).
4. Submit for review — usually resolves within minutes to a day.
5. Repeat for every distinct message shape you need (lead alert,
   offer/discount link, appointment confirmation, etc.) — each wording
   variant needs its own approved template.

## 7. Messaging Limits & Tiers
New WABAs start in a limited tier and scale up automatically based on
quality and volume of business-initiated conversations in a rolling
24-hour window:
- Tier 1: 250 unique customers/24hr
- Tier 2: 1,000
- Tier 3: 10,000
- Tier 4: unlimited

Business Verification is what unlocks moving beyond Tier 1. Tiers
upgrade automatically as you maintain volume and a healthy quality
rating — you can't request an upgrade manually.

## 8. Phone Number Quality Rating
Each number gets a quality rating (High/Medium/Low) based on block
rates and negative feedback. A number that drops to Low risks
messaging restrictions or being disabled. Practical implications for
SEMRS's own sending number:
- Only send genuine, expected Utility-category lead alerts to clients
  who are actually paying for and expecting them — never repurpose
  this number for anything marketing-flavored, which drives blocks
  much faster than transactional alerts do.
- Keep templates precisely matched to what they're actually for (a
  lead alert, nothing else) — category mismatches drive blocks.
- Monitor this in WhatsApp Manager → Phone Numbers → Quality Rating —
  a dropping quality rating threatens the "instant notification"
  promise the whole Conversion & Lead Generation plan is sold on, not
  just an abstract risk.

## 9. Go Live: Moving Off the Test Number
The auto-created test number/WABA from Step 1 only works with numbers
you've explicitly added as testers and has no real messaging limits.
To go live for real clients:
1. Add SEMRS's own real, verified phone number (Step 3) under
   the same WABA — this becomes the production sending number.
2. Submit the app for App Review to request Advanced Access on
   `whatsapp_business_messaging` and `whatsapp_business_management` —
   required once messaging real end users, not just testers.
3. App Review requires two short screen recordings:
   - A message sent from your app and received in the actual WhatsApp
     client.
   - A template being created via your app (or WhatsApp Manager, if
     your app calls the API to do it).
4. Fill in required app metadata first: app icon, privacy policy URL,
   category — App Review won't proceed without these.

## 10. Conversation-Based Pricing
Meta bills per 24-hour conversation, not per message, split into
categories:
- Marketing — promotions, offers, discounts
- Utility — transactional/account updates (a lead alert to the client
  likely falls here)
- Authentication — OTPs/verification codes
- Service — free-form replies within a customer-initiated 24-hour
  window (a lead replying opens a free window — no per-conversation
  charge for replies inside it)

Rates vary by country/recipient. This is the concrete billing mechanism
behind CLAUDE.md's existing "WhatsApp Business API costs" Hard
Constraint exception (real, per-conversation usage cost, separate from
Claude API usage, client-funded, SEMRS never holds or moves that
payment) — check current rates before quoting a client, never assume
last year's numbers still hold, same "platform policy checks must be
current, not stale" discipline as everywhere else in this system.

## 11. Security Checklist Before Production
- [ ] Permanent access token stored in a secrets manager, never in code
      or client-side
- [ ] Webhook signature verification implemented (reject unsigned/
      invalid requests)
- [ ] Webhook endpoint uses valid HTTPS (not self-signed)
- [ ] System user has only the scopes it needs — not full Business
      Manager admin beyond what's listed in Step 2
- [ ] Token rotation plan in place even though expiry is set to Never
      (Meta can still revoke on suspicious activity)

## 12. Pre-Launch Testing Checklist
- [ ] Test number can send and receive with your webhook logging both
      directions
- [ ] Real phone number verified and added to the same WABA
- [ ] At least one template approved and successfully sent to a real
      (non-tester) number
- [ ] Webhook signature verification tested with a deliberately invalid
      signature (should reject)
- [ ] Business Verification approved
- [ ] App Review submitted and approved for Advanced Access
