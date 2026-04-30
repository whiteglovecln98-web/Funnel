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
│   └── 05-nurture-day10.md     # Day 10: "Soft Surrender" + final book nudge
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

Optional refinements:

- Add an **If/Else** branch after step 4: if the contact has tag `book-purchaser`,
  skip the Amazon CTA emails and route them into a thank-you/review-request branch.
- Add a **link-click trigger** on the Amazon URL (`https://www.amazon.com/dp/B0GX2XLSRZ`)
  that adds the tag `clicked-amazon-cta` for retargeting.

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
