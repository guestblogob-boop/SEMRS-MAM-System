# SEMRS MAM System

SEMRS's own multi-agent marketing system — an AI Social Media Marketing Agency (AISMMA) — used internally to do marketing work on behalf of SEMRS's clients across website, social, WhatsApp, and email channels. Services are scoped to SMMA work (SEO, ads, GEO/AEM, content creation, copywriting, social media management, analytics & reporting, lead generation through to conversion) — guest posting, link building, generic "authority building," and "AI Agent Services" are not sold as client services (see CLAUDE.md, Project Purpose).

Clients place orders — they don't operate the system themselves. No work starts until the CEO approves the order, and nothing ships until the CEO gives final delivery approval. The client is kept informed at every stage in between.

## Lead Generation + AI Sales

Extends the Content, Ads Campaign, and Analytics agents with automatic lead handling, for orders that select Lead Generation as a service:

1. Leads are captured from ads, website forms, and organic channels into one attributed record per lead, tagged by the exact content piece or campaign that produced it (see [agents/lead-capture-agent.md](agents/lead-capture-agent.md)).
2. If, and only if, the client has separately opted in to AI-led WhatsApp sales conversations, an AI agent qualifies each lead, diagnoses their need, and either books a meeting or escalates to a human rep — it never finalizes pricing, contracts, or any other binding commitment itself (see [agents/qualification-sales-agent.md](agents/qualification-sales-agent.md)).
3. The Analytics Agent reports full-funnel performance — leads generated per content piece/ad, qualification rate, meetings booked, and (once the client reports it) close rate.

See [CLAUDE.md](CLAUDE.md), "Lead Generation Track," for the full flow, guardrails, and approval boundaries.
