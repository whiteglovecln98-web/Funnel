# Local SEO Analysis — janesvillejanitorial.com

> **Update 2026-11-09:** the brands are being separated (Janesville Janitorial = WI, White Glove Cleaning = IL). The schema and action #1 below reflect that. The full plan is in the "Website Split Brief for WTI" doc.

**Audited:** 2026-11-09 · **Entry URL:** whiteglovecleaningandjanitorialservices.com (redirects to janesvillejanitorial.com) · **Platform:** WordPress 7.1.4 + Yoast SEO · **Pages reviewed:** 13

## Local SEO Score: 35/100

| Dimension | Weight | Score | Verdict |
|---|---|---|---|
| GBP signals | 25 | 7 | No link to the Google Business Profile, no reviews widget, no hours. The map is a custom My Maps embed, not your GBP pin |
| Reviews & reputation | 20 | 5 | 4 first-name testimonials. No Google star rating, review count, dates, or "leave a review" link |
| Local on-page | 20 | 12 | Strong service pages and copy. Generic homepage H1. City pages are thin and buried. Beloit has no page |
| NAP consistency & citations | 15 | 6 | Three brand names and two different Facebook URLs. No address anywhere (OK for a service-area business, but it must match GBP) |
| Local schema | 10 | 2 | Only a generic `Organization` from Yoast. No `LocalBusiness`, `areaServed`, phone, hours, or rating |
| Local links & authority | 10 | 3 | Licensed/bonded/insured/background-checked is claimed. No BBB, Chamber, press, or community signals |

**Business type:** Service Area Business (SAB). No street address is published, and the site says "Serving Illinois & Wisconsin" with a city list.
**Vertical:** Commercial janitorial (home-services pattern, B2B). Industries served: office, medical, manufacturing.

---

## What's working (keep it)
- **The copy sells.** "Stop Babysitting Your Cleaning Company" is exactly the pain a property or facility manager feels. Most janitorial sites don't have this.
- **Dedicated service pages** for Office, Janitorial, Medical, Manufacturing, Floor Care, Windows and Custom Programs. Per Whitespark, this is the #1 local organic factor.
- **City pages are genuinely unique.** The city pages share only 1–7% of their content with each other, so there's no doorway-page penalty risk.
- Click-to-call (`tel:815-742-8100`), a free-walkthrough CTA, a clean robots.txt and a Yoast sitemap.
- "Since 1998 / 28+ years" is a real trust asset.

## What's costing you bid requests

### 1. Brand/NAP confusion (Critical)
Google, ChatGPT and buyers see three different names:

| Where | Name shown |
|---|---|
| Site, title tags, schema | Janesville Janitorial |
| Footer, one testimonial | "A Division of White Glove Cleaning Since 1998" |
| TikTok in schema | @whiteglovecln_ |
| Domain you advertise | whiteglovecleaningandjanitorialservices.com |

The Facebook link is also inconsistent: the page links to `facebook.com/profile.php?id=61594573315547`, while the schema says `facebook.com/Janesvillejanitorial/`. **The name on the site must match the name on your Google Business Profile exactly.** Otherwise Google splits your authority between two businesses.

### 2. No path from Google reviews to the site, or back (Critical)
- There's no Google star rating or review count anywhere on the site.
- There's no "Review us on Google" link.
- The 4 testimonials are first-name only, undated and not verifiable, so property managers discount them.
- For B2B janitorial work, a "4.9★ from 37 Google reviews" badge next to the walkthrough button is the single biggest trust lever.

### 3. City pages are invisible (High)
- No city page is linked from the homepage, the nav or any service page. The only path is `/service-area/`.
- `/milton-wi/` is in the sitemap but linked from **nowhere** (an orphan page).
- `/service-area/` repeats the city-page content (1,966 words), so it competes with the city pages for the same searches.
- The city pages are thin (376–460 words) compared with 900+ on the service pages.
- **Beloit** is in your homepage title and meta description but has **no page**. The same goes for Loves Park, Roscoe, Rockton, Freeport, Dixon, Cherry Valley and Winnebago.

