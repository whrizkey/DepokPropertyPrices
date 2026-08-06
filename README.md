# Depok Residential Property Market Analysis (2026) 🏡

Work in Progress (Phase 1: Data Cleaning Completed)

##  Project Overview
This project aims to analyze residential property prices and demand trends in Depok, West Java (Jabodetabek region). The goal is to identify pricing patterns, regional disparities, and key drivers of property value using Python.

##  Tools Used
*   **Python:** Pandas, NumPy, Regular Expressions (`re`)
*   **Environment:** Google Colab / Jupyter Notebook

##  Dataset
*   **Source:** Scraped property listings from Kaggle (Jan 2026).
*   **Raw Data:** ~40,200 rows of unstructured scraped data.
*   **Processed Data:** Cleaned, standardized numeric dataset ready for EDA.

##  Phase 1 Progress: Overcoming "Dirty" Real Estate Data
Real estate data scraped from Indonesian property portals is notoriously messy. This phase focused on building a robust cleaning pipeline to handle severe formatting inconsistencies and scraped layout shifts.

**Key Data Engineering Challenges Solved:**

1.  **Text-to-Numeric Currency Conversion:**
    *   *The Problem:* Prices were stored as raw text strings with varying Indonesian denominators (e.g., `"385 Juta"`, `"2,5 Miliar"`, `"5,3 Miliar Total"`).
    *   *The Solution:* Built a custom parsing function using Regular Expressions to identify the denominator, strip text, handle Indonesian decimal commas, and multiply out to standard `float` values.
2.  **Handling "Shifted" Scraped Data:**
    *   *The Problem:* Due to inconsistent web page layouts, data often shifted into the wrong columns (e.g., Land Area `LT:1368 m²` appearing in the `Bedrooms` column).
    *   *The Solution:* Instead of blindly parsing columns, I combined all feature columns into a single text string per row. I then used specific `regex` patterns (hunting for "LT" and "LB") to intelligently extract Land Area and Building Area regardless of which column the scraper originally placed it in.
3.  **Outlier Mitigation:**
    *   Filtered out severe scraping errors (e.g., properties resulting in > 20 bedrooms) by converting them to `NaN` for later imputation or removal.

## Next Steps (Upcoming)
- [ ] **Exploratory Data Analysis (EDA):** Price per sqm calculations and district-level aggregations.
- [ ] **Data Visualization:** Heatmaps and distribution plots using Seaborn/Plotly.
- [ ] **Insights Generation:** Determining the premium associated with specific districts or property features.

---
*Explore the `notebooks/01_data_cleaning.ipynb` file to see the Python cleaning pipeline.*
