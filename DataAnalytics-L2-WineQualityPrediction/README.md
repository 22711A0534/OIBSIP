# Data Analytics L2-T2 — Wine Quality Prediction

## 📌 Overview

This project focuses on predicting **wine quality using Machine Learning classification techniques**.

The project uses the **Wine Quality – Red Wine dataset** and converts the original wine quality score into two classes: **Not Good** and **Good**. Three classification algorithms are trained and compared to identify the model with the best test accuracy.

The complete workflow includes data loading, dataset inspection, descriptive statistics, missing-value analysis, quality distribution analysis, correlation analysis, target transformation, preprocessing, train-test splitting, feature scaling, model training, evaluation, confusion matrices, feature importance, and model comparison.

## 🎯 Objective

The main objectives of this project are to:

- Load and understand the Wine Quality dataset.
- Perform exploratory data analysis.
- Check for missing values.
- Analyse the distribution of wine quality scores.
- Study relationships between physicochemical properties.
- Convert wine quality scores into binary classes.
- Prepare the data for machine learning.
- Split the dataset into training and testing sets.
- Train multiple classification models.
- Evaluate model performance using accuracy, precision, recall, and F1-score.
- Analyse confusion matrices.
- Identify important chemical features using Random Forest.
- Compare the classification models.
- Select the best-performing model based on test accuracy.

## 📊 Dataset

**Dataset:** Wine Quality – Red Wine

**Dataset file:** `winequality-red.csv`

**Target variable:** `quality`

The dataset contains physicochemical measurements of red wines along with their original quality score.

### Dataset Details

- **Records:** 1,599
- **Columns:** 12
- **Input features:** 11
- **Target:** `quality`
- **Missing values:** 0

The 11 physicochemical features are:

- fixed acidity
- volatile acidity
- citric acid
- residual sugar
- chlorides
- free sulfur dioxide
- total sulfur dioxide
- density
- pH
- sulphates
- alcohol

The original `quality` score is converted into a binary classification target called `quality_label`.

## 🛠️ Technologies Used

- **Python**
- **Pandas** – Data manipulation and analysis
- **NumPy** – Numerical operations
- **Matplotlib** – Data visualization
- **Seaborn** – Statistical visualization
- **Scikit-learn** – Machine learning and evaluation
- **Jupyter Notebook** – Development environment

## 📂 Project Structure

```text
DataAnalytics-L2-T2-WineQuality/
│
├── dataset/
│   └── winequality-red.csv
│
├── notebook/
│   └── Level2_Task2_Wine_Quality.ipynb
│
├── report/
│   └── OASIS_Level2_Task2_Wine_Quality_Report.pdf
│
├── screenshots/
│   ├── 01_Dataset_Loading.png
│   ├── 02_Dataset_Head.png
│   ├── 03_Dataset_Info.png
│   ├── 04_Descriptive_Statistics.png
│   ├── 05_Missing_Values.png
│   ├── 06_Quality_Distribution.png
│   ├── 07_Feature_Distributions.png
│   ├── 08_Correlation_Heatmap.png
│   ├── 09_Binary_Quality_Classes.png
│   ├── 10_Class_Distribution.png
│   ├── 11_Train_Test_Split.png
│   ├── 12_Feature_Scaling.png
│   ├── 13_Random_Forest.png
│   ├── 14_Random_Forest_Classification_Report.png
│   ├── 15_Random_Forest_Confusion_Matrix.png
│   ├── 16_SGD_Classifier.png
│   ├── 17_SGD_Classification_Report.png
│   ├── 18_SGD_Confusion_Matrix.png
│   ├── 19_SVC.png
│   ├── 20_SVC_Classification_Report.png
│   ├── 21_SVC_Confusion_Matrix.png
│   ├── 22_Model_Comparison.png
│   ├── 23_Model_Accuracy_Chart.png
│   ├── 24_Feature_Importance.png
│   └── 25_Final_Findings.png
│
├── demovideo/
│
└── README.md
```

> Rename the screenshot/report files in this structure if your actual filenames are different.

## 🔍 Project Workflow

### 1. Dataset Loading

The dataset was loaded using Pandas:

```python
df = pd.read_csv("../dataset/winequality-red.csv", sep=";")
```

The dataset contains **1,599 rows and 12 columns**.

The first five records were displayed to understand the structure and available wine characteristics.

### 2. Dataset Inspection

The dataset structure was inspected using `df.info()`.

The dataset contains:

- **11 floating-point physicochemical features**
- **1 integer quality column**
- **1,599 observations**
- **No missing values**

### 3. Descriptive Statistics

Descriptive statistics were generated to understand:

- Mean
- Standard deviation
- Minimum value
- Quartiles
- Maximum value

This provides an overview of the numerical distribution of the wine characteristics.

