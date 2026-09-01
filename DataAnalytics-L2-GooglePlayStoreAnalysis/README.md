# Data Analytics L2-T4 — Google Play Store Analysis

## 📌 Overview

This project focuses on analysing the **Google Play Store Apps and User Reviews datasets** to generate data-driven insights about app categories, ratings, installations, pricing, estimated revenue, and user sentiment.

The project follows a complete data analytics workflow including data loading, data inspection, missing-value handling, duplicate removal, data cleaning, exploratory analysis, category analysis, rating analysis, app-size analysis, installation analysis, free-versus-paid analysis, revenue estimation, sentiment analysis, and interactive visualization.

## 🎯 Objective

The main objectives of this project are to:

- Load and understand the Google Play Store Apps dataset.
- Load and analyse the User Reviews dataset.
- Inspect the structure and quality of both datasets.
- Identify and handle missing values.
- Detect and remove duplicate records.
- Clean numerical columns such as `Installs` and `Price`.
- Convert app size values into MB.
- Analyse app distribution across categories.
- Analyse ratings and installations.
- Compare free and paid applications.
- Estimate revenue for paid applications.
- Analyse user reviews using sentiment analysis.
- Compare sentiment across app categories.
- Generate data-driven recommendations for developing a new app.

## 📊 Datasets

### 1. Google Play Store Apps Dataset

**File:** `googleplaystore.csv`

Initial dataset size:

- **10,841 rows**
- **13 columns**

Important columns include:

- `App`
- `Category`
- `Rating`
- `Reviews`
- `Size`
- `Installs`
- `Type`
- `Price`
- `Content Rating`
- `Genres`
- `Last Updated`
- `Current Ver`
- `Android Ver`

### 2. Google Play Store User Reviews Dataset

**File:** `googleplaystore_user_reviews.csv`

Initial dataset size:

- **64,295 rows**
- **5 columns**

Important columns include:

- `App`
- `Translated_Review`
- `Sentiment`
- `Sentiment_Polarity`
- `Sentiment_Subjectivity`

## 🛠️ Technologies Used

- **Python**
- **Pandas** – Data manipulation and analysis
- **NumPy** – Numerical operations
- **Matplotlib** – Data visualization
- **Seaborn** – Statistical visualization
- **TextBlob** – Sentiment analysis
- **Plotly** – Interactive visualization
- **Jupyter Notebook** – Development environment

## 📂 Project Structure

```text
DataAnalytics-L2-T4-GooglePlayStore/
│
├── dataset/
│   ├── googleplaystore.csv
│   └── googleplaystore_user_reviews.csv
│
├── notebook/
│   └── Level2_Task4_Google_Play_Store.ipynb
│
├── report/
│   └── OASIS_Level2_Task4_Google_Play_Store_Report.pdf
│
├── screenshots/
│   ├── 01_dataset_loading.png
│   ├── 02_dataset_head.png
│   ├── 03_dataset_info.png
│   ├── 04_missing_values.png
│   ├── 05_duplicate_analysis.png
│   ├── 06_data_cleaning.png
│   ├── 07_category_analysis.png
│   ├── 08_rating_distribution.png
│   ├── 09_average_rating_by_category.png
│   ├── 10_app_size_distribution.png
│   ├── 11_installs_distribution.png
│   ├── 12_size_vs_installs.png
│   ├── 13_free_vs_paid.png
│   ├── 14_paid_price_distribution.png
│   ├── 15_revenue_by_category.png
│   ├── 16_sentiment_distribution.png
│   └── 17_sentiment_by_category.png
│
├── demovideo/
│
└── README.md
```

> Update the notebook, report, or screenshot names if your actual project uses different filenames.

## 🔍 Project Workflow

### 1. Data Loading

Both datasets were loaded using Pandas.

```python
apps_df = pd.read_csv("../dataset/googleplaystore.csv")
reviews_df = pd.read_csv("../dataset/googleplaystore_user_reviews.csv")
```

The Apps dataset contains **10,841 rows and 13 columns**, while the User Reviews dataset contains **64,295 rows and 5 columns**.

### 2. Dataset Inspection

The structure of both datasets was inspected using `info()` and the first few records were displayed using `head()`.

The Apps dataset contains information about app category, rating, reviews, size, installations, type, price, content rating, genre, and version details.

The User Reviews dataset contains review text and sentiment-related information.

## 🧹 Data Cleaning

### 3. Missing-Value Analysis

Missing values were checked in both datasets.

For the Apps dataset, the main missing values were found in:

- `Rating`
- `Current Ver`
- `Android Ver`
- `Content Rating`
- `Type`

For the User Reviews dataset, missing values were mainly present in:

- `Translated_Review`
- `Sentiment`
- `Sentiment_Polarity`
- `Sentiment_Subjectivity`

### 4. Duplicate Removal

Duplicate rows were identified and removed.

Initial duplicate counts:

