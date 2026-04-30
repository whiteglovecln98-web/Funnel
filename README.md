# You Are Loved — Lead Magnet Funnel

A clean, minimal, high-converting lead magnet landing page for the book
**_You Are Loved — When faith feels complicated_** by Joelle Merschman
([Amazon](https://www.amazon.com/dp/B0GX2XLSRZ)).

The funnel offers a free **7-Day Reflection Guide** in exchange for an email,
captured through a GoHighLevel form, and triggers a faith-centered nurture
sequence that ends with a soft Amazon CTA.

---

## What's in this repo

```
.
├── index.html                  # Static landing page (single self-contained file)
├── emails/                     # GHL workflow email copy (paste-ready)
│   ├── 01-welcome-delivery.md  # Instant: deliver the PDF
│   ├── 02-day2-amazon-cta.md   # Day 2: Amazon book CTA
│   ├── 03-nurture-day4.md      # Day 4: "When God Feels Far"
│   ├── 04-nurture-day7.md      # Day 7: "Holding Doubt Gently"
│   ├── 05-nurture-day10.md     # Day 10: "Soft Surrender" + final book nudge
│   ├── 06-purchase-thank-you.md# Post-purchase: thank-you (purchaser branch)
│   └── 07-review-request.md    # +7 days after purchase: Amazon review request
└── devotional/
    └── outline.md              # 7-day reflection guide outline + design notes
```

---

## 1. Hosting the landing page

It’s a single static HTML file. Drop it on any host:

- **Netlify / Vercel / Cloudflare Pages:** drag-and-drop deploy, or connect this repo.
- **GitHub Pages:** enable Pages on the branch, point at root.
- **GoHighLevel Sites:** create a custom HTML page and paste the contents of `index.html`.
- **Any web host:** upload `index.html` to the document root.

No build step. No dependencies.

---

## 2. Wiring up the GoHighLevel form

In GHL:

1. **Sites → Forms → New Form.**
   Fields: First name, Email. Set the success message to *"Your guide is on its way — check your inbox."*
2. After saving, click **Integrate Form → iframe** and copy the embed snippet.
3. In `index.html`, find this block in the hero:
   ```html
   {{GHL_FORM_EMBED}}
   <div class="placeholder-note"> ... </div>
   ```
   Replace the placeholder line **and** the `<div class="placeholder-note">…</div>`
   with your `<iframe …></iframe>` snippet.
4. Optional: in the form settings, **add a tag** on submission, e.g. `lead-magnet-devotional`.
   The workflow below uses that tag as its trigger.

---

## 3. Building the GHL workflow

In **Automation → Workflows → New Workflow**:

| Step | Action | Configuration |
|------|--------|---------------|
| 1 | **Trigger** | Contact tag added: `lead-magnet-devotional` (or "Form Submitted" → your form). |
| 2 | **Send Email** | Use copy from `emails/01-welcome-delivery.md`. Insert public PDF URL where `{{DEVOTIONAL_PDF_URL}}` appears. |
| 3 | **Wait** | 2 days |
| 4 | **Send Email** | `emails/02-day2-amazon-cta.md` |
| 5 | **Wait** | 2 days |
| 6 | **Send Email** | `emails/03-nurture-day4.md` |
| 7 | **Wait** | 3 days |
| 8 | **Send Email** | `emails/04-nurture-day7.md` |
| 9 | **Wait** | 3 days |
| 10 | **Send Email** | `emails/05-nurture-day10.md` |
| 11 | **Add Tag** | `nurture-complete` |

Add a **link-click trigger** on the Amazon URL (`https://www.amazon.com/dp/B0GX2XLSRZ`)
that adds the tag `clicked-amazon-cta` for retargeting.

### 3a. Post-purchase branch (If/Else)

Once a contact is tagged `book-purchaser`, route them out of the Amazon CTA
nurture and into a thank-you + review-request flow.

**Where the tag comes from.** Amazon doesn't expose buyer data, so
`book-purchaser` is added one of three ways:

1. **Self-report link.** In Email 2 (Amazon CTA), include a small line like
   *"Already grabbed it? [Tap here so I can say thank you →]"* pointing to a
   GHL trigger link that adds the `book-purchaser` tag.
2. **Manual tag** when readers reply to say they bought it.
3. **Zap / webhook** if you sell signed copies through Shopify / Stripe / etc.

**Workflow shape:**

```
Trigger: tag added "lead-magnet-devotional"
   │
   ▼
[Email 1] Welcome + deliver PDF
   │
   ▼
Wait 2 days
   │
   ▼
If/Else  ── has tag "book-purchaser"? ──┐
   │ NO                                  │ YES
   ▼                                     ▼
[Email 2] Amazon CTA              [Email 6] Thank-you
   │                                     │
   ▼                                     ▼
Wait 2 days                       Wait 7 days
   │                                     │
   ▼                                     ▼
[Email 3] Nurture day 4           [Email 7] Review request
   │                                     │
   ▼                                     ▼
Wait 3 days                       Add tag: purchase-flow-complete
   │                                    (end)
   ▼
[Email 4] Nurture day 7
   │
   ▼
Wait 3 days
   │
   ▼
[Email 5] Soft surrender + final nudge
   │
   ▼
Add tag: nurture-complete
(end)
```

**Bonus: catching late purchasers.**
Create a second small workflow:

| Step | Action | Configuration |
|------|--------|---------------|
| 1 | **Trigger** | Tag added: `book-purchaser` |
| 2 | **Goal / Remove from workflow** | Remove contact from the main lead-magnet workflow |
| 3 | **Send Email** | `emails/06-purchase-thank-you.md` |
| 4 | **Wait** | 7 days |
| 5 | **Send Email** | `emails/07-review-request.md` |
| 6 | **Add Tag** | `purchase-flow-complete` |

This way, if someone buys the book on day 5 of the nurture, they're pulled out
of the CTA emails and sent down the purchaser path instead — no double-asking.

---

## 4. Hosting the devotional PDF

`devotional/outline.md` contains the full 7-day content, structure, and design specs.

1. Design the PDF in Canva, Figma, or InDesign using the palette in the outline
   (cream background, plum headers, coral accent, gold ornament).
2. Export as `you-are-loved-7-day-guide.pdf`.
3. Upload to **GHL → Media Library** (or Google Drive / S3 with public sharing).
4. Copy the public URL and paste it into Email 1 anywhere `{{DEVOTIONAL_PDF_URL}}` appears.

---

## 5. Replace before launch

- `{{GHL_FORM_EMBED}}` in `index.html` → your GHL iframe snippet.
- `{{DEVOTIONAL_PDF_URL}}` in `emails/01-welcome-delivery.md` → public PDF URL.
- `hello@yourdomain.com` in every email → the verified send address.

That’s the whole funnel. 💛
