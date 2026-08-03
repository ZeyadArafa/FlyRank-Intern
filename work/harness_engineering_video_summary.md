# Video Notes & Summary — Build the Systems That Build Software

- **Title:** Build the Systems That Build Software w/ Mirza Ašćerić
- **Video URL:** https://www.youtube.com/watch?v=rraHPF4ZgCw
- **Track:** Backend AI Engineering & Harness Engineering
- **Duration:** 90 min

---

## Key Concepts & Takeaways

### 1. The Paradigm Shift (Before vs. Now)
- **Traditional Coding:** Engineers wrote every line of syntax manually.
- **Harness Engineering:** AI models generate code implementations; the engineer's primary job is designing the **harness** — the system of rules, specifications, context files, and automated test gates that guide the AI and catch errors before shipping.

### 2. Context is Memory
- AI coding agents operate statelessly between sessions.
- Everything the agent needs to know must be provided systematically via structured context files rather than ephemeral prompt memory.

### 3. The 4 Layers of Harness Engineering

| Layer | Purpose | Repository Realization |
|---|---|---|
| **Knowledge Layer** | Structural map & domain rules | AGENTS.md, skills/README.md, skills/* router |
| **Spec Layer** | Execution blueprint & definition of done | implementation_plan.md, capstone_report.md |
| **Loop Layer** | Automated task execution & iteration | 
un_all.py, automated notebook execution scripts |
| **Trust Layer** | Automated gates, tests, & guards | Pytest, DuckDB query verifications, CI leak-guards |

### 4. Codebase as the Interface
- Strong typing, explicit function signatures, descriptive variable names, and clear folder structures act as high-bandwidth prompts for LLMs.
- Standardized directory layouts (work/, scripts/, docs/) allow AI agents to navigate and edit code reliably.

### 5. What Stays Human
- **System Architecture & Trade-Offs:** Choosing the right data contracts, split designs, and algorithm classes.
- **Data Privacy & Safety:** Enforcing data safety rules (no raw PII/queries in git, public-safe language).
- **Final Verification:** Skeptical manual review of model metrics, error analysis, and edge-case behavior before shipping to production.

---

## Submission Deliverable Link
- **URL to Submit on Portal:** https://www.youtube.com/watch?v=rraHPF4ZgCw
