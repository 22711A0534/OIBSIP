
# Data Analytics L2-T3 — Fraud Detection

## 📌 Overview

This project focuses on detecting **fraudulent financial transactions using Machine Learning classification techniques**.

The project uses a highly imbalanced **Credit Card Fraud Detection** dataset. The workflow includes data loading, dataset inspection, descriptive statistics, missing-value analysis, class-distribution analysis, transaction analysis, feature preparation, stratified train-test splitting, feature scaling, SMOTE oversampling, model training, evaluation, confusion matrices, ROC curve comparison, and feature-importance analysis.

Two classification models are implemented and compared:

- Logistic Regression
- Random Forest Classifier

## 🎯 Objective

The main objectives of this project are to:

- Load and understand the credit card transaction dataset.
- Perform exploratory data analysis.
- Check for missing values.
- Analyse the highly imbalanced fraud and non-fraud classes.
- Study transaction amount and time-based patterns.
- Prepare the features and target variable.
- Split the data using stratified sampling.
- Standardize the input features.
- Handle class imbalance using SMOTE.
- Train Logistic Regression and Random Forest models.
- Evaluate the models using Accuracy, Precision, Recall, F1-Score, and ROC-AUC.
- Analyse confusion matrices.
- Compare model performance using a results table and ROC curve.
- Identify important features using Random Forest feature importance.
- Select the model that provides the best balance for fraud detection.

## 📊 Dataset

**Dataset:** Credit Card Fraud Detection Dataset

**Dataset file:** `creditcard.csv`

**Target variable:** `Class`

The target variable is binary:

| Class | Meaning |
|---:|---|
| 0 | Non-Fraudulent Transaction |
| 1 | Fraudulent Transaction |

### Dataset Details

- **Total transactions:** 284,807
- **Total columns:** 31
- **Input features used:** 30
- **Fraudulent transactions:** 492
- **Non-fraudulent transactions:** 284,315
- **Fraud percentage:** 0.1727%
- **Non-fraud percentage:** 99.8273%
- **Missing values:** 0

The dataset contains transaction time, transaction amount, anonymized features `V1` to `V28`, and the target `Class`.

## 🛠️ Technologies Used

- **Python**
- **Pandas** – Data manipulation and analysis
- **NumPy** – Numerical operations
- **Matplotlib** – Data visualization
- **Seaborn** – Statistical visualization
- **Scikit-learn** – Machine learning and evaluation
- **Imbalanced-learn** – SMOTE for handling class imbalance
- **Jupyter Notebook** – Development environment

## 📂 Project Structure

```text
DataAnalytics-L2-T3-FraudDetection/
│
├── dataset/
│   └── creditcard.csv
│
├── notebook/
│   └── Fraud_Detection.ipynb
│
├── report/
│   └── OASIS_Level2_Task3_Fraud_Detection_Report.pdf
│
├── screenshots/
│   ├── 01_Dataset_Loading.png
│   ├── 02_Dataset_Head.png
│   ├── 03_Dataset_Info.png
│   ├── 04_Descriptive_Statistics.png
│   ├── 05_Missing_Values.png
│   ├── 06_Class_Distribution.png
│   ├── 07_Transaction_Amount_Distribution.png
│   ├── 08_Transaction_Amount_Boxplot.png
│   ├── 09_Fraud_By_Hour.png
│   ├── 10_Transaction_Distribution_By_Hour.png
│   ├── 11_Train_Test_Split.png
│   ├── 12_Feature_Scaling.png
│   ├── 13_SMOTE.png
│   ├── 14_Class_Distribution_After_SMOTE.png
│   ├── 15_Logistic_Regression.png
│   ├── 16_Random_Forest.png
│   ├── 17_Logistic_Regression_Evaluation.png
│   ├── 18_Random_Forest_Evaluation.png
│   ├── 19_Random_Forest_Confusion_Matrix.png
│   ├── 20_Logistic_Regression_Confusion_Matrix.png
│   ├── 21_Model_Comparison.png
│   ├── 22_ROC_Curve_Comparison.png
│   ├── 23_Feature_Importance.png
│   └── 24_Final_Findings.png
│
├── demovideo/
│
└── README.md
```

