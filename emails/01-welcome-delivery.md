# Email 1 — Welcome + Devotional Delivery

**Trigger:** Form submission on the landing page
**Send:** Immediately
**From:** Joelle Merschman <hello@yourdomain.com>
**Reply-To:** Joelle Merschman <hello@yourdomain.com>

---

## Subject line options
- Your 7-Day Reflection Guide is here 💛
- A soft place to land — your guide is inside
- Welcome, friend. Here’s your guide.

## Preheader
Seven gentle days for the seasons when faith feels complicated.

---

## Body (HTML/plain text)

Hi {{contact.first_name | default: "friend"}},

I’m so glad you’re here.

If you’re anything like me, you’ve had seasons where faith felt clear and close — and others where it felt complicated, distant, or quietly heavy. This little guide is for those in-between days.

**Your free 7-Day Reflection Guide is ready:**

👉 [Download the guide (PDF)]({{DEVOTIONAL_PDF_URL}})

Each day takes less than five minutes. One short reflection. One verse. One gentle prompt. That’s it. No pressure to feel anything in particular — just an invitation to come as you are.

A small encouragement before you begin:
You don’t have to have it all figured out to be deeply, completely loved. That’s the whole heart of this guide — and the book it came from.

I’ll check back in with you in a couple of days with something I think you’ll love. In the meantime, save the PDF somewhere you’ll see it (your desktop, your phone, your favorite reading app), and start whenever you’re ready.

With love,
Joelle

P.S. If the download link doesn’t open, just reply to this email and I’ll send it your way personally.

---

## Notes for GHL setup
- Replace `{{DEVOTIONAL_PDF_URL}}` with the public URL of your hosted PDF (Google Drive share link, S3, GHL media library, etc.).
- Use GHL’s `{{contact.first_name}}` merge tag with a fallback (`| default: "friend"`).
- Add a tag on send: `lead-magnet-devotional`.
