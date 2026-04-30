# 07 — Build Checklist & DNS

Step-by-step from "GHL account exists" to "launched."

---

## Phase 1 — Account prep (Day 1, ~1 hour)

- [ ] Confirm GHL plan supports custom domains + funnels (Starter is fine).
- [ ] Create a **Sub-account / Location** named `Joelle Merschman — You Are Loved` (or use existing).
- [ ] In **Settings → Business Info**, set business name, support email, physical mailing address (required by CAN-SPAM and ConvertKit).
- [ ] In **Settings → Email Services**, verify the sending domain `faithfirstleadership.com` (DKIM, SPF — see DNS section below).
- [ ] In **Settings → Tracking Code**, paste GA4 + Meta Pixel snippets.
- [ ] In **Sites → Cookie Settings**, enable cookie banner with GDPR + CCPA modes.

## Phase 2 — Build the funnel (Day 1–2, ~3 hours)

- [ ] Create funnel `You Are Loved`.
- [ ] Page 1: `/` — Landing. Build per `01-landing-page.md`.
- [ ] Page 2: `/free-chapter` — Opt-in. Build per `02-optin-page.md`.
- [ ] Page 3: `/free-chapter/thank-you` — Thank-you. Build per `03-thankyou-page.md`.
- [ ] Set the **opt-in form** redirect to the thank-you page.
- [ ] Mobile-preview every page; tighten the spacing scale.
- [ ] Add favicon (32x32 + 192x192) — generated from book cover.
- [ ] Add OG image to each page (cream background + cover).

## Phase 3 — Assets (Day 2)

- [ ] Upload Joelle's headshot to **Media Library**.
- [ ] Upload book cover (transparent PNG preferred).
- [ ] Upload the prismatic rainbow image (full-res + a pre-faded version at 25% opacity for the hero corner).
- [ ] Upload Chapter 1 PDF — name it `you-are-loved-chapter-1.pdf`. Get the public URL.
- [ ] Replace `LINK_TO_CHAPTER_PDF` in:
  - GHL workflow Step-5 email
  - ConvertKit Email 1
- [ ] Replace `AMAZON_LINK` in:
  - Landing page hero secondary CTA
  - Landing page closing CTA
  - Thank-you page primary button
  - ConvertKit Emails 1, 4, 5
- [ ] Replace all `[PLACEHOLDER]` blocks: bio, early-reader quotes, story sections in Email 2 and 3, real chapter titles in Section 4 of the landing page.

## Phase 4 — Automation (Day 2–3, ~2 hours)

- [ ] Create the 5 GHL tags listed in `05-ghl-automation.md`.
- [ ] In ConvertKit, create form `Free Chapter — You Are Loved` and matching tags.
- [ ] Build ConvertKit visual automation (sequence + tag flow).
- [ ] Author the 5 emails in ConvertKit. Send a test of each to yourself. Read each on mobile.
- [ ] Wire GHL → ConvertKit (Option A: Zapier, or Option B: Webhook). Test with a real email.
- [ ] Build the GHL workflow `Free Chapter — Deliver + Sync to ConvertKit`.
- [ ] End-to-end test:
  - Submit the opt-in form with a fresh email.
  - Verify GHL contact created with correct tags.
  - Verify ConvertKit subscriber created with correct tags.
  - Verify GHL Step-5 email arrives within 1 minute.
  - Verify ConvertKit Email 1 arrives within ~5 minutes.
  - Click Amazon link in Email 1. Verify `clicked-amazon-cta` tag applies.

## Phase 5 — Domain + DNS (Day 3)

The domain is `faithfirstleadership.com`. Decide if this funnel lives at:

- **Apex** (`faithfirstleadership.com`) — recommended if the book funnel *is* the main site for now.
- **Subdomain** (`book.faithfirstleadership.com`) — recommended if there's already a Faith First Leadership site at the apex.

### If apex (`faithfirstleadership.com`)

