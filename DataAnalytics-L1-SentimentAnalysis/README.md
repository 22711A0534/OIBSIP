Data Analytics L1-T4 — Sentiment Analysis

📌 Overview

This project performs Sentiment Analysis on Twitter text data using Natural Language Processing (NLP) and Machine Learning techniques. The objective is to classify text into Positive, Negative, and Neutral sentiment categories and evaluate different machine learning models.

🎯 Objective

The main objectives of this project are to:

Load and inspect the Twitter sentiment datasets.

Analyse the distribution of sentiment categories.

Preprocess and clean text data for NLP.

Convert text into numerical features using TF-IDF.

Split the dataset into training and testing sets.

Build machine learning models for sentiment classification.

Compare Multinomial Naive Bayes and Logistic Regression.

Evaluate model performance using classification metrics.

Generate a confusion matrix for model evaluation.

Analyse correctly and incorrectly classified examples.

Generate word clouds for Positive, Neutral, and Negative sentiments.

Provide useful insights from the sentiment analysis results.

🛠️ Technologies Used

Python

Pandas

NumPy

NLTK

Scikit-learn

Matplotlib

Seaborn

WordCloud

Jupyter Notebook

📂 Project Structure

DataAnalytics-L1-T4/
│
├── dataset/
│   ├── twitter_training.csv
│   └── twitter_validation.csv
│
├── notebook/
│   └── Level1_Task4_Sentiment_Analysis.ipynb
│
├── output/
│   ├── classification_report_lr.csv
│   ├── classification_report_nb.csv
│   ├── misclassified_examples.csv
│   └── model_comparison.csv
│
├── report/
│   └── OASIS_Level1_Task4_Sentiment_Analysis_Report.pdf
│
├── screenshots/
│   ├── 01_Dataset_Loading.png
│   ├── 02_Sentiment_Distribution.png
│   ├── 03_Text_Preprocessing.png
│   ├── 04_TFIDF_Features.png
│   ├── 05_Train_Test_Split.png
│   ├── 06_Naive_Bayes.png
│   ├── 07_Logistic_Regression.png
│   ├── 08_Model_Evaluation.png
│   ├── 09_Confusion_Matrix.png
│   ├── 10_WordCloud_Positive.png
│   ├── 11_WordCloud_Neutral.png
│   ├── 12_WordCloud_Negative.png
│   └── 13_Error_Analysis.png
│
└── README.md

📊 Analysis Workflow

1. Dataset Loading

The Twitter training and validation datasets were loaded using Pandas. The dataset structure and available sentiment information were inspected before beginning the analysis.

2. Sentiment Distribution

The distribution of sentiment categories was analysed to understand the balance of Positive, Negative, and Neutral text samples.

3. Text Preprocessing

The text data was cleaned and prepared for machine learning. Preprocessing included handling unnecessary characters, normalizing text, tokenization, and removal of stopwords where appropriate.

4. TF-IDF Feature Extraction

TF-IDF (Term Frequency–Inverse Document Frequency) was used to convert the preprocessed text into numerical feature vectors. These features were then used as input to the machine learning models.

5. Train-Test Split

The prepared data was divided into training and testing sets so that the trained models could be evaluated on unseen text data.

6. Multinomial Naive Bayes

A Multinomial Naive Bayes classifier was trained for sentiment classification. The model was evaluated using standard classification metrics.

7. Logistic Regression

A Logistic Regression classifier was also trained using the TF-IDF features. Its performance was evaluated and compared with the Naive Bayes model.

8. Model Evaluation

The models were evaluated using classification reports containing metrics such as precision, recall, F1-score, and accuracy. The results were stored in the output/ folder.

9. Confusion Matrix

A confusion matrix was generated to examine the classification performance across Positive, Negative, and Neutral sentiment categories.

10. Word Cloud Analysis

Word clouds were generated separately for Positive, Neutral, and Negative text to visualize frequently occurring words within each sentiment category.

11. Error Analysis

Misclassified examples were extracted and analysed to understand cases where the models predicted the sentiment incorrectly.

🤖 Machine Learning Models

Two machine learning models were implemented:

Multinomial Naive Bayes

Logistic Regression

The performance of both models was compared using the generated evaluation metrics.

📁 Output Files

classification_report_lr.csv — Classification metrics for Logistic Regression.

classification_report_nb.csv — Classification metrics for Multinomial Naive Bayes.

misclassified_examples.csv — Examples of incorrectly classified text.

model_comparison.csv — Comparison of the implemented machine learning models.

📸 Screenshots

The screenshots/ folder contains visual evidence of the major project stages:

Dataset loading

Sentiment distribution

Text preprocessing

TF-IDF feature extraction

Train-test split

Naive Bayes model

Logistic Regression model

Model evaluation

Confusion matrix

Positive word cloud

Neutral word cloud

Negative word cloud

Error analysis

▶️ How to Run

Open the project folder in VS Code or Jupyter Notebook.

Open the notebook folder.

Launch Level1_Task4_Sentiment_Analysis.ipynb.

Ensure both Twitter datasets are available inside the dataset folder.

Install the required Python libraries if they are not already installed.

Run the notebook cells from top to bottom.

Check the generated results in the output folder.

🎥 Demo Video

Add the project demonstration video link here after uploading it:

https://drive.google.com/file/d/1UiJtBk3nnHafTvdwWVnMOBkQq4THh_n7/view?usp=sharing

✅ Conclusion

This project demonstrates an end-to-end sentiment analysis workflow using Natural Language Processing and Machine Learning. Twitter text data was loaded, analyzed, preprocessed, converted into TF-IDF features, and classified using Multinomial Naive Bayes and Logistic Regression. Model evaluation, confusion matrix analysis, word clouds, and error analysis were also performed to understand the classification results.

👩‍💻 Author

Sai Sprisha

Track: Data Analytics
Level: Level 1
Task: Task 4 — Sentiment Analysis
Internship: Oasis Infobyte