### 4. Homepage H1 says nothing to Google (High)
`<h1>One Call. One Solution.</h1>` contains no service and no city. The title tag is good; the H1 throws that work away.

### 5. No LocalBusiness schema (Medium)
Yoast outputs only `Organization`, so AI search tools can't easily read your phone number, service area or services. A ready-to-paste fix is below.

### 6. Messaging inconsistencies (Low)
- The homepage says "28+ years" while the Office page says "20+ years". Pick one.
- The homepage testimonial heading reads "What Says Our Client About Us", which is a grammar error on your most important page. Change it to "What Our Clients Say".

---

## GBP optimization checklist
| Item | Status |
|---|---|
| GBP link from website | ❌ Missing |
| GBP name matches site name exactly | ⚠️ Verify ("Janesville Janitorial" vs "White Glove Cleaning") |
| Primary category = **Commercial cleaning service** | ⚠️ Verify in GBP (wrong primary category is the #1 negative ranking factor) |
| Secondary categories: Janitorial service, Floor refinishing service, Window cleaning service, Carpet cleaning service | ⚠️ Verify |
| Service areas set to the 13 cities you list, with no address shown | ⚠️ Verify |
| Hours listed (site has none) | ❌ Add to the site and GBP |
| Weekly photo uploads (before/afters from jobs) | ⚠️ Verify |
| GBP website link points to `/office-cleaning/` or `/service-area/`, not the homepage | Recommended |
| Bing Places claimed (feeds ChatGPT/Copilot) | ⚠️ Verify |
| Apple Business Connect claimed | ⚠️ Verify |

## Review health snapshot
- **On-site:** 4 testimonials (Amanda C., Dr. Ryan B., Lisa M., Carrie B.). Undated, first name only, no company named.
- **Google rating/count:** not shown on the site, and I couldn't check it from here (see Limitations).
- **Target:** 10+ Google reviews (Sterling Sky's threshold), a 4.5★+ rating, and a new review at least every 2–3 weeks.
- **Never** screen customers' satisfaction before sending the review link ("review gating"). It violates Google policy and the FTC can fine $53,088 per violation.

## Citation presence (Tier 1)
I couldn't check Yelp, BBB, Facebook, Bing or Apple from this environment. Check these yourself, and make sure each one uses the **identical name and phone** (`815-742-8100`):
Google Business Profile · Bing Places · Apple Business Connect · Yelp · BBB · Facebook · LinkedIn · Nextdoor · Thumbtack · Angi · Janesville Area Chamber · Rockford Chamber · Greater Beloit Chamber · ISSA member directory (if you're a member)
Data aggregators: Data Axle, Foursquare, Neustar/TransUnion.

---

## Ready-to-paste LocalBusiness schema
Put this in the homepage via Yoast → Schema, or a header-code plugin. **Replace the `[ ]` placeholders before publishing.**

```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "@id": "https://janesvillejanitorial.com/#localbusiness",
  "name": "Janesville Janitorial",
  "description": "Commercial cleaning and janitorial services for offices, medical facilities and manufacturing plants in southern Wisconsin since 1998.",
  "url": "https://janesvillejanitorial.com/",
  "telephone": "[+1-608 new number]",
  "email": "Joelle@JanesvilleJanitorial.com",
  "logo": "https://janesvillejanitorial.com/wp-content/uploads/2026/07/janesville_logo_badge.png",
  "image": "https://janesvillejanitorial.com/wp-content/uploads/2026/07/janesville_logo_badge.png",
  "foundingDate": "1998",
  "priceRange": "$$",
  "areaServed": [
    "Janesville, WI", "Beloit, WI", "Milton, WI"
  ],
  "openingHoursSpecification": [{
    "@type": "OpeningHoursSpecification",
    "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"],
    "opens": "[08:00]", "closes": "[17:00]"
  }],
  "hasOfferCatalog": {
    "@type": "OfferCatalog",
    "name": "Commercial Cleaning Services",
    "itemListElement": [
      {"@type":"Offer","itemOffered":{"@type":"Service","name":"Office Cleaning","url":"https://janesvillejanitorial.com/office-cleaning/"}},
      {"@type":"Offer","itemOffered":{"@type":"Service","name":"Janitorial Services","url":"https://janesvillejanitorial.com/janitorial-services/"}},
      {"@type":"Offer","itemOffered":{"@type":"Service","name":"Medical Facility Cleaning","url":"https://janesvillejanitorial.com/medical-facilities/"}},
      {"@type":"Offer","itemOffered":{"@type":"Service","name":"Manufacturing Facility Cleaning","url":"https://janesvillejanitorial.com/manufacturing-facilities/"}},
      {"@type":"Offer","itemOffered":{"@type":"Service","name":"Floor Stripping, Waxing & Carpet Extraction","url":"https://janesvillejanitorial.com/floor-care/"}},
      {"@type":"Offer","itemOffered":{"@type":"Service","name":"Commercial Window Cleaning","url":"https://janesvillejanitorial.com/windows/"}}
    ]
  },
  "sameAs": [
    "[YOUR GOOGLE BUSINESS PROFILE URL]",
    "[ONE CORRECT FACEBOOK URL]",
    "https://www.linkedin.com/company/janesvillejanitorial/"
  ]
}
```
Only add `aggregateRating` once you display real Google review numbers on the page. Marking up ratings that aren't visible on the page breaks Google's rules.

---

## Top 10 prioritized actions

| # | Priority | Action | Why it matters for revenue |
|---|---|---|---|
| 1 | Critical | **Split the brands fully**: Janesville Janitorial = Wisconsin, White Glove Cleaning = northern Illinois, each with its own site, phone, email and GBP. See the "Website Split Brief for WTI" doc | Shared identity across two GBPs risks a duplicate-listing suspension |
| 2 | Critical | Add a **Google rating badge plus a "Leave a review" link** to the homepage, the reviews page and the post-service email | Reviews make up ~20% of the map-pack ranking weight, and they're what property managers check first |
| 3 | Critical | **Start a review cadence**: ask every recurring account after 30 days of service and after every strip & wax job. Goal: 2 per month, every month | A few weeks with no new reviews can cost you rankings; steadier competitors hold |
| 4 | High | Change the homepage H1 to **"Commercial Cleaning & Janitorial Services in Janesville, Beloit & Rockford"** and keep "One Call. One Solution." as the subheading | Free ranking signal on your strongest page |
| 5 | High | **Build a Beloit, WI page** (it's in your title but has no page), then Loves Park and Roscoe | Each city page targets its own "commercial cleaning [city]" searches |
| 6 | High | **Link the city pages** from the homepage ("Areas We Serve" row), the footer and each service page. Fix the orphaned Milton page | Pages Google can't reach don't rank |
| 7 | High | Bring each city page up to 700+ words, with one named local client or industry, one local before/after photo and 3 city-specific FAQs | Thin pages lose to competitors with depth |
| 8 | Medium | Add the LocalBusiness schema above | Helps AI tools (ChatGPT, Copilot) read your service area and phone |
| 9 | Medium | Claim and match **Bing Places, Apple Business Connect, BBB and Yelp**. Join one Chamber (Janesville or Rockford) | 3 of the top 5 AI-visibility factors come from listings like these; ChatGPT pulls from Bing, Yelp and BBB |
| 10 | Low | Post hours on the site and GBP. Fix "28+" vs "20+ years". Fix "What Says Our Client" | Credibility polish |

---

## Limitations
I could not check:
- Your actual Google Business Profile (category, rating, review count, photos, Insights)
- Live map-pack positions or geo-grid rankings
- Yelp/BBB/Bing/Apple listings, because this environment blocks those sites
- Backlinks and Domain Authority
- Page speed and Core Web Vitals

To fill those gaps:
- Paste your GBP link and I'll check it.
- Use BrightLocal or Local Falcon for a geo-grid ranking map (~$20–50/mo).
- Use the free Google Search Console and PageSpeed Insights.
