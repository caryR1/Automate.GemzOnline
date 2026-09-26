# Handoff from the cloud "Automate" session (2026-09-26)

Cary opened a cloud session called "Automate" by accident and is closing it. He
wants Automate to be a **desktop** session. This file carries over what that
session learned and decided.

## Who you are
You are **Automate**, the session that manages https://automate.gemzonline.com
(repo `caryR1/Automate.GemzOnline`, static HTML/CSS/JS on Hostinger) and the work
around it: GoHighLevel (GHL) plans and checkout, lead funnels, and **pricing and
quoting for Cary's web and automation business**. Read `CLAUDE.md` (your role, the
standing quoting rule) and `PRICING.md` (the full pricing model and rate sheet).
Both are in PR #2. If it's still open, ask Cary to merge it.

## Cary's agenda, in this order
1. **Finish the pricing model, then write down business policies.** Pick up here.
2. **Melicia's changes to Au-Some Notarific** (first client; notary plus
   Jamaican passport/license renewal, Bay County FL; au-somenotarific.com; repo
   `caryR1/Au-some`). Her requests come before Automate's own site. What she
   wants isn't known yet, so ask Cary.
3. **Automate as a going concern:** build proper funnels for automate.gemzonline.com
   and the three GHL plans.

## Pricing: what's settled vs. open
Settled (details in PRICING.md): $100 GHL setup fee; $25/hr consultation (going
to $30–35 later); $100 per significant section for a new static build; $60 per
section for a refresh; custom-coded work priced per project; $20 per AI blog
article; graphics $15–$150 by complexity; the site map doubles as the quote.
Melicia's pilot price: 7 × $100 = $700, discounted to $400.

Gaps to interview Cary about (my list; nothing below has been decided):
- Payment terms: deposit % up front, when the balance is due, payment methods.
- Revisions: how many rounds are included per section; the rate after that.
- Friends-and-family discount: a standard % or case by case? (Melicia got ~43% off.)
- Hosting/domain and ongoing maintenance: who pays; a monthly care plan?
- Consultation: first call free? Credited toward the project if they go ahead?
- Content: does the client supply text and photos? Copywriting price per section?
- Adding a new section to an existing site: $100 (new) or $60 (refresh)?
- Minimum project size, rush fee.
- GHL plans: contract term, cancellation, setup fee waived for annual?
- Local-SEO / Google Business Profile setup (relevant for clients like Melicia).
Every newly priced item goes into the PRICING.md rate sheet as a permanent row,
with low/average/agency market figures (see the standing rule in CLAUDE.md).

## Site facts found (verified 2026-09-26)
- **Live site ≠ `main`.** Live is PR #1 (`simplify-starter-offers`, open,
  unmerged): "Never Miss a Call. Never Miss a Lead.", with plans Leads & Reviews
  $99/mo, AI Attendant $200/mo, Complete $249/mo.
- **Live checkout buttons are dead:** the homepage still has the placeholders
  `YOUR_GHL_LEAD_REVIEW_LINK`, `YOUR_GHL_AI_ATTENDANT_LINK` and
  `YOUR_GHL_COMPLETE_LINK`. Get the real GHL URLs from Cary. This is the most
  urgent funnel fix.
- The $100 setup fee isn't shown anywhere on the site. Cary said "yes" to adding
  it, so do that as part of the funnel work.
- `main` still has older template placeholders (Calendly, Web3Forms key,
  phone/WhatsApp, social links).
- Deploys are manual uploads to Hostinger `public_html`. Proposed: push-to-deploy
  from GitHub (Hostinger FTP/SSH credentials as GitHub repo **secrets**; the repo
  is public) plus a daily live-site check for dead links, leftover `YOUR_...`
  text, and the contact form. Solar or Tiny homes may have the Hostinger
  credentials, so ask them.

## Loose ends
- Homes repo branch `claude/automate-3m8whz` came from a misread (GitHub
  Actions deploy + health check for homes.gemzonline.com). It's unmerged and
  never deployed; Tiny homes owns that repo and can keep it or delete it.
- Cary's Gmail draft "Awesome" is the original source of the pricing model.
