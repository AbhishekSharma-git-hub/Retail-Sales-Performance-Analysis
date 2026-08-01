# 📊 Retail Sales Performance Analysis — Excel Analytics Project

**End-to-end business analytics project on a 1,000-row US retail (Superstore-style) transactional dataset — from raw data to an executive KPI dashboard, using Excel formulas only (no VBA, no add-ins, no external tools).**

![Excel](https://img.shields.io/badge/Tool-Microsoft%20Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Formulas](https://img.shields.io/badge/Formulas-14%2C190-blue)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📁 Repository Structure

```
Retail-Sales-Performance-Analysis/
│
├── data/
│   └── Dataset - Retail Sales Performance.xlsx
│
├── analysis/
│   └── Analysis - Retail Sales Performance.xlsx
│
├── docs/
│   └── Project Report - Retail Sales Performance.md
│
├── images/
│   └── Image- Retail Sales Performance/  (or place images directly here)
│
├── .gitattributes
├── LICENSE
└── README.md
```

> **Note:** the analysis workbook is a *single self-contained file* — every sheet listed under "Workbook Guide" below is a tab inside `Retail_Sales_Performance_Analysis.xlsx`. There is no separate dashboard file.

---

## 🧭 Business Problem

A US retail company (Consumer / Corporate / Home Office segments, Furniture / Office Supplies / Technology categories) needs to understand **where it makes money, where it loses money, and why** — across regions, product lines, customer segments, and shipping methods — in order to correct margin leakage and prioritize growth investment for the next planning cycle.

## 🎯 Objectives

- Quantify overall sales and profitability performance (2014–2017)
- Identify which categories, sub-categories, regions, and segments drive **profit**, not just revenue
- Diagnose the relationship between **discounting and profitability**
- Engineer analysis-ready features (time, margin, customer, delivery) using only Excel formulas
- Deliver an executive-ready KPI dashboard and a prioritized set of strategic recommendations

## 📦 Dataset

| | |
|---|---|
| **Source** | US retail transactional extract (Superstore-style schema) |
| **Rows** | 1,000 order line items |
| **Columns** | 21 original + 14 engineered = 35 |
| **Period** | Jan 2014 – Dec 2017 |
| **Grain** | One row per order line item (1,000 lines roll up to 479 distinct orders) |
| **Data quality** | 0 missing values · 0 duplicates · 0 invalid dates found (see Cleaning Log tab) |

---

## 🗂️ Workbook Guide (`analysis/Retail_Sales_Performance_Analysis.xlsx`)

| Tab | What's in it |
|---|---|
| `Read Me` | In-workbook navigation and project summary |
| `Data Dictionary` | Every column: data type, business meaning, quality notes, importance |
| `Cleaning Log` | 15-point data-quality checklist with method and result for each check |
| `Raw Data` | Original 1,000-row extract, untouched (audit trail) |
| `Enriched Data` | Cleaned data **+ 14 engineered feature columns**, 100% live formulas, formatted as an Excel Table |
| `Summary Tables` | 8 pivot-style breakdowns (Category, Sub-Category, Region, Segment, Ship Mode, Year, Top-10 States, Quarter) built with `SUMIF`/`COUNTIF` |
| `KPI Dashboard` | 8 formula-driven KPI cards + 4 native Excel charts (bar, pie, line, horizontal bar) |
| `Business Questions` | 41 business questions (beginner → advanced), each answered with a real figure and its source |
| `Insights & Recommendations` | 25 insights, each paired with a prioritized strategic recommendation |

---

## 🛠️ Tools & Excel Skills Used

- **Formulas:** `SUMIF`, `COUNTIF`, `AVERAGE`, `IFERROR`, nested `IF`, `SUMPRODUCT` (distinct counts), `TEXT`, `YEAR`, `MONTH`, `ROUNDUP`
- **Structures:** Excel Tables (structured references), frozen panes, conditional/priority color coding
- **Feature engineering:** date decomposition, margin/unit-price calculation, tiering/binning logic, customer segmentation logic
- **Visualization:** native Excel charts (clustered column, pie with % labels, line trend, horizontal bar) driven entirely by formula-based summary tables
- **QA:** every formula recalculated and verified with zero errors before delivery (14,190 formulas, 0 errors)

## 🔑 Engineered Features

| Feature | Logic |
|---|---|
| Order Year / Month / Quarter / Weekday | `YEAR()`, `TEXT(...,"mmm")`, quarter from `MONTH()`, `TEXT(...,"ddd")` |
| Shipping Delay (Days) | `Ship Date − Order Date` |
| Unit Price | `Sales / Quantity` |
| Profit Margin % | `Profit / Sales` |
| Discount Tier | No Discount / Low (1–20%) / Medium (21–40%) / High (40%+) |
| Revenue Band | Low (<$50) / Medium / High / Premium ($500+) |
| Order Size Category | Small / Medium / Large, by quantity |
| Profitability Status | Loss-Making vs Profitable |
| Performance Level | Underperforming / Low / Healthy / High margin |
| Customer Type | Single Purchase vs Repeat Customer (order-line frequency proxy) |
| Delivery Speed Category | Fast (≤2 days) / Standard (3–5) / Slow (6+) |

---

## 📈 Key KPIs

| KPI | Value |
|---|---|
| Total Sales | **$241,131** |
| Total Profit | **$18,746** |
| Overall Profit Margin | **7.8%** |
| Distinct Orders | **479** |
| Average Order Value | **$503.40** |
| Unique Customers | **362** |
| Average Discount Rate | **16.3%** |
| Loss-Making Order Lines | **18.6%** of all lines |

---
## 📸 Dashboard Preview
<img width="1920" height="1140" alt="Preview Dashboard 1" src="https://github.com/user-attachments/assets/069f8e2b-c9ce-4ad9-8baf-1a6f10e5648b" />
<img width="1920" height="1140" alt="Preview Dashboard 2" src="https://github.com/user-attachments/assets/745e9381-682c-4ba9-b014-713d636bb1f4" />

---

## 💡 Top Insights (see full list of 25 in-workbook)

1. **Technology drives revenue** — 38.8% of total sales at a healthy 8.6% margin.
2. **Furniture is the only loss-making category** (-2.2% margin), concentrated specifically in Tables and Bookcases.
3. **Discounting is the strongest predictor of loss** — lines discounted above 40% average **-63% margin**, versus **+31%** on full-price lines.
4. **Same Day shipping is unprofitable overall** (-$2,833), the only ship mode operating at a net loss.
5. **West region is the best performer on every axis** — highest sales *and* highest margin (15.4%).

## ✅ Strategic Recommendations (see full list of 25 in-workbook)

- Introduce a **discount-approval threshold** (e.g. manager sign-off above 20–30%), prioritized for Furniture and Machines.
- **Re-price or restrict Same Day shipping** eligibility so premium speed doesn't erode margin.
- Use the **West region as a template** for expansion; audit **Central region** discounting/cost-to-serve.
- Elevate discount governance to a **company-wide policy initiative** — it is the common thread behind every major loss driver identified.

---

## 🚀 How to Use This Repository

1. Clone or download the repo.
2. Open `analysis/Retail_Sales_Performance_Analysis.xlsx` in Microsoft Excel (2016+ recommended for full chart fidelity).
3. Start on the `Read Me` tab, then explore in the order listed in the Workbook Guide above.
4. All KPI cards and summary tables are **live formulas** — if you replace the data in `Enriched Data`, the whole workbook recalculates automatically.

## 🔮 Future Improvements

- Migrate the pivot-style `SUMIF` summary tables to native Excel PivotTables / PivotCharts for interactive slicing
- Add a Power BI / Tableau version for interactive filtering by end users
- Extend the dataset with cost-of-goods and marketing-spend data to move from margin analysis to full P&L modeling
- Add cohort-based repeat-purchase analysis (true distinct-order customer type, rather than the line-item frequency proxy used here)

## ⚠️ Limitations

- Dataset is a curated 1,000-row extract, not the full multi-year transactional history — trends should be read directionally, not as statistically definitive
- "Customer Type" (repeat vs. single) uses order-line frequency as a proxy in the absence of a clean distinct-order-per-customer field
- No cost-of-goods-sold or marketing-spend data is available, so profitability reflects the `Profit` field as provided, not a full P&L view

---

## 👤 Author

**Abhishek Sharma** — Aspiring Data Analyst 
📧 dusyantmudgal@gmail.com and datawithabhi@gmail.com · 🔗 [LinkedIn](https://www.linkedin.com/in/abhishek-sharma-data-analyst/) · 💻 [GitHub](https://github.com/AbhishekSharma-git-hub)

## 📄 License


This project is licensed under the MIT License.

See the LICENSE file for complete details.

The dataset is a synthetic/curated educational dataset intended for learning and portfolio purposes.

## 🙏 Acknowledgements

Dataset schema inspired by the widely-used "Superstore" retail analytics dataset format, commonly used for BI/analytics training.
