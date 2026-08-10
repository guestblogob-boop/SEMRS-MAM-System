# System Changelog

CEO-only internal record of changes to this system itself — new
agents, workflow edits, guardrail changes, template additions. Never
client-visible (see CLAUDE.md, Folder Structure). Append-only: never
edit or delete a past entry, only add new, separately dated ones (same
rule as CLAUDE.md, Security & Misuse Guardrails — "Append-only approval
and message records").

Entries below are backfilled from this repository's git history at the
point this changelog was created.

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
