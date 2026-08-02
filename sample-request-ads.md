# Sample Client Request — Ads-Scoped Order

A second fictional client order, specifically to test the Ads Track
(CLAUDE.md's Ads Track section, plus agents/ads-agent.md and
prompts/budget-approval-summary.md) end-to-end. Not a real engagement.
sample-request.md (Bright Leaf Coffee Roasters) explicitly declined
ads, so this is a separate fixture rather than retconning that one.

## Order as received (defined SEMRS intake channel)

> From: Deshawn Carter (owner) <deshawn@riversideplumbing.example>
> Subject: SEO + Google Ads for Riverside Plumbing & Drain
>
> Hi SEMRS team,
>
> We're a local plumbing company — emergency calls plus scheduled
> work (drain cleaning, water heater installs, etc.). We want more
> emergency calls coming in, and steadier scheduled bookings.
>
> We'd like:
> - SEO for our website
> - Google Ads management — we've never run ads before, want to start
>   modest and see what works
>
> We're not ready for social ads yet, just Google to start. We have a
> website and a Facebook page already.
>
> For the organic side we'd like to review drafts before anything goes
> up — we're not ready to hand over our website/Facebook access. For
> the ads side, we understand you'll need official access to manage
> the Google Ads account once we agree on a budget.
>
> Thanks,
> Deshawn

## Client meeting notes (as discussed and agreed)
- Confirmed by phone 2026-08-10 with Deshawn Carter, owner.
- Services agreed: SEO, SEM/Ads Management (Google Ads only, no social
  ads for now).
- Organic channels agreed: Website/Blog, Facebook.
- Delivery Path (organic): Draft-Only Handoff.
- Ads: client understands official Google Ads Manager Account access
  is required before launch, once budget is approved — separate from
  the organic Delivery Path choice.
- Tone: straightforward, trustworthy, no-nonsense — no hard-sell
  language.
- Goal: more emergency calls this month, steadier scheduled bookings
  over time.
- Budget-conscious — wants to start modest and see results before
  scaling.
- Key business details: 24/7 emergency availability, licensed and
  insured, serves the Riverside metro area only (not statewide).

## How to use this fixture
1. Orchestrator fills prompts/client-brief.md (organic side) as usual.
2. Ads Agent runs in parallel with Research once Order Approval is
   recorded (Ads Track, step A) — check that its own process (policy
   check, targeting, budget/commission proposal) actually works using
   only what this order provides.
3. Check whether the Budget & Campaign Approval Summary has everything
   it needs without inventing figures the client never gave.
