# Depok Residential Property Market Analysis (2026) 

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

##  Phase 2 Progress: EDA & Interactive Visualization
With the data cleaned, the project transitioned into Exploratory Data Analysis (EDA) and visualization. I built an interactive **Power BI** dashboard to explore price-per-sqm calculations, market spread, and district-level aggregations.


<img width="1545" height="1049" alt="Screenshot 2026-08-06 at 13 37 32" src="https://github.com/user-attachments/assets/35e7cac9-ee70-4540-a9f4-8f2cbce70940" />
<img width="1549" height="983" alt="Screenshot 2026-08-06 at 13 38 08" src="https://github.com/user-attachments/assets/5efa323d-5ebc-4118-9f0c-8dbb4abc9417" />


### Dashboard Features:
* **Dynamic KPI Summary:** Cards displaying Total Market Listings, Median Property Price, and Median Price-per-m² that update instantly when filtering the data.
* **District Liquidity:** Visualizing the volume of listings across all 37 Depok districts to highlight high-supply vs. exclusive neighborhoods.
* **Market Spread Scatter Plot:** Mapping property scale against Pricing Tiers to spot market distributions and pricing clusters.

*Explore the `notebooks/01_data_cleaning.ipynb` file to see the Python cleaning pipeline.*
