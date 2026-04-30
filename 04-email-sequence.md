# 04 — ConvertKit (Kit) 5-Email Sequence

Sequence name: **You Are Loved — Welcome**
Trigger: Subscriber added to ConvertKit form `Free Chapter — You Are Loved` (created in `05-ghl-automation.md`).
From name: `Joelle Merschman`
Reply-to: a real, monitored inbox. Not `noreply@`.

Tone notes:
- Talk like a friend, not a marketer. Lowercase subject lines feel personal and outperform Title Case for this audience.
- No pressure language. No fake scarcity. No "act now."
- Sign each email simply: *— Joelle*

Merge tags use ConvertKit syntax: `{{ subscriber.first_name | default: "friend" }}`.

---

## Email 1 — Day 0 (immediate) — Deliver the chapter

**Subject:** here's your chapter, {{ subscriber.first_name | default: "friend" }}
**Preview text:** plus one small thing before you read.

**Body:**

Hi {{ subscriber.first_name | default: "friend" }},

Here's the first chapter of *You Are Loved — When Faith Feels Complicated*:

→ **[Read Chapter 1 (PDF)](LINK_TO_CHAPTER_PDF)**

Before you open it, one small thing.

This book wasn't written to argue you back into anything. It wasn't written to fix you, hurry you, or make you perform a tidier version of faith than the one you actually have. It was written for the kind of nights when the words stop working — and you just need someone to say *you are not too far gone, and you are not alone.*

So read it slowly. Read it once and put it down for a week. Read it on the couch with a dog on your feet. There's no wrong way.

I'll write again in a couple of days with a little of the story behind why I wrote it.

— Joelle

P.S. If you'd rather have the whole book in your hands, the paperback is on Amazon — [here](AMAZON_LINK). No pressure either way.

---

## Email 2 — Day 2 — The story behind the book

**Subject:** the chapter i almost didn't write
**Preview text:** the version of God i had to put down first.

**Body:**

{{ subscriber.first_name | default: "Hi friend" }},

There's a chapter in this book I almost didn't write.

For a long time, the version of God I'd been handed was a God who was mostly disappointed in me. Polite about it, but disappointed. The kind of God you keep apologizing to in the back of your own head, every day, just in case.

I don't think I noticed how heavy that was until I tried to put it down.

[PLACEHOLDER — Joelle: 1–2 short paragraphs of personal story here. What was the moment you realized the inherited version of God wasn't working? Keep it specific and small — a kitchen table, a drive home, a hospital hallway. Don't tidy it up.]

If anything in that resonates — that quiet, exhausted feeling of carrying around a God who never quite smiles at you — that's a lot of why this book exists. You're not the only one. You weren't crazy to feel it. And you're not stuck with that version.

Tomorrow's a rest day from me. I'll write again in a couple of days.

— Joelle

---

## Email 3 — Day 4 — Reader words

**Subject:** what one early reader said
**Preview text:** "I cried twice. I wasn't expecting that."

**Body:**

{{ subscriber.first_name | default: "Hi" }},

A few people read *You Are Loved* before it went anywhere, and one of them said something I keep thinking about:

> *[PLACEHOLDER — paste a real early-reader quote here. 2–3 sentences. Someone who isn't famous; someone who sounds like a real person.]*
> — [PLACEHOLDER name, 1-line context]

I'm not sharing that to brag. I'm sharing it because if you're here, on this list, reading these emails — there's a decent chance you're carrying something similar. Doubt that won't quit. Grief about a community you used to belong to. A faith that flickers more than it burns. A long, long question you've been afraid to say out loud.

You're not alone in any of it. That's not a slogan. It's just true.

If you've already read Chapter 1 — what did you sit with? Hit reply and tell me. I read every one.

— Joelle

---

## Email 4 — Day 6 — A deeper hook (one idea from the book)

**Subject:** doubt is not the opposite of faith
**Preview text:** a small idea that changed how i pray.

**Body:**

{{ subscriber.first_name | default: "Hi friend" }},

One short idea today.

For most of my life I thought doubt was the opposite of faith — the thing faith was supposed to push back, beat down, get rid of. If I had questions, I had a problem. If I had a *lot* of questions, I had a *big* problem.

I don't think that anymore.

I think doubt is much closer to *evidence* of faith than its opposite. You don't doubt something you don't care about. You don't argue with a God you don't believe is there. The questions are a sign you're still in the room. The questions are a sign you're still alive.

The opposite of faith isn't doubt. It's indifference. And if you're reading this email, you are clearly not indifferent.

Whatever your questions are right now — they're allowed. You don't have to answer them this week. You don't have to answer them this year. You're allowed to just *carry* them for a while, and still be loved while you do.

I'll write once more in a couple of days.

— Joelle

P.S. This is a tiny piece of one chapter. The whole book sits with these questions much longer. If you'd like it, [it's on Amazon](AMAZON_LINK).

---

## Email 5 — Day 8 — Soft Amazon CTA

**Subject:** if the chapter helped, the book might too
**Preview text:** a simple, no-pressure note.

**Body:**

{{ subscriber.first_name | default: "Hi" }},

This is the last note in this little welcome series, and I want to keep it simple.

If the free chapter helped — if it landed in a tender spot and you'd like to keep reading — the full paperback of *You Are Loved* is on Amazon:

→ **[Get the paperback on Amazon ($34.99)](AMAZON_LINK)**

A few honest notes:
- The paperback is the easiest way to support the work. Each copy puts the book on one more shelf and into one more conversation that needs it.
- If you can't buy it right now, that is genuinely okay. The free chapter is yours to keep, and you'll still hear from me from time to time when there's something worth saying.
- If you've already ordered it — thank you. Truly. A short, honest review on Amazon does more for a book like this than almost anything else.

Whatever you decide: I'm glad you're here.

— Joelle

P.S. After this email, my notes get less frequent — maybe once or twice a month, only when I have something worth your inbox. You can always reply, and you can always [unsubscribe in one click](UNSUBSCRIBE_LINK).

---

## Sequence settings (ConvertKit)

- **Send window:** 9:00 AM subscriber local time. Skip weekends? **No** (these emails are devotional in tone — Sundays often perform well).
- **Re-engage:** Tag-on-open (`engaged-welcome-seq`) so you can segment readers who actually opened.
- **Click tracking:** On.
- **Goal:** click on Amazon link in email 5 → tag `clicked-amazon-cta` → exit sequence (already done).
- **End-of-sequence action:** Add tag `completed-welcome-seq`. Move to broadcast list `Joelle — General`.

## Things to fill in before launch

- `LINK_TO_CHAPTER_PDF` (host the PDF on GHL Files or a cloud bucket; use a stable URL).
- `AMAZON_LINK` (your Amazon Associates short link — replace in **all 5 emails**).
- All `[PLACEHOLDER]` blocks in emails 2 and 3 — Joelle's actual story + a real early-reader quote.
- `UNSUBSCRIBE_LINK` is rendered automatically by ConvertKit; the literal token is just so you can preview it.
