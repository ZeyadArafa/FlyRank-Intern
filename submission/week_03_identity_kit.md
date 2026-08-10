# Week 3 Assignment Submission: Decide Once (Build Your Identity Kit)

- **Track & Course:** General AI Fluency (Week 3 — Foundations)
- **Assignment Code:** `FL-03-IdentityKit`
- **Author:** Zeyad Ayman (`ZeyadArafa`)
- **GitHub Repository:** [`https://github.com/ZeyadArafa/FlyRank-Intern`](https://github.com/ZeyadArafa/FlyRank-Intern)
- **Deployed Research Paper:** [`https://zeyadarafa.github.io/FlyRank-Intern/`](https://zeyadarafa.github.io/FlyRank-Intern/)
- **Mentors:** Mirza Ašćerić (ML Track Lead) · Hole (Data Engineering Lead)
- **Date:** August 2026

---

## 1. Executive Summary & Design Philosophy

A consistent look is what separates a portfolio that feels intentional from one that feels thrown together. By deciding typography, color palette, logo monogram, and tone rules once, every page in the portfolio (`/index.html`, `/case-study.html`, `/about.html`, `/contact.html`) inherits a cohesive, high-rigor engineering aesthetic.

---

## 2. The Identity Kit Specification Sheet

### 🅰️ 1. Typography System (Google Fonts)

Only two free Google Fonts are used across the entire design system to guarantee visual harmony and zero font fatigue:

| Font Role | Font Family | Weights Used | Purpose & Justification |
|---|---|---|---|
| **Headings (`<h1>`–`<h4>`)** | **`Outfit`** | `600` (SemiBold), `700` (Bold) | Technical, sharp, geometric sans-serif that establishes strong visual hierarchy and modern ML authority. |
| **Body & Code (`<p>`, `<table>`)** | **`Inter`** | `400` (Regular), `500` (Medium) | Ultra-legible, neutral sans-serif designed for high-density technical reading, metric tables, and code snippets. |

```css
/* Core Typography Rules */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500&family=Outfit:wght@600;700&display=swap');

h1, h2, h3, h4 {
  font-family: 'Outfit', sans-serif;
  font-weight: 700;
  letter-spacing: -0.02em;
}

body, p, table, input {
  font-family: 'Inter', sans-serif;
  font-weight: 400;
  line-height: 1.6;
}
```

---

### 🎨 2. Color Palette (Calibrated Hex Codes)

A tight 4-color palette designed to create a calm, high-contrast dark environment where model results (e.g. 0.900 Precision@10) remain the loudest element on the page:

| Color Role | Color Name | Hex Code | Visual Preview | Strategic Design Function |
|---|---|:---:|:---:|---|
| **Primary Accent** | Sky Search Blue | **`#0EA5E9`** | `[ #0EA5E9 ]` | Highlights key metric wins (0.900 Precision@10), primary CTA buttons, and active navigation links. |
| **Dark Background** | Deep Slate | **`#0F172A`** | `[ #0F172A ]` | Calming, low-eyestrain dark surface that focuses reader attention directly on data and text proof. |
| **Card Surface** | Slate Container | **`#1E293B`** | `[ #1E293B ]` | Container background for metric cards, table headers, and 3-beat case study blocks. |
| **Near-White Text** | Slate White | **`#F8FAFC`** | `[ #F8FAFC ]` | High-contrast, non-glare text color for effortless readability across desktop and mobile screens. |

```css
:root {
  --color-accent: #0EA5E9;       /* Sky Search Blue */
  --color-bg: #0F172A;           /* Deep Slate Background */
  --color-card: #1E293B;         /* Slate Container Surface */
  --color-text: #F8FAFC;         /* High-contrast Slate White */
  --color-text-muted: #94A3B8;   /* Secondary Muted Text */
  --color-border: #334155;       /* Subtle Border Rule */
}
```

---

### 🏷️ 3. Logo Monogram & Favicon Mark

Keep it simple: a clean, minimalist monogram combining Zeyad Ayman's initials (`ZA`) set in **Outfit Bold 700** with the primary `#0EA5E9` sky blue accent.

#### Text Logo (`/index.html` Header)
```html
<div class="brand-logo">
  <span class="logo-text">ZEYAD AYMAN</span>
  <span class="logo-dot">.</span>
  <span class="logo-sub">ML SEARCH LABS</span>
</div>
```

#### SVG Favicon Mark (`favicon.svg`)
```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64 64" width="32" height="32">
  <rect width="64" height="64" rx="12" fill="#0F172A" stroke="#0EA5E9" stroke-width="3"/>
  <text x="32" y="42" font-family="Outfit, sans-serif" font-weight="700" font-size="28" fill="#F8FAFC" text-anchor="middle">ZA</text>
  <circle cx="50" cy="20" r="4" fill="#0EA5E9"/>
</svg>
```

---

## 3. Two-Line Style Note (Standing Instruction)

This two-line style note is added to the Claude Project (`FlyRank-Search-ML-Portfolio-2026`) as a standing instruction to maintain design consistency across all code, markdown files, and CSS components:

> **Style Note Line 1 (Technical Spec):**  
> `Typography: Outfit (Headings) + Inter (Body). Palette: #0EA5E9 (Sky Accent), #0F172A (Deep Slate BG), #1E293B (Card Surface), #F8FAFC (Near-White Text).`  
>  
> **Style Note Line 2 (Mood & Philosophy):**  
> `Mood: High-rigor engineering precision with a calm, high-contrast dark aesthetic that makes empirical data evidence and model metrics the loudest element on every page.`

---

## 4. Design System Tokens (CSS Tokens Reference)

```css
/* Base Reset & Core Design System Tokens */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: var(--color-bg);
  color: var(--color-text);
  font-family: 'Inter', sans-serif;
  font-size: 1rem;
  line-height: 1.6;
}

.metric-card {
  background-color: var(--color-card);
  border: 1px solid var(--color-border);
  border-radius: 8px;
  padding: 1.5rem;
}

.metric-value {
  color: var(--color-accent);
  font-family: 'Outfit', sans-serif;
  font-weight: 700;
  font-size: 2.5rem;
}

.btn-primary {
  background-color: var(--color-accent);
  color: #0F172A;
  font-family: 'Outfit', sans-serif;
  font-weight: 600;
  padding: 0.75rem 1.5rem;
  border-radius: 6px;
  text-decoration: none;
  display: inline-block;
}
```

---

## 5. Pass / Revise Verification Checklist

- [x] **One or Two Fonts Chosen:** Exactly 2 Google Fonts (`Outfit` for headings, `Inter` for body).
- [x] **Tight Color Palette with Hex Codes:** Exactly 4 calibrated hex codes (`#0EA5E9`, `#0F172A`, `#1E293B`, `#F8FAFC`).
- [x] **Simple Logo & Favicon Created:** Clean `[ZA.]` text logo and SVG monogram icon.
- [x] **Two-Line Style Note Documented:** Included exact technical spec and single, coherent engineering mood.
- [x] **Claude Project Updated:** Added style note to standing project instructions for automated build consistency.

---

*Submitted by Zeyad Ayman (`ZeyadArafa`) for FlyRank General AI Fluency — Week 3 Assignment.*
