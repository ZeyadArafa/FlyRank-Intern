# Week 7 Assignment Submission: Survive the Crit

- **Track & Course:** General AI Fluency (Week 7 — Build+ Phase)
- **Assignment Code:** `FL-07-SurviveCrit`
- **Author:** Zeyad Ayman (`ZeyadArafa`)
- **GitHub Repository:** [`https://github.com/ZeyadArafa/FlyRank-Intern`](https://github.com/ZeyadArafa/FlyRank-Intern)
- **Live Portfolio URL:** [`https://zeyadarafa.github.io/FlyRank-Intern/`](https://zeyadarafa.github.io/FlyRank-Intern/)
- **Mentors:** Mirza Ašćerić (ML Track Lead) · Hole (Data Engineering Lead)
- **Date:** August 2026

---

## 1. Executive Summary & Design Review Protocol

You cannot see your own portfolio clearly after staring at it for weeks. This assignment documents a formal design critique with Senior ML & Search Lead **Mirza Ašćerić**. The review was evaluated against our Week 1 Proof Statement without defending, and feedback was sorted into Must-Fix items (fixed live) vs. Nice-to-Have ideas.

---

## 2. Initial 10-Second Test Questions & Results

| Initial Review Question | Reviewer Answer (Mirza Ašćerić) | Verdict & Assessment |
|---|---|:---:|
| **1. "In 10 seconds, what do I do?"** | *"You build machine learning search intelligence models that predict content decay across large article datasets to focus editorial refresh capacity."* | **PASS** Core claim landed instantly in under 10 seconds. |
| **2. "Would you believe I'm good at it?"** | *"Yes. The 0.900 Precision@10 vs. 0.400 rule baseline metric table on a 6-client out-of-domain holdout split provides immediate empirical proof."* | **PASS** Technical evidence established credibility. |

---

## 3. Honest Feedback Triage (Must-Fix vs. Nice-to-Have)

### 🔴 Must-Fix Items (Addressed Immediately on Live Site)

1. **Navigation Anchor Scroll Offset:**  
   - *Feedback:* Clicking navigation header links (`#case-studies`, `#methods`) caused the top of section headings to be hidden behind the sticky header bar.  
   - *Fix Implemented:* Added `scroll-margin-top: 85px;` to all section container elements in `docs/styles.css`. Smooth scrolling now stops perfectly below the header bar.
2. **Reason Code Table Clarity:**  
   - *Feedback:* The reason codes (`stale_visible_page`, `low_ctr_visible_page`) required explicit plain-spoken human action definitions inside the table view.  
   - *Fix Implemented:* Updated the metric playbook table in `docs/index.html` to include a dedicated *Recommended Editorial Action* column explaining exact tasks (e.g. rewrite title snippet, expand content depth).

### 🟢 Nice-to-Have Items (Logged for Future Sprints)

1. **Interactive Budget Slider:** Reviewer suggested an interactive slider allowing visitors to adjust weekly article refresh capacity (e.g., 25 vs. 50 vs. 100 articles) to see dynamic ROI calculations. *Status: Logged for v2 release.*

---

## 4. Evidence of Must-Fixes Addressed on Live Site

```css
/* Fix Implemented in docs/styles.css */
section {
  scroll-margin-top: 85px; /* Resolves sticky header overlap */
}
```

```html
<!-- Updated Table Column in docs/index.html -->
<td class="action-desc">
  <strong>Refresh Facts & Dates:</strong> Human editor updates outdated 2024 statistics and case study links.
</td>
```

---

## 5. Pass / Revise Verification Checklist

- [x] **Submitted with Proof Statement:** Reviewed against Week 1 proof statement.
- [x] **10-Second Test Passed:** Reviewer correctly stated core positioning and felt work backed it up.
- [x] **Feedback Sorted Honestly:** Divided into Must-Fix vs Nice-to-Have without defending.
- [x] **Must-Fixes Addressed Live:** Sticky header offset and table column descriptions updated live on GitHub Pages.

---

*Submitted by Zeyad Ayman (`ZeyadArafa`) for FlyRank General AI Fluency — Week 7 Assignment.*
