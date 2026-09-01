# Data Analytics L2-T1 — House Price Prediction

## 📌 Overview

This project focuses on predicting house prices using **Machine Learning and Regression techniques**. The project uses the Kaggle **House Prices – Advanced Regression Techniques** dataset and builds regression models to predict the `SalePrice` of houses based on their property characteristics.

The workflow includes data loading, exploratory data analysis, missing-value analysis, feature selection, preprocessing, model training, evaluation, visualization, residual analysis, and comparison of Linear Regression, Ridge Regression, and Lasso Regression models.

## 🎯 Objective

The main objectives of this project are to:

- Load and inspect the house price dataset.
- Analyse the structure and characteristics of the dataset.
- Identify and analyse missing values.
- Generate descriptive statistics.
- Analyse the distribution of house sale prices.
- Identify features correlated with `SalePrice`.
- Select relevant features for prediction.
- Handle missing numerical and categorical values.
- Convert categorical features using One-Hot Encoding.
- Split the dataset into training and testing sets.
- Build a Linear Regression model.
- Build Ridge and Lasso Regression models for comparison.
- Evaluate model performance using MSE, RMSE, and R² Score.
- Analyse actual vs predicted prices.
- Perform residual analysis.
- Compare the performance of different regression models.
- Identify the best-performing model.

## 🛠️ Technologies Used

- Python 3.13.7
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## 📂 Project Structure

```text
DataAnalytics-L2-T1/
│
├── dataset/
│   └── train.csv
│
├── notebook/
│   └── Level2_Task1_House_Price.ipynb
│
├── report/
│   └── OASIS_Level2_Task1_House_Price_Report.pdf
│
├── screenshots/
│   ├── 01_Dataset_Loading.png
│   ├── 02_Dataset_Head.png
│   ├── 03_Dataset_Info.png
│   ├── 04_Missing_Values.png
│   ├── 05_Descriptive_Statistics.png
│   ├── 06_SalePrice_Distribution.png
│   ├── 07_Correlation_Analysis.png
│   ├── 08_Feature_Selection.png
│   ├── 09_Preprocessing.png
│   ├── 10_Train_Test_Split.png
│   ├── 11_Linear_Regression.png
│   ├── 12_Model_Evaluation.png
│   ├── 13_Actual_vs_Predicted.png
│   ├── 14_Residual_Analysis.png
│   ├── 15_Feature_Impact.png
│   └── 16_Model_Comparison.png
│
└── README.md
```

## 📊 Analysis Workflow

### 1. Dataset Loading

The House Prices dataset was loaded using Pandas from:

```text
../dataset/train.csv
```

The dataset contains **1,460 records and 81 columns**. The target variable used for prediction is `SalePrice`. fileciteturn5file0L64-L85

### 2. Dataset Inspection

The first five rows were displayed to understand the available property-related features.

The dataset contains numerical and categorical variables such as:

- `OverallQual`
- `OverallCond`
- `YearBuilt`
- `YearRemodAdd`
- `GrLivArea`
- `GarageCars`
- `GarageArea`
- `TotalBsmtSF`
- `Neighborhood`
- `SaleCondition`
- `SalePrice`

The notebook reports **36 numerical features and 43 categorical features**, with 79 input features before encoding after excluding `SalePrice` and `Id`. fileciteturn5file0L294-L338

### 3. Dataset Information

The dataset contains:

- **1,460 rows**
- **81 columns**
- **35 integer columns**
- **3 float columns**
- **43 object/categorical columns**

The `SalePrice` column contains the house sale price used as the prediction target. fileciteturn5file0L300-L397

### 4. Missing-Value Analysis

Missing values were identified across several property features.

Major missing-value columns include:

- `PoolQC`
- `MiscFeature`
- `Alley`
- `Fence`
- `MasVnrType`
- `FireplaceQu`
- `LotFrontage`
- Garage-related features
- Basement-related features
- `MasVnrArea`
- `Electrical`