- **Apps dataset:** 483 duplicate rows
- **Reviews dataset:** 33,616 duplicate rows

After removing completely duplicated rows:

- Apps dataset: **10,358 rows**
- Reviews dataset: **30,679 rows**

Duplicate app names were then checked separately. There were **698 duplicate app names**, and one record was retained for each app.

The Apps dataset was reduced to **9,660 unique apps**.

### 5. Missing-Value Handling

Missing values in the Apps dataset were handled using:

- **Median imputation** for numerical columns such as `Rating`, `Size_MB`, `Installs`, and `Price`
- **Mode imputation** for categorical columns such as `Current Ver`, `Android Ver`, `Content Rating`, and `Type`

For sentiment analysis, rows without review text were removed.

After cleaning:

- Apps dataset: **9,660 rows × 14 columns**
- Reviews dataset: **29,692 rows × 5 columns**
- Remaining missing values: **0**
- Remaining duplicate rows: **0**

## 🔢 Data Transformation

### 6. Cleaning the Installs Column

Values such as:

```text
10,000+
5,000,000+
50,000,000+
```

were converted into numerical values by removing commas and the `+` symbol.

This allowed installation data to be used for numerical analysis.

### 7. Cleaning the Price Column

The `$` symbol was removed from the `Price` column and the values were converted into numeric form.

### 8. Converting App Size

App sizes such as `19M`, `8.7M`, and `2.8M` were converted into a numerical `Size_MB` column.

Values expressed in kilobytes were converted into megabytes.

## 📱 App Category Analysis

### 9. Number of Apps by Category

The number of applications in each category was calculated.

The most represented categories include:

- **FAMILY**
- **GAME**
- **TOOLS**
- **BUSINESS**
- **MEDICAL**
- **PERSONALIZATION**
- **PRODUCTIVITY**
- **LIFESTYLE**
- **FINANCE**
- **SPORTS**

The **FAMILY** category has the largest number of apps, followed by **GAME** and **TOOLS**.

### 10. Top 10 Most Saturated Categories

The top 10 categories by number of applications were visualized using a bar chart.

This analysis helps identify highly competitive and saturated areas of the Google Play Store.

## ⭐ Rating Analysis

### 11. Rating Distribution

The distribution of app ratings was analysed using a histogram.

The ratings are mainly concentrated around the **4.0–4.5 range**, showing that many apps have relatively high user ratings.

### 12. Average Rating by Category

Average ratings were calculated for each category and visualized using a horizontal bar chart.

This helps compare user satisfaction across different app categories.

## 📦 App Size and Installation Analysis

### 13. App Size Distribution

A distribution plot was created for app sizes after converting the values into MB.

This helps understand the typical size of applications available on the platform.

### 14. Install Distribution

The distribution of app installations was analysed after converting the `Installs` column into numerical values.

This helps identify how widely applications are installed.

### 15. App Size vs Installations

A relationship between app size and number of installations was visualized.

This analysis helps explore whether application size appears to have a noticeable relationship with installation volume.

## 💰 Free vs Paid App Analysis

### 16. Free vs Paid Apps

Applications were classified based on their `Type`:

- **Free**
- **Paid**

A bar chart was created to compare the number of free and paid applications.

This provides insight into the dominant pricing model on the Google Play Store.

### 17. Paid App Price Distribution

The prices of paid applications were analysed using a distribution plot.

This helps understand the range and concentration of prices among paid apps.

## 💵 Revenue Estimation

### 18. Estimated Revenue

Estimated revenue was calculated for paid applications using:

```text
Estimated Revenue = Price × Number of Installs
```

The cleaned installation values and numerical prices were used for this calculation.

Revenue was then grouped by app category.

### 19. Top Categories by Estimated Revenue

The analysis identified the categories with the highest estimated revenue.

The top categories included:

- **FAMILY**
- **LIFESTYLE**
- **GAME**
- **FINANCE**
- **PHOTOGRAPHY**
- **PERSONALIZATION**
- **MEDICAL**
- **TOOLS**
- **SPORTS**
- **PRODUCTIVITY**

The **FAMILY** category had the highest estimated revenue among the categories shown in the analysis.

> Note: This is an estimated value based on listed price multiplied by listed install count. It should not be interpreted as actual reported company revenue.

## 💬 Sentiment Analysis

### 20. Review Data Preparation

For sentiment analysis, rows without review text were removed.

This resulted in **29,692 review records** available for analysis.

### 21. TextBlob Sentiment Analysis

TextBlob was used to analyse the sentiment of user reviews.

The sentiment categories are:

- **Positive**
- **Neutral**
- **Negative**

Sentiment polarity and subjectivity were also considered in the review dataset.

### 22. Sentiment Distribution

A visualization was created to show the overall distribution of user review sentiments.

The analysis indicates that user reviews are predominantly **positive**.

### 23. Sentiment by App Category

Sentiment was grouped by app category to understand how user opinions vary across different areas of the Play Store.

