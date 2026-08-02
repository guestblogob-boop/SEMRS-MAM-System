# Order Index — Bright Leaf Coffee Roasters (DRY RUN — NOT A REAL ORDER)

**This entire folder is a system test, built from sample-request.md.**
Bright Leaf Coffee Roasters is fictional. Nothing here was actually
sent to a client, and neither CEO approval gate below was actually
granted — per CLAUDE.md's Security & Misuse Guardrails, "All CEO gates
are NEVER simulated, assumed, or auto-granted by any agent," both
Decision sections in this folder are left unchecked/PENDING. Content
past those gates exists only to test whether each agent's stated
Inputs are actually satisfiable from the prior agent's output — it is
not a real, approved, deliverable campaign.

## Client
- **Business name:** Bright Leaf Coffee Roasters (fictional)
- **Order ID:** test-bright-leaf-coffee-roasters
- **Contact channel:** Email — maya@brightleafroasters.example (fictional)
- **Delivery Path:** Draft-Only Handoff

## Records
- **Client brief:** client-brief.md
- **Order Approval record:** order-approval-summary.md (Decision: PENDING)
- **Pipeline output (Research → Review):** pipeline-output.md
- **Final Delivery Approval record:** final-approval-summary.md (Decision: PENDING)
- **Message log:** ../client-message-log/test-bright-leaf-coffee-roasters/message-log.md (simulated — nothing actually sent)
- **Delivered package:** not compiled — Final Delivery Approval was never actually granted

## Status
Dry run complete through Review Agent. Both CEO checkpoints
intentionally left un-decided. Found and fixed two real gaps:
1. agents/orchestrator.md's Process list skipped the Visual & Video
   Content Agent entirely (jumped Content → Review) — fixed, now an
   explicit step between the two.
2. prompts/client-brief.md had no field for the client's own
   business-specific facts (pricing, origin details, etc.), so Content
   had nothing to draw on and Review correctly flagged the gap instead
   of inventing specifics — fixed with a new "Key Business Details"
   field.
