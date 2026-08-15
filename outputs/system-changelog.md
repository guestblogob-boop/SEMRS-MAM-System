# System Changelog

CEO-only internal record of changes to this system itself — new
agents, workflow edits, guardrail changes, template additions. Never
client-visible (see CLAUDE.md, Folder Structure). Append-only: never
edit or delete a past entry, only add new, separately dated ones (same
rule as CLAUDE.md, Security & Misuse Guardrails — "Append-only approval
and message records").

Entries below are backfilled from this repository's git history at the
point this changelog was created.

## 2026-08-15 (WordPress decision-identity label renamed to match)
- The CEO renamed semrs.com's real WordPress user account (the one
  whose Application Password authenticates every direct-publish and
  staff-dashboard action) from "SEMRS Dashboard" to "SEMRS OS," per
  explicit instruction, following the same-day system rename below.
  Updated the 5 code locations that default the dashboard's "Decided
  by"/"Entered by"/"Attempted by" fields to that real username
  (`components/dashboard/RecordApprovalForm.tsx`,
  `RecordBriefApprovalForm.tsx`, `RecordPaymentForm.tsx`,
  `ChannelDrafts.tsx` ×2) to match, plus CLAUDE.md's "Standing
  decision-identity label" section describing them. These were
  deliberately left untouched during the same-day system rename below
  until the real WordPress account was confirmed renamed too — renaming
  the label without the real account would have misrepresented which
  account actually authenticates, per this same section's own stated
  reasoning.

## 2026-08-15 (System renamed to SEMRS OS; CEO correspondence address changed)
- Permanently renamed the system's official identity from "SEMRS
  AISMMA — AI Social Media Marketing Agency" to "SEMRS OS — AI Social
  Media Marketing Agency," per explicit instruction. Every live
  reference to "SEMRS AISMMA" / "AISMMA" was updated to "SEMRS OS":
  CLAUDE.md (System Identity, Project Purpose's "(AISMMA)"
  parenthetical, Agent Roles, both Mermaid diagrams), README.md,
  agents/orchestrator.md (title and Role section), and docs/org-chart.md
  (intro text and Mermaid diagram). The Orchestrator's display name is
  now "SEMRS OS Orchestrator" (Managing Director); "the Orchestrator"
  remains the shorthand used throughout both documents' prose,
  unchanged — same non-full-find-replace approach used for the prior
  2026-08-11 identity formalization entry below. Historical entries in
  this changelog that describe the prior "SEMRS AISMMA"/"AISMMA" name
  are left as-is, per this file's own append-only rule.
- Permanently changed the CEO Correspondence Channel address from
  admin@semrs.com to purfits@gmail.com, per explicit instruction.
  Updated everywhere it appeared: CLAUDE.md (Delivery Model's Path 1
  hand-off, CEO Correspondence Channel, Client Contact Channel's
  distinction from the client-facing address, Output Format) and
  prompts/client-brief.md (Client Contact Channel). This address stays
  internal-only (Orchestrator↔CEO traffic), distinct from the
  client-facing guestblogob@gmail.com address, unchanged by this
  update.

## 2026-08-11 (Product listing copy)
- Added product listing copy (title/description/tags for a product an
  e-commerce client already sells) as a Content Agent deliverable, per
  explicit instruction — most relevant when paired with SEM/Ads
  Management, since paid ad traffic needs a real product page to land
  on. Deliberately narrow: copy only. Explicitly declined and
  permanently excluded in the same pass, per the CEO's own fallback
  rule ("if not related to our system, go for option 1" — no
  restructuring): platform listing/publishing integration (Shopify/Etsy
  API work) and product research/sourcing/"winning product" strategy
  advisory (deciding what a client should sell) — both a different
  business line (e-commerce operations/consulting) from marketing a
  client's existing offer, and both would have required a new Web
  Development department that was considered and declined this same
  session.