> Rename the notebook, report, or screenshot filenames above if your actual project uses different names.

## 🔍 Project Workflow

### 1. Dataset Loading

The dataset was loaded using Pandas:

```python
df = pd.read_csv("../dataset/creditcard.csv")
```

The dataset contains **284,807 transactions and 31 columns**.

The first few records were displayed to understand the transaction data.

### 2. Dataset Inspection

The dataset structure was examined using `df.info()`.

The dataset contains:

- 284,807 observations
- 31 columns
- 30 floating-point features
- 1 integer target column
- No missing values

The features include `Time`, `V1` through `V28`, `Amount`, and `Class`.

### 3. Descriptive Statistics

Descriptive statistics were generated to understand the numerical characteristics of the transaction data.

The analysis provides information such as:

- Mean
- Standard deviation
- Minimum
- Quartiles
- Maximum

### 4. Missing-Value Analysis

Missing values were checked for every column.

**Total missing values: 0**

Therefore, no missing-value imputation was required for this dataset.

## ⚠️ Class Imbalance Analysis

### 5. Fraud vs Non-Fraud Distribution

The dataset is highly imbalanced.

Out of 284,807 transactions:

- **284,315 are non-fraudulent**
- **492 are fraudulent**

This means fraudulent transactions represent only **0.1727%** of the dataset.

A class-distribution graph was created to clearly visualize this imbalance.

### Why Accuracy Alone Is Misleading

For this dataset, accuracy alone is not a suitable metric.

A model that predicts almost every transaction as non-fraudulent could achieve very high accuracy while failing to detect actual fraud.

Therefore, this project focuses especially on:

- **Precision**
- **Recall**
- **F1-Score**
- **ROC-AUC**

Recall is particularly important because missing a fraudulent transaction can result in financial loss.

## 💰 Transaction Analysis

### 6. Transaction Amount Distribution

The transaction amount distribution was analysed separately for fraud and non-fraud transactions.

This visualization helps understand whether transaction amounts show different patterns between fraudulent and legitimate transactions.

### 7. Transaction Amount Boxplot

A boxplot was created to compare transaction amounts across the two classes.

This helps identify differences in the spread and extreme values of transaction amounts.

## 🕐 Time-Based Analysis

### 8. Hour of Day

The original transaction `Time` value was converted into an hour-of-day feature:

```python
df["Hour"] = (df["Time"] / 3600) % 24
df["Hour"] = df["Hour"].astype(int)
```

Fraud percentages were then calculated for each hour.

Two visualizations were created:

- Fraud percentage by hour of day
- Transaction distribution by hour

These graphs help explore whether fraudulent activity varies across different times of the day.

The temporary `Hour` feature was not used as a model input.

## ⚙️ Data Preparation

### 9. Feature and Target Separation

The target variable `Class` was separated from the input features.

The model features were created using:

```python
X = df.drop(columns=["Class", "Hour"])
y = df["Class"]
```

This resulted in **30 model input features**.

### 10. Stratified Train-Test Split

The data was divided into:

- **80% Training Data:** 227,845 transactions
- **20% Testing Data:** 56,962 transactions
- **Random State:** 42
- **Stratified Sampling:** Yes

The stratified split maintains the fraud/non-fraud class proportions in both the training and testing datasets.

### 11. Feature Scaling

Feature scaling was performed using:

```python
StandardScaler()
```

The scaler was fitted only on the training data and then applied to both training and testing data.

This prevents information from the test set from being used during training.

## ⚖️ Handling Class Imbalance with SMOTE

### 12. SMOTE

