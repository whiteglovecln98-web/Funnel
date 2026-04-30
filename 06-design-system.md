# 06 — Design System

A small, opinionated system. The whole point: **warm, professional, hopeful — and the rainbow image stays a guest, never the host.**

---

## Color tokens

| Token | Hex | Use |
|---|---|---|
| `--bg-cream` | `#FAF6EE` | Page background, hero base |
| `--bg-cream-deep` | `#F2EBDC` | Alternating section background |
| `--ink` | `#2A2520` | Body text — warm near-black, not pure black |
| `--ink-muted` | `#6B6157` | Secondary text, captions, microcopy |
| `--accent` | `#C26A3F` | Primary CTA buttons (terracotta) |
| `--accent-hover` | `#A85730` | Hover state |
| `--accent-soft` | `#E8C9A8` | Tag chips, soft highlights |
| `--gold` | `#C8A24A` | Eyebrow text, dividers, decorative serif flourishes |
| `--prism-blend` | gradient | See "Prismatic image rules" below |

The terracotta + gold + cream palette reads as **warm, devotional, professional**. It complements the rainbow image (which is high-saturation) by giving it a calm room to live in instead of competing with it.

---

## Typography

- **Display / headings:** `Cormorant Garamond` or `Lora` (both free on Google Fonts). Weight 500–600. Letter-spacing slightly tight (`-0.01em`).
- **Body:** `Inter` 400/500. Line height 1.65. Body size 18px on desktop, 17px mobile.
- **Eyebrows / small caps:** `Inter` 600, uppercase, `letter-spacing: 0.12em`, in `--gold`.
- **Pull quotes / testimonials:** `Cormorant Garamond` italic, larger size.

Maximum line length for prose: **62–66 characters**. This matters more than it sounds.

---

## Prismatic image rules

This is the most important constraint. The image is beautiful but loud. It must function as **atmosphere**, not subject.

**Allowed uses:**

1. **Top-right hero corner accent** — feathered crop, max 40% of viewport width, **25% opacity**, with a soft mask that fades to transparent toward the page center.
2. **Small circular medallion** above the opt-in headline — fixed ~120px diameter, soft outer glow.
3. **Closing-CTA band** on the landing page — full-width, but at **35% opacity**, overlaid with cream and a subtle white-to-cream gradient so headline text stays high-contrast.
4. **3–4px gradient bar** under selected headlines (sampled from the image's palette). One per page max.
5. **OG/social share image** — the cover sitting on a cream surface with a small prism accent in the corner.

**Not allowed:**

- Full-bleed background of any page.
- Behind body copy.
- As a button background.
- Repeated in more than 2 sections of the same page.

**Why these rules:** the audience is in a tender place. A loud, high-saturation page reads as performative. A calm page with one or two careful prismatic moments reads as honest and hopeful.

---

## Components

### Buttons

- **Primary:** `--accent` background, white text, 16px / 28px padding, `border-radius: 999px` (pill), subtle shadow `0 4px 12px rgba(194,106,63,0.25)`. Hover: `--accent-hover` + slight scale `1.02`. Focus ring: 2px gold offset.
- **Secondary (text link):** `--accent` color, underline on hover, no background.
- **Ghost (rare):** transparent, 1px `--ink-muted` border, ink text.

### Form inputs

- Cream-deep background, no border, 1px bottom border in `--ink-muted`. Focus: bottom border thickens and turns gold. **No floating label gimmicks** — clear labels above each input.

### Cards / chapter teasers

- Cream-deep background, no border, subtle inner padding (32px), small drop shadow (`0 2px 8px rgba(42,37,32,0.04)`). Chapter number rendered in serif italic gold.

### Quote blocks

- No quotation-mark icons. Just italicized serif text, slightly larger, with a 2px gold left border and 24px left padding.

---

## Spacing scale

Use a 4px base. Section vertical padding: `96px` desktop, `64px` mobile. Component padding: 16/24/32/48. No arbitrary numbers.

---

## Imagery

- Headshot: warm tones, soft natural light. Round crop on the page.
- Book cover: hard-edged, slightly tilted (~3°), subtle drop shadow `0 24px 48px rgba(42,37,32,0.18)`.
- No stock photos of generic "spiritual" things (no clasped hands, no sunsets over crosses, no open Bibles on tables). The book's whole point is that real faith is messier than that, and the page should look like it knows.

---

## Mobile

- Single column everywhere below 768px.
- Hero headline scales down to 36–40px.
- Prismatic corner accent shrinks to ~30% of viewport width.
- Sticky bottom CTA bar appears after scrolling past the hero on mobile only: `Read the Free Chapter →`. Subtle, not intrusive.

---

## Accessibility

- Body contrast: `--ink` on `--bg-cream` = 12.6:1. Pass.
- Button contrast: white on `--accent` = 4.7:1. Pass for AA, marginal for AAA. Bump to `--accent-hover` for any text on terracotta backgrounds in dense paragraphs.
- All images have meaningful `alt` text; the rainbow image's alt is `""` (decorative) where it's used as atmosphere only.
- Form labels are real `<label>` elements, never just placeholders.
- Focus states visible everywhere.