### 4. Missing-Value Analysis

Missing values were checked for every column.

The analysis found:

**Total missing values: 0**

Therefore, no missing-value imputation was required for the original dataset.

### 5. Wine Quality Distribution

The distribution of the original wine quality scores was analysed.

The quality scores were mainly concentrated around **5 and 6**, showing that medium-quality wines make up a large portion of the dataset.

A count plot was used to visually display the number of wines for each quality score.

### 6. Feature Distribution Analysis

Histograms with KDE curves were created for the physicochemical features.

These graphs help understand the distribution and spread of variables such as:

- Alcohol
- pH
- Density
- Sulphates
- Volatile acidity
- Citric acid
- Residual sugar

### 7. Correlation Analysis

A correlation heatmap was created to understand relationships between the physicochemical features and wine quality.

The analysis showed that:

- **Alcohol** had the strongest positive correlation with wine quality.
- **Volatile acidity** had the strongest negative correlation with wine quality.

The heatmap also helps identify relationships between the different chemical properties.

## 🎯 Target Transformation

### Binary Quality Classification

The original wine quality score was converted into a binary classification target:

```python
df["quality_label"] = (df["quality"] >= 6).astype(int)
```

The classes are defined as:

| Quality Label | Meaning |
|---:|---|
| 0 | Not Good — Quality < 6 |
| 1 | Good — Quality ≥ 6 |

This transformation converts the original multi-level quality score into a simple binary classification problem.

## ⚙️ Data Preparation

The original `quality` and newly created `quality_label` columns were separated from the input features.

The final feature matrix contains:

- **1,599 samples**
- **11 input features**

The target variable contains the binary `quality_label`.

## ✂️ Train-Test Split

The dataset was divided into:

- **80% Training Data:** 1,279 samples
- **20% Testing Data:** 320 samples
- **Random State:** 42
- **Stratified Sampling:** Yes

Stratification was used to maintain a similar class distribution in both training and testing datasets.

## 📏 Feature Scaling

Feature scaling was performed using:

```python
StandardScaler()
```

The scaled features were used for:

- SGD Classifier
- Support Vector Classifier

Random Forest was trained using the original feature values because tree-based models do not require standardization in the same way.

## 🤖 Machine Learning Models

Three classification algorithms were implemented.

### 1. Random Forest Classifier

Random Forest was trained using:

```python
RandomForestClassifier(
    n_estimators=200,
    random_state=42
)
```

**Test Accuracy: 81.56%**

Random Forest combines multiple decision trees and uses their combined predictions for classification.

### 2. SGD Classifier

A Stochastic Gradient Descent classifier was trained using the scaled features.

**Test Accuracy: 65.62%**

SGD provides a linear classification approach and was included to compare its performance with the other models.

### 3. Support Vector Classifier

An SVC model using an RBF kernel was trained on the scaled data.

```python
SVC(
    kernel="rbf",
    random_state=42
)
```

**Test Accuracy: 76.25%**

SVC attempts to find a decision boundary that separates the two wine-quality classes.

## 📈 Model Evaluation

The models were evaluated using:

- **Accuracy**
- **Precision**
- **Recall**
- **F1-score**
- **Confusion Matrix**

### Model Comparison

| Model | Accuracy |
|---|---:|
| **Random Forest** | **81.56%** |
| SVC | 76.25% |
| SGD Classifier | 65.62% |

### 🏆 Best Performing Model

**Random Forest Classifier** achieved the highest test accuracy among the three models.

**Accuracy: 81.56%**

Therefore, Random Forest was the best-performing model for this classification task based on test accuracy.

## 📋 Classification Report Summary

### Random Forest

| Class | Precision | Recall | F1-score |
|---|---:|---:|---:|
| Not Good | 0.79 | 0.82 | 0.81 |
| Good | 0.84 | 0.81 | 0.82 |

**Overall Accuracy: 0.82**

### SGD Classifier

| Class | Precision | Recall | F1-score |
|---|---:|---:|---:|
| Not Good | 0.65 | 0.56 | 0.60 |
| Good | 0.66 | 0.74 | 0.70 |

**Overall Accuracy: 0.66**

### SVC

| Class | Precision | Recall | F1-score |
|---|---:|---:|---:|
| Not Good | 0.72 | 0.81 | 0.76 |
| Good | 0.81 | 0.72 | 0.76 |

**Overall Accuracy: 0.76**

## 📊 Graphs and Figures

### 1. Wine Quality Distribution

The quality distribution graph shows the number of wines for each original quality score.

It shows that the dataset is mainly concentrated around quality scores **5 and 6**.

### 2. Feature Distribution Graphs

The individual distribution plots show how each chemical feature is distributed across the wine samples.

These plots help identify the range and general pattern of each physicochemical property.

