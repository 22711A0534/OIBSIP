Data Analytics L1-T1 — EDA on Retail Sales Data

📌 Overview

This project performs Exploratory Data Analysis (EDA) on a retail sales dataset to identify sales patterns, customer behaviour trends, product performance, category-level revenue, profitability, and actionable business insights.

🎯 Objective

The main objectives of this project are to:

Inspect and understand the retail sales dataset.

Calculate descriptive statistics for numerical variables.

Analyse monthly and quarterly sales trends.

Study customer demographics by age group and gender.

Identify the top 10 best-selling products.

Analyse revenue by product category.

Examine relationships between numerical variables using a correlation heatmap.

Analyse profit margins across product categories.

Generate actionable business recommendations from the findings.

🛠️ Technologies Used

Python

Pandas

NumPy

Matplotlib

Seaborn

Jupyter Notebook

📂 Project Structure

DataAnalytics-L1-EDARetailSales/
│
├── dataset/
├── notebook/
├── output/
├── report/
├── screenshots/
└── README.md

📊 Analysis Performed

1. Dataset Inspection

The dataset was loaded and examined for its structure, shape, column data types, and numerical variables.

2. Descriptive Statistics

Mean, median, mode, and standard deviation were calculated for numerical variables to understand central tendency and variability.

3. Monthly Sales Trend

The Date column was converted to datetime format and monthly revenue trends were analysed using a line chart. The analysis helped identify fluctuations and seasonal patterns in sales over time.

4. Quarterly Sales Trend

Quarterly revenue was analysed to identify broader seasonal and time-based patterns and compare sales performance across quarters.

5. Customer Demographics

Customer age groups and gender distribution were analysed.

Adults (35–64) form the largest customer segment.

Young Adults (25–34) are the next largest segment.

The gender distribution is relatively balanced, with male customers slightly higher.

6. Top 10 Best-Selling Products

Products were ranked according to total order quantity to identify the products with the highest demand.

The analysis identified Water Bottle – 30 oz. and Patch Kit/8 Patches among the highest-selling products by quantity.

7. Revenue by Product Category

Revenue was analysed by product category.

Bikes generated the highest total revenue.

Accessories followed Bikes.

Clothing generated the lowest revenue among the categories analysed.

8. Correlation Analysis

A correlation matrix and heatmap were used to examine relationships between numerical variables.

Strong positive relationships were observed between important sales and financial variables such as cost, revenue, and profit.

9. Profit Margin Analysis

Profit margin was analysed by product category to compare profitability independently of total revenue.

Accessories achieved the highest profit margin among the analysed categories, while Clothing and Bikes had comparatively lower margins.

💡 Key Business Insights

Accessories provide the highest profit margin and represent an opportunity for improving overall profitability.

Bikes are the strongest revenue-generating product category and require appropriate inventory and promotional support.

High-demand products should be kept consistently available to avoid missed sales opportunities.

Sales fluctuate over time, so seasonal demand should be considered when planning inventory and marketing.

Adults aged 35–64 and Young Adults aged 25–34 represent the strongest customer segments.

📈 Business Recommendations

Prioritize high-margin Accessories through promotions, cross-selling, and product bundles.

Maintain strong Bike inventory and use historical sales patterns for stock planning.

Keep high-demand products consistently available.

Plan inventory, marketing, and staffing around seasonal demand patterns.

Develop targeted customer marketing for the largest age groups while creating strategies to improve engagement among smaller segments.

📁 Project Files

notebook/ — Jupyter Notebook containing the complete EDA implementation.

dataset/ — Dataset used for the analysis.

output/ — Generated analysis outputs.

screenshots/ — Project screenshots.

report/ — Project report.
https://drive.google.com/file/d/1YkkQPWCbtyaeW7Q2wkIFHseUu2j3mba_/view?usp=sharing
▶️ How to Run

Clone or download the repository.

Open the notebook folder.

Launch the Jupyter Notebook.

Ensure the dataset is available at the path expected by the notebook.

Run the notebook cells from top to bottom.

✅ Conclusion

The exploratory analysis provides useful insights into retail sales performance, customer demographics, product demand, revenue contribution, and profitability. The findings can support better inventory planning, targeted marketing, product promotion, and profitability-focused business decisions.

👩‍💻 Author

Sai Sprisha

Track: Data Analytics
Level: Level 1
Task: Task 1 — EDA on Retail Sales Data
Internship: Oasis Infobyte
