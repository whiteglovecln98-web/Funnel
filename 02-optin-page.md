# 02 — Free Chapter Opt-in Page

URL: `https://faithfirstleadership.com/free-chapter`

This is a single-purpose page. No nav, no distractions. One job: capture an email and deliver Chapter 1.

---

## Layout

Single column, centered, max 640px. Cream `#FAF6EE` background. The prismatic rainbow image used **only** as a small (≈120px) circular accent above the headline — like a sunrise medallion. Nothing else competes.

No header navigation. No footer beyond a privacy line.

---

## Copy

**Small accent image** (the rainbow art, circular crop, soft outer glow)

**Eyebrow (small caps, muted):**
> Free chapter from *You Are Loved*

**Headline (serif, 44–56px):**
> The first chapter is yours.

**Subhead (sans, 18–20px):**
> Tell me where to send it. I'll email it to you in the next minute or two — no fluff, no follow-up storm. Just the chapter.

**Form** (two fields stacked, full-width, generous padding):

- First name *(label: "What should I call you?")*
- Email *(label: "Where should I send it?")*
- **Button:** Send Me the Chapter →

**Below the button (tiny grey text):**
> I'll add you to occasional notes from Joelle. Unsubscribe anytime, in one click. I will never sell your email — that's a real promise, not a checkbox.

**Below that (even smaller):**
> Already read it? Get the paperback on Amazon →

---

## Form behavior (GHL)

- Fields: `first_name`, `email`
- On submit:
  1. Create/update contact in GHL.
  2. Tag contact: `book-optin-free-chapter`, `source-landing-page`
  3. Trigger workflow: **"Free Chapter — Deliver + Sync to ConvertKit"** (see `05-ghl-automation.md`).
  4. Redirect to `/free-chapter/thank-you`.

- Double opt-in: **off** (one-step opt-in keeps deliverability of the chapter immediate; ConvertKit can re-confirm later if desired).
- reCAPTCHA: **on** (GHL native, invisible).

---

## Validation / errors

- Email format check inline.
- If contact already exists with this email + tag, still submit (re-deliver chapter; do not double-add to nurture — workflow handles dedupe with an `If/Else` on tag presence).
- On error: keep field values; show a friendly inline message: *"Something hiccuped on our end — try once more?"*

---

## SEO / meta

- Title: `Free Chapter — You Are Loved | Joelle Merschman`
- Description: `Read the first chapter of "You Are Loved — When Faith Feels Complicated" free. A gentle, honest book for anyone whose faith has gotten messy.`
- OG image: book cover on cream background with the rainbow accent.
- Canonical: this URL.
- `noindex` if you don't want the opt-in indexed (recommended; the main `/` page is the SEO target).
