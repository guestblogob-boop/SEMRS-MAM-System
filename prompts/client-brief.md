# Client Brief

This brief is built by the Orchestrator from the incoming client order
and is the single shared input every agent reads. Do not begin any
specialist work until CEO Order Approval has been recorded (see
CLAUDE.md, Approval Gates).

## Client Business Name


## Service(s) Ordered from SEMRS
SMMA services only (see CLAUDE.md, Project Purpose — SEMRS positions
itself as a social media marketing agency, not a full-service
SEO/link-building shop). Select all that apply:
- [ ] SEO
- [ ] SEM / Ads Management
- [ ] GEO/AEM
- [ ] Content Writing
- [ ] Copywriting
- [ ] Social Media Management
- [ ] Analytics & Reporting
- [ ] Lead Generation
- [ ] Conversion

## Target Audience


## Goal


## Key Business Details
Specific, real facts about this client's actual business — pricing,
exact offerings, unique story/origin, certifications, notable specifics
— that the Content Agent needs to avoid generic filler (see
agents/content-agent.md, Constraints, and CLAUDE.md, Security & Misuse
Guardrails, "Content quality and Google-penalty avoidance" — genuine
E-E-A-T signals specific to this client). The Research Agent covers
market/competitor/audience research, not these — this section must be
filled from the actual client order or meeting, not invented. If a
detail isn't available yet, leave it blank rather than guessing; the
Content Agent should flag the gap rather than fabricate a specific.


## Channels in Scope
Select all that apply — no agent may draft or publish to a channel not
checked here:
- [ ] Website/Blog
- [ ] Facebook
- [ ] Instagram
- [ ] Twitter/X
- [ ] TikTok
- [ ] Pinterest
- [ ] LinkedIn
- [ ] YouTube
- [ ] WhatsApp
- [ ] Email

## Tone


## Delivery Path
Select one (see CLAUDE.md, Delivery Model):
- [ ] Draft-Only Handoff (default) — client publishes the approved
      content themselves
- [ ] SEMRS as Virtual Assistant (opt-in) — client grants scoped
      platform access (never a raw password) and SEMRS publishes
      directly per the agreed upload/posting plan

If SEMRS as Virtual Assistant is selected, note the client's granted
access per platform here once provided:


## Client Contact Channel
How the client wants to receive status updates and the final package
(see CLAUDE.md, Client Contact Channel). SEMRS reaches the client from
its own dedicated client-facing identity (guestblogob@gmail.com /
WhatsApp) — separate from admin@semrs.com, which stays internal-only —
branded as "SEMRS" so the client sees the business name only, never a
bare address or phone number. The Client Portal/dashboard is the
preferred two-way channel; email/WhatsApp are the fallback.

Select one:
- [ ] Email — client's address:
- [ ] WhatsApp — client's number:

## SEMRS Commission Rate
Ads-scoped orders only (leave blank if SEM/Ads Management wasn't
selected above). SEMRS's standard rate is 15% of monthly ad spend PER
PLATFORM, calculated separately per platform (never blended across a
client's combined spend), with a $30/month minimum fee per platform
(see CLAUDE.md, Paid Media Model). Record the actual agreed rate for
this client here, and which platform(s) are in scope — defaults to
the standard rate unless the CEO has negotiated something different:


## Conversion & Lead Generation Pricing
Only fill in if Conversion and/or Lead Generation was selected above
(see CLAUDE.md, "Conversion & Lead Generation Pricing Model"). Note
which onboarding path this is:
- [ ] Phase 2 upsell — client already has an active organic/paid
      engagement with SEMRS
- [ ] Standalone — Conversion &/or Lead Generation is this client's
      only purchase (see CLAUDE.md, "Onboarding a Conversion & Lead
      Generation-Only Client")

The Plan — $249/month: Conversion tracking, Lead Generation, and the
AI-Led WhatsApp Sales Agent, all included. (A percentage/success-fee
alternative was considered and rejected — it depended on the client
self-reporting closed deals with no way for SEMRS to verify them; see
CLAUDE.md.)
Billing: [ ] Monthly  [ ] Annual ($2,490/year — pay 10 months, get 12)

Analytics & Reporting is included free — never a separate line item.

**WhatsApp Business number** — gate before onboarding proceeds: the
client will use their own **Meta-verified** WhatsApp Business number to
message and close leads themselves — never a SEMRS-owned one and never
an unverified number (see CLAUDE.md, "Conversion & Lead Generation
Pricing Model," for why verification is required, not optional). SEMRS
does not need any access to this number — record it only so it can be
confirmed verified:

- [ ] Number confirmed Meta-verified (if not yet verified, that's the
      client's first task — do not proceed until it is)


## Content Ownership/Confidentiality Notes
Any exceptions to SEMRS's standard policy (see CLAUDE.md, Operational
Policies — "Content ownership & confidentiality"). Leave blank if none.


## Conversion Definition
Only fill in if Conversion was selected above (see CLAUDE.md, "What
'Conversion' means," and agents/analytics-agent.md's Conversion
Integration duty). Independent of whether Lead Generation is also
selected — Conversion is the cross-channel measurement/optimization
service; Lead Generation is the operational capture-and-AI-qualify
track. A client can order one without the other.

**What counts as a conversion for this client** — a captured lead, a
sale, a booking, a sign-up, a download, whatever this client's actual
goal defines it as. Must come from the actual client meeting, not
assumed:


**Landing pages in scope for conversion tracking** — which specific
page(s) conversion is being measured against (see Website/Blog Draft
Agent, Deliverable Formats, for landing page drafting):


## Lead Generation Details
Only fill in if Lead Generation was selected above (see CLAUDE.md,
Lead Generation Track, and agents/lead-capture-agent.md /
agents/qualification-sales-agent.md). Leave entirely blank otherwise.

**Lead capture channels in scope** — which in-scope channels above
will actually carry lead-capture CTAs (website form, WhatsApp
click-to-chat, platform-native ad lead forms):


**Qualification Criteria** — the real questions/signals that make a
lead HOT, WARM, or COLD for this specific client's business, based on
what the capture form/CTA actually collects (the Qualification + AI
Sales Agent scores from this data only — it never holds a conversation
with the lead to find out more; see agents/qualification-sales-agent.md).
Must come from the actual client meeting, not invented:


**Notification Preferences** — how the client wants to be instantly
alerted the moment a new lead is captured and scored (see CLAUDE.md,
Lead Generation Track, step C — this happens automatically, with no
delay, for every Lead Generation client; there is no separate opt-in
for it):
- [x] Email — always on, free, default channel. Client's address to
      send alerts and the CSV/Excel lead report to:
- [ ] WhatsApp (optional add-on, not a replacement for email) — only
      if the client specifically wants it and understands it may carry
      a small real Meta conversation cost (see CLAUDE.md, Hard
      Constraint, "WhatsApp Business API costs"). Client's number:

**Lead Report Cadence** — how often the full CSV/Excel lead report
(every captured lead's name, phone, WhatsApp, email, score, remark,
source, and capture date) is emailed, on top of the instant per-lead
alert above. Also available on demand from the Client Portal:
- [ ] Daily  [ ] Weekly  [ ] Monthly

**Who follows up with the lead** — always the client's own team, on
the client's own WhatsApp Business number (see "WhatsApp Business
number," above). This system never messages, calls, or otherwise
contacts a lead directly, with no exception (see
agents/qualification-sales-agent.md, Constraints) — record here only if
this client has a specific internal process (e.g. a named team member,
a response-time target) worth noting for context:

