# 05 — GHL Automation + ConvertKit Integration

This file specifies the workflows, tags, and integrations to wire up inside GoHighLevel and ConvertKit.

---

## 1. Tags (create these in GHL first)

GHL → **Contacts → Smart Lists → Tags** → create:

- `book-optin-free-chapter` — anyone who submitted the opt-in form.
- `source-landing-page` — submitted from `/free-chapter` (vs. future ad LPs).
- `synced-to-convertkit` — successfully pushed to ConvertKit.
- `clicked-amazon-cta` — clicked an Amazon link from email or thank-you page.
- `completed-welcome-seq` — finished the 5-email sequence.

In **ConvertKit**, create matching tags so segmenting stays consistent:

- `book-optin-free-chapter`
- `source-landing-page`
- `clicked-amazon-cta`
- `completed-welcome-seq`

Also create one **Form** in ConvertKit named `Free Chapter — You Are Loved` (an "incoming form" that exists only to trigger the sequence — no public-facing UI). Note its **Form ID** for the integration step.

---

## 2. ConvertKit ↔ GHL integration

GHL doesn't have a native ConvertKit app, so use one of these (pick **one**):

### Option A — Zapier (simplest, $0–$20/mo)

1. **Trigger:** GHL → "Inbound Webhook" or "New Contact with Tag" → tag `book-optin-free-chapter`.
2. **Action:** ConvertKit → "Add Subscriber to Form" → Form ID = `Free Chapter — You Are Loved`. Pass `email`, `first_name`, and tags `book-optin-free-chapter`, `source-landing-page`.
3. **Action 2:** GHL → "Add Tag to Contact" → `synced-to-convertkit`.

### Option B — Direct webhook from GHL (no Zapier)

In a GHL workflow, add a **"Webhook"** action that POSTs to ConvertKit's API:

```
POST https://api.convertkit.com/v3/forms/{{CONVERTKIT_FORM_ID}}/subscribe
Content-Type: application/json

{
  "api_key": "{{CONVERTKIT_API_KEY}}",
  "email": "{{contact.email}}",
  "first_name": "{{contact.first_name}}",
  "tags": [{{TAG_ID_BOOK_OPTIN}}, {{TAG_ID_SOURCE_LP}}]
}
```

Get `api_key` from ConvertKit → **Settings → Advanced → API**.
Get tag IDs by calling `GET https://api.convertkit.com/v3/tags?api_key=...` once (or copy from the URL when editing each tag).

> Recommendation: **Option B** if you're comfortable with one-time copy/paste of an API key; **Option A** if not. Either is fine.

---

## 3. GHL Workflow — "Free Chapter — Deliver + Sync to ConvertKit"

GHL → **Automation → Workflows → Create**.

**Trigger:**
- *Form Submitted* → Form: `Free Chapter Opt-in` (the one on `/free-chapter`).

**Steps (in order):**

1. **Add Tag** → `book-optin-free-chapter`, `source-landing-page`.
2. **If/Else** → branch on tag `synced-to-convertkit`:
   - **Yes (already synced):** skip to step 5.
   - **No (first time):** continue.
3. **Webhook** (Option B above) — push to ConvertKit form.
4. **Add Tag** → `synced-to-convertkit`.
5. **Send Email (GHL native)** — instant chapter delivery (see template below). Even though ConvertKit also kicks off Email 1 of the sequence, the GHL email is the safety net: it goes immediately, from your domain, with the PDF as an attachment or a stable hosted link. ConvertKit's Email 1 then arrives a few minutes later as the official "from Joelle" note.
6. **Wait 2 minutes**.
7. **Internal notification** (email or SMS to Joelle) — optional, can be turned off after launch:
   > New free-chapter opt-in: {{contact.first_name}} — {{contact.email}}

**End workflow.**

### Step-5 GHL email template — "Your Chapter (instant)"

> **Subject:** here's your chapter (just in case the longer note is slow)
>
> Hi {{contact.first_name}},
>
> Your copy of Chapter 1 of *You Are Loved* is right here:
>
> → [Read Chapter 1 (PDF)](LINK_TO_CHAPTER_PDF)
>
> A longer note from me is on its way separately in the next few minutes — keep an eye out.
>
> — Joelle

---

## 4. Stripe note

Stripe was selected as a sales channel originally, but the chosen funnel structure is **free chapter → Amazon paperback** with no digital upsell. So Stripe is **not wired up** in this version. If you later add a digital workbook or audiobook upsell, the natural place to insert it is:

- A new page at `/free-chapter/companion-offer` shown *between* the opt-in submit and the thank-you redirect.
- A GHL → Stripe product + checkout, with a workflow branch that tags `purchased-workbook` and excludes those subscribers from the Email 5 Amazon push (or replaces it with a thank-you).

Leaving this as a clearly marked TODO so the current launch isn't blocked.

---

## 5. ConvertKit Visual Automation

In ConvertKit → **Automate → Visual Automations → New**.

```
[ Trigger: Joins form "Free Chapter — You Are Loved" ]
            │
            ▼
[ Add tag: book-optin-free-chapter ]
            │
            ▼
[ Email sequence: "You Are Loved — Welcome" (5 emails, see 04-email-sequence.md) ]
            │
            ▼
[ Add tag: completed-welcome-seq ]
            │
            ▼
[ Move to: Broadcast list "Joelle — General" ]
            │
            ▼
[ End ]
```

Click events on `AMAZON_LINK` inside any sequence email apply tag `clicked-amazon-cta` (set this on each link's "Trigger automation on click" option).

---

## 6. Tracking & analytics

Install once, in GHL → **Settings → Tracking Code**:

- **Google Analytics 4** — measurement ID `G-XXXXXXXX`.
- **Meta Pixel** — pixel ID `XXXXXXXXXX`.
- **GHL native events** — already on by default.

Events to fire:

| Event | Where | Pixel/GA4 mapping |
|---|---|---|
| `view_landing` | `/` page load | GA4 page_view |
| `lead` | After opt-in submit (on thank-you page) | Meta `Lead`, GA4 `generate_lead` |
| `outbound_amazon_click` | Amazon button click on `/free-chapter/thank-you` | Meta `ViewContent` (custom), GA4 `select_content` |

Use GHL's "Custom Code" block on each page to fire pixel events on load, and `onclick` on Amazon buttons.

---

## 7. Compliance

- Privacy policy at `/privacy` (GHL has a generator under **Sites → Legal**).
- Terms at `/terms`.
- ConvertKit physical mailing address required at the bottom of every email — set in **Account Settings → General**.
- Cookie banner: GHL → **Sites → Cookie Settings** → enable. Configure for GA + Meta.
