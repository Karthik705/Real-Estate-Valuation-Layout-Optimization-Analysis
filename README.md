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
*(Insert a screenshot of your Power BI dashboard here showing the map, bar chart, and property type slicer)*

## 📂 Repository Structure
* `/data` - Contains the processed `Cleaned_Bangalore_Housing.csv` dataset.
* `/notebooks` - Jupyter Notebook detailing the data wrangling and EDA process.
* `/dashboards` - Power BI `.pbix` file and dashboard layout exports.