In your DNS provider (wherever the domain is registered):

| Type | Name | Value |
|---|---|---|
| A | `@` | (GHL's IP — copy from GHL → Sites → Domains) |
| CNAME | `www` | `faithfirstleadership.com` |

In GHL → **Sites → Domains → Add Domain** → enter `faithfirstleadership.com` → follow the verification flow.

### If subdomain (`book.faithfirstleadership.com`)

| Type | Name | Value |
|---|---|---|
| CNAME | `book` | (GHL's hostname — copy from GHL) |

### Email-sending DNS (required either way, on the apex)

ConvertKit and GHL both want to send as `@faithfirstleadership.com`. Add:

| Type | Name | Value | Source |
|---|---|---|---|
| TXT (SPF) | `@` | `v=spf1 include:mailgun.org include:_spf.kit.com ~all` | Combined GHL (Mailgun) + ConvertKit |
| CNAME (DKIM, GHL) | `mta._domainkey` | Provided by GHL | GHL → Email Services |
| CNAME (DKIM, Kit) | `kit._domainkey` | Provided by ConvertKit | Kit → Account → Email |
| TXT (DMARC) | `_dmarc` | `v=DMARC1; p=none; rua=mailto:dmarc@faithfirstleadership.com` | Start at `p=none`, tighten later |

> If a single SPF record gets long, use ConvertKit's recommended `include:_spf.kit.com` syntax exactly as their docs show; do not have two separate SPF TXT records — that breaks SPF.

Wait 30–60 minutes for DNS to propagate. Then verify in both GHL and ConvertKit that the domain shows green.

## Phase 6 — Pre-launch QA (Day 4)

- [ ] Open the live `/` page on iPhone Safari, Android Chrome, desktop Chrome, desktop Safari, desktop Firefox. Look for layout breaks.
- [ ] Tap every CTA. Confirm it goes where it should.
- [ ] Submit the form on each device. Confirm the email arrives.
- [ ] Test with Gmail, Outlook, iCloud, and Yahoo addresses (deliverability varies).
- [ ] Check that none of the test emails landed in Promotions/Spam. If they did: confirm DKIM is verified, lower image-to-text ratio, send a "warmup" broadcast to your existing list before launch.
- [ ] Run [Mail-Tester](https://www.mail-tester.com/) on Email 1 of the sequence — aim for 9+/10.
- [ ] Run a Lighthouse audit on `/` — target 90+ on Performance, 100 on Accessibility.
- [ ] Verify GA4 + Meta Pixel are firing (use GA4 DebugView and Meta Pixel Helper extension).
- [ ] Re-read every page and email out loud. Anything that sounds like a marketer wrote it: rewrite it.

## Phase 7 — Soft launch (Day 5)

- [ ] Send the URL to 5–10 trusted people. Ask: *"Does this feel like me? Anything land wrong?"* Take notes.
- [ ] Fix anything obvious.
- [ ] Then announce to the existing list / socials.

## Phase 8 — Post-launch (week 2+)

- [ ] After ~50 opt-ins, look at ConvertKit open + click rates. If Email 1 < 50% open, fix subject line. If Email 5 < 5% click, rewrite the CTA section.
- [ ] After ~200 opt-ins, A/B test the landing page headline.
- [ ] Add a workbook upsell (see `05-ghl-automation.md` §4) when ready.
- [ ] Tighten DMARC: `p=none` → `p=quarantine` after 2–4 weeks of clean sending.

---

## What's blocked / TODOs the user owns

- Real bio paragraphs and headshot file.
- Real chapter titles for Section 4 of the landing page.
- 2–3 real early-reader quotes (or hide that section).
- Joelle's personal story for Email 2.
- Amazon paperback URL (with Associates tag if applicable).
- Chapter 1 PDF file.
- Decision: apex or subdomain.
- ConvertKit account + API key (or Zapier account if going that route).
- GA4 measurement ID + Meta Pixel ID (if using).
