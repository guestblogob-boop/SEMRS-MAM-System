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
- [ ] Reddit
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


## Content Ownership/Confidentiality Notes
Any exceptions to SEMRS's standard policy (see CLAUDE.md, Operational
Policies — "Content ownership & confidentiality"). Leave blank if none.


## Lead Generation Details
Only fill in if Lead Generation was selected above (see CLAUDE.md,
Lead Generation Track, and agents/lead-capture-agent.md /
agents/qualification-sales-agent.md). Leave entirely blank otherwise.

**Lead capture channels in scope** — which in-scope channels above
will actually carry lead-capture CTAs (website form, WhatsApp
click-to-chat, platform-native ad lead forms):


**Qualification Criteria** — the real questions/signals that make a
lead hot, warm, or cold for this specific client's business. Must come
from the actual client meeting, not invented:


**Brand Voice/Tone for AI Sales Conversations** — how this client
wants an AI-led WhatsApp conversation to sound. May match the general
Tone field above, or be more specific to sales conversations:


**Escalation Rules** — when a lead should be handed to a human rep
instead of continuing with the AI agent, and who that human rep is:


**AI-Led WhatsApp Sales Agent — Enabled?**
Select one. This is a separate, stricter opt-in than the general
"SEMRS as Virtual Assistant" delivery path above — selecting Virtual
Assistant does NOT by itself authorize an AI agent to hold live sales
conversations with this client's leads (see
agents/qualification-sales-agent.md, Constraints):
- [ ] Yes — client has been briefed on what this means and explicitly
      requested it
- [ ] No — leads are captured and recorded, but qualification/outreach
      is handled by the client's own team

Note: even when enabled here, the Qualification + AI Sales Agent still
requires a separate, documented WhatsApp opt-in from each individual
lead before messaging them (see CLAUDE.md, Security & Misuse
Guardrails, "Email/WhatsApp compliance requirements") — this checkbox
authorizes SEMRS to run the agent for this client; it does not
substitute for a lead's own consent.

