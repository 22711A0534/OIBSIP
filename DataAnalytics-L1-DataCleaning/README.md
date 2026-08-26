Data Analytics L1-T3 — Data Cleaning

📌 Overview

This project focuses on cleaning and preparing a Titanic dataset for further analysis. The workflow identifies data quality issues, handles missing values, removes duplicate records, standardizes data, detects outliers, performs a final quality check, and saves the cleaned dataset.

🎯 Objective

The main objectives of this project are to:

Inspect the structure and quality of the Titanic dataset.

Identify missing values and data quality issues.

Generate a data quality report.

Handle missing values using appropriate cleaning methods.

Identify and remove duplicate records.

Standardize inconsistent data formats.

Detect numerical outliers using the IQR method.

Perform a final data quality check.

Save the cleaned dataset as a new CSV file.

🛠️ Technologies Used

Python

Pandas

NumPy

Matplotlib

Seaborn

Jupyter Notebook

📂 Project Structure

DataAnalytics-L1-DataCleaning/
├── dataset/
│   └── Titanic-Dataset.csv
├── notebook/
│   └── Level1_Task3_Data_Cleaning.ipynb
├── output/
│   └── Titanic_Cleaned.csv
├── report/
│   └── OASIS_Level1_Task3_Data_Cleaning_Report.pdf
├── screenshots/
│   ├── 01_Library_Import.png
│   ├── 02_Data_Quality_Report.png
│   ├── 03_Missing_Value_Handling.png
│   ├── 04_Duplicate_Removal.png
│   ├── 05_Data_Standardisation.png
│   ├── 06_Outlier_Detection_IQR.png
│   ├── 07_Final_Data_Quality_Check.png
│   └── 08_Cleaned_Dataset_Saved.png
└── README.md

🔍 Data Cleaning Workflow

1. Library Import

The required Python libraries were imported for data manipulation, analysis, and visualization.

2. Dataset Inspection

The Titanic dataset was loaded and inspected to understand its structure, columns, data types, missing values, and overall data quality.

3. Data Quality Report

A data quality report was created to identify missing values, duplicate records, data types, and potential value-range issues.

4. Missing Value Handling

Missing values were identified and handled using appropriate data-cleaning techniques so that the dataset could be used reliably for further analysis.

5. Duplicate Removal

The dataset was checked for duplicate records. Duplicate rows were removed where required to improve data consistency.

6. Data Standardisation

Inconsistent data formats and values were standardized to maintain consistency across the dataset.

7. Outlier Detection

The Interquartile Range (IQR) method was used to detect potential outliers in relevant numerical variables. The detected values were reviewed and treated according to the cleaning approach used in the notebook.

8. Final Data Quality Check

After completing the cleaning process, a final quality check was performed to verify that the major data-quality issues had been addressed.

9. Save Cleaned Dataset

The cleaned dataset was saved as Titanic_Cleaned.csv in the output/ folder for further analysis.

📸 Screenshots

The project includes screenshots documenting the main stages of the cleaning process:

01_Library_Import.png — Required libraries imported successfully.

02_Data_Quality_Report.png — Data quality inspection.

03_Missing_Value_Handling.png — Missing-value treatment.

04_Duplicate_Removal.png — Duplicate record handling.

05_Data_Standardisation.png — Data standardization.

06_Outlier_Detection_IQR.png — IQR-based outlier detection.

07_Final_Data_Quality_Check.png — Final validation.

08_Cleaned_Dataset_Saved.png — Cleaned dataset saved.

📁 Project Files

dataset/ — Original Titanic dataset.

notebook/ — Complete Jupyter Notebook implementation.

output/ — Cleaned Titanic dataset.

report/ — Project report.

screenshots/ — Screenshots of the major steps.

README.md — Project documentation.

▶️ How to Run

Open the project folder.

Open the notebook folder.

Launch Level1_Task3_Data_Cleaning.ipynb using Jupyter Notebook, JupyterLab, or VS Code.

Ensure Titanic-Dataset.csv is inside the dataset folder.

Install the required Python libraries if necessary.

Run the notebook cells from top to bottom.

The cleaned dataset will be saved in the output folder.

🎥 Demo Video

Add your demo-video link here after uploading it:

https://drive.google.com/file/d/1DA30CfyI5U6FSJgFwqGBr-ySIXjCQUyV/view?usp=sharing

✅ Conclusion

This project demonstrates a complete data-cleaning workflow using Python. The Titanic dataset was inspected, data-quality issues were identified, missing values and duplicates were handled, data was standardized, outliers were detected using the IQR method, and a final quality check was performed. The cleaned dataset was then saved as a new CSV file for further analysis.

👩‍💻 Author

Sai Sprisha

Track: Data Analytics
Level: Level 1
Task: Task 3 — Data Cleaning
Internship: Oasis Infobyte
