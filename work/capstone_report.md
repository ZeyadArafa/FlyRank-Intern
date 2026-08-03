# Capstone Report — Content Refresh & Opportunity Scoring

- **Author:** Zeyad Ayman (`ZeyadArafa`)
- **Lane:** Content Refresh / Opportunity Scoring
- **Repo:** [https://github.com/ZeyadArafa/FlyRank-Intern](https://github.com/ZeyadArafa/FlyRank-Intern)
- **Deployed Paper URL:** [https://zeyadarafa.github.io/FlyRank-Intern/](https://zeyadarafa.github.io/FlyRank-Intern/)
- **Date:** August 2026

---

## 1. Problem framing

Out of tens of thousands of published web content items, search intelligence teams require an accurate mechanism to prioritize which decaying pages to review and refresh first. 
- **Unit of Analysis:** One row = one pseudonymized content item (`content_id`).
- **Output:** Pointwise probability decay score and ranked queue with actionable reason codes (`stale_visible_page`, `low_ctr_visible_page`, `thin_visible_page`, `page_one_decay_risk`).
- **Action Taken:** Human editorial leads allocate weekly refresh sprint workloads (e.g. top 20 pages per sprint).
- **Cost of a Wrong Call:** 
  - *False Positives:* Wasting editorial budget ($150–$300/article) updating healthy, stable cornerstone pages.
  - *False Negatives:* Allowing high-demand organic traffic assets to experience permanent rank erosion.

---

## 2. Data safety

- **Dataset Used:** FlyRank Anonymized Search Intelligence Dataset (30,000 content items × 44 attributes) covering 32 pseudonymized client domains.
- **Deliberately Excluded Columns:** 
  - `trend_pct` and `trend_direction` — Excluded from model features to prevent circular target leakage (`is_declining_label` is derived from `trend_direction == 'down'`).
  - `content_id` and `client_id` — Pseudonymized hashes used exclusively for grouped validation splits and output keying.
- **Public Safety Assurance:** Zero private client names, URLs, domain names, or raw search queries appear in this repository.

---

## 3. Baseline

- **Hand-Written Rule Baseline:** Deterministic weighted linear combination combining demand scale (`log_impressions_90d`), update recency risk (`days_since_last_update`), position opportunity (`avg_position`), and CTR benchmark gap (`ctr`).
- **Baseline Holdout Performance:** Evaluated on the 6-client holdout test set ($N=3,381$):
  - **Precision@10:** 0.400
  - **Precision@20:** 0.350
  - **Precision@50:** 0.460
  - **ROC-AUC:** 0.580
  - **Base Rate:** 0.525

---

## 4. Model / analysis

- **Method Chosen:** Evaluated Logistic Regression (L2 Regularized, Balanced Weights) vs Decision Tree (`max_depth=5`) vs Random Forest (`n_estimators=200`).
- **Feature Selection:** 16 non-leakage numeric & categorical features: `log_impressions_90d`, `log_clicks_90d`, `log_sessions_90d`, `log_ai_sessions_90d`, `days_since_last_update`, `content_age_days`, `avg_position`, `ctr`, `engagement_rate`, `scroll_rate`, `word_count`, `search_volume`, `cpc`, `has_clicks`, `has_ai_sessions`, `measurable_opportunity`, `content_type`, `competition_level`, `main_intent`.
- **Target Definition:** `is_declining_label = (trend_direction == 'down')`.

---

## 5. Evaluation

- **Validation Split Design:** 80/20 Grouped Client-Holdout Split (26 training clients = 26,619 rows; 6 test holdout clients = 3,381 rows) to test true generalizable performance on unseen domain data.
- **Holdout Evaluation Matrix:**

| Model / System Architecture | Precision@10 | Precision@20 | Precision@50 | Precision@100 | ROC-AUC | PR-AUC |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **Dataset Base Rate** | 0.525 | 0.525 | 0.525 | 0.525 | N/A | N/A |
| **Week-4 Rule Baseline** | 0.400 | 0.350 | 0.460 | 0.440 | 0.580 | 0.555 |
| **Logistic Regression (Best)** | **0.900** | **0.800** | **0.720** | **0.810** | 0.660 | **0.666** |
| **Decision Tree (depth=5)** | 0.700 | 0.650 | 0.660 | 0.690 | **0.666** | 0.636 |
| **Random Forest (n=200)** | 0.400 | 0.500 | **0.720** | 0.740 | **0.666** | 0.657 |

- **Error Analysis:** High-impression pages with low CTR sometimes score high probabilities of decay despite stable organic search volume (false positives due to non-search referral traffic).

---

## 6. Interpretation

- **Top Signal Drivers:** `days_since_last_update` (strongest positive driver of decline risk), `avg_position` (pages ranking 4–20 offer prime refresh lift), `ctr` underperformance, and `word_count` (<1,000 words indicates thin content risk).
- **Key Insight:** Learned Logistic Regression achieves **0.900 Precision@10** (a 2.25× lift over rule-based baseline) by learning calibrated linear trade-offs between rank position and expected CTR benchmarks.

---

## 7. Recommendation

- **Operational Playbook Actions:**
  - `stale_visible_page` → **`refresh`** (Update statistics, dates, case studies).
  - `low_ctr_visible_page` → **`refresh_and_review_ctr`** (Rewrite meta title/description for SERP click-through).
  - `thin_visible_page` → **`expand_and_refresh`** (Expand word count, add H2/H3 sub-sections).
- **Strict No-Go Automation List:**
  - ❌ No automated AI overwrites or auto-publishing without human editor sign-off.
  - ❌ No automated URL deletions, permalink changes, or 301 redirects.
  - ❌ No un-reviewed edits on YMYL, legal, financial, or pricing content.

---

## 8. Reproducibility

- **Environment & Seeds:** Python 3.13, `RANDOM_STATE = 42`.
- **Command to Reproduce Pipeline:**
  ```bash
  python scripts/01_prepare_features.py
  python scripts/02_baseline_score.py
  python scripts/03_train_model.py
  python scripts/04_evaluate_and_export.py
  ```
- **Notebook Trajectory:**
  - `work/notebooks/w04_baseline_score.ipynb`
  - `work/notebooks/w05_model.ipynb`
  - `work/notebooks/w06_validation_audit.ipynb`
  - `work/notebooks/w07_action_playbook.ipynb`
  - `work/notebooks/capstone.ipynb`
- **Data Credit:** Built on the FlyRank Machine Learning Internship dataset provided by [FlyRank](https://flyrank.ai).
