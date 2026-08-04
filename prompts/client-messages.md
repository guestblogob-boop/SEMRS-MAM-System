# Client Messages

Templates used by the Client Communication Agent (see
agents/client-communication-agent.md). Fill in the bracketed fields for
each send, adjust wording to match the client's stated tone (see
prompts/client-brief.md), and log every sent message in
outputs/client-message-log/ with a timestamp and the order's current
status. Never send a message that overstates status — see
agents/client-communication-agent.md, Constraints.

## 1. Order Received / Greeting

Subject: We've received your order, [Client Business Name]!

Hi [Client Contact Name],

Thank you for choosing SEMRS! We've received your order for
[Services Requested] and we're excited to get started.

Here's a quick summary of what we've got on file:
- Services: [Services Requested]
- Channels: [Channels in Scope]
- Goal: [Goal]

Before any work begins, your order goes through a quick internal
review to make sure everything matches what we discussed. We'll be in
touch as soon as that's done.

You can also check live status anytime in the Client Portal.

Warmly,
The SEMRS Team

## 2. Awaiting CEO Order Approval

Subject: Your order is being reviewed

Hi [Client Contact Name],

Quick update: your order is currently being reviewed internally before
we begin work. This is a standard step for every order we take on —
we'll let you know the moment work is underway.

You can also check live status anytime in the Client Portal.

Warmly,
The SEMRS Team

## 3. Order Approved / Work in Progress

Subject: Good news — work has begun on your campaign!

Hi [Client Contact Name],

Your order has been approved and our team is now actively working on
your campaign. From here, you can expect us to move through research,
strategy, and content creation, all built around your goal:
[Goal].

We'll reach out again once everything is ready for final review.

You can also check live status anytime in the Client Portal.

Warmly,
The SEMRS Team

## 3a. Awaiting CEO Budget & Campaign Approval (ads-scoped orders only)

Subject: An update on your ad campaign budget

Hi [Client Contact Name],

Quick update: our team has put together a campaign and budget plan for
your ads, and it's now going through internal approval before we move
forward. This is a separate check specifically for budget and campaign
decisions, on top of the usual review your other content goes through.

We'll follow up as soon as it's approved, with the full plan for you to
review — including our management fee shown as a clear, separate line
item from your ad spend.

You can also check live status anytime in the Client Portal.

Warmly,
The SEMRS Team

## 4. Work Complete / Awaiting Final CEO Approval

Subject: Your campaign is complete and in final review

Hi [Client Contact Name],

Great news — your campaign work is complete! It's now going through
our final internal sign-off before we hand it over to you.

We'll be in touch shortly with everything ready for you to review.

You can also check live status anytime in the Client Portal.

Warmly,
The SEMRS Team

## 5. Delivered

Subject: Your campaign is ready!

Hi [Client Contact Name],

Your campaign is complete and ready for you. Here's a quick summary of
what's included:

[Summary of Delivered Work]

You can find everything here: [Delivery Package Link]

If you have any questions or would like to discuss next steps, just
reply to this message — we're here to help.

Thank you for choosing SEMRS!

Warmly,
The SEMRS Team

## Additional: Declined at Order Approval

Subject: An update on your order

Hi [Client Contact Name],

Thank you for your interest in working with SEMRS. After review, we're
unable to move forward with this order at this time. [Brief, honest,
respectful reason if appropriate to share.]

We'd welcome the chance to work together in the future — please don't
hesitate to reach out.

Warmly,
The SEMRS Team

## Additional: Changes Requested at Final Delivery

Subject: A quick update on your campaign

Hi [Client Contact Name],

Thanks for your patience — we're making a few adjustments to your
campaign before it's finalized. We'll follow up shortly with the
updated work for your review.

You can also check live status anytime in the Client Portal.

Warmly,
The SEMRS Team

## Additional: Client-Initiated Status Inquiry Reply

Used whenever a client asks directly for a status update, on whichever
channel they used. Pull the real current stage and active
department/agent from the Orchestrator before replying — never a
generic placeholder.

Hi [Client Contact Name],

Thanks for checking in! Your project is currently with our
[Real Active Department/Agent, from the managing director] team,
working on [What They're Actively Doing]. Everything's on track.

You can also check live status anytime in the Client Portal.

Warmly,
The SEMRS Team
