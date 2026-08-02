# Message Log — Bright Leaf Coffee Roasters (DRY RUN — NOT A REAL ORDER)

Nothing in this file was actually sent — Bright Leaf Coffee Roasters is
fictional (see sample-request.md) and no real email/WhatsApp/dashboard
message went anywhere. Per Workflow Order, only the first two entries
below would genuinely have gone out at this point in a real run, since
CEO Order Approval was left PENDING (see
outputs/test-bright-leaf-coffee-roasters/order-approval-summary.md) —
everything after that is marked hypothetical, included only to check
that prompts/client-messages.md's templates actually fill in cleanly.

## Entry 1 (genuinely reachable at this stage)
- **Timestamp:** 2026-08-03 (simulated)
- **Stage:** Order received / Greeting
- **Channel:** Email — maya@brightleafroasters.example (fictional)
- **Message sent:** Template 1 from prompts/client-messages.md, filled:
  "We've received your order, Bright Leaf Coffee Roasters! ... Services:
  SEO, Content Writing, Copywriting. Channels: Website/Blog, Facebook,
  Instagram, Email. Goal: more local foot traffic and more online bean-
  subscription sign-ups this quarter. ..."

## Entry 2 (genuinely reachable at this stage)
- **Timestamp:** 2026-08-03 (simulated)
- **Stage:** Awaiting CEO order approval
- **Channel:** Email — maya@brightleafroasters.example (fictional)
- **Message sent:** Template 2 from prompts/client-messages.md, filled
  as-is (no client-specific fields needed).

## Entries 3+ (HYPOTHETICAL ONLY — order approval never actually granted)
These are included only to confirm the templates fill in without
missing fields, not because they were sent:

- **Stage:** Order approved / Work in progress → Template 3, filled
  with Goal field: "more local foot traffic and more online bean-
  subscription sign-ups this quarter."
- **Stage:** Work complete / Awaiting final CEO approval → Template 4,
  filled as-is.
- **Stage:** Delivered → Template 5 — NOT filled here, since Final
  Delivery Approval was also left PENDING and no package was ever
  compiled to link.
