# Global Retail Profitability & Supply Chain Diagnostic

An end-to-end data analytics project diagnosing margin erosion, discount sensitivity, and fulfillment efficiency across 51,290 global retail transactions.

## Tech Stack & Architecture
- **Data Ingestion & Cleaning:** Python (Pandas, NumPy) in Google Colab
- **Feature Engineering:** Temporal extraction (.dt), Lead Time computation, Discretized Discount Bins (pd.cut)
- **Relational Querying:** SQLite (In-Memory DB), Window Functions (`DENSE_RANK`), CTEs, `HAVING` filters
- **BI & Visualization:** Power BI Desktop, DAX Measures (`DIVIDE`, `DISTINCTCOUNT`, `SWITCH`)

---

## Key Strategic Findings

### 1. The Heavy Furniture Margin Bleed (Tables)
- **Finding:** Tables generated **$757,041.92** in revenue but resulted in a net operational loss of **-$64,083.39** (average margin: **-24.20%**).
- **Root Cause:** A combination of high dimensional freight costs and unconstrained promotional discounting (>20%).
- **Recommendation:** Cap promotional discounts on Furniture at 15% and introduce dimensional-weight logistics surcharges.

### 2. The 20% Discount Elasticity Tipping Point
- **Finding:** Discounts between 0% and 20% maintained healthy margins (+24% to +32%). Profitability turned net-negative once discounts exceeded 20%, plummeting to -60% to -85% for clearance tiers (>50%).
- **Recommendation:** Implement an automated sales approval gate requiring management sign-off for discounts above 20%.

### 3. Logistics & Fulfillment SLA Compliance
- **Finding:** Premium shipping tiers strictly meet delivery SLAs (Same Day: ~0.04 days, First Class: ~2.18 days), while Standard Class averages 5.01 days across 60%+ of order volume.
- **Recommendation:** Strategically position regional fulfillment hubs near high-density metro zones to compress standard lead times to 3 days.

---

## How to Reproduce
1. Clone the repository.
2. Run `notebooks/01_eda_and_sql_pipeline.ipynb` to regenerate `global_superstore_cleaned.csv`.
3. Open `dashboard/Global_Superstore.pbix` in Power BI Desktop to inspect the DAX model and visuals.
