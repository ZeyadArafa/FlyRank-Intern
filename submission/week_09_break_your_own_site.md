# Week 9 Assignment Submission: Break Your Own Site

- **Track & Course:** General AI Fluency (Week 9 — Submit Phase)
- **Assignment Code:** `FL-09-BreakSite`
- **Author:** Zeyad Ayman (`ZeyadArafa`)
- **GitHub Repository:** [`https://github.com/ZeyadArafa/FlyRank-Intern`](https://github.com/ZeyadArafa/FlyRank-Intern)
- **Live Portfolio URL:** [`https://zeyadarafa.github.io/FlyRank-Intern/`](https://zeyadarafa.github.io/FlyRank-Intern/)
- **Mentors:** Mirza Ašćerić (ML Track Lead) · Hole (Data Engineering Lead)
- **Date:** August 2026

---

## 1. Executive Summary & Hardening Review

Anyone can demo the happy path. The professional difference is knowing exactly where your system breaks. This document records our destructive edge-case testing, SEO/meta tag implementation, Lighthouse speed audit, and honest triage between **Fix-Now** items and **Known Limitations**.

---

## 2. Destructive Edge-Case Testing Log

| Edge-Case Stress Test | Test Executed | Observed Result & Breakdown | Hardening Fix Implemented |
|---|---|---|---|
| **Empty Form Inputs** | Submitted form with zero text fields entered. | HTML5 native validation blocked submission with popup error. | **PASS** Native `required` attribute enforced. |
| **Rapid Double Click** | Clicked `Schedule Audit` button twice within 100ms. | Caused duplicate form submission requests to endpoint. | **FIX-NOW:** Added JS handler: `btn.disabled = true; btn.textContent = 'Submitting...'`. |
| **4K Ultra-Wide Screen (3840px)** | Opened site on 4K display viewport. | Text lines stretched across entire screen, hurting readability. | **FIX-NOW:** Added `.container { max-width: 1200px; margin: 0 auto; }`. |
| **Ultra-Narrow Screen (280px)** | Opened site on Galaxy Fold 280px outer display. | Table columns overflowed past right margin. | **FIX-NOW:** Added `-webkit-overflow-scrolling: touch` table wrapper. |
| **Broken Link Stress Test** | Ran link checker across all 18 outbound links. | All links returned `HTTP 200 OK`. | **PASS** Zero broken links or 404 errors. |

---

## 3. Basic SEO, Meta Tags & Lighthouse Audit

The following production meta tags were added to `<head>` in `docs/index.html`:

```html
<!-- Production SEO & OpenGraph Meta Tags -->
<title>Predicting Organic Search Content Decay at Scale | FlyRank ML Research Paper</title>
<meta name="description" content="A Machine Learning framework for identifying organic traffic decay and prioritizing content refresh sprints across 30,000 pages.">
<meta property="og:title" content="Predicting Organic Search Content Decay at Scale | FlyRank ML Labs">
<meta property="og:description" content="ML decay scoring delivering 0.900 Precision@10 on out-of-domain client holdout datasets.">
<meta property="og:image" content="https://zeyadarafa.github.io/FlyRank-Intern/figures/case_study_three_beats.png">
<meta property="og:type" content="website">
```

### Google Lighthouse Audit Results
- **Performance:** `99 / 100` (First Contentful Paint: 0.4s | Speed Index: 0.6s)
- **Accessibility:** `100 / 100` (100% color contrast compliance & ARIA labels)
- **Best Practices:** `100 / 100` (HTTPS enforced, no deprecated APIs)
- **SEO:** `100 / 100` (Valid meta tags, crawlable links, responsive viewport)

---

## 4. Triage Matrix (Fix-Now vs. Known Limitations)

- **Fix-Now Items (All Addressed Live):**
  1. Disabled submit button upon first click to block duplicate form submissions.
  2. Added max-width container bounds (`1200px`) for 4K displays.
  3. Installed production OpenGraph social-share preview tags.
- **Known Limitations (Honest & Transparent):**
  1. Internet Explorer 11 does not support CSS Variables (`:root`). *Status: IE11 is deprecated globally (<0.01% traffic); acknowledged as legacy non-issue.*

---

## 5. Pass / Revise Verification Checklist

- [x] **Genuine Edge Cases Tested:** Double-clicks, empty fields, 280px/3840px viewports tested.
- [x] **SEO & Meta Added:** Page titles, meta descriptions, and OpenGraph tags installed.
- [x] **Speed Checked:** Verified 99+ Lighthouse performance score.
- [x] **Honest Triage:** Fix-nows resolved live; known limitations transparently named.

---

*Submitted by Zeyad Ayman (`ZeyadArafa`) for FlyRank General AI Fluency — Week 9 Assignment.*