## 2026-08-11 (Official system identity)
- Formalized the system's official identity, per explicit instruction:
  name "SEMRS AISMMA — AI Social Media Marketing Agency," owner SEMRS,
  human authority the SEMRS CEO, primary AI controller the AISMMA
  Orchestrator (Managing Director). Added a new "System Identity"
  section to CLAUDE.md stating this explicitly. Renamed the
  Orchestrator's formal title from "Marketing Director" to "Managing
  Director" and its display name to "AISMMA Orchestrator"
  (agents/orchestrator.md's title, both CLAUDE.md Mermaid diagrams,
  docs/org-chart.md's Mermaid diagram and Notes, README.md). "The
  Orchestrator" remains the shorthand used throughout the rest of both
  documents' prose — not a full find-replace, since the role is
  unchanged, only its formal name/title.
- Not implemented from the accompanying example flowchart: a "Teams"
  restructuring (Research/Strategy/Audit Teams → Specialist Teams:
  Content/Social/SEO/YouTube/Web-Ecom). This doesn't map onto the real,
  built agent roster — no Audit agent exists, YouTube is a channel
  under the Social Content Draft Agent rather than a standalone team,
  and "Web/Ecom" would be new scope beyond the SMMA-only positioning
  just reconfirmed. Flagged to the CEO as a real decision rather than
  silently reshaping the agent roster to fit an illustrative diagram.

## 2026-08-11 (Reddit removed)
- Removed Reddit as a supported channel entirely, per explicit
  instruction — no longer in CLAUDE.md's Channels Supported, the
  client brief's Channels in Scope checklist, the Social Content Draft
  Agent's channel list, the Visual & Video Content Agent's per-channel
  visual guidance, or semrs.com's own linked self-marketing platforms.
  In SEMRS-Dashboard: removed from `CHANNEL_OPTIONS`, its
  `lib/directPublishHelp.ts` walkthrough entry, and its
  `lib/publisherFields.ts` credential schema. Website/Blog's WordPress
  Application Password walkthrough was explicitly confirmed untouched
  and permanent throughout this pass — it stays required for direct
  publish access on the client's own site, never in scope for removal.

## 2026-08-11 (Content Agent — speeches/lectures/scripts)
- Added speeches, lectures, and scripts as a Content Agent deliverable
  format (agents/content-agent.md, CLAUDE.md's Deliverable Formats) —
  scoped strictly to this client's own speakers (an executive, founder,
  or presenter representing the client's business, e.g. a keynote or
  conference talk). Explicitly declined and permanently excluded, per
  direct instruction and independent judgment: any academic work a
  student would submit as their own (theses, essays, dissertations,
  homework, exam answers) — this is academic ghostwriting/contract
  cheating, a real integrity and (in some jurisdictions) legal issue,
  and also doesn't fit this system's SMMA-only positioning (a business
  client ordering marketing work, not an individual student). Recorded
  as a hard Constraint on the Content Agent, not just a scoping note,
  so it can't be reinterpreted later by request framing.

## 2026-08-10 (Conversion service)
- Added "Conversion" as its own client-orderable service, distinct
  from Lead Generation per explicit instruction: Conversion is the
  cross-channel measurement/optimization service — the Analytics
  Agent assembles and calculates conversion performance across organic
  content, social platforms, ads, and landing pages together, using
  this client's own definition of what counts as a conversion (a
  captured lead, a sale, a booking, a sign-up). Lead Generation stays
  the separate operational capture-and-AI-qualify track; a client can
  order either without the other. Added CLAUDE.md's "What 'Conversion'
  means" section, a "Conversion Definition" section on the client
  brief, and a "Conversion Integration" duty on the Analytics, Content,
  and Ads Campaign agents (the latter two carry the same trackable-tag
  discipline as their existing Lead Gen Integration duties, so a
  conversion can be attributed back to the exact piece/campaign that
  produced it).

## 2026-08-10 (repositioning)
- Repositioned the system as an AI Social Media Marketing Agency
  (AISMMA), per explicit instruction: SEMRS sells SMMA services, not a
  full-service SEO/link-building shop. Removed "Link Building," "Guest
  Posting," "Authority Building," and "AI Agent Services" from the
  client-orderable Service(s) Ordered checklist (prompts/client-brief.md)
  and from CLAUDE.md's Project Purpose. Added "Social Media Management"
  and "Analytics & Reporting" as explicit orderable categories — these
  were already real agent work (Content/Social Draft agents; Analytics
  Agent) but not previously named as their own catalog line items. Kept
  SEO, GEO/AEM, Content Writing, Copywriting, Lead Generation, and the
  Website/Blog channel — all confirmed still in scope. The "No
  manipulative SEO/link-building tactics" guardrail stays, reframed as
  applying to SEMRS's own self-marketing use of guest posting/link
  building (semrs.com's own growth, Self-Marketing Track — untouched by
  this change) rather than to a client-facing service.
