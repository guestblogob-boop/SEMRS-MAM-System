# System Changelog

CEO-only internal record of changes to this system itself — new
agents, workflow edits, guardrail changes, template additions. Never
client-visible (see CLAUDE.md, Folder Structure). Append-only: never
edit or delete a past entry, only add new, separately dated ones (same
rule as CLAUDE.md, Security & Misuse Guardrails — "Append-only approval
and message records").

Entries below are backfilled from this repository's git history at the
point this changelog was created.

## 2026-08-20 (VA Service Fee reference pricing; Conversion/LeadGen exclusions spelled out)
- Per explicit instruction, the Virtual Assistant Service Fee (Delivery
  Model, "Path 2") now has real starting reference pricing instead of
  "no standard default rate established yet": Option 1, a flat
  $500/mo covering every channel in scope; Option 2, a per-channel
  rate set equal to that channel's own existing content price (not a
  new invented number, per explicit instruction — "according to
  platform charges") — Blog $69/mo, Facebook/Instagram/LinkedIn/X/
  Pinterest $15/mo, TikTok/YouTube $25/mo, Google Business Profile
  $10/mo. Same "starting default, CEO confirms per client" treatment
  as the Ads Commission Rate — doesn't replace the per-client
  `virtualAssistantFee` record on the brief. Shown on the real public
  pricing page for the first time (`data/pricingCatalog.ts` →
  `virtualAssistant`, `components/pricing/PricingTable.tsx`).
- Per explicit instruction, also spelled out unambiguously that the
  $249/mo Conversion & Lead Generation plan charges for Conversion
  tracking, Lead Generation, and Sales Agent qualification ALONE —
  Social/organic channels, Blog, SEO, and Ads are never included and
  always stay separately charged, whether bought before, after, or
  alongside this plan. Also clarified the two different reasons
  Analytics & Reporting is free either way (already a Phase 2
  client's standing duty vs. baked into the $249 for a standalone
  client) — this reasoning already existed in CLAUDE.md but wasn't
  reflected on the actual pricing page copy until now.
- Verified live on the real `/pricing` page.

## 2026-08-20 (Conversion & Lead Generation: standalone-price clarification)
- Per a user-flagged gap ("Lead Generation price not included in
  pricing page"): investigated live and confirmed the combined
  "Conversion & Lead Generation" $249/mo plan does render on the
  public pricing page and does mention Lead Generation — but nowhere
  stated whether ordering just Lead Generation, or just Conversion,
  alone costs less, which is a real ambiguity given this document
  explicitly allows ordering either one alone (see "What 'Conversion'
  means," above).
- Confirmed with the business owner: this is a flat price either way,
  by deliberate design — not a missing standalone tier. Added a
  clarifying sentence to CLAUDE.md itself (see "What 'Conversion'
  means") and a matching callout on the real pricing page
  (`conversionLeadGen.standaloneNote` in SEMRS-Dashboard's
  `data/pricingCatalog.ts`, rendered in `PricingTable.tsx`) so this
  is unambiguous everywhere a client or staff member might read it.

## 2026-08-20 (VA Clients moved to its own dedicated page)
- Per explicit instruction, the VA Clients section is no longer shown
  inline on the main staff dashboard — it's now a single link out to
  a new dedicated page, exactly mirroring the pattern Admin/System
  Settings already uses for its Agents Organization link: one entry
  point on the front page, the real grouped/foldable content one
  click behind it. Keeps the front page from growing crowded as more
  VA clients sign on, without moving the concern into the CEO-only
  Admin section — still reachable in one click from the main
  dashboard.
- Verified live: the main dashboard now shows a single "VA Clients"
  link; the new page renders all current subsections (SEMRS
  Self-Marketing, and every real/test client) folded by default, with
  a working back link, and a real click still correctly expands a
  subsection.

## 2026-08-20 (VA Clients subsections folded by default, link-button toggle)
- Per explicit instruction, every subsection in the VA Clients list
  (SEMRS's own self-marketing, each real client, and any future one —
  the grouping logic is fully dynamic) now starts folded, with its
  name styled as a clickable link-button rather than plain bold text,
  so the control clearly reads as something to click.
- Verified live: all subsections render collapsed on page load; a real
  click on a client's name correctly expands it to show that client's
  brief(s).

## 2026-08-20 (VA Clients grouped by client; Self-Marketing moved into it)
- Per explicit instruction, the "VA Clients" section on the main staff
  dashboard is now grouped into one foldable subsection per client,
  rather than one flat list — real clients grouped by their linked
  account (each unlinked brief gets its own subsection, since there's
  no stable account identity to group multiple unlinked briefs under).
- Per explicit instruction, SEMRS's own self-marketing is now the
  first, permanent subsection in that same VA Clients list — framed
  as SEMRS hiring itself as its own Virtual Assistant client, the same
  direct-publish pattern as every paying VA client below it. The
  "Self-Marketing Approval" section previously on `/dashboard/admin`
  was removed entirely; the underlying page
  (`/dashboard/self-marketing`) is unchanged, only its entry point
  moved.
- Verified live: the dashboard now shows a "SEMRS — Self-Marketing"
  subsection plus one subsection per real client (confirmed against a
  real linked client and two unlinked test briefs), and the Admin page
  confirmed to no longer reference Self-Marketing at all.

## 2026-08-20 ("Your Content" picker style; VA Clients dashboard section)
- Per explicit instruction, brought the Client Portal's "Your Content"
  section (per-channel content downloads) into the same single-picker
  style already used everywhere else a client picks one item from
  several (status badges + one dropdown, one item's detail shown at a
  time) — it had been left as a stacked list. Since a brief can carry
  multiple drafts on the same channel (e.g. several blog posts over
  time), the picker is keyed by draft, not channel, with the badge
  label naming the specific draft whenever a channel has more than
  one. Mirrored read-only in the staff Preview Client Portal, same
  "no live form, no network call" rule as every other Preview
  component.
- Per explicit instruction ("VA CLIENT SECTION STILL NOT SHOWN, BUILD
  IT IN MAIN DASHBOARD"), added a "VA Clients" section directly on the
  main staff dashboard landing page — every client on SEMRS as Virtual
  Assistant (CLAUDE.md, Delivery Model, "Path 2"), with status, linked
  client contact info (or a clear "not yet linked" flag), channels,
  and the recorded VA fee, one click from "Manage brief." Previously
  this required navigating into Admin/System Settings or an individual
  brief to see at all — not acceptable for something staff need to
  triage daily.
- Verified live: real click and dropdown-change events confirmed the
  picker's detail panel actually switches (not just the initial
  server-rendered state); the existing per-draft PDF/Word/Excel/Google
  Sheet/Slides downloads confirmed still working through the new
  picker; the staff Preview mirror confirmed to render both drafts
  with no download form present; the new dashboard section confirmed
  against real Virtual Assistant briefs, covering both a linked and an
  unlinked client account. Test data removed after verification.

## 2026-08-20 (Real "Your Plan & Billing" section; walkthrough default fixed)
- Per direct user testing/correction: the real Client Portal had no
  billing information at all, and no dedicated section confirming a
  Virtual Assistant client's plan/fee — two symptoms of the same real
  gap. Fixed with a new **"Your Plan & Billing"** section (shown for
  Virtual Assistant clients, ads-scoped clients with a recorded
  commission rate, or any client with a recorded payment): delivery
  path, the Virtual Assistant Service Fee, the Ads Commission Rate,
  and — genuinely new — the real payment history
  (`ClientBrief.payments`, staff-confirmed amount/method/reference/
  date), which existed in the database since payments were first
  recorded but was never queried or shown to the client anywhere.
  Mirrored in the staff Preview Client Portal.
- Also fixed, same investigation: `ConnectAccountsSection`'s walkthrough
  defaulted closed, so a client filling in an unfamiliar field
  ("Application Password"? "Page Access Token"?) saw a bare form with
  no guidance until they discovered and clicked a small "Walkthrough"
  toggle — inconsistent with the staff preview version, which
  correctly defaulted open. Now defaults open on both.
- Verified live with real test data (a real payment record, a real VA
  fee, a real commission rate) logged in as the actual client account,
  not just a code read — confirmed the section renders correctly and
  the walkthrough shows immediately without an extra click. Test data
  removed after.

## 2026-08-20 (Blog Post Type badge now shown to the self-service client too)
- The Normal/SEO Blog Post distinction (see entry below) was only
  visible to staff. Per explicit follow-up instruction, a self-service
  (Draft-Only) client downloading their content from the real Client
  Portal now sees the same "Normal Blog Post" / "SEO Blog Post" badge
  next to each Website/Blog item in "Your Content" — so they can see
  which of the two paid tiers (data/pricingCatalog.ts) they're
  downloading, matching exactly what they ordered/paid for. No new
  payment logic was added: the whole "Your Deliverables" section
  already gates on the brief reaching "finalized" (payment
  confirmed) — this only adds the visible label, since which tier a
  given post is was decided at drafting/ordering time, not something
  this change introduces a new purchase flow for.
- Verified live: created a real "normal" Website/Blog draft, confirmed
  the badge renders correctly on the real `/portal` page next to the
  channel/title. Test draft deleted after.

## 2026-08-20 (Normal vs SEO Blog Post distinction, tied to real pricing)
- Per explicit instruction, differentiated the Channel Draft form
  between the two real, differently-priced blog-content products
  already in the pricing catalog (`data/pricingCatalog.ts`): the plain
  "Blog post" ($19 each) and the "1000-word SEO content article" ($25
  each, `contentPerArticle`) — confirmed via direct code research
  before building anything, since no such distinction previously
  existed anywhere in this system (CLAUDE.md previously stated every
  blog post gets full RankMath treatment uniformly).
- New `ChannelDraft.blogPostType` field ("normal" | "seo", Website/Blog
  only, defaults to "seo" so existing drafts keep today's exact
  behavior). New radio selector at the top of the Website/Blog draft
  form. Per explicit instruction, the underlying fields and every
  compulsory validation rule (categories, links, image alt text) are
  identical between the two types — "keep the form built now" for
  Normal, unchanged. The only difference: when SEO is selected, each
  relevant field is labeled with the exact RankMath checklist point it
  satisfies (Title → "Focus Keyword near start of SEO title", Meta
  Description → "Focus Keyword in meta description", etc.) — purely
  informational, showing what the heavier price pays for.
  `ChannelDraft.blogPostType` is also shown as a small badge on
  existing drafts in the In Progress/Completed lists.
- Verified live via direct DOM interaction: switching the selector to
  SEO shows all 8 RankMath labels with the correct text; switching to
  Normal removes every label while every field/requirement (Title,
  Meta Description, Categories, etc.) stays present and unchanged.

## 2026-08-19 (Download always available even after publish; real RankMath checklist score)
- Confirmed nothing was removed: `ChannelDrafts.tsx` (blog/social
  draft form — RankMath SEO fields, live word-count/link/image-alt
  checks, Save Draft/Publish Post/Rejected-with-remarks/Dismiss
  Forever buttons) was never touched this session and remains fully
  wired on both the staff brief page and Self-Marketing. Verified via
  direct grep against the file, not just recollection.
- Real gap found and fixed: a Virtual Assistant client's "Your
  Content" list showed EITHER a "Published live" badge OR the
  Download menu, never both — once SEMRS published something live for
  them, they lost the ability to download it in any format. Per
  explicit correction, this is now additive: the live badge and the
  full Download menu (PDF/Word/Excel/Google Sheet/Google Slides) both
  show together, always, for every VA/Self-Marketing draft. Fixed in
  both the real Client Portal and its staff Preview mirror.
- New `lib/rankMathChecklist.ts` — a real, computed checklist against
  CLAUDE.md's Technical On-Page SEO Checklist for every Website/Blog
  draft (Focus Keyword set/in meta description/in SEO title, word
  count 600–2,500, real internal + external anchor-text links, image
  alt text, Feature Image + alt, at least one Category) — reuses the
  exact same `lib/blogContentChecks.ts` functions
  `components/dashboard/ChannelDrafts.tsx` already runs live while
  authoring, so there's no separate, possibly-drifting copy of the
  compliance logic. Shown as a real checkbox list with an "X/10" score
  on both the staff Audit Report page and its PDF download — this is
  the "checkbox audit score" the CEO checks at final delivery,
  addressed as a concrete gap rather than the already-existing color-
  coded inline hints in the draft form.
- Verified live: created a real, deliberately-partial-compliance
  Website/Blog draft — checklist correctly scored 8/10 and correctly
  flagged the one deliberately-missing item (Focus Keyword not in SEO
  title); confirmed present in both the Audit Report page and a real
  downloaded PDF. Separately confirmed a live-published draft shows
  both the "Published live" badge and the Download menu together on
  the real Client Portal. All test data cleaned up after.

## 2026-08-19 (Unified "connect a social account" style across every surface)
- Per explicit instruction, restyled every place in this system that
  shows a channel's connect/grant-access walkthrough to the same
  single-picker layout `components/dashboard/DirectPublishAccessSection.tsx`
  (Self-Marketing, every staff brief page) already used: a compact
  status-badge row (one per channel) plus a single dropdown below it
  showing the selected channel's full walkthrough with the grant/
  request toggle — replacing the "one expandable card per channel,
  stacked" layout that had drifted onto the real and Preview Client
  Portal pages in earlier passes today.
- New shared `components/shared/DirectPublishWalkthroughContent.tsx` —
  pure presentational rendering of one `DirectPublishHelp` entry, so
  every surface reads identical guidance text from one source instead
  of near-duplicate copies.
- `components/portal/ConnectAccountsSection.tsx` (real Client Portal)
  rebuilt on the shared content renderer, same real credential-submit
  form as before, restyled to the badge-row + picker layout.
- New `components/dashboard/PreviewConnectAccountsPicker.tsx` (staff
  Preview Client Portal) — same picker style, read-only, no form;
  replaces and deletes the now-superseded
  `PreviewDirectPublishCard.tsx` from earlier today.
- New `components/dashboard/SocialAccountGuide.tsx` — a pure,
  client-independent reference lookup added to the Admin Client Portal
  panel (`/dashboard/admin/client-portal`): every channel's walkthrough
  in one picker, with no status/form, for checking a platform's
  requirements without any specific client's brief open.
- Deliberately left `DirectPublishAccessSection.tsx`'s own walkthrough
  text unchanged — it's staff-facing ("Send this to the client — they
  do these steps themselves") rather than client-facing ("What you
  need"), an intentional difference in audience, not something to
  merge into the shared client-facing renderer.
- Verified live: the Admin guide's dropdown genuinely switches
  platforms and content (tested via a real `change` event dispatch);
  the Preview Client Portal's picker shows both channel badges plus
  the selected one's full walkthrough; the real `/portal` page's
  server-rendered HTML confirmed to use the exact same badge-row +
  dropdown + Walkthrough-toggle structure.

## 2026-08-19 (Preview Client Portal: restored the real grant/request toggle buttons)
- Correction to the same-day walkthrough-visibility pass, below: that
  pass had flattened the real Portal's "I'll grant access" / "Ask
  SEMRS to request access instead" toggle buttons into static,
  always-both-shown text — per explicit instruction, this wasn't
  faithful enough ("the button are missing... keep same and all
  facilitation"). Fixed:
  - New `components/dashboard/PreviewDirectPublishCard.tsx` — a
    faithful, real client component mirroring
    `components/portal/ConnectAccountsSection.tsx`'s PlatformCard
    exactly (same expand button, same Connected/Not-connected badge,
    same grant/request toggle buttons, same walkthrough text) — the
    one deliberate omission is the actual credential input + submit
    form, since that's the one part that genuinely mutates data as if
    impersonating the client (unchanged reasoning from when Preview
    Client Portal was first built).
  - Ad Account Access now reuses the real
    `components/portal/AdAccessInfoSection.tsx` directly — it never
    had a data-mutating form to begin with (confirmed by its own
    header comment), so there was no reason to reimplement it as
    static text at all.
  - Verified live via direct DOM interaction (the Browser pane wasn't
    compositing frames for pixel-coordinate clicks this session, so
    real `button.click()` calls against the live page were used
    instead): expanding a channel shows the full real walkthrough;
    clicking "Ask SEMRS to request access instead" genuinely swaps the
    content to the request-access steps, same as the real Portal.

## 2026-08-19 (Real walkthrough guides in Preview Client Portal; Agent Roster given its own page)
- Preview Client Portal's "Connect Your Accounts" and "Ad Account
  Access" sections previously showed only a flat status badge per
  channel/platform — no way for staff to check the actual guidance
  text the client sees. Both now expand (read-only `<details>`, no
  live form) to show the real walkthrough content — what the client
  needs, the access-mechanism steps, the SEMRS-requests-access
  alternative, and what happens after connecting — read from the exact
  same `lib/directPublishHelp.ts` / `lib/adPlatformHelp.ts` the real
  Client Portal itself uses. Ad Account Access also now lists every ad
  platform, not only ones with an existing access record, matching
  what the client actually sees rather than only what's already logged.
- Real, separate flagged gap: Admin/System Settings had the full Agent
  Roster (every department, every agent) and the Formal Organizational
  Chart dumped raw/inline on the page, cluttering what's meant to be a
  settings hub. Moved both to a new dedicated
  `/dashboard/admin/agents-organization` page, linked via an "Open →"
  button — same pattern Self-Marketing Approval and Client Portal
  already use. Content itself is unchanged, still read live from the
  spec repo; only its location moved.
- Verified live: the walkthrough content renders with real step text
  on a real client's Preview Client Portal page; the Admin page no
  longer inlines the roster; the new Agents Organization page renders
  the roster, chart, and Virtual Office link correctly.

## 2026-08-19 (Admin Client Portal panel + verified the real client signup/login flow)
- Per explicit instruction, verified live (not just code review) that
  the real client-facing signup/login flow at `/portal/signup` is
  genuinely locked down and working: a real account is created with a
  real bcrypt password hash (never plaintext); the emailed
  verification link is single-use, expires, and correctly rejects
  reuse; a duplicate-email signup is rejected (409); a weak password
  is rejected (400, <8 chars); wrong-password login is rejected (401);
  correct-password login succeeds; and an unauthenticated visit to
  `/portal` correctly redirects to `/portal/login` rather than leaking
  any content. All test data was cleaned up after.
- New CEO-only **"Client Portal"** admin panel
  (`/dashboard/admin/client-portal`, linked from Admin/System Settings
  right alongside Self-Marketing Approval, per explicit instruction on
  where to place it) — lists every real Client Portal account and
  every order linked to it, each with a "Preview →" straight into that
  order's existing Preview Client Portal page. This is the missing
  front door to the Preview Client Portal feature built earlier: that
  page always existed per-brief, but there was no single place to see
  every client at once without already knowing which brief to look at.
  No client credentials are ever used — same non-impersonation design
  as Preview Client Portal itself.

## 2026-08-19 (Self-Marketing: "Preview Client Portal" link was missing)
- Real gap: `/dashboard/self-marketing` had an "Audit Report →" button
  but no "Preview Client Portal →" button, even though every real
  client's brief page has had one since it was built. Staff had no way
  to see self-marketing's own "client portal" experience without
  actually logging out and back in as a client — an unnecessary
  detour, since self-marketing isn't a real client relationship
  (`ClientBrief.clientId` is null for it) and the CEO/staff are
  already authenticated via the admin session that gates this page.
- Added the same "Preview Client Portal →" link
  (`/dashboard/briefs/[id]/portal-preview`) already used everywhere
  else — no new page needed, since that route only ever required the
  regular dashboard session, not a client login, and already handles a
  null `client` gracefully ("Welcome, (client)"). Verified live: the
  link renders with the self-marketing brief's real ID, and the target
  page returns a clean 200 for it.

## 2026-08-19 (Download menu extended to every individual deliverable, not just the whole package)
- Per explicit instruction ("this download menu... is placed with
  every single piece of content"): the 5-format Download menu (PDF/
  Word/Excel/Google Sheet/Google Slides) now sits next to each
  individual Performance Summary and each individual Ads Performance
  Report entry in the Client Portal, not only at the top of "Your
  Deliverables" and on each Channel Draft. Ads Performance Reports
  keep the same CEO Budget & Campaign Approval gate as everywhere else
  — never downloadable before that's granted.
- New generic, reusable single-item content-block generators
  (`lib/pdf/textBlockPdf.ts`, `lib/docx/textBlockDocx.ts`,
  `lib/xlsx/textBlockXlsx.ts`, `lib/content/textBlockGoogleText.ts`)
  instead of one-off generators per content type — a title/subtitle
  plus labeled fields, which both Performance Summaries and Ads
  Performance Reports (`lib/content/adsReportFields.ts` for the
  latter's field list, including the structured funnel numbers) build
  on. New `AnalyticsSummary.googleSheetUrl`/`googleSlidesUrl` and
  `AdsPerformanceReport.googleSheetUrl`/`googleSlidesUrl` cache fields.
- Deliberately did NOT add this menu to "Delivered Links" — each of
  those is already a direct link to real content staff placed
  elsewhere (typically a Google Doc), so there's no independent
  structured content on this side to regenerate a file from; the link
  itself is the access mechanism.
- Verified live: real magic bytes on all 6 new PDF/Word/Excel routes;
  a real Google Sheet was created via the new per-summary route,
  confirmed the create-or-reuse caching returns the same URL on a
  second call, then the test Sheet (and test data) were deleted.

## 2026-08-18 (SEMRS Virtual Assistant is now a separate, paid recurring service)
- Business-model clarification, per explicit instruction: hiring SEMRS
  as a Virtual Assistant (Delivery Model, Path 2 — SEMRS manages/posts
  to a client's own live accounts directly, on a standing basis) is
  now documented as a separate, additional recurring fee (monthly or
  yearly, same "pay 10, get 12" annual mechanic as Conversion & Lead
  Generation) on top of whatever base engagement the client already
  ordered — distinct from the Paid Media Model's ad-spend commission,
  which is for running ad campaigns, not organic/social account
  management. No default rate was invented — same "CEO confirms the
  actual number per client" pattern as the Ads Commission Rate and
  Data Retention defaults, since there's no established SEMRS-wide
  Virtual Assistant rate yet.
- Enabling Path 2 for a client now explicitly requires BOTH the
  platform access grant (already documented) AND this fee being
  agreed/recorded — neither alone is enough for SEMRS to start
  managing an account.
- New "SEMRS Virtual Assistant Service Fee" section on
  prompts/client-brief.md (agreed fee, billing cycle, channels
  covered, confirmed-by) — same template shape as "SEMRS Commission
  Rate."
- Clarified, in the same pass, that Path 1 (Draft-Only) clients get
  their content as instant, self-serve downloads (the multi-format
  Download menu — see entry below) the moment payment is confirmed —
  this IS that path's delivery mechanism, not just a courtesy extra.

## 2026-08-18 (Multi-format Download menu — PDF/Word/Excel/Google Sheet/Google Slides)
- Replaced the single "Download PDF" buttons in the Client Portal
  (both the whole-package "Your Deliverables" download and each
  per-channel-draft "Your Content" row) with a real `DownloadMenu`
  offering **PDF, Word (.docx), Excel (.xlsx), Google Sheet, and
  Google Slides** — per explicit instruction that a paid client should
  be able to get their content in whichever format lets them edit it
  on their own premises, not just view a fixed-layout PDF.
- New `lib/content/draftContent.ts` — single shared field list/order
  for a channel draft's content, so every format (PDF, Word, Excel,
  Sheet, Slides) reads identically; refactored the existing PDF
  generator to use it instead of duplicating the field list.
- New generators: `lib/docx/*.ts` (via the free `docx` npm package),
  `lib/xlsx/*.ts` (via the free `exceljs` npm package) — both for a
  single channel draft and for the whole delivered package.
- Google Sheet/Slides reuse the existing, already-proven
  `lib/googleWorkspaceFiles.ts` `createGoogleFile()` call (same one
  the staff-side "Create Google Doc" button uses) — new tab-delimited
  grid/slide text compilers (`lib/content/draftGoogleText.ts`,
  `lib/content/deliverablesGoogleText.ts`; tab-delimited specifically
  because real captions/hashtags routinely contain commas, and
  `createGoogleFile`'s grid parser has no quote-escaping support).
  Created once, then cached (`ChannelDraft.googleSheetUrl`/
  `googleSlidesUrl`, `ClientBrief.deliverablesGoogleSheetUrl`/
  `deliverablesGoogleSlidesUrl`) so a repeat click reuses the same
  file instead of littering Drive with duplicates. Kept at the
  existing "anyone with the link can view" sharing level (never
  loosened to editor) — a client wanting a genuinely editable copy of
  a Google file uses Google's own "File > Make a copy," or just picks
  Word/Excel instead for a real local editable file.
- Verified live: real `%PDF`/`PK\x03\x04` (docx+xlsx) magic bytes and
  correct headers on every new route; the Google Sheet create-or-reuse
  route was confirmed to actually create a real Sheet in SEMRS's
  connected Drive (cached correctly on the draft) — that test file was
  deleted afterward via the Drive API to avoid leaving clutter in the
  real connected account.

## 2026-08-18 (Per-channel content downloads for Draft-Only clients)
- Closed a real gap in the Client Portal: it only ever showed a
  client manually-added `DeliveredDocLink`s and a free-text package
  summary — never the client's actual per-channel content (a blog
  post's real body, a social caption) automatically. A Draft-Only
  Handoff client (CLAUDE.md, Delivery Model, Path 1 — never granted
  SEMRS Virtual Assistant access) had no self-serve way to get the
  real content they need to post themselves; staff had to manually
  type/paste everything into Final Package Content or add doc links
  by hand.
- New "Your Content" list in the Client Portal's "Your Deliverables"
  section: one row per real, non-rejected/non-dismissed Channel Draft
  in scope, each with its own "Download PDF" button
  (`/api/portal/briefs/[id]/channel-drafts/[draftId]/pdf`, built via
  `lib/pdf/channelDraftPdf.ts` from that draft's own real structured
  fields) plus a "View Doc ↗" link when staff has already turned it
  into a Google Doc (`ChannelDraft.googleDocUrl`). Same
  auth/ownership/`finalized`-status gate as the other portal PDF
  routes.
- A draft that was actually published live for an opted-in Virtual
  Assistant client shows a green "Published live" badge with the real
  live URL instead of a download button — nothing left to post. This
  correctly still shows a download for WhatsApp/Email drafts even for
  Virtual Assistant clients, since those two channels stay draft-only
  regardless (CLAUDE.md, Delivery Model).
- Mirrored as a read-only status readout (not a live link — it needs
  the client's own portal session) on the staff-only Preview Client
  Portal page, same pattern as the deliverables "Download PDF" note
  added earlier today.
- Verified live: created a real test Channel Draft, confirmed its
  "Download PDF" button renders with the correct URL and returns a
  real `%PDF-1.3` file; then added a real `PublishAttempt`
  (status=success, mode=publish) and confirmed the same row switches
  to the "Published live" badge with the live URL; cleaned up both
  test records afterward.

## 2026-08-18 (Real PDF downloads — Audit Report + client deliverables)
- Replaced browser print-to-PDF as the only "download" path for the
  Audit Report — it depended on the visiting browser/OS's own print
  dialog and settings (e.g. background colors/status badges only show
  if "background graphics" is enabled), which is what the CEO flagged
  as "not working properly." New real, server-generated PDF via
  `pdfkit` (free, MIT-licensed, no headless-browser binary — Hard
  Constraint stays satisfied) at
  `/api/briefs/[id]/audit-report/pdf`, downloaded via a "Download PDF"
  button on the Audit Report page. The Print button stays as a
  quick-preview fallback, not the primary path.
- New client-facing **"Download PDF"** button in the Client Portal's
  "Your Deliverables" section (`/api/portal/briefs/[id]/deliverables/
  pdf`) — a real file, gated the same way that section already is:
  only generates once `brief.status === "finalized"` (payment
  confirmed) and only for the brief's own linked client (portal
  session-scoped, same defense-in-depth pattern as every other
  `/api/portal/briefs/[id]/*` route). Deliberately excludes CEO
  approval notes/summary (internal-only) — mirrors exactly what that
  Portal section already shows the client, just as a downloadable
  file instead of read-only page content. The staff-only Preview
  Client Portal page was updated to note this button exists (as a
  read-only label, not a live link, since it needs the client's own
  portal session — a staff dashboard session can't fetch it).
- Fixed a genuine packaging bug hit while building this: `pdfkit`
  reads its font metric files off disk by relative path at runtime,
  which webpack's default bundling breaks (`ENOENT ... Helvetica.afm`)
  — fixed by marking it as a `serverComponentsExternalPackages` in
  `next.config.js` so Next.js requires it directly instead of bundling
  it.

## 2026-08-18 (Audit Report, per-channel content fields, real Google Doc creation)
- Added real, dedicated storage for the Review Agent's score/remarks —
  `ReviewRecord` (append-only), entered via a new
  `RecordReviewForm.tsx` on both the main brief page and the
  Self-Marketing page (same pipeline, same standard, per CLAUDE.md's
  Agent Roles preamble — this wasn't wired to self-marketing at first,
  caught and fixed in the same pass). CLAUDE.md's Output Format has
  always required "review score, improvement notes" in the final
  package; there was no dedicated field for it before, only free text
  inside a `BriefApproval` summary.
- New, staff-only, printable **Audit Report**
  (`/dashboard/briefs/[id]/audit-report`) compiling the review score
  history, every CEO approval record, and a channel-draft status
  summary — linked via a new "Audit Report →" button. The latest
  review score/remarks are now also included automatically in the
  Final Delivery notification email (`lib/notifyEmail.ts`).
- Found and closed a real, pre-existing gap while building this: the
  Google Workspace connection has existed since before this session,
  described as being for "real Docs/Sheets/Slides for every client,"
  and `components/dashboard/CreateGoogleFile.tsx` already does that
  for the final compiled package — but nothing let a single Channel
  Draft become its own Google Doc. New per-draft "Create Google Doc"
  button (`app/api/briefs/[id]/channel-drafts/[draftId]/create-doc/
  route.ts`) reuses the exact same proven `lib/googleWorkspaceFiles.ts`
  call, storing the result on that draft (`ChannelDraft.googleDocUrl`)
  rather than as a client-facing `DeliveredDocLink`.
- Every non-Website/Blog channel now has its own real, separately-
  labeled content fields instead of one generic text box —
  `lib/channelContentFields.ts` defines each channel's actual
  requirements (title/subject, body/caption, hashtags, tags, CTA
  type, image, link), matching what agents/content-agent.md already
  described per channel. `hashtags` (Facebook/Instagram/X/TikTok/
  LinkedIn/Pinterest) has no separate field on any of these platforms'
  real APIs — captured for authoring clarity, then appended into the
  caption/text at publish time (now wired into all three live
  publishers). `tags` (YouTube) and `ctaType` (Google Business
  Profile) ARE genuinely distinct fields on those platforms' real
  APIs — stored ready for when those channels get a live publisher,
  same pattern already used for their credential fields.
- Also corrected two stale code comments/email text found while
  wiring this in: `lib/notifyEmail.ts` previously said this app "has
  no real Google Doc creation anywhere in it" — no longer true, fixed
  to describe what's actually there now.

## 2026-08-18 (Corrected Client Support Module: upload/playlist placement was already automated)
- Per explicit instruction, confirmed and documented the real,
  already-built pipeline: whenever the CEO asks for a Client Support
  video, the Visual & Video Content Agent produces the creative
  brief/script/visual direction only (never the video file, never the
  upload — outside its Responsibilities); a human produces the actual
  video file from that brief; staff then uploads it once through
  SEMRS-Dashboard's real "YouTube Connection" form
  (`/dashboard/admin`, `lib/youtubeUpload.ts`), which genuinely hosts
  it on SEMRS's real channel AND adds it to the "SEMRS Client Support"
  playlist automatically, in the same action.
- CLAUDE.md's Client Support Module section previously described
  upload AND playlist placement as a manual step ("uploads it... into
  the playlist, themselves") — that was stale relative to the real
  `lib/youtubeUpload.ts` code, which already automates both together.
  Corrected to state plainly: creation is still manual (no AI video
  editing/rendering in this system), upload + playlist placement are
  not. Mirrored a short cross-reference into
  agents/visual-agent.md's Responsibilities.
- Confirms the full loop the CEO described: hosted at the real
  channel always, never inside this app; `/support` embeds it back
  automatically via the free playlist RSS feed the moment it's made
  Public.

## 2026-08-18 (Client Support Module: real playlist ID set, then corrected)
- Set `SUPPORT_PLAYLIST_ID` to a real playlist (`PLNZWWLo4UI-4`) the
  CEO provided — confirmed its RSS feed's `channelId` matches SEMRS's
  real confirmed channel, but its actual title was "SEMRS OS: Complete
  Onboarding & Integration Guide," not "SEMRS Client Support."
- Same day, the CEO provided a second playlist (`PLCZKgF0V6Cn4`) whose
  RSS feed title is literally "SEMRS Client Support" — the exact name
  CLAUDE.md's design is built around, same real channel confirmed.
  Replaced the first ID with this one, per the CEO's explicit choice
  (asked rather than assumed, since supporting both would have been a
  real code change — merging two feeds — not a one-line swap).
  `/support` correctly still shows "No support videos yet" — this
  playlist is genuinely empty right now (0 entries in its own RSS
  feed), not a bug; it'll appear automatically once a real video is
  uploaded into it.

## 2026-08-18 (Closed flagged gaps: Ads Client Help in Portal, staff Portal preview)
- Fixed a real gap introduced the same day: `AnalyticsPropertyAccess`
  (Client Portal GA4/Search Console submissions) wasn't visible
  anywhere on the staff dashboard's brief detail page. Added to its
  Prisma `include` and a real status-display section.
- Closed the previously-flagged gap where the Ads "Client Help"
  walkthrough (`prompts/client-help-meta-ads-integration.md`) was
  written to be client-facing but only ever rendered in the internal
  staff dashboard. New `components/portal/AdAccessInfoSection.tsx`
  shows the client the same walkthrough + their current
  `AdAccountAccess` status, directly in `/portal`. Deliberately
  read-only for the client — establishing/confirming access stays a
  staff-confirmed action, since it happens on the ad platform itself,
  not through this app.
- Built a real answer to "I can't access the Client Portal, how do I
  check it": a new, staff-only, read-only **`/dashboard/briefs/[id]/
  portal-preview`** page (linked from that brief's main dashboard page)
  that mirrors exactly what that client sees — status stepper using
  the client's own labels, Connect Your Accounts / Connect Analytics /
  Ad Account Access statuses, delivered content. Deliberately NOT a
  minted client session or any form of impersonation — every
  interactive form the real Portal has is rendered here as a plain
  status readout, so staff can never accidentally submit or change
  anything as if they were the client.
- **Not fixed, needs real input**: `SUPPORT_PLAYLIST_ID` is still unset
  — `/support` correctly shows "No support videos yet" by design
  (never crashes on a missing/broken feed) rather than real content.
  This can't be filled in without the real "SEMRS Client Support"
  YouTube playlist ID, which only whoever controls the real
  `@SEMRS-GBOB` channel can provide.

## 2026-08-18 (Client Portal GA4 & Search Console access)
- Added a real "Connect Analytics" section to the Client Portal
  (`components/portal/AnalyticsAccessSection.tsx`, new
  `AnalyticsPropertyAccess` model), per explicit instruction. A client
  grants SEMRS's already-connected Search Console & Analytics account
  read-only Viewer access to their OWN Search Console property and/or
  GA4 property, entirely through Google's own sharing UI — no OAuth
  flow or credential ever passes through this app, same official-access
  principle as ad account access (Paid Media Model). "Verify Now" is
  real, not a manual staff confirmation: it asks Google, via SEMRS's
  connected account, which sites/properties it can currently see
  (`lib/searchConsole.ts`'s `listAccessibleSites`,
  `lib/analyticsGA4.ts`'s `listAccessibleProperties`) and checks
  whether the client's submitted property is in that list.
- Extended the existing Search Console connection (built 2026-08-17 for
  sitemap resubmission) with the `analytics.readonly` scope rather than
  building a separate connection — same shared SEMRS account now serves
  both the admin-side sitemap nudge and client-side analytics
  verification. Confirmed the `analyticsadmin` v1beta API surface
  (`accountSummaries.list`, nested `propertySummaries`) exists in the
  installed `googleapis` package before writing the call.
- Updated CLAUDE.md's Analytics Agent description: organic performance
  data can now come from a client sharing it back OR from this granted
  read-only access — explicitly scoped as connection-and-verification
  only for this pass, not the full data-pulling/reporting pipeline on
  top of it, which stays separate future work (per the prior session's
  explicit decision to scope that out).

## 2026-08-17 (Colored review buttons + strict compliance + sitemap resubmission)
- Added two new draft-review decisions to SEMRS-Dashboard's Channel
  Draft form, alongside the existing Save Draft (now blue) and Publish
  Post (now green): **Rejected** (amber, requires remarks explaining
  what needs fixing — the draft stays visible with those remarks) and
  **Dismiss Forever** (red, permanent from the UI's perspective,
  confirmed before acting, filtered out of every view — the record
  itself is kept, never truly deleted, same convention as
  `DirectPublishAccess.revoked`). New `ChannelDraft.reviewStatus`/
  `reviewRemarks`/`reviewedBy`/`reviewedAt` fields and a new review API
  route.
- Added a compulsory image-alt-text check (every `<img>` in the body,
  not just the Feature Image) — same client+server enforcement pattern
  as the internal/external link check, via
  `lib/blogContentChecks.ts`'s new `checkImageAlt`.
- Tied "every required RankMath field must be filled" to the existing
  Review Agent gate in CLAUDE.md: a Website/Blog piece missing any
  required field is sent back to the Content Agent, the same path
  already used for a low content score — not a new mechanism. Also
  made explicit, and confirmed already true in
  `lib/publishers/wordpress.ts`, that a field this app didn't collect
  is left exactly as WordPress/RankMath would default it, never sent
  as an empty override.
- Built real Search Console sitemap resubmission
  (`lib/searchConsole.ts`, a new `SearchConsoleConnection` and its own
  OAuth connect/callback/disconnect flow in `/dashboard/admin`,
  reusing `GOOGLE_OAUTH_CLIENT_ID/SECRET` with a new
  `SEARCH_CONSOLE_OAUTH_REDIRECT_URI`): after a real live Website/Blog
  publish, the target site's sitemap is resubmitted to nudge faster
  crawling. **Deliberately not Google's Indexing API** — that API is
  restricted by Google's own terms to JobPosting/BroadcastEvent
  content, and using it for ordinary blog posts risks the connected
  account being flagged for misuse; sitemap resubmission is the real,
  sanctioned mechanism for everything else, and makes no promise of
  instant indexing. Non-fatal if the site isn't yet verified in Search
  Console or the connection isn't set up — surfaced as a warning, never
  blocks the post itself from publishing.
- **Explicitly scoped out, per explicit instruction**: real analytics/
  performance reporting on organic traffic gained from these posts —
  a genuinely large, separate feature (new Search Console/Analytics
  data-pull scopes, a reporting UI) left for its own dedicated pass
  rather than tacked onto this one.

## 2026-08-17 (Compulsory anchor-text links + categories + word count)
- Strengthened CLAUDE.md's Technical On-Page SEO Checklist per explicit
  instruction: the internal and external links were already required
  bullets, but now explicitly say they must be real anchor text inside
  the body content (never just noted in the separate Link field), and
  this is now genuinely enforced, not just written policy —
  SEMRS-Dashboard's Channel Draft form blocks Save for a Website/Blog
  draft until the body contains at least one internal (relative href)
  and one external (absolute URL) anchor-text link, checked both
  client-side (live feedback) and server-side (real 400 error) via a
  new shared `lib/blogContentChecks.ts`.
- Added a required Categories field: a suggested SMMA category
  checklist (`lib/blogCategories.ts` — SEO & GEO, Social Media
  Marketing, Paid Ads (SEM), Content Marketing, Lead Generation &
  Conversion, Analytics & Reporting, Case Studies, Company News,
  Guides & How-Tos, Industry Trends), at least one required, same
  compulsory client+server enforcement as the links above. On publish,
  `lib/publishers/wordpress.ts` looks up each selected category by
  real name via WordPress's own categories search, creates it if
  missing, and assigns the real category IDs to the post — never just
  a label sitting unused in this app. Non-fatal per category, same
  pattern as the Feature Image upload.
- Added a live word count under the Body field (green/amber against
  the existing 600–2,500 target) — mirrored into CLAUDE.md's Basic SEO
  bullet as "tracked live," not just a written estimate.
- The existing "Link to include" (linkUrl) field was left untouched,
  per explicit instruction — this is a separate, already-built field,
  not replaced by the new compulsory in-body links.
- Mirrored into agents/content-agent.md's Website/Blog Responsibilities
  and Output Format.

## 2026-08-17 (Structured blog-post sections + real Channel Draft build)
- Added the concrete "Delivered structure" rule to CLAUDE.md's
  Technical On-Page SEO Checklist, per explicit instruction: a
  Website/Blog piece is never handed off or entered as one raw block
  of text — Title, Meta Description, Focus Keyword, LSI & Related
  Keywords, Semantic SEO Words, and Feature Image (+ alt text) are
  distinct, separately-labeled sections all the way through, plus an
  image-placement rule (Feature Image inline after the first H2's
  paragraph, in addition to being set as the real Featured Image;
  another image roughly every 600 words after that). Mirrored into
  agents/content-agent.md, agents/visual-agent.md, and
  agents/website-agent.md.
- SEMRS-Dashboard: built the real dashboard side to match, not just
  the spec — `ChannelDraft` (prisma schema) gained 6 new fields
  (metaDescription, focusKeyword, lsiKeywords, semanticSeoWords,
  featureImageUrl, featureImageAlt), `ChannelDrafts.tsx` now collects
  each as its own labeled field instead of one bodyHtml blob, and
  `lib/publishers/wordpress.ts` now sends RankMath's real
  `rank_math_title`/`rank_math_description`/`rank_math_focus_keyword`
  post meta (LSI/semantic words appended into the focus-keyword field,
  matching RankMath's own multi-keyword support) and uploads the
  Feature Image to WordPress's media library, sets its alt text, and
  sets it as the post's real `featured_media` — non-fatal if the image
  upload fails, so a bad image URL never blocks the actual post.
- Also restructured the Channel Drafts UI per explicit instruction:
  drafts with no publish attempt yet stay in an always-visible "In
  Progress" list with the full Draft/Publish buttons (already existed
  as "Save as draft"/"Publish live"); once a draft has any successful
  publish attempt, it moves into a toggleable, compact "Completed"
  list (title + publish date + status, expandable for the rest) —
  clicking either publish button is the "final action" that empties it
  out of active editing.

## 2026-08-17 (Technical On-Page SEO Checklist, RankMath-aligned)
- Added a new CLAUDE.md section, "Technical On-Page SEO Checklist
  (RankMath-Aligned)," per explicit instruction: every Website/Blog
  post must satisfy RankMath's free on-page SEO analysis criteria
  (Basic SEO, Additional, Title Readability, Content Readability) on
  top of the existing "Content quality and Google-penalty avoidance"
  guardrail, not instead of it. Split the work across five agents
  rather than duplicating the full checklist in each: SEO & GEO Agent
  now sets one explicit Focus Keyword per Website/Blog piece (distinct
  from its broader keyword list); Content Agent writes to the full
  checklist (title/meta/URL/heading keyword placement, 600-2,500
  words, ~1% density, DoFollow external + internal links, Table of
  Contents, short paragraphs, title readability); Visual & Video
  Content Agent builds at least one image's alt text around the Focus
  Keyword; Strategy Agent flags Pillar Content on the calendar
  (matching RankMath's own flag); Website/Blog Draft Agent carries the
  SEO title/meta description/slug/Focus Keyword/Pillar flag through to
  the final draft, formatted ready for RankMath's own fields.
- Explicitly declined, not adopted: RankMath's paid "Content AI"
  add-on (part of the source checklist) — the Content Agent, powered
  by Claude, already writes and optimizes the post itself for free, so
  it would add nothing; matches this project's standing free-tools-only
  Hard Constraint.
- Explicitly scoped out: SEM/paid ads and non-WordPress social
  channels — RankMath is a WordPress on-page tool with no equivalent
  meaning for an ad or a social post, so this checklist governs
  Website/Blog content only, not the Ads Campaign Agent's existing
  policy-compliance duties or each social channel's own format norms.
- Mirrored into agents/seo-agent.md, agents/content-agent.md,
  agents/visual-agent.md, agents/strategy-agent.md,
  agents/website-agent.md, and README.md (a short pointer section, per
  its existing style).

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
