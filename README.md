# Data Analysis Project: Optimizing Marketing ROI
Group: **Nova**

## 🎯 Problem Statement
Marketing budgets are limited. The company runs multiple campaigns, but it is unclear which customer groups respond best or which channels create the most impact. A data-driven strategy is needed to optimize future marketing decisions. The marketing team is currently wasting budget on mass marketing campaigns without knowing which customers respond best. We need to identify high-value customer segments to optimize campaign ROI and reduce churn.

## ❓ Decision Questions (Key KPIs)
This project aims to answer three core questions to support business decisions:
1. **Customer Value:** Which demographic segment (Income/Age/Education) generates the highest total revenue?
2. **Channel Efficiency:** Which sales channel (Web vs. Store vs. Catalog) drives the most high-value purchases?
3. **Campaign Optimization:** Is there a correlation between household structure (kids/teens) and the acceptance of premium marketing campaigns?

---

## 📁 Project Structure
* **/data** → Raw & cleaned datasets (`marketing_data.csv`)
* **/sql** → SQL scripts for data cleaning, joins, and KPI logic
* **/notebooks** → Python/Colab notebooks for EDA, statistical checks, and visualization
* **/dashboard** → Power BI (`.pbix`) files for interactive reporting
* **/report** → Presentation slides, final insights, and documentation

## 🔄 Workflow Summary
# 1. **Week 1:** Defined problem & setup GitHub. (✅ Completed)

# 2. **Week 2:** Exploratory Data Analysis (EDA) with Python. (✅ Completed)
Exploratory Data Analysis (EDA) to identify errors and understand data distribution before cleaning.
*/
**Data Quality Check**
**Identify customers with unrealistic birth years** (To determine filtering threshold for Week 3)
SELECT * FROM marketing_data 
WHERE Year_Birth < 1940; 
**Finding:** Found 3 customers born in 1893, 1899, 1900 -> Need to be removed.
**Check for missing income values** (Null Income)
SELECT COUNT(*) as Missing_Income_Count 
FROM marketing_data 
WHERE Income IS NULL;
**Basic Statistics**
**Analyze customer distribution by Education level**
SELECT Education, COUNT(ID) as Total_Customers
FROM marketing_data
GROUP BY Education
ORDER BY Total_Customers DESC;
**Preliminary analysis of sales performance by channel**
SELECT 
    SUM(NumWebPurchases) as Total_Web,
    SUM(NumStorePurchases) as Total_Store,
    SUM(NumCatalogPurchases) as Total_Catalog
FROM marketing_data;

# 3. **Week 3:** SQL Data Modelling & KPI Definition. (✅ Completed)
**SQL Logic defining the Data Model for Visualization Tool**
**Create Dimension Table** (Attributes)
CREATE VIEW Dim_Customer AS
SELECT 
    ID, 
    Year_Birth, 
    (2014 - Year_Birth) AS Age,
    Education, 
    Marital_Status, 
    Country,
    Income 
FROM marketing_data
WHERE Year_Birth > 1940;
**Create Fact Table** (Metrics)
CREATE VIEW Fact_Performance AS
SELECT 
    ID, 
    Recency, 
    (MntWines + MntFruits + MntMeatProducts + MntFishProducts + MntSweetProducts + MntGoldProds) AS Total_Spend,
    NumWebPurchases, 
    NumStorePurchases, 
    AcceptedCmp1 + AcceptedCmp2 + AcceptedCmp3 + AcceptedCmp4 + AcceptedCmp5 AS Total_Campaigns_Accepted,
    Response AS Last_Campaign_Success
FROM marketing_data
WHERE Year_Birth > 1940;
📊 Data Model & KPIs
We have designed a **Star Schema** data model to optimize performance in Tableau:
# **Data Schema**
* **Dim_Customer:** Stores static customer attributes (ID, Age, Education, Marital Status).
* **Fact_Performance:** Stores transactional data (Sales, Recency, Campaign Responses).
* **Relationship:** One-to-Many relationship on `ID`.
# **Key Metrics Defined**
* **Total Spend:** Sum of all product categories (`MntWines` + `MntFruits` + ...).
* **Conversion Rate:** `Total Accepted Campaigns` / `Total Customers`.
* **Age:** Calculated as `2014 - Year_Birth`.
* **Active Users:** Customers with `Recency < 60 days`.

# 4. **Visualize** → Build interactive charts in `/dashboard`
# 5. **Report** → Summarize findings in `/report`

## 👥 Team Members
* Phan Dương Ánh Linh - mssv: 22010053
* Trần Khánh Linh - mssv: 22010022
* Nguyễn Lê Bảo Uyên - mssv: 22070002

## 🔗 Google Drive Backup
* **Drive folder:** <insert [link](https://drive.google.com/drive/folders/1mBb-yUGS2zl9mDDt_n9sU09yt-iXiC2p?usp=share_link)>
