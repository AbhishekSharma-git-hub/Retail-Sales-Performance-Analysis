# Retail Sales Performance Analysis — Project Report

## 1. Executive Summary

Between 2014 and 2017, the business generated **$241,131 in sales** and **$18,746 in profit**, an overall margin of **7.8%**. Performance is uneven: **Technology** is the clear revenue engine (38.8% of sales, 8.6% margin) and **Office Supplies** is the profitability engine (18.3% margin), while **Furniture** is the only category losing money overall (-2.2% margin), driven specifically by the Tables and Bookcases sub-categories. The single strongest driver of unprofitability across the entire dataset is **discounting**: line items discounted above 40% average a **-63% margin**, compared with **+31%** on full-price lines. Geographically, the **West region** is the strongest market on every measured axis (highest sales and highest margin), while **Central** carries the second-highest sales volume but the weakest margin of any region (3.2%). The recommended highest-leverage action is introducing formal **discount governance** — approval thresholds above 20-30% — targeted first at Furniture, Machines, and Same Day shipping, the three areas where discounting is most clearly destroying value.

---

## 2. Business Understanding

**Industry:** Multi-category US retail (Furniture, Office Supplies, Technology), selling to Consumer, Corporate, and Home Office customers across 40 states.

**Business problem:** Leadership can see topline sales but lacks a systematic view of *where profit is actually created or destroyed* across product, region, segment, and fulfilment dimensions — and lacks visibility into how discounting policy is affecting the bottom line.

**Why this analysis is needed:** Blended company-wide margin (7.8%) masks large internal variation — from Copiers at 39.1% margin to Machines at a net loss. Without category/region/segment-level visibility, pricing, marketing, and inventory decisions are made on incomplete information.

**Goals:**
1. Establish a single source of truth for sales and profit performance across all key dimensions.
2. Quantify the relationship between discounting and profitability.
3. Translate findings into prioritized, actionable recommendations.

**Scope:** Analysis of the 1,000-row order-line extract provided (2014-2017, United States only). Does not include cost-of-goods, marketing spend, or inventory/supply-chain data.

**Assumptions:**
- "Profit" in the source data already reflects cost and discount (net profit), not gross margin.
- "Customer Type" (repeat vs. single) is approximated using order-line frequency, since a clean distinct-order-per-customer field with purchase-date sequencing was not available.
- The 1,000-row extract is representative of the underlying transactional population for directional (not statistically definitive) conclusions.

**Stakeholders:** VP of Sales, Category/Merchandising Managers, Regional Sales Directors, Finance/FP&A, Logistics & Fulfilment Operations, E-commerce/Pricing team.

**Expected business value:** A clear, prioritized roadmap for closing the profitability gap without needing to grow revenue — primarily through disciplined discount governance and targeted category/shipping-tier fixes.

---

## 3. Dataset Understanding

The dataset contains 1,000 order line items across 21 original fields spanning identifiers (Row ID, Order ID, Customer ID, Product ID), dates (Order Date, Ship Date), geography (City, State, Region, Postal Code, Country), categorical dimensions (Segment, Category, Sub-Category, Ship Mode), and numeric measures (Sales, Quantity, Discount, Profit). A full column-by-column data dictionary — including data type, business meaning, and quality notes — is provided in the `Data Dictionary` tab of the analysis workbook.

Key structural facts:
- 1,000 line items roll up to **479 distinct orders** from **362 unique customers** and **764 unique products**.
- Data spans **2014-01-04 to 2017-12-30** (order dates); shipping always occurs on or after the order date (0 violations).
- No missing values, no duplicate rows, no invalid categorical values were found.

---

## 4. Data Cleaning

A 15-point data-quality checklist was run against the full extract (full detail in the `Cleaning Log` tab):

- ✅ Missing values: 0 across all 21 columns
- ✅ Duplicate rows: 0
- ✅ Duplicate keys (Row ID): 0
- ✅ Date validity and logical sequencing (Ship Date ≥ Order Date): 0 violations
- ✅ Text formatting / casing / whitespace: consistent, no issues found; TRIM safeguards applied defensively
- ✅ Categorical domain checks (Category, Region, Segment, Ship Mode): all clean, expected value sets
- ✅ Numeric range checks (Sales, Quantity, Discount): all within valid, expected bounds
- ⚠️ Negative Profit values (186 of 1,000 rows, 18.6%): reviewed and confirmed as genuine business outcomes of discounting/cost, **not** data errors — retained and flagged via a `Profitability Status` feature rather than removed
- ⚠️ High-value outliers in Sales/Profit: reviewed and confirmed as legitimate bulk/enterprise orders, retained