- SEMRS-Dashboard: removed guest-post-tier and link-building pricing
  from the actual live quotation catalog (`data/pricingCatalog.ts`,
  `lib/pricingCalculator.ts`, both Bundle Builder/public pricing UI
  components) to match — the real "FINAL pricing" document's guest post
  and link building line items are no longer sold.

## 2026-08-10
- Added Lead Generation as a full track: two new agents (Lead Capture
  Agent, Qualification + AI Sales Agent — agents/lead-capture-agent.md,
  agents/qualification-sales-agent.md), a new Lead Generation Track in
  CLAUDE.md (ongoing/reactive once channels are live, not part of the
  one-time drafting pipeline), Lead Gen Integration duties added to
  Content, Ads Campaign, and Analytics agents, new Security & Misuse
  Guardrails (lead PII as a narrow exception to "no personal data
  collection," webhook signature verification, human-in-the-loop for
  binding commitments, escalation audit trail), a client-funded
  exception for real WhatsApp Business API costs (Hard Constraint),
  and new client-brief fields (qualification criteria, brand voice for
  AI sales, escalation rules, a separate AI-led-sales opt-in distinct
  from the general Virtual Assistant path). Org chart count moves from
  15 agents/6 departments to 17 agents/7 departments (docs/org-chart.md
  and both CLAUDE.md Mermaid diagrams updated to match). No new CEO
  approval gate introduced — Lead Generation is authorized by the
  existing Order Approval Checkpoint plus the client's own explicit
  opt-in fields, the same pattern already used for the Virtual
  Assistant delivery path.
- Not adopted from the source spec this was built from: a tiered SaaS
  subscription/billing model (Starter/Growth/Pro/Agency, Stripe
  self-serve) — this is a business-model decision distinct from the
  technical addition above, and conflicts with this system's current
  per-order Bundle Builder pricing; flagged to the CEO rather than
  silently adopted.

## 2026-08-09
- Added Google Business Profile to Channels Supported (now twelve
  channels, not eleven). Found, not invented: SEMRS-Dashboard's pricing
  catalog already sells it ("gmb," part of the Bundle Builder's organic
  channel tiers) with no workflow-channel equivalent — a real mismatch
  between what's sold and what the agent pipeline can be scoped to,
  closed rather than left silently inconsistent.
- SEMRS-Dashboard: built real live-publish integrations for Instagram
  (Graph API container-then-publish flow, same Meta Business Manager
  access mechanism as Facebook) and LinkedIn (UGC Posts API, LinkedIn
  Developer Portal OAuth token). Both join Website/Blog and Facebook as
  channels with genuine, working publish actions — Twitter/X, TikTok,
  Reddit, Pinterest, YouTube, and Google Business Profile still have
  real walkthroughs and credential schemas but no live-publish code
  yet, on purpose.
- SEMRS-Dashboard: the Client Portal now has a real "Connect Your
  Accounts" section for Virtual-Assistant clients, showing each
  in-scope channel's real access walkthrough directly to the client
  (not just buried in the internal staff dashboard) and letting the
  client paste their own access credential into an encrypted form
  themselves — never emailed/WhatsApped as plaintext for staff to
  paste in. Found the same gap already existed for the Ads Client Help
  guide (prompts/client-help-meta-ads-integration.md) — written to be
  shown to the client but never actually wired into the app; not fixed
  in this pass, flagged for later.

## 2026-08-08
- Added the "SEMRS Dashboard" standing decision-identity label
  (CLAUDE.md, Operational Policies) — confirmed by the CEO after being
  asked whether it fits the append-only audit-trail requirement, and
  renamed from an initial placeholder ("SEMRS-DB") to match the actual
  real WordPress user account semrs.com's Application Password
  credential authenticates as, so the label names a genuine account
  rather than an arbitrary tag. All dashboard "Decided by"/"Entered
  by"/"Attempted by" fields (Order, Final Delivery, Budget & Campaign,
  and Self-Marketing Approval; Channel Draft entry; Publish actions)
  now default to "SEMRS Dashboard" for both client work and
  self-marketing work, since the real accountability boundary is
  control of the authenticated dashboard session itself, not the
  free-text name. A real human still has to click the decision/action
  button — nothing here simulates or auto-grants a CEO gate.
