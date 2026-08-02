# Sample Client Request

A fictional client order for testing the system end-to-end — tracing
it through all 19 Workflow Order steps in CLAUDE.md. Not a real
engagement. Delete or replace once real orders start arriving through
the actual intake channel (see CLAUDE.md, Operational Policies —
"Order-intake verification").

## Order as received (defined SEMRS intake channel)

> From: Maya Odom (owner) <maya@brightleafroasters.example>
> Subject: Marketing help for Bright Leaf Coffee Roasters
>
> Hi SEMRS team,
>
> We're a small-batch coffee roaster and café — one physical location,
> plus online bean sales. We want more local customers finding us
> online and a more consistent social presence. We don't run ads right
> now and aren't ready to start.
>
> We'd like:
> - SEO for our website (we have a WordPress site but no blog yet)
> - Content writing — blog posts and email
> - Copywriting help for our website's About/Home copy
>
> Channels: our website/blog, Instagram, Facebook, and email
> (we have a small mailing list from in-café signups).
>
> Our brand voice is warm, a little playful, never corporate-sounding.
> Goal: more local foot traffic and more online bean subscription
> sign-ups over the next quarter.
>
> We'd rather review drafts ourselves and post them — we're not ready
> to hand over account access yet.
>
> Thanks,
> Maya

## Client meeting notes (as discussed and agreed)
- Confirmed by phone 2026-08-03 with Maya Odom, owner.
- Services agreed: SEO, Content Writing, Copywriting.
- Channels agreed: Website/Blog, Instagram, Facebook, Email.
- No ads management — explicitly declined for now.
- Delivery Path: Draft-Only Handoff (client publishes themselves;
  confirmed not ready for the Virtual Assistant / direct-publish
  opt-in).
- Tone: warm, a little playful, never corporate.
- Goal: more local foot traffic + more online bean-subscription
  sign-ups this quarter.
- No YMYL, no restricted-category content — straightforward local
  business.

## How to use this fixture
1. Orchestrator reads this file and fills in prompts/client-brief.md
   (Client Business Name: Bright Leaf Coffee Roasters; Services:
   SEO, Content Writing, Copywriting; Channels: Website/Blog,
   Instagram, Facebook, Email; Delivery Path: Draft-Only Handoff).
2. Proceed through CLAUDE.md's Workflow Order from step 1. No Ads
   Track applies (ads were explicitly declined) — the standard
   sequence only.
3. Use this fixture to sanity-check each handoff: does every agent
   actually receive what its "Inputs" section expects? Does the
   Review Agent have both content and visuals to check? Does the
   Orchestrator's Final Delivery Approval Summary have real content to
   summarize?