An interactive Plotly visualization was also created to compare:

- Positive sentiment
- Neutral sentiment
- Negative sentiment

across app categories.

Categories such as **GAME** and **SOCIAL** show comparatively higher negative sentiment and can therefore provide useful areas for identifying user pain points.

## 📊 Interactive Visualization

An interactive Plotly bar chart was created for sentiment analysis by app category.

The chart allows comparison of positive, neutral, and negative sentiment percentages across the top app categories.

## 💡 Key Findings

- The initial Apps dataset contains **10,841 records and 13 columns**.
- The initial User Reviews dataset contains **64,295 records and 5 columns**.
- The Apps dataset contained **483 duplicate rows**.
- The Reviews dataset contained **33,616 duplicate rows**.
- There were **698 duplicate app names** in the Apps dataset.
- After cleaning, the Apps dataset contains **9,660 unique apps**.
- After cleaning, the Reviews dataset contains **29,692 review records**.
- Missing values were handled successfully.
- The FAMILY category has the highest number of apps.
- GAME and TOOLS are also highly represented categories.
- App ratings are generally concentrated around **4.0–4.5**.
- Installation values were converted into numerical values for analysis.
- App sizes were converted into MB.
- Free applications dominate the Google Play Store compared with paid applications.
- Estimated revenue was calculated for paid applications using price and installation counts.
- FAMILY had the highest estimated revenue among the categories shown.
- User reviews are predominantly positive.
- Sentiment analysis was performed using TextBlob.
- Interactive sentiment analysis was created using Plotly.

## 🎯 Data-Driven Recommendations for a New App

Based on the analysis:

### 1. Focus on High-Demand Categories

FAMILY, GAME, and TOOLS are among the most represented categories.

A new app should study these high-demand areas while identifying a specific underserved niche.

### 2. Prioritize User Experience

Most app ratings are concentrated around 4.0–4.5.

Maintaining a strong rating requires good app quality, reliability, and user satisfaction.

### 3. Use User Sentiment

User reviews provide valuable feedback about what users like and dislike.

A new app should continuously analyse user feedback and address common complaints to improve user satisfaction, retention, and reputation.

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone <your-github-repository-link>
cd DataAnalytics-L2-T4-GooglePlayStore
```

### 2. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn textblob plotly jupyter
```

### 3. Open Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
notebook/Level2_Task4_Google_Play_Store.ipynb
```

Make sure the datasets are available at:

```text
dataset/googleplaystore.csv
dataset/googleplaystore_user_reviews.csv
```

Then run the notebook cells from top to bottom.

## 📄 Project Report

The detailed project report can be placed inside:

```text
report/
```

Example:

```text
OASIS_Level2_Task4_Google_Play_Store_Report.pdf
```

## 🎥 Demo Video

The project demonstration video is available here:

https://drive.google.com/file/d/1n5C_I7NBR8rxFxJxvU3hLuoAokvPzqDk/view?usp=sharing


The demo explains:

- Dataset loading
- Data cleaning
- Missing values
- Duplicate removal
- Category analysis
- Rating analysis
- Installation analysis
- Free vs paid analysis
- Revenue estimation
- Sentiment analysis
- Interactive visualization
- Final recommendations

## 📸 Screenshots

The `screenshots/` folder contains visual evidence of the major stages of the project, including data cleaning, category analysis, ratings, app size, installations, pricing, revenue, sentiment distribution, and sentiment by category.

## 🧠 Learning Outcomes

This project provided practical experience in:

- Data loading
- Data cleaning
- Missing-value handling
- Duplicate detection
- Duplicate removal
- Data transformation
- Exploratory Data Analysis
- Category analysis
- Rating analysis
- Installation analysis
- Revenue estimation
- Sentiment analysis
- TextBlob
- Matplotlib
- Seaborn
- Plotly
- Interactive visualization
- Data-driven recommendations

## 🏁 Conclusion

This project demonstrates an end-to-end **Google Play Store data analytics workflow**.

The Apps and User Reviews datasets were inspected and cleaned by handling missing values, removing duplicates, transforming numerical columns, and preparing the data for analysis.

The project explored app categories, ratings, installations, app sizes, pricing models, estimated revenue, and user sentiment.

The analysis showed that **FAMILY, GAME, and TOOLS** are among the most represented categories, app ratings are generally concentrated around **4.0–4.5**, and user reviews are predominantly positive.

Revenue estimation showed that the **FAMILY** category had the highest estimated revenue among the categories analysed. Sentiment analysis also provided useful insights into how user opinions vary across app categories.

Overall, the project demonstrates how data analytics can be used to understand the Google Play Store ecosystem and support **data-driven decisions for developing a new app**.

## 👩‍💻 Author

**Sai Sprisha**

Track: Data Analytics  
Level: Level 2  
Task: Task 4 — Google Play Store Analysis  
Internship: Oasis Infobyte
