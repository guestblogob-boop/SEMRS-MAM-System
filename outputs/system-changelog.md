# System Changelog

CEO-only internal record of changes to this system itself — new
agents, workflow edits, guardrail changes, template additions. Never
client-visible (see CLAUDE.md, Folder Structure). Append-only: never
edit or delete a past entry, only add new, separately dated ones (same
rule as CLAUDE.md, Security & Misuse Guardrails — "Append-only approval
and message records").

Entries below are backfilled from this repository's git history at the
point this changelog was created.

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
