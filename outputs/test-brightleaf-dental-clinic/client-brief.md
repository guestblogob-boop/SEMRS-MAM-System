# Client Brief

This brief is built by the Orchestrator from the incoming client order
and is the single shared input every agent reads. Do not begin any
specialist work until CEO Order Approval has been recorded (see
CLAUDE.md, Approval Gates).

**LESSON-PLAN DRY RUN — NOT A REAL ORDER.** BrightLeaf Dental Clinic is
the fictional sample brief from SEMRS-MAMS_Lesson-Plan.html, Section
11, used for Steps 9–12's testing. Nothing here was received through a
real, verified SEMRS intake channel.

## Client Business Name
BrightLeaf Dental Clinic

## Service(s) Ordered from SEMRS
Select all that apply:
- [x] SEO
- [ ] SEM / Ads Management
- [ ] GEO/AEM
- [ ] Link Building
- [x] Guest Posting
- [x] Content Writing
- [ ] Copywriting
- [ ] Authority Building
- [ ] AI Agent Services

Note: the order text was "SEO Content Writing + Guest Posting + Social
Management." "Social Management" isn't its own line item on this
checklist — mapped instead to the Channels in Scope below (Facebook,
Instagram, LinkedIn). Flagging this mapping rather than silently
guessing which checkbox it meant.

## Target Audience
Local patients searching for dental care online

## Goal
Increase organic website traffic, local search rankings, and
appointment bookings

## Key Business Details
Not available in the test brief — no city, specific treatment list
beyond general "dental care," staff/dentist names, or certifications
were given. Flagged at every downstream step (Content Agent, Review
Agent) rather than fabricated; see pipeline-output.md.

## Channels in Scope
Select all that apply — no agent may draft or publish to a channel not
checked here:
- [x] Website/Blog
- [x] Facebook
- [x] Instagram
- [ ] Twitter/X
- [ ] TikTok
- [ ] Reddit
- [ ] Pinterest
- [x] LinkedIn
- [ ] YouTube
- [x] WhatsApp
- [x] Email

## Tone
Warm, professional, reassuring

## Delivery Path
Select one (see CLAUDE.md, Delivery Model):
- [x] Draft-Only Handoff (default) — client publishes the approved
      content themselves
- [ ] SEMRS as Virtual Assistant (opt-in) — client grants scoped
      platform access (never a raw password) and SEMRS publishes
      directly per the agreed upload/posting plan

Defaulted to Draft-Only Handoff — no opt-in was indicated anywhere in
the test brief.

## Client Contact Channel
Not specified in the test brief — no contact name, email, or WhatsApp
number was given. Left blank rather than invented; a real order would
need this before the Client Communication Agent could actually reach
anyone.

Select one:
- [ ] Email — client's address:
- [ ] WhatsApp — client's number:

## SEMRS Commission Rate
Not applicable — SEM/Ads Management was not selected above.

## Content Ownership/Confidentiality Notes
None — standard SEMRS policy applies (see CLAUDE.md, Operational
Policies).
