# Week 7 Assignment Submission: Open It on Your Phone

- **Track & Course:** General AI Fluency (Week 7 — Build+ Phase)
- **Assignment Code:** `FL-07-MobileAudit`
- **Author:** Zeyad Ayman (`ZeyadArafa`)
- **GitHub Repository:** [`https://github.com/ZeyadArafa/FlyRank-Intern`](https://github.com/ZeyadArafa/FlyRank-Intern)
- **Live Portfolio URL:** [`https://zeyadarafa.github.io/FlyRank-Intern/`](https://zeyadarafa.github.io/FlyRank-Intern/)
- **Mentors:** Mirza Ašćerić (ML Track Lead) · Hole (Data Engineering Lead)
- **Date:** August 2026

---

## 1. Executive Summary & Mobile-First Audit

The jump from "amateur" to "trustworthy" is a short, disciplined checklist almost everyone skips. This document logs the mobile-first accessibility and responsiveness audit conducted on a real smartphone and across simulated viewports (375px, 414px, 768px, 1280px). All broken layouts, small touch targets, and table overflows were systematically fixed.

---

## 2. Mobile Audit Fix Log (Before vs. After)

| Audit Category | Identified Issue (Before) | Fix Implemented (After) | Verification Result |
|---|---|---|:---:|
| **Hero Heading Sizing** | `<h1>` font size was 2.8rem, causing awkward 1-word text wraps on 375px screens. | Added media query: `@media (max-width: 640px) { h1 { font-size: 1.85rem; line-height: 1.25; } }`. | **PASS** Clean 3-line heading layout on mobile. |
| **Touch Target Area** | CTA buttons had 32px height, making tap targets hard to hit on touchscreens. | Increased button padding to `padding: 0.85rem 1.5rem` enforcing minimum 44px $\times$ 44px tap target. | **PASS** Meets Apple iOS & Android touch guidelines. |
| **Metrics Table Overflow** | Scikit-learn classification table (5 columns) spilled past 375px viewport edge. | Wrapped table in `<div style="overflow-x: auto;">` with touch momentum scrolling. | **PASS** Smooth horizontal swipe scrolling without page break. |
| **Figure Image Responsiveness** | Architecture diagram images had fixed pixel widths. | Applied `max-width: 100%; height: auto; border-radius: 8px;` across all figure captures. | **PASS** Zero image overflow or distortion. |
| **Link Integrity Check** | Verified all outbound links (LinkedIn, GitHub, Paper, Booking). | All links set to `target="_blank" rel="noopener noreferrer"` with 100% 200 OK responses. | **PASS** All links working cleanly. |

---

## 3. CSS Media Query Implementation (`docs/styles.css`)

```css
/* Mobile Viewport Polish Rules (Screen Width < 640px) */
@media (max-width: 640px) {
  h1 {
    font-size: 1.85rem;
    line-height: 1.25;
  }
  
  .metric-value {
    font-size: 2.1rem;
  }

  .btn-primary, .btn-secondary {
    width: 100%;
    text-align: center;
    min-height: 44px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .table-responsive {
    width: 100%;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
  }
}
```

---

## 4. Pass / Revise Verification Checklist

- [x] **Tested on Real Phone:** Tested on 375px mobile viewport and physical device.
- [x] **Readable Typography & Contrast:** Minimum 16px body font size, high-contrast Slate White (`#F8FAFC`) on Deep Slate (`#0F172A`).
- [x] **Crisp Work Captures:** All figures set to responsive scale (`max-width: 100%`).
- [x] **All Links Functioning:** GitHub, LinkedIn, Paper, and Booking links active.
- [x] **Real Fix Log Documented:** 5 specific audit items logged with before/after fixes.

---

*Submitted by Zeyad Ayman (`ZeyadArafa`) for FlyRank General AI Fluency — Week 7 Assignment.*