- Established the standing content-production template applied to
  semrs.com's own blog posts going forward: title as H1, an SEO title
  sized to Rank Math's ~50-60 character guidance with the focus
  keyword up front, a header image after the intro, a second image
  after the first H2, a third image at the ~500-600 word mark (mixing
  licensed stock sourcing with free-tier AI generation per
  agents/visual-agent.md), and both internal links (to real existing
  semrs.com pages) and external links (to the real sources any cited
  data comes from) with descriptive anchor text. Applied for the first
  time to the two self-marketing posts "Euro Market SEO: Why One
  Campaign for 20 Countries Fails" and "Guest Posting Service: What to
  Look For (2026 Guide)."

## 2026-08-07
- Made the front-office division of labor explicit and permanent in
  CLAUDE.md's Agent Roles: the Client Communication Agent works
  exclusively with real, paying clients, forever; the SEMRS
  Communicator Agent works exclusively on semrs.com's own
  self-marketing, forever; every other agent applies the same job
  description and compliance bar to both, undifferentiated. Mirrored
  into agents/client-communication-agent.md, agents/
  semrs-communicator-agent.md, and agents/orchestrator.md's Constraints
  and Context sections.
- Gave the Visual & Video Content Agent a real generation capability,
  not just curation: it may now generate images, video, icons, GIFs,
  and data visualizations (charts/graphs/trend lines/tables) directly
  with a free-tier AI model (ChatGPT, Claude, Gemini, Grok, or
  equivalent — never a paid tier by default, same Hard Constraint as
  everywhere else), in addition to sourcing from licensed stock/CC
  sites. Added a "Prompt-Engineering Toolkit" to agents/visual-agent.md
  — SEMRS's own internal set of prompt modifiers (explore, deep
  research, humanize, simplify, deepen analysis, stress-test, generate
  alternatives, assign a persona, few-shot, negative-prompt, specify
  format, self-critique, style-reference, brand-check, flag unverified
  claims) the agent applies when constructing its own generation
  prompts. The existing no-real-people/no-copyrighted-IP restriction
  and the never-fabricate-data rule both apply with equal force to
  generated output, not just sourced media. Updated CLAUDE.md's Agent
  Roles, Security & Misuse Guardrails, and Deliverable Formats sections
  to match.

## 2026-08-02
- Extended the free-tools-only rule (CLAUDE.md, Hard Constraint) to
  cover client work, with an explicit exception when a client requests
  and pays for a paid tool themselves.
- Added a free-only standing rule to the Self-Marketing Track.
- Added the self-marketing approval summary template
  (prompts/self-marketing-approval-summary.md), closing the last gap
  in the four-gate approval template pattern.
- Expanded CLAUDE.md's Folder Structure into a full annotated file
  tree.
- Added an organizational chart, a departmental chart, and a workflow
  diagram (all Mermaid) to CLAUDE.md; reframed the Delivery Model as
  an explicit client choice between Draft-Only Handoff and SEMRS as
  Virtual Assistant.
- Renamed "Orchestrator" to "managing director" in client-facing text
  only (internal references unchanged).
- Added the client message templates (prompts/client-messages.md).
- Added the budget & campaign, final delivery, and order approval
  summary templates.
- Added the client brief template (prompts/client-brief.md) and
  recognized "AI Agent Services" as an orderable category in CLAUDE.md.

## 2026-08-01
- Initialized the SEMRS multi-agent marketing system project
  (README.md, CLAUDE.md).
- Added all 15 agent job descriptions (Orchestrator, Client
  Communication, Research, SEO & GEO, Strategy, Content, Visual &
  Video Content, Review, Website/Blog Draft, Social Content Draft,
  WhatsApp Draft, Email Draft, Analytics, Ads Campaign, SEMRS
  Communicator).
- Fixed a garbled step and a nonexistent "Publishing Agent" reference
  in the Orchestrator's process.
- Fixed broken numeric cross-references in CLAUDE.md's Security &
  Misuse Guardrails, and a dangling "Section 21" reference in the
  SEMRS Communicator agent.
- Added .gitignore for Office lock files.
