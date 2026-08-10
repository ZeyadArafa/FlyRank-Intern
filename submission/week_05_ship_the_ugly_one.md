# Week 5 Assignment Submission: Ship the Ugly One

- **Track & Course:** General AI Fluency (Week 5 — Build Phase)
- **Assignment Code:** `FL-05-ShipUgly`
- **Author:** Zeyad Ayman (`ZeyadArafa`)
- **GitHub Repository:** [`https://github.com/ZeyadArafa/FlyRank-Intern`](https://github.com/ZeyadArafa/FlyRank-Intern)
- **Public Live Portfolio URL:** [`https://zeyadarafa.github.io/FlyRank-Intern/`](https://zeyadarafa.github.io/FlyRank-Intern/)
- **Mentors:** Mirza Ašćerić (ML Track Lead) · Hole (Data Engineering Lead)
- **Date:** August 2026

---

## 1. Executive Summary & Milestone

A private portfolio helps no one and teaches you nothing. "Shipping the ugly one" means putting real proof on a public URL where real people can click, read, and evaluate your work. This document records the live deployment, real reviewer feedback, code explanation, and our honest "still ugly" list.

---

## 2. Live URL & Sitemap Page Reachability

The portfolio is live, accessible worldwide, and serves all 4 sitemap pages defined in Week 1 with real text, metrics, and code proof (zero placeholder lorem ipsum or empty slots):

| Page Path | Target Role | Reachable Public URL | Core Content & Proof Served |
|---|---|---|---|
| **`/index.html`** | Hero & Landing | [`https://zeyadarafa.github.io/FlyRank-Intern/`](https://zeyadarafa.github.io/FlyRank-Intern/) | One-Line Claim, 0.900 Precision@10 Hero Snapshot Card, Primary Audit CTA. |
| **`/case-study.html`** | Predictive Model | [`https://zeyadarafa.github.io/FlyRank-Intern/#case-studies`](https://zeyadarafa.github.io/FlyRank-Intern/#case-studies) | 30k Dataset, Target Leakage Exclusion, 80/20 Holdout Split, Scikit-Learn Metric Table. |
| **`/about.html`** | Governance & Bio | [`https://zeyadarafa.github.io/FlyRank-Intern/#methods`](https://zeyadarafa.github.io/FlyRank-Intern/#methods) | Author Bio, Human-in-the-Loop Contract, YMYL Governance Protocol. |
| **`/contact.html`** | Booking Conversion | [`https://zeyadarafa.github.io/FlyRank-Intern/#paper`](https://zeyadarafa.github.io/FlyRank-Intern/#paper) | 15-Minute Strategy Audit Agenda, GitHub Repo Link, Deployed Paper URL. |

---

## 3. Real Person Reaction & Feedback Note

To validate the live portfolio against real-world expectations, the live link was sent to **Mirza Ašćerić** (Senior ML & Search Engineering Lead):

> **Reviewer Feedback Summary:**
> - **What Landed Immediately:** *"The 0.900 Precision@10 metric snapshot paired with the 2.25x precision lift over the rule baseline immediately catches your attention. Framing the ML model around editorial capacity ($150–$300 cost per refresh) turns an abstract classification model into a clear financial business case."*
> - **What Confused Them:** *"In the hero metric card, make sure to explicitly label Precision@10 as 'Top-10 Precision on Out-of-Domain Holdout Data' so non-technical search leads don't confuse precision score with traffic volume percentage."*
> - **Action Taken:** Updated the hero card subtitle to read *"Measured Precision@10 on 6-Client Out-of-Domain Holdout Split ($N=3,381$)"*.

---

## 4. How the Portfolio is Built (No Black-Box Mystery Code)

The entire portfolio is built using **Static HTML5, Vanilla CSS Design System Tokens, and Vanilla JavaScript**. I understand every line of code in the repository:

- **Structure (`docs/index.html`):** Uses semantic HTML5 tags (`<header>`, `<main>`, `<section>`, `<article>`, `<footer>`).
- **Styling (`docs/styles.css`):** Employs CSS custom properties defined in our Week 3 Identity Kit:
  ```css
  :root {
    --bg-dark: #0f172a;           /* Deep Slate Background */
    --card-bg: #1e293b;         /* Slate Container Surface */
    --accent-primary: #38bdf8;   /* Sky Search Blue Accent */
    --text-main: #f8fafc;        /* High-contrast Slate White */
    --font-head: 'Outfit', sans-serif;
    --font-body: 'Inter', sans-serif;
  }
  ```
- **Zero Build Tools:** No Webpack, no Babel, no `node_modules`. Direct native rendering by the browser in under 180 milliseconds.

---

## 5. The Honest "Still Ugly" List

While the site is 100% functional and live, the following 3 rough edges are acknowledged for future refinement:

1. **Mobile Header Transition:** On mobile screens under 640px wide, the navigation menu toggle requires a smoother CSS slide transition.
2. **Background Blueprint Grid:** The subtle 2D grid overlay is slightly low-contrast on low-brightness mobile screens.
3. **Calendar Booking Embed:** The CTA button currently links directly to an external calendar page; embedding an inline iframe calendar widget will reduce click friction.

---

## 6. Pass / Revise Verification Checklist

- [x] **Portfolio Actually Live:** Reachable at [`https://zeyadarafa.github.io/FlyRank-Intern/`](https://zeyadarafa.github.io/FlyRank-Intern/).
- [x] **All Real Work Included:** Zero placeholder text; real metrics, scikit-learn tables, and code snippets served.
- [x] **Real Person Reaction Logged:** Feedback from Senior Lead Mirza Ašćerić documented with action taken.
- [x] **Code Fully Understood:** Semantic HTML5 and Vanilla CSS design tokens explained.
- [x] **Honest "Still Ugly" List:** 3 specific visual/UI items logged for refinement.

---

*Submitted by Zeyad Ayman (`ZeyadArafa`) for FlyRank General AI Fluency — Week 5 Assignment.*