The notebook identifies the missing-value counts for these columns before preprocessing. fileciteturn5file0L407-L545

### 5. Descriptive Statistics

Descriptive statistics were generated using:

```python
df.describe().T
```

This was used to understand the count, mean, standard deviation, minimum, quartiles, and maximum values of numerical variables.

For example, the dataset shows an average `SalePrice` of approximately **180,921.20**, with values ranging from **34,900 to 755,000**. fileciteturn2file0L23-L62

### 6. SalePrice Distribution

A histogram was created to analyse the distribution of house sale prices.

The visualization helps understand the spread of `SalePrice` values across the dataset.

### 7. Correlation Analysis

Correlation analysis was performed to identify numerical features that have strong relationships with `SalePrice`.

The strongest correlations identified were:

| Feature | Correlation |
|---|---:|
| OverallQual | 0.790982 |
| GrLivArea | 0.708624 |
| GarageCars | 0.640409 |
| GarageArea | 0.623431 |
| TotalBsmtSF | 0.613581 |
| 1stFlrSF | 0.605852 |
| FullBath | 0.560664 |
| TotRmsAbvGrd | 0.533723 |
| YearBuilt | 0.522897 |
| YearRemodAdd | 0.507101 |

`OverallQual` was the strongest numerical feature correlated with `SalePrice`, followed by `GrLivArea`. fileciteturn2file0L157-L265

### 8. Feature Selection

The correlation analysis showed that house quality, living area, garage capacity, basement area, number of rooms, and construction or renovation year can be useful for predicting house prices.

Categorical variables such as `Neighborhood` were also considered potentially important because location can influence property value.

The `Id` column was excluded because it is an identifier rather than a meaningful house characteristic. fileciteturn2file0L292-L307

### 9. Data Preprocessing

A Scikit-learn preprocessing pipeline was created using `ColumnTransformer` and `Pipeline`.

#### Numerical Features

Missing numerical values were handled using:

```text
Median Imputation
```

#### Categorical Features

Missing categorical values were handled using:

```text
Most-Frequent Imputation
```

Categorical features were then transformed using:

```text
One-Hot Encoding
```

The encoder was configured with:

```python
OneHotEncoder(handle_unknown="ignore")
```

This preprocessing pipeline was integrated directly with the regression models. fileciteturn2file0L327-L387

### 10. Train-Test Split

The dataset was divided into:

- **Training samples:** 1,168
- **Testing samples:** 292
- **Test size:** 20%
- **Random state:** 42

The split was performed using Scikit-learn's `train_test_split()`. fileciteturn2file0L391-L417

## 🤖 Machine Learning Models

Three regression models were implemented and compared:

### 1. Linear Regression

Linear Regression was used as the baseline model for house price prediction.

```python
LinearRegression()
```

The model was trained using the preprocessing pipeline and generated predictions for the test dataset. fileciteturn2file0L421-L451

### 2. Ridge Regression

Ridge Regression was implemented as a regularized regression model using:

```python
Ridge(alpha=10)
```

### 3. Lasso Regression

Lasso Regression was implemented using:

```python
Lasso(alpha=100, max_iter=50000)
```

Ridge and Lasso were included to compare regularized regression performance against the Linear Regression baseline. fileciteturn3file0L59-L101

## 📈 Model Evaluation

The models were evaluated using:

- **Mean Squared Error (MSE)**
- **Root Mean Squared Error (RMSE)**
- **R² Score**

### Model Comparison

| Model | MSE | RMSE | R² Score |
|---|---:|---:|---:|
| Linear Regression | 979,376,460.09 | 31,294.99 | 0.872316 |
| Ridge Regression | 1,194,765,000+ | 34,565.37 | 0.844235 |
| **Lasso Regression** | **801,128,000+** | **28,304.21** | **0.895555** |

The exact notebook output reports Lasso with the lowest RMSE and highest R² Score among the three evaluated models. fileciteturn3file0L23-L52

