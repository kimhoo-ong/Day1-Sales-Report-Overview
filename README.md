# Day 01 — Sales Performance Dashboard
### 30-Day Dashboard Portfolio Challenge

> **Analyst:** Kim Hoo | **Industry:** Retail / Electronics | **Dataset:** `day01_sales_performance.csv` | **Period:** 2024 Full Year

---

## Overview

This Power BI dashboard was built as Day 01 of a 30-day dashboard portfolio challenge. It analyses 2,000 sales transactions across a retail electronics business for the full 2024 calendar year, surfacing revenue performance, profitability gaps, regional disparities, and discount impact.

The dashboard is designed for **Sales Directors, Regional Managers, and Senior Sales Reps** to support daily reviews, weekly team meetings, and monthly executive reporting.

**Primary question answered:** Are we on track to hit revenue and profit targets — and where are the gaps?

---

## Key Findings

| Metric | Value | Signal |
|---|---|---|
| Total Revenue (2024) | MYR 13,975,633 | Benchmark for YTD tracking |
| Total Profit (2024) | MYR 5,690,607 | 40.7% blended margin |
| Total Orders | 2,000 | Avg 167 orders/month |
| Average Order Value | MYR 6,988 | High AOV — B2B nature |
| Loss-Making Orders | 579 (28.9%) | **CRITICAL: nearly 1 in 3 orders destroys value** |
| Target Attainment Rate | 38.9% | Only 777 of 2,000 orders hit target |
| Best Quarter | Q4 — MYR 3,611,694 | Seasonal uplift Oct–Dec |
| Weakest Quarter | Q3 — MYR 3,355,950 | 7.2% below Q4 |

---

## Dashboard Pages

| Page | Purpose |
|---|---|
| **Overview** | KPI cards, monthly revenue vs target, region bar chart |
| **Product & Category** | Treemap, category revenue & margin, discount impact |
| **Sales Rep Leaderboard** | Rep-level attainment %, margin %, trend |
| **Loss Order Analysis** | Loss-making orders breakdown by category and region |

---

## KPI Cards

| KPI | Target | RAG Rule |
|---|---|---|
| Total Revenue (YTD) | MYR 14M | Green >95%, Amber 85–95%, Red <85% |
| Total Profit (YTD) | MYR 5.7M | Green >40% margin, Amber 35–40%, Red <35% |
| Gross Margin % | 40%+ | Green >40%, Amber 35–40%, Red <35% |
| Target Attainment % | 100% | Green >90%, Amber 70–90%, Red <70% |
| Avg Order Value | MYR 7,000 | Trend arrow MoM |
| Loss-Making Order % | <10% | Green <10%, Amber 10–25%, **Red >25%** |

---

## Data Model

**Dataset:** `day01_sales_performance.csv` — 2,000 rows, 13 columns, 0 nulls.

| Column | Type | Description |
|---|---|---|
| order_id | String | Unique order key |
| order_date | Date | Transaction date — enables MoM, YTD analysis |
| product_name | String | 10 products |
| category | String | 4 categories (Peripherals, Furniture, Accessories, Computers) |
| region | String | 5 regions (North, South, East, West, Central) |
| sales_rep | String | 20 reps |
| quantity | Integer | Units ordered |
| unit_price | Float | Selling price per unit (MYR) |
| discount_pct | Integer | Discount tier: 0, 5, 10, 15, 20% |
| cost_price | Float | COGS per unit (MYR) |
| revenue | Float | unit_price × qty × (1 − disc%) |
| profit | Float | revenue − (cost_price × qty) |
| target_revenue | Float | Target revenue per order |

> **Data Note:** Profit can be negative when `cost_price × quantity` exceeds `revenue`. This occurs in **28.9% of orders** and is a critical business signal — not a data error.

---

## Critical Business Insights

### 1. Discount Erosion
Every 5% of discount reduces margin by ~2.5%. The 20% discount tier yields **34.3% margin vs 45.1% at no discount** — a 10.8pp gap.

| Discount | Avg Margin % | Orders |
|---|---|---|
| 0% | 45.1% | 878 |
| 5% | 35.7% | 256 |
| 10% | 40.2% | 284 |
| 15% | 36.2% | 300 |
| 20% | 34.3% | 282 |

**Recommendation:** Set a 15% discount ceiling unless approved by the Sales Director.

### 2. Regional Gap
North region leads with MYR 3,006,494 revenue. Central trails by **MYR 432K (14.4%)**.

**Recommendation:** Dedicated Regional Drill-Down page for the Central manager with rep-level breakdowns.

### 3. Category Mix Opportunity
Accessories deliver the highest margin (43.3%) but rank 3rd in revenue. A 10% mix shift from Furniture to Accessories could add ~MYR 55K in additional profit annually.

### 4. Target Attainment Crisis
Only 38.9% of orders hit target. Targets may be set too high, or reps need coaching.

---

## Design Standards

| Element | Colour | Hex |
|---|---|---|
| Primary Brand | Navy | `#1F3864` |
| Positive / Good | Green | `#375623` |
| Warning | Amber | `#C55A11` |
| Negative / Bad | Red | `#C00000` |
| Neutral Background | Light Grey | `#F2F2F2` |
| Chart Accent | Steel Blue | `#2F5496` |

Fonts: **Arial Bold 14pt** (titles) · **Arial Bold 24pt** (KPI values) · **Arial Regular 10pt** (body)

---

## Files in This Repo

| File | Description |
|---|---|
| `Day1_SalesPerformance.pbip` | Power BI project file |
| `Day1_SalesPerformance.Report/` | Report definition (pages, visuals, layout) |
| `Day1_SalesPerformance.SemanticModel/` | Data model (tables, relationships, DAX measures) |
| `Day01_Analysis_Requirements.docx` | Full analysis & requirements document |
| `Day1_SalesPerformance.pdf` | Exported PDF snapshot of the dashboard |

---

## Requirements Document

The full analysis methodology, data profiling, DAX measures, chart requirements, layout blueprint, and build execution plan are documented in [`Day01_Analysis_Requirements.docx`](Day01_Analysis_Requirements.docx).

---

*Day 01 of 30 · Built with Power BI Desktop · Kim Hoo*
