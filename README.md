# Walmart Retail Sales & Demand Analytics

## Executive Summary
This project evaluates retail sales performance, category demand drivers, regional store performance, and product sales volatility using the **Walmart M5 Dataset**. 

The project utilizes a hybrid analytical approach: **Python (Pandas)** handles heavy data preparation and unpivoting of daily time-series records; **Microsoft Excel** serves as the interactive reporting engine featuring custom PivotTables, dynamic KPI cards, and PivotCharts; and **Google Gemini** provides AI-assisted hypothesis testing to validate analytical findings against empirical data.

---

## Technical Architecture & Tool Stack
* **Data Processing & ETL:** Python (Pandas) — Reshaping wide daily sales data (`pd.melt`), joining price/calendar datasets (`pd.merge`), and generating compressed analytical tables.
* **Dashboard & Analysis:** Microsoft Excel (Excel for Web) — Data tables, summary PivotTables, weighted average price calculations, executive KPI summary cards, and visual PivotCharts.
* **AI-Assisted Validation:** Google Gemini — Formulating operational hypotheses and auditing analytical reasoning against dataset outputs.
* **Documentation & Version Control:** GitHub — Structured repository organization and professional project presentation.

---

## Executive Key Performance Indicators (KPIs)

| Metric | Verified Value | Business Meaning |
|---|---|---|
| **Total Net Revenue** | **$187,676,570.02** (~$187.68M) | Overall revenue generated across all 10 store locations over the dataset period. |
| **Total Units Sold** | **65,695,409** (~65.70M units) | Total physical volume of products sold. |
| **Weighted Average Unit Price** | **$2.86 / unit** | True average dollar value realized per physical unit sold ($\frac{\text{Total Revenue}}{\text{Total Units}}$). |
| **Top Category (Volume)** | **FOODS (68.6% Share)** | Main driver of customer foot traffic and purchase frequency (45.09M units sold). |
| **Top Regional Market** | **California / CA (44.9% Revenue Share)** | Highest-performing state market ($84.25M net revenue across 4 stores). |

---

## AI Recommendation & Analytical Validation Framework

| AI Hypothesis / Assumption | Analyst Verification Method | Final Empirical Finding |
|---|---|---|
| **Hypothesis 1:** *"FOODS drives the vast majority of unit volume at low prices, while HOUSEHOLD yields higher revenue per unit."* | Evaluated category summary PivotTable in Excel and verified unit volume vs. weighted average prices. | **CONFIRMED:** `FOODS` accounts for 68.6% of unit volume ($2.42/unit weighted price), whereas `HOUSEHOLD` yields $3.86/unit weighted price (+60% yield per item). |
| **Hypothesis 2:** *"Sales volume is split evenly (~33% each) across California, Texas, and Wisconsin."* | Aggregated state-level totals from the monthly store dataset. | **REFUTED:** Regional sales are heavily skewed. California leads with 44.9% of revenue ($84.2M), outperforming Texas (28.8% / $54.0M) and Wisconsin (26.3% / $49.4M). |
| **Hypothesis 3:** *"Hobby products exhibit higher demand volatility than staple consumer groceries."* | Computed Coefficient of Variation ($\text{CV} = \frac{\text{Std Dev}}{\text{Mean}}$) for top 300 active items. | **CONFIRMED:** `HOBBIES` items average a high demand volatility score ($\text{CV} = 1.33$), whereas staple groceries show steady, low volatility down to a $\text{CV}$ of 0.25. |

---

## Strategic Business Recommendations

1. **Adopt Flexible Inventory Stocking for Unpredictable Categories (`HOBBIES`)**
   * **Insight:** Grocery sales are steady and predictable, whereas hobby items experience erratic sales spikes.
   * **Action:** Shift from fixed reorder points to flexible safety-stock levels for `HOBBIES`. This prevents stock-outs during demand surges while avoiding tying up working capital in unsold inventory during slow periods.

2. **Prioritize Supply Chain & Inventory for Top-Performing Regions (`CA`)**
   * **Insight:** California stores generate nearly 45% of overall revenue ($84.2M), significantly outperforming Texas ($54.0M) and Wisconsin ($49.4M).
   * **Action:** Direct warehouse replenishment and logistics throughput toward California distribution centers to maintain maximum product availability in the business's highest-earning market.

3. **Leverage Grocery Foot Traffic to Cross-Sell High-Margin Goods**
   * **Insight:** Food products bring shoppers through the door (68.6% of total unit volume), but household items yield 60% higher revenue per item sold ($3.86 vs. $2.42).
   * **Action:** Maintain competitive pricing on staple groceries to preserve store foot traffic while strategically placing higher-yielding household products on end-cap displays near grocery aisles.

---

## Repository Directory Structure

```text
03_Walmart_Retail_Analytics/
├── data/
│   ├── raw/                        # Original M5 Kaggle CSV datasets (calendar, sell_prices, sales_train)
│   └── processed/                  # Cleaned & aggregated CSV extracts (monthly_store_category_sales, item_volatility)
├── python/
│   └── 01_m5_data_prep.py          # Python aggregation and unpivoting script
├── excel/
│   └── Walmart_Sales_Demand_Analytics.xlsx   # Master workbook, PivotTables, and dashboard
└── README.md                       # Comprehensive project documentation