### 3. Correlation Heatmap

The correlation heatmap shows the strength and direction of relationships between the chemical properties and wine quality.

The important observations are:

- Alcohol has the strongest positive relationship with quality.
- Volatile acidity has the strongest negative relationship with quality.

### 4. Binary Class Distribution

After converting the quality score into two classes, the class distribution graph shows the number of:

- **Not Good wines**
- **Good wines**

This helps understand the balance between the two classification classes.

### 5. Random Forest Confusion Matrix

The Random Forest confusion matrix shows the number of correctly and incorrectly classified wines for both classes.

It helps understand how well the model distinguishes between **Not Good** and **Good** wines.

### 6. SGD Confusion Matrix

The SGD confusion matrix shows the classification errors made by the SGD model.

Compared with Random Forest, SGD produces more classification errors and therefore has lower accuracy.

### 7. SVC Confusion Matrix

The SVC confusion matrix shows the classification performance of the Support Vector Classifier for both wine-quality classes.

### 8. Model Comparison Chart

The model comparison bar chart displays the test accuracy of all three classifiers.

The chart clearly shows that:

**Random Forest > SVC > SGD Classifier**

in terms of test accuracy.

### 9. Random Forest Feature Importance

The Random Forest feature-importance plot shows which physicochemical properties contributed most to the classification decisions.

This provides an interpretable view of which chemical features are more useful for predicting whether a wine belongs to the Good or Not Good class.

## 💡 Key Findings

- The dataset contains **1,599 red-wine samples and 12 columns**.
- There are **11 physicochemical input features**.
- The dataset contains **no missing values**.
- Wine quality scores are mainly concentrated around **5 and 6**.
- The original quality score was converted into a binary classification problem.
- Quality scores below 6 were classified as **Not Good**.
- Quality scores of 6 or above were classified as **Good**.
- The data was split into **80% training and 20% testing data**.
- StandardScaler was used for SGD and SVC.
- Random Forest achieved the highest accuracy of **81.56%**.
- SVC achieved an accuracy of **76.25%**.
- SGD Classifier achieved an accuracy of **65.62%**.
- Alcohol showed the strongest positive correlation with wine quality.
- Volatile acidity showed the strongest negative correlation with wine quality.
- Random Forest feature importance was used to understand the contribution of chemical properties.

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone <your-github-repository-link>
cd DataAnalytics-L2-T2-WineQuality
```

### 2. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3. Open Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
notebook/Level2_Task2_Wine_Quality.ipynb
```

Make sure the dataset is available at:

```text
dataset/winequality-red.csv
```

Then run the notebook cells from top to bottom.

## 📄 Project Report

The detailed project report can be placed inside:

```text
report/
```

Example:

```text
OASIS_Level2_Task2_Wine_Quality_Report.pdf
```

## 🎥 Demo Video

https://drive.google.com/file/d/1W2YVM478N11TrqhwUNvstDG3V0eo9xK8/view?usp=sharing



A demo video should briefly explain:

- Dataset
- Exploratory analysis
- Correlation heatmap
- Binary classification
- Data preprocessing
- Machine learning models
- Confusion matrices
- Model comparison
- Feature importance
- Final result

## 📸 Screenshots

The `screenshots/` folder contains visual evidence of the important stages of the project, including dataset inspection, EDA, preprocessing, model training, evaluation, confusion matrices, model comparison, and feature importance.

## 🧠 Learning Outcomes

This project provided practical experience in:

- Exploratory Data Analysis
- Data inspection
- Missing-value analysis
- Descriptive statistics
- Feature distribution analysis
- Correlation analysis
- Target transformation
- Binary classification
- Train-test splitting
- Stratified sampling
- Feature scaling
- Random Forest
- SGD Classifier
- Support Vector Classifier
- Classification metrics
- Confusion matrix analysis
- Feature importance
- Model comparison
- Data visualization

## 🏁 Conclusion

This project successfully developed and evaluated machine learning classification models for predicting wine quality based on physicochemical properties.

The original wine quality score was converted into two classes: **Not Good** and **Good**. Three classification models—**Random Forest, SGD Classifier, and SVC**—were trained and evaluated.

Among the three models, **Random Forest achieved the highest test accuracy of 81.56%**, followed by SVC at 76.25% and SGD Classifier at 65.62%.

The analysis also showed that **alcohol** had the strongest positive correlation with wine quality, while **volatile acidity** had the strongest negative correlation.

Overall, the project demonstrates the importance of data exploration, preprocessing, classification algorithms, evaluation metrics, visualization, and model comparison in solving a real-world wine quality prediction problem.

## 👩‍💻 Author

**Sai Sprisha**

Track: Data Analytics  
Level: Level 2  
Task: Task 2 — Wine Quality Prediction  
Internship: Oasis Infobyte
