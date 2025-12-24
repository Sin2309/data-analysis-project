# Data Analysis Project: Optimizing Marketing ROI
**Group:** Nova

## 🎯 Problem Statement
Marketing budgets are limited. The company runs multiple campaigns, but it is unclear which customer groups respond best or which channels create the most impact. A data-driven strategy is needed to optimize future marketing decisions. We need to identify high-value customer segments to optimize campaign ROI and reduce churn.

## ❓ Decision Questions (Key KPIs)
This project aims to answer three core questions to support business decisions:
1. **Customer Value:** Which demographic segment (Income/Age/Education) generates the highest total revenue?
2. **Channel Efficiency:** Which sales channel (Web vs. Store vs. Catalog) drives the most high-value purchases?
3. **Campaign Optimization:** Is there a correlation between household structure (kids/teens) and the acceptance of premium marketing campaigns?

---

## 📁 Project Structure
* **/data** → Raw & cleaned datasets (`marketing_data.csv`)
* **/sql** → SQL scripts for data cleaning, Star Schema views (`Dim_Customer`, `Fact_Performance`)
* **/notebooks** → Python/Colab notebooks for EDA & statistical checks
* **/dashboard** → Tableau Public link & Dashboard Screenshots
* **/report** → Presentation slides, final insights, and documentation

---

## 🔄 Workflow Summary

### 1. **Week 1:** Planning & Setup (✅ Completed)
* Defined problem statement & setup GitHub repository.
* Established team roles and decision questions.

### 2. **Week 2:** Exploratory Data Analysis (EDA) (✅ Completed)
Used Python & SQL to identify errors and understand data distribution.
* **Data Quality Check:** Identified outliers (Age > 100, Income > $600k) and null values.
* **Findings:** * Found 3 customers born before 1900 (removed).
    * Validated Income distribution to set filtering thresholds.

### 3. **Week 3:** SQL Data Modelling (✅ Completed)
Built a **Star Schema** to optimize performance for Tableau.
* **Data Cleaning Logic:** Applied filters `Year_Birth >= 1940` and `Income <= 200,000`.
* **Schema Design:**
    * `Dim_Customer`: ID, Age, Education, Marital Status, Kidhome.
    * `Fact_Performance`: Total Spend, Conversion Rate, Channel Purchases.
* **KPI Definitions:**
    * *Total Spend* = Sum of all Mnt products.
    * *Conversion Rate* = Accepted Campaigns / Total Customers.

### 4. **Week 4:** Dashboard & Strategic Insights (✅ Completed)
**Goal:** Visualize insights using Tableau to answer the 3 Decision Questions.

#### a. Dashboard Components
We constructed an interactive dashboard with 4 key visualizations:
1.  **Revenue by Education (Bar Chart):** Identified "Graduation" and "PhD" as the top revenue-generating segments.
2.  **Income vs. Spending (Scatter Plot):** Confirmed a strong positive correlation between income and spending, with specific outliers identified.
3.  **Channel Efficiency (Bar Chart):** "Store" is the dominant channel, followed by "Web".
4.  **The 'Kid Penalty' (Line Chart):** Visualized the negative impact of family size on conversion rates.

#### b. Key Strategic Findings
* **High-Value Profile:** Customers with **PhD/Graduation** degrees and **Income > $70k** drive ~60% of revenue.
* **The "Kid Penalty":** Household structure is the strongest predictor of campaign success.
    * *0 Kids:* **~17.5%** Conversion Rate (High)
    * *1 Kid:* **~12.2%** Conversion Rate (Medium)
    * *2 Kids:* **~4.1%** Conversion Rate (Low)
* **Channel Strategy:** While Stores drive volume, the **Web** channel is crucial for high-income, childless professionals.

---

## 👥 Team Members
* **Phan Dương Ánh Linh** (MSSV: 22010053)
* **Trần Khánh Linh** (MSSV: 22010022)
* **Nguyễn Lê Bảo Uyên** (MSSV: 22070002)

## 🔗 Project Resources
* **Google Drive:** [https://drive.google.com/drive/folders/1mBb-yUGS2zl9mDDt_n9sU09yt-iXiC2p?usp=sharing]
* **Tableau Public:** [Link to Dashboard]
