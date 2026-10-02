# Bangalore Real Estate Valuation & Layout Optimization Analysis

An end-to-end data analytics and business intelligence project exploring how micro-locations, furnishing status, and property types influence housing valuations in Bangalore.

## 📊 Project Overview
This project bridges hard data analytics with spatial layout planning. Using a dataset of 4,000+ real estate listings, the project cleans messy raw data, engineers custom valuation metrics, performs statistical correlation analysis, and delivers an interactive Power BI dashboard.

## 🛠️ Tech Stack
* **Python (Pandas, Seaborn, Matplotlib):** Data cleaning, feature engineering, and statistical correlation analysis.
* **Power BI:** Interactive dashboarding, geographic mapping, and dynamic filtering.
* **Folium:** Geospatial validation mapping.

## 📈 Key Insights
* **The Bedroom Paradox:** Exploratory analysis revealed a near-zero correlation ($r = 0.05$) between bedroom count and total property price, proving that spatial quantity alone does not dictate market value.
* **Structural Value Drivers:** Furnishing status and property type demonstrated a strong positive correlation ($r = 0.58$), highlighting that modern high-rises and pre-furnished units command higher valuation premiums.

## 🚀 Dashboard Preview
<img width="1509" height="841" alt="image" src="https://github.com/user-attachments/assets/c1dd1700-b678-4d00-baa7-3d0b0e8db9ad" />
<img width="1498" height="840" alt="image" src="https://github.com/user-attachments/assets/64e9219c-7f41-484c-9bd7-36875cca087e" />

## 📂 Repository Structure
* `/data` - Contains the processed `Cleaned_Bangalore_Housing.csv` dataset.
* `/notebooks` - Jupyter Notebook detailing the data wrangling and EDA process.
* `/dashboards` - Power BI `.pbix` file and dashboard layout exports.

## 🏷️ Price-Review Queue (Random Forest Anomaly Flagging)
An extension of the valuation analysis: a repeatable process that estimates an expected price for each Bangalore villa/house listing, flags sharp deviations, and separates genuine pricing concerns from data-quality noise.

📄 **[Read the full case-study write-up (PDF)](reports/Real_Estate_Price_Review_Report.pdf)** — figures below are from the current pipeline (`real_estate_outputs/project_summary.csv`) and supersede the PDF's, which were drawn from an earlier run before the grouped cross-validation fix.

**Process:** Audit → Clean → De-duplicate (listing fingerprint) → Estimate (Random Forest, 5-fold cross-validation grouped by fingerprint to avoid leakage) → Flag (≥ +100% over-priced, ≤ -50% under-priced) → Triage with data-quality context.

**Headline results**
* 10,320 raw listings → 5,479 usable records; **527 flagged for review (9.6%)** — 305 over-priced, 222 under-priced.
* Owner-posted listings are flagged more than any other seller type (17.6%), vs 6.0% for agent-posted; ready-to-move properties are flagged far more often than under-construction (16.7% vs 2.5%).
* 71.5% of records are repeat postings of the same property.
* Extreme-area records are flagged 36.7% of the time vs 1.8% for repeated listings — an area check at submission would remove many false alarms before any model runs.
* Three localities (the grouped "Other" bucket, Sarjapur Road, Whitefield) account for 384 of the 527 flags (73%).

**Limitations:** grouped cross-validation R² is 0.28 (MAE ≈ ₹94.6 lakh) — the model ranks relative outliers rather than quoting a price. An earlier, non-grouped version of this model scored R² ≈ 0.85, but that number was inflated by leakage between duplicate postings of the same property across train/test; the notebook now reports the honest, leakage-free figure. Flags are review candidates, not verdicts. Scope is villas and independent houses only.

Outputs are in `/real_estate_outputs` and the modelling notebook is `Real_Estate_Valuation_Analysis.ipynb`.
