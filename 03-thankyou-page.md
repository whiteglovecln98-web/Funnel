# 03 — Thank-You Page

URL: `https://faithfirstleadership.com/free-chapter/thank-you`

Goal: confirm the chapter is on its way, set expectations, and softly point readers toward Amazon for the full paperback. **No upsell page** — per scope.

---

## Layout

Single column, centered, max 720px. Same cream base. The book cover sits at the top, slightly tilted, with a soft shadow. Rainbow accent: a thin gradient bar (3–4px) under the headline only.

---

## Copy

**Book cover image (tilted ~3°, ~280px tall)**

**Headline (serif, 40–48px):**
> It's on its way.

**Body:**
> Check your inbox in the next minute or two — Chapter 1 is heading there now. If it doesn't show up, peek in Promotions or Spam and drag it to your main inbox so the next note finds you.

**Subhead (a beat softer):**
> While you wait — a small thing, if you're up for it.

**Body:**
> If reading the chapter is enough for now, that's good. Truly.
>
> If you'd like the whole book in your hands — to mark up, dog-ear, or hand to someone who needs it — the paperback is on Amazon. It's the easiest way to support the work, and it puts the book on more shelves where it's needed.

**Primary button:**
> Get the Paperback on Amazon — $34.99 →

→ Amazon link, opens in new tab. (Use your Amazon Associates link if you have one.)

**Below the button (small):**
> Or just keep an eye on your inbox — there's no wrong way to do this.

---

## Optional: social share row

Three small icon buttons under a quiet line:

> If someone you love is in a hard season of faith, you can pass the free chapter along.

- Share via Email (`mailto:` with prefilled subject + link to `/free-chapter`)
- Share to Facebook
- Share to Text/SMS (`sms:` link, mobile only)

---

## Tracking

- Fire GHL conversion event: `free_chapter_optin_complete`.
- Fire pixel events (if installed): Meta `Lead`, GA4 `generate_lead`.
- Fire `outbound_amazon_click` on the Amazon button (GHL custom event + GA4).

---

## SEO

- `noindex, nofollow` — this is a post-conversion page only.