Because the training data was extremely imbalanced, **SMOTE (Synthetic Minority Over-sampling Technique)** was applied to the training data only.

Before SMOTE:

- Non-Fraud: 227,451
- Fraud: 394

After SMOTE:

- Non-Fraud: 227,451
- Fraud: 227,451

SMOTE creates synthetic minority-class samples to balance the training data.

The test data was kept unchanged so that model evaluation represents the original class distribution.

## 🤖 Machine Learning Models

Two classification algorithms were implemented.

### 1. Logistic Regression

Logistic Regression was trained on the SMOTE-balanced training data.

```python
LogisticRegression(
    max_iter=1000,
    random_state=42
)
```

### 2. Random Forest Classifier

Random Forest was trained using:

```python
RandomForestClassifier(
    n_estimators=50,
    max_depth=15,
    random_state=42,
    n_jobs=-1
)
```

Random Forest combines multiple decision trees to make classification predictions.

## 📈 Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
- Classification Report
- Confusion Matrix

### Model Comparison

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 97.41% | 5.78% | **91.84%** | 10.88% | 0.9708 |
| **Random Forest** | **99.88%** | **62.12%** | 83.67% | **71.30%** | **0.9729** |

## 🏆 Best Performing Model

Based on the overall balance between precision, recall, F1-score, and ROC-AUC, **Random Forest** performed better for this project.

### Random Forest Results

- **Accuracy:** 99.88%
- **Precision:** 62.12%
- **Recall:** 83.67%
- **F1-Score:** 71.30%
- **ROC-AUC:** 0.9729

Although Logistic Regression achieved a higher recall of **91.84%**, its precision was only **5.78%**, meaning that it produced many false positive fraud alerts.

Random Forest achieved a much better precision of **62.12%** while still detecting **83.67%** of the actual fraudulent transactions.

Therefore, Random Forest provides a better balance between detecting fraud and reducing false alarms for this project.

## 📊 Graphs and Figures

### 1. Class Distribution

The class-distribution graph clearly shows the extreme imbalance between legitimate and fraudulent transactions.

### 2. Transaction Amount Distribution

This graph compares the distribution of transaction amounts for fraudulent and non-fraudulent transactions.

### 3. Transaction Amount Boxplot

The boxplot provides a visual comparison of transaction amounts and helps identify differences and extreme values between the two classes.

### 4. Fraud Percentage by Hour

This graph shows the percentage of fraudulent transactions for each hour of the day and helps identify possible time-based patterns.

### 5. Transaction Distribution by Hour

This graph compares the number of fraudulent and non-fraudulent transactions across different hours.

### 6. SMOTE Class Distribution

The SMOTE graph shows how the minority fraud class was balanced with the majority class in the training data.

### 7. Confusion Matrices

The confusion matrices show:

- True Negatives
- False Positives
- False Negatives
- True Positives

They help evaluate how effectively each model distinguishes fraudulent transactions from legitimate transactions.

### 8. Model Comparison

The model comparison table and visualization show the performance of Logistic Regression and Random Forest across multiple evaluation metrics.

### 9. ROC Curve Comparison

The ROC curve compares the ability of both models to distinguish between fraud and non-fraud transactions.

The Random Forest model achieved a slightly higher ROC-AUC of **0.9729**, compared with **0.9708** for Logistic Regression.

### 10. Feature Importance

The Random Forest feature-importance analysis identifies the features that contributed most to fraud classification.

The top features include:

| Feature | Importance |
|---|---:|
| V14 | 0.289198 |
| V10 | 0.100619 |
| V4 | 0.094927 |
| V17 | 0.086248 |
| V3 | 0.077684 |
| V12 | 0.069758 |
| V16 | 0.051961 |

`V14` was the most important feature in the Random Forest model.

## 💡 Key Findings