## 🏆 Best Performing Model

**Lasso Regression** achieved the best performance on the test dataset.

### Lasso Performance

- **RMSE:** 28,304.21
- **R² Score:** 0.895555

This means the Lasso model explained approximately **89.56% of the variation** in the test-set house prices.

## 📊 Visualizations

The project includes visual analysis for:

- Dataset loading
- Dataset structure
- Missing values
- Descriptive statistics
- SalePrice distribution
- Correlation analysis
- Feature selection
- Data preprocessing
- Train-test split
- Linear Regression
- Model evaluation
- Actual vs Predicted prices
- Residual analysis
- Feature impact
- Model comparison

### Actual vs Predicted Analysis

The Actual vs Predicted visualization was used to compare the actual house prices with the prices predicted by the regression model.

Predictions following the general diagonal trend indicate better agreement between actual and predicted values.

### Residual Analysis

Residual analysis was performed to examine prediction errors.

Most residuals were concentrated around zero, although larger errors were observed for some higher-priced houses. fileciteturn3file0L109-L129

## 📁 Project Results

The project demonstrates that:

- Linear Regression provides a strong baseline.
- Ridge Regression performed below the Linear Regression baseline on this test split.
- Lasso Regression achieved the best overall test performance.
- Feature preprocessing is important when working with mixed numerical and categorical house-price data.
- `OverallQual` and `GrLivArea` were the strongest numerical predictors identified through correlation analysis.

## ▶️ How to Run

1. Open the project folder in **VS Code** or **Jupyter Notebook**.
2. Open the `notebook/` folder.
3. Launch:

```text
Level2_Task1_House_Price.ipynb
```

4. Ensure the dataset is available at:

```text
dataset/train.csv
```

5. Install the required Python libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

6. Run the notebook cells from top to bottom.
7. Review the generated visualizations and model evaluation results.

## 📄 Project Report

The detailed project report can be placed inside the:

```text
report/
```

folder.

Example:

```text
OASIS_Level2_Task1_House_Price_Report.pdf
```

## 🎥 Demo Video

https://drive.google.com/file/d/13epWh-4uoPD2oVerOs3NMqU4k1vpeVKU/view?usp=sharing

## 📸 Screenshots

The `screenshots/` folder contains visual evidence of the major stages of the project, including:

- Dataset loading
- Dataset inspection
- Missing-value analysis
- Descriptive statistics
- SalePrice distribution
- Correlation analysis
- Feature selection
- Preprocessing
- Train-test split
- Model training
- Model evaluation
- Actual vs Predicted analysis
- Residual analysis
- Feature impact
- Model comparison

## 🧠 Learning Outcomes

This project provided practical experience in:

- Exploratory Data Analysis
- Data preprocessing
- Missing-value handling
- Feature selection
- Correlation analysis
- One-Hot Encoding
- Machine Learning pipelines
- Train-test splitting
- Linear Regression
- Ridge Regression
- Lasso Regression
- Regression model evaluation
- Residual analysis
- Data visualization
- Model comparison

## ✅ Conclusion

This project demonstrates an end-to-end machine learning workflow for **house price prediction**.

The House Prices dataset was loaded and analysed, missing values were handled using a preprocessing pipeline, categorical features were converted using One-Hot Encoding, and the data was divided into training and testing sets.

Linear Regression achieved an R² score of **0.8723**, while Ridge and Lasso Regression were evaluated as regularized alternatives. Among the three models, **Lasso Regression achieved the best performance**, with an R² score of **0.8956** and an RMSE of approximately **28,304.21**. fileciteturn3file0L109-L129

Overall, the project demonstrates the importance of data preprocessing, feature analysis, model evaluation, and model comparison in developing an effective house price prediction model.

## 👩‍💻 Author

**Sai Sprisha**

Track: Data Analytics  
Level: Level 2  
Task: Task 1 — House Price Prediction  
Internship: Oasis Infobyte
