Data Analytics L1-T2 — Customer Segmentation Analysis

📌 Overview

This project focuses on Customer Segmentation Analysis using machine learning techniques to group customers based on their purchasing behaviour. The objective is to identify meaningful customer segments and generate insights that can support targeted marketing and customer relationship strategies.

🎯 Objective

The main objectives of this project are to:

Understand customer purchasing behaviour.

Prepare and preprocess customer transaction data.

Create meaningful customer-level behavioural features.

Apply K-Means clustering for customer segmentation.

Use the Elbow Method to determine a suitable number of clusters.

Visualize customer segments.

Profile and compare the identified customer groups.

Analyse customer counts across segments.

Generate actionable marketing recommendations for different customer segments.

🛠️ Technologies Used

Python

Pandas

NumPy

Matplotlib

Seaborn

Scikit-learn

Jupyter Notebook

📂 Project Structure

DataAnalytics-L1-CustomerSegmentation/
│
├── dataset/
│   └── Online Retail.xlsx
│
├── notebook/
│   └── Level1_Task2_Customer_Segmentation.ipynb
│
├── output/
│   └── customer_segment_summary.csv
│
├── report/
│   └── OASIS_Level1_Task2_Customer_Segmentation_Report.pdf
│
├── screenshots/
│   ├── 01_Elbow_Method.png
│   ├── 02_Recency_vs_Monetary.png
│   ├── 03_Frequency_vs_Monetary.png
│   ├── 04_Customer_Count_By_Segment.png
│   └── 05_Marketing_Recommendations.png
│
└── README.md

📊 Methodology

1. Data Loading and Understanding

The Online Retail dataset was loaded and examined to understand its structure, available fields, data types, and transaction-level information.

2. Data Preparation

The transaction data was prepared for customer-level analysis by handling the required data preparation steps and selecting relevant information for customer segmentation.

3. Customer Behaviour Features

Customer-level behavioural features were created from the transaction data to represent purchasing patterns. These features were used as the basis for segmentation.

4. Feature Scaling

The selected numerical features were standardized using StandardScaler so that differences in feature scales would not disproportionately influence the clustering algorithm.

5. K-Means Clustering

K-Means clustering was applied to group customers with similar behavioural characteristics into distinct segments.

6. Elbow Method

The Elbow Method was used to evaluate different values of K and determine a suitable number of customer clusters.

7. Customer Segment Visualization

The resulting customer segments were visualized using plots such as Recency vs Monetary and Frequency vs Monetary to understand the distribution and characteristics of the clusters.

8. Customer Count Analysis

The number of customers in each segment was analysed to understand the size of the different customer groups.

9. Segment Profiling and Marketing Recommendations

The identified customer segments were interpreted based on their behavioural characteristics. Marketing recommendations were developed to help businesses target each segment more effectively.

📈 Analysis and Visualizations

The project includes the following visual analyses:

Elbow Method for selecting the number of clusters.

Recency vs Monetary customer segmentation visualization.

Frequency vs Monetary customer segmentation visualization.

Customer count by segment.

Marketing recommendations based on customer segment characteristics.

💡 Key Insights

Customer segmentation helps identify groups of customers with similar purchasing behaviour rather than treating all customers in the same way.

The analysis provides a basis for understanding differences in customer activity, purchase frequency, recency, and monetary contribution. These differences can be used to develop more personalized marketing and customer retention strategies.

📈 Marketing Recommendations

High-value customers: Provide loyalty rewards, exclusive offers, and personalized experiences to retain valuable customers.

Frequent customers: Encourage continued engagement through loyalty programs, personalized recommendations, and repeat-purchase incentives.

At-risk or inactive customers: Use targeted re-engagement campaigns, reminders, and suitable discounts to encourage customers to return.

Lower-value customers: Use cost-effective promotional campaigns and product recommendations to increase purchase frequency and customer value.

Segment-specific campaigns: Avoid using the same marketing strategy for every customer. Tailor campaigns according to the behaviour and characteristics of each segment.

📁 Project Files

dataset/ — Contains the Online Retail dataset used for customer segmentation.

notebook/ — Contains the Jupyter Notebook with the complete implementation.

output/ — Contains the generated customer segment summary.

report/ — Contains the project report.

screenshots/ — Contains screenshots of the analysis, visualizations, and recommendations.

README.md — Contains project documentation.
https://drive.google.com/file/d/1E32RDKiDm4doFmyG_VITWGOMYkSvaeQ8/view?usp=sharing
▶️ How to Run

Clone or download the repository.

Open the notebook folder.

Launch Level1_Task2_Customer_Segmentation.ipynb using Jupyter Notebook or JupyterLab.

Ensure the Online Retail.xlsx dataset is available in the dataset folder.

Install the required Python libraries if they are not already installed.

Run the notebook cells from top to bottom.

📌 Output

The project generates a customer segment summary file:

customer_segment_summary.csv

This output summarizes the identified customer segments and can be used for further analysis and interpretation.

✅ Conclusion

Customer segmentation provides businesses with a practical way to understand differences in customer purchasing behaviour. By applying K-Means clustering and analysing the resulting customer groups, this project provides a foundation for targeted marketing, customer retention, loyalty strategies, and improved customer relationship management.

👩‍💻 Author

Sai Sprisha

Track: Data Analytics
Level: Level 1
Task: Task 2 — Customer Segmentation