**Conclusion:** the source extract required validation and documentation more than remediation — a result worth stating explicitly, since it demonstrates the analysis is built on trustworthy inputs.

---

## 5. Feature Engineering

Fourteen calculated columns were added in the `Enriched Data` tab, all as live Excel formulas (not hardcoded values), including: Order Year/Month/Quarter/Weekday, Shipping Delay (Days), Unit Price, Profit Margin %, Discount Tier, Revenue Band, Order Size Category, Profitability Status, Performance Level, Customer Type, and Delivery Speed Category. Full formula logic and rationale are documented in the `README` tab of the workbook and in the repository README.

---

## 6. KPIs

| KPI | Value | Why it matters |
|---|---|---|
| Total Sales | $241,131 | Topline scale of the business |
| Total Profit | $18,746 | Bottom-line outcome |
| Overall Profit Margin | 7.8% | Efficiency of converting sales to profit |
| Distinct Orders | 479 | Transaction volume |
| Average Order Value | $503.40 | Basket-size health |
| Unique Customers | 362 | Customer base size |
| Average Discount Rate | 16.3% | Pricing discipline |
| Loss-Making Order Lines | 18.6% | Scale of the profitability problem |

---

## 7. Analysis & Findings

Full pivot-style breakdowns by Category, Sub-Category, Region, Segment, Ship Mode, Year, State, and Quarter are provided in the `Summary Tables` tab, and 41 specific business questions are answered with sourced figures in the `Business Questions` tab. Highlights:

- **Category:** Technology leads sales (38.8% share, 8.6% margin); Office Supplies leads margin (18.3%); Furniture is the only net-loss category (-2.2%).
- **Region:** West leads on both sales and margin (15.4%); Central has the weakest margin (3.2%) despite the #2 sales volume.
- **Segment:** Consumer is the largest by revenue (49%); Home Office converts best (14.3% margin); Corporate has the weakest margin (2.8%).
- **Discounting:** 53.7% of lines carry a discount; lines above 40% discount average -63% margin versus +31% for full-price lines (correlation of discount to profit ≈ -0.25).
- **Shipping:** Same Day is the only ship mode with a net loss overall (-$2,833); Standard Class carries the longest average delay (5.0 days).
- **Seasonality:** November-December account for 36% of annual sales; Monday and Sunday are the highest-selling weekdays.

---

## 8. Insights & Recommendations

Twenty-five insight/recommendation pairs, each with a priority rating (High / Medium / Monitor), are documented in the `Insights & Recommendations` tab. The four highest-priority actions are:

1. Introduce discount-approval governance (threshold ~20-30%), targeted first at Furniture and Machines.
2. Commission a Furniture pricing/cost review before the next planning cycle.
3. Re-price or restrict Same Day shipping eligibility so it stops operating at a loss.
4. Audit Central region's discounting and cost-to-serve, given its volume-without-profit pattern.

---

## 9. Methodology & Tools

- **Tool:** Microsoft Excel (formulas only — `SUMIF`, `COUNTIF`, `AVERAGE`, `IFERROR`, nested `IF`, `SUMPRODUCT`, `TEXT`, date functions)
- **Process:** raw data audit → cleaning/validation checklist → feature engineering → pivot-style summary tables → KPI dashboard → business-question answering → insight synthesis → recommendation prioritization
- **QA standard:** every formula in the workbook (14,190 total) was recalculated and verified to produce zero errors before delivery, and spot-checked against independent Python/pandas calculations for accuracy

---

## 10. Conclusion

The business is modestly profitable overall (7.8% margin) but carries clearly identifiable, fixable sources of margin leakage — concentrated in specific sub-categories (Machines, Tables, Bookcases), one shipping tier (Same Day), and one region (Central) — and unified by a single common driver: undisciplined discounting. Addressing discount governance is the highest-leverage, lowest-complexity lever available in this dataset to materially improve company-wide profitability without requiring new revenue growth.

## 11. Limitations & Future Scope

**Limitations:** single-extract dataset (not full transactional history); no cost-of-goods or marketing-spend data (limits this to a Profit-field-based view, not full P&L); "Customer Type" uses a line-item-frequency proxy rather than true distinct-order sequencing.

**Future scope:** migrate summary tables to native Excel PivotTables/PivotCharts for interactive exploration; build an interactive Power BI/Tableau companion dashboard; extend the model with cost and marketing data for full P&L-level profitability analysis; build true cohort-based repeat-purchase and customer-lifetime-value metrics.