- The dataset contains **284,807 transactions**.
- Only **492 transactions are fraudulent**.
- Fraudulent transactions represent just **0.1727%** of all transactions.
- The dataset contains **no missing values**.
- Accuracy alone is not sufficient for evaluating fraud detection models.
- SMOTE was applied only to the training data to address class imbalance.
- Logistic Regression achieved a recall of **91.84%**, which means it detected a high proportion of actual fraud cases.
- Logistic Regression had very low precision of **5.78%**, resulting in many false-positive alerts.
- Random Forest achieved **99.88% accuracy**.
- Random Forest achieved **62.12% precision**, **83.67% recall**, and **71.30% F1-score**.
- Random Forest achieved the highest ROC-AUC of **0.9729**.
- `V14` was the most important feature according to Random Forest feature importance.
- Random Forest provided a better overall balance between fraud detection and false alarms.

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone <your-github-repository-link>
cd DataAnalytics-L2-T3-FraudDetection
```

### 2. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn jupyter
```

### 3. Open Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
notebook/Fraud_Detection.ipynb
```

Make sure the dataset is available at:

```text
dataset/creditcard.csv
```

Then run the notebook cells from top to bottom.

## 📄 Project Report

The detailed project report can be placed inside:

```text
report/
```

Example:

```text
OASIS_Level2_Task3_Fraud_Detection_Report.pdf
```

## 🎥 Demo Video

The project demonstration video is available here:

https://drive.google.com/file/d/13N7w8VyLXEypeuoh0HA55babnl2LJOza/view?usp=sharing

The demo explains:

- Dataset
- Class imbalance
- Transaction analysis
- Time-based analysis
- SMOTE
- Machine learning models
- Evaluation metrics
- Confusion matrices
- ROC curve
- Feature importance
- Final model comparison

## 📸 Screenshots

The `screenshots/` folder contains visual evidence of the important stages of the project, including dataset inspection, class imbalance, transaction analysis, SMOTE, model training, evaluation, confusion matrices, ROC curve, model comparison, and feature importance.

## 📈 Scalability Consideration

A fraud detection system processing **1 million transactions per hour** would need to handle approximately **278 transactions per second**.

For such a workload, the trained model could be deployed as a real-time prediction service using streaming or batch-processing infrastructure. Prediction services could be scaled horizontally as transaction volume increases.

The system should monitor:

- Prediction latency
- Throughput
- False positives
- False negatives
- Fraud detection performance

Suspicious transactions could be sent for additional investigation, while prediction results could be stored for auditing and analysis. Periodic model retraining would also be useful because fraud patterns can change over time.

## 🧠 Learning Outcomes

This project provided practical experience in:

- Exploratory Data Analysis
- Fraud detection
- Imbalanced datasets
- Missing-value analysis
- Data preprocessing
- Feature scaling
- Stratified train-test splitting
- SMOTE
- Logistic Regression
- Random Forest
- Classification metrics
- Confusion matrix analysis
- ROC-AUC
- ROC curve visualization
- Feature importance
- Model comparison
- Fraud detection interpretation

## 🏁 Conclusion

This project demonstrates an end-to-end machine learning approach for **fraudulent transaction detection**.

The dataset was highly imbalanced, with fraudulent transactions representing only **0.1727%** of all transactions. To address this challenge, the project used stratified sampling, feature scaling, and SMOTE on the training data.

Two classification models—**Logistic Regression and Random Forest**—were trained and evaluated using multiple metrics.

Logistic Regression achieved a higher recall of **91.84%**, but its precision was only **5.78%**. Random Forest achieved a strong balance with **62.12% precision, 83.67% recall, 71.30% F1-score, and 0.9729 ROC-AUC**.

Therefore, **Random Forest was selected as the better overall model for this project**, particularly because it provides a better balance between detecting fraudulent transactions and limiting false-positive alerts.

## 👩‍💻 Author

**Sai Sprisha**

Track: Data Analytics  
Level: Level 2  
Task: Task 3 — Fraud Detection  
Internship: Oasis Infobyte
