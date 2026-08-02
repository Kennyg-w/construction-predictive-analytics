# Infrastructure Analytics & EVM Project Intelligence

**End-to-end analytics pipeline** on 1,300 construction tasks across a **$64.4M portfolio** — detecting optimism bias, forecasting schedules with ML, and delivering insights through SQLite, Excel, and Power BI.

---

## 🔍 Project Overview

This project rebuilds an infrastructure analytics pipeline using four tools across three stages:

- **Python** — EVM metric calculation, optimism bias detection, Random Forest forecasting
- **SQLite** — Database storage with 5 SQL queries and an EVM dashboard view
- **Excel** — Manual SPI, CPI, nested IF, and optimism bias formulas
- **Power BI** — Interactive dashboard with risk distribution, SPI vs CPI scatter plot, and task table

---

## 📊 Key Findings

| Finding | Value |
|---|---|
| Total portfolio | 1,300 tasks / $64.4M |
| Optimism bias detected | 60.1 days / ~44% underestimate |
| High risk task bias | +60% overrun |
| Random Forest MAE | 29.79 days |
| Improvement over baseline | 50% better than naive forecast |
| Critical tasks (SPI < 0.8) | ~263 tasks (20%) |

---

## 🛠️ Tools & Pipeline
### Stage 1 — Python
- Loaded 1,300-row construction dataset
- Simulated Actual Duration using domain-driven risk multipliers (Low=1.1x, Medium=1.3x, High=1.6x)
- Calculated SPI and CPI for every task
- Detected 60.1-day optimism bias across the portfolio
- Trained Random Forest Regressor achieving MAE of 29.79 days

### Stage 2 — SQLite
- Created `construction_tasks` table with schema validation
- Wrote 5 SQL queries: inspection, risk aggregation, average duration, SPI via CASE WHEN, traffic light flagging
- Built `evm_dashboard` VIEW combining all EVM calculations

### Stage 3 — Excel
- Built SPI formula: `=C2/D2`
- Built CPI formula: `=E2/F2`
- Built status logic: `=IF(G2>=1,"Healthy",IF(G2>=0.8,"Stakeholder Alert","Critical"))`
- Calculated optimism bias: 44.8% underestimate across sample tasks

### Stage 4 — Power BI
- Connected to SQLite export (evm_clean.csv)
- Built 4 visuals: Risk Distribution bar chart, SPI vs CPI scatter plot, Task table, Count card
- Cross-filtering enabled across all visuals

---

## 📁 Repository Structure
---

## 🚀 How to Run

```bash
git clone https://github.com/Kennyg-w/construction-predictive-analytics.git
cd construction-predictive-analytics
pip install -r requirements.txt
jupyter notebook notebooks/exploration.ipynb
```

---

## 📋 EVM Reference

| Metric | Formula | Value = 1.0 | Value < 1.0 |
|---|---|---|---|
| SPI | Planned Days / Actual Days | On schedule | Behind schedule |
| CPI | Planned Cost / Actual Cost | On budget | Over budget |

**Status thresholds:**
- 🔴 Critical: SPI < 0.8 — escalate immediately
- 🟡 Stakeholder Alert: SPI 0.8–1.0 — monitor closely
- 🟢 Healthy: SPI ≥ 1.0 — normal tracking

---

**Author:** Kenesuo Wolowolo
**Qualifications:** MSc Data Science (Commendation) | MSc Project | Management BEng Mechanical/Offshore Engineering | 
**LinkedIn:** [linkedin.com/in/kenwolo](https://linkedin.com/in/kenwolo)
**GitHub:** [github.com/Kennyg-w](https://github.com/Kennyg-w)