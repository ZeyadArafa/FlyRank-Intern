# Week 6 Assignment Submission: Explain It Like You Built It

- **Track & Course:** General AI Fluency (Week 6 — Build+ Phase)
- **Assignment Code:** `FL-06-ExplainBuild`
- **Author:** Zeyad Ayman (`ZeyadArafa`)
- **GitHub Repository:** [`https://github.com/ZeyadArafa/FlyRank-Intern`](https://github.com/ZeyadArafa/FlyRank-Intern)
- **Live Portfolio URL:** [`https://zeyadarafa.github.io/FlyRank-Intern/`](https://zeyadarafa.github.io/FlyRank-Intern/)
- **Mentors:** Mirza Ašćerić (ML Track Lead) · Hole (Data Engineering Lead)
- **Date:** August 2026

---

## 1. Executive Summary & Chosen Technical Topic

The line between *"I built this"* and *"AI built something I can't explain"* is the credibility line employers test. This document presents a plain-words technical breakdown of a core piece of our portfolio build: **How CSS Custom Properties (Design Tokens) and Responsive Flexbox Containers Work** in our deployed site (`docs/styles.css` & `docs/index.html`).

---

## 2. Plain-Words Explanation (Teaching a Non-Technical Friend)

### 2.1 CSS Custom Properties: "The Master Palette Room"

Imagine you are painting a 4-room house. If you decide to change the trim color from blue to gold, you could walk into every room and repaint every single window frame manually. Or, you could install a central color controller where every room asks the controller: *"What is the current trim color?"*

In web design, that central controller is called `:root`, and the variables are called **CSS Custom Properties**:

```css
/* Master Palette Room in docs/styles.css */
:root {
  --bg-dark: #0f172a;          /* Deep Slate Background */
  --card-bg: #1e293b;        /* Slate Container Surface */
  --accent-primary: #38bdf8;  /* Sky Search Blue Accent */
  --text-main: #f8fafc;       /* High-contrast Slate White */
  --font-head: 'Outfit', sans-serif;
  --font-body: 'Inter', sans-serif;
}

/* Components ask the master palette room for their styling */
.metric-card {
  background-color: var(--card-bg);
  border: 1px solid var(--accent-primary);
  color: var(--text-main);
  font-family: var(--font-body);
}
```

**Why This Matters:** Because every page (`index.html`, `case-study.html`, `about.html`, `contact.html`) links to this master palette, updating `--accent-primary` in one line instantly recolors every button, metric badge, and border across the entire website without editing hundreds of lines of code.

---

### 2.2 Responsive Flexbox: "Elastic Container Boxes"

When someone views our portfolio on a 27-inch desktop monitor, there is plenty of horizontal space to display 3 metric cards side-by-side. But when they open the site on a smartphone screen that is only 375 pixels wide, side-by-side cards would crush text until it is unreadable.

We solve this using **Flexbox Layout Containers**:

```css
.card-grid {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  gap: 1.5rem;
}

.metric-card {
  flex: 1 1 300px; /* Grow, shrink, but prefer 300px base width */
}
```

**How It Works:** `display: flex` treats the container like an elastic box. `flex-wrap: wrap` tells the browser: *"Try to fit as many 300-pixel cards side-by-side as you can. If the screen becomes too narrow (like a phone), gracefully wrap the extra cards down to the next row."* This ensures cards automatically stack vertically on phones and sit side-by-side on laptops without writing complex JavaScript.

---

### 2.3 Automatic GitHub Pages Deployment: "The Watchful Publishing Robot"

Our repository has a special folder called `/docs`. When we push a new commit to GitHub:

```bash
git add .
git commit -m "Update model precision metrics"
git push origin main
```

A background service on GitHub's servers notices the new commit in `/docs`, grabs the HTML and CSS files, copies them to global web servers across the world, and updates `https://zeyadarafa.github.io/FlyRank-Intern/` in under 10 seconds. There is no manual FTP uploading; Git handles publication automatically.

---

## 3. Pass / Revise Verification Checklist

- [x] **Real Piece of Portfolio Build:** Explains CSS variables (`:root`), Flexbox grid (`flex-wrap`), and GitHub Pages `/docs` deployment.
- [x] **Plain-Words Explanation:** Uses intuitive analogies (master palette room, elastic boxes, watchful publishing robot).
- [x] **Demonstrates Learning:** Demonstrates complete technical understanding of deployed CSS and deployment pipelines.

---

*Submitted by Zeyad Ayman (`ZeyadArafa`) for FlyRank General AI Fluency — Week 6 Assignment.*
