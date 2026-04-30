# Email 7 — Amazon Review Request

**Trigger:** 7 days after Email 6 (post-purchase branch)
**From:** Joelle Merschman <hello@yourdomain.com>

---

## Subject line options
- A small favor (it really helps) 🙏
- Would you do this one little thing for me?
- 60 seconds, if you’re willing

## Preheader
A short, honest review on Amazon helps another tender heart find this book.

---

## Body

Hi {{contact.first_name | default: "friend"}},

I have a small ask, and I’ll be honest with you about why.

If *You Are Loved* has met you somewhere — even in just one chapter — would you consider leaving a short review on Amazon?

Here’s the truth: independent and faith-centered books like this one don’t have huge marketing engines behind them. They live and die by readers like you. A 2-sentence Amazon review is genuinely the kindest, most powerful thing you can do to help this book find the next person who needs it.

You don’t have to write anything fancy. The reviews that move the needle most are the simple, honest ones:

> *“This book met me in a complicated season. The chapter on _____ wrecked me in the best way.”*

That’s it. Truly.

👉 **[Leave a quick review on Amazon](https://www.amazon.com/dp/B0GX2XLSRZ)**

(Scroll to **“Write a customer review”** on the product page.)

Even one or two sentences is enough. And if it’s not your season for this — no pressure at all. You being here, reading these words, is already a gift.

Thank you for being part of the reason this book exists in the world.

With so much love,
Joelle

P.S. If you do leave a review, hit reply and let me know — I’d love to thank you personally. 💛

---

## Notes for GHL setup
- Wait step before this email: **7 days** after Email 6.
- Add tag on link click: `clicked-review-link`.
- This is the final scheduled email in the post-purchase branch.
- Tag contact `purchase-flow-complete` after send.
