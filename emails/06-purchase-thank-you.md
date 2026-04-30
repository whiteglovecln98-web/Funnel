# Email 6 — Thank-You for Buying the Book

**Trigger:** Tag `book-purchaser` added to contact
**Send:** Immediately (when entering this branch)
**From:** Joelle Merschman <hello@yourdomain.com>

---

## Subject line options
- Thank you. Truly.
- You picked up the book — here’s a small note 💛
- A quiet thank-you from me to you

## Preheader
Thank you for letting *You Are Loved* into your story.

---

## Body

Hi {{contact.first_name | default: "friend"}},

I just saw you grabbed a copy of *You Are Loved.* I wanted to say something before you turn the first page.

**Thank you.** Genuinely.

When I was writing this book, I imagined someone exactly like you on the other end — someone who knows what it’s like for faith to feel complicated, and who is brave enough to keep showing up to it anyway. The fact that you said *yes* to walking through these pages means more to me than I can say.

A few small things to make the most of it:

- **Take your time.** This book wasn’t built to be sprinted through. One chapter a sitting is plenty.
- **Keep your reflection guide nearby.** The seven-day guide you downloaded pairs beautifully with the early chapters.
- **Underline freely.** Argue in the margins. Cry on a page. This is your copy now.

I’ll check back in with you in about a week with one small ask. Until then — settle in, friend. You’re exactly where you’re meant to be.

With so much love,
Joelle

P.S. If a chapter ever wrecks you in the best way, I would love to hear about it. Hit reply anytime — I read every message myself.

---

## Notes for GHL setup
- This is the first email in the **post-purchase branch**.
- After sending: **Wait 7 days**, then send Email 7 (review request).
- Removes contact from the standard Amazon CTA / nurture branch.
