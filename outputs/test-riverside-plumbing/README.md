# Order Index — Riverside Plumbing & Drain (DRY RUN — NOT A REAL ORDER)

**This entire folder is a system test, built from sample-request-ads.md**,
specifically to exercise the Ads Track (untested until now). Riverside
Plumbing & Drain is fictional. Nothing here was actually sent to a
client, no real Google Ads account was accessed, and neither CEO
approval gate below was actually granted — per CLAUDE.md's Security &
Misuse Guardrails, "All CEO gates are NEVER simulated, assumed, or
auto-granted by any agent," both Decision sections in this folder are
left unchecked/PENDING.

## Client
- **Business name:** Riverside Plumbing & Drain (fictional)
- **Order ID:** test-riverside-plumbing
- **Services:** SEO, SEM/Ads Management (Google Ads only)
- **Organic channels:** Website/Blog, Facebook
- **Delivery Path (organic):** Draft-Only Handoff

## Records
- **Client brief:** client-brief.md
- **Order Approval record:** order-approval-summary.md (Decision: PENDING)
- **Ads campaign proposal (Ads Agent, steps 1–7):** ads-campaign-proposal.md
- **Budget & Campaign Approval record:** budget-approval-summary.md (Decision: PENDING)

## Status
Ads Track dry run complete through the Budget & Campaign Approval
Summary (Ads Track step D). Both CEO checkpoints intentionally left
un-decided. Organic pipeline (Research → ... → Review) not re-run here
— already validated by outputs/test-bright-leaf-coffee-roasters/; this
fixture focuses specifically on the ads-only mechanics.

Found and fixed one real gap: SEMRS's commission rate was never
captured anywhere in the system, even though ads-agent.md requires it
and CLAUDE.md's Paid Media Model requires it shown as a line item on
every budget proposal. Fixed with a default rate (15% of ad spend,
$150/month minimum) in CLAUDE.md's Paid Media Model, plus a per-client
"SEMRS Commission Rate" field in prompts/client-brief.md. Confirmed
fixed in this fixture — see ads-campaign-proposal.md and
budget-approval-summary.md, both updated to show the resolved
$150/month commission (the minimum-fee floor correctly applying on a
small illustrative $300/month test budget).
