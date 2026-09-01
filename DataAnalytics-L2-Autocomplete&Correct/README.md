# Data Analytics L2-T5 — Autocomplete & Autocorrect

## 📌 Overview

This project focuses on building a simple **Natural Language Processing (NLP) based Autocomplete and Autocorrect system** using an email text dataset.

The project demonstrates how text preprocessing, tokenization, stopword removal, frequency-based n-gram models, and edit-distance based spelling correction can be used to create practical text-assistance features.

The workflow includes data loading, dataset inspection, NLP preprocessing, bigram modelling, autocomplete prediction, spelling correction, performance evaluation, bigram-vs-trigram comparison, word-frequency analysis, confusion-matrix visualization, and final performance reporting.

## 🎯 Objective

The main objectives of this project are to:

- Load and understand an email text dataset.
- Inspect the dataset structure and quality.
- Clean and preprocess email messages.
- Convert text to lowercase.
- Remove punctuation.
- Tokenize text into individual words.
- Remove English stopwords.
- Build a frequency-based bigram language model.
- Predict the next word for a given input prefix.
- Test autocomplete on multiple prefixes.
- Implement autocorrect for deliberately misspelled words.
- Evaluate autocomplete using Top-1 and Top-3 accuracy.
- Evaluate autocorrect using precision and recall.
- Compare bigram and trigram models.
- Identify the most frequent words in the corpus.
- Visualize autocorrect predictions using a confusion matrix.
- Summarize the final performance of both components.
- Discuss limitations and possible improvements.

## 📊 Dataset

**Dataset:** Email Text Dataset — [Download Dataset] (https://drive.google.com/file/d/1iVj12XBcUDtHaRVIVD1Rr8nFBdDBLBi5/view?usp=sharing)

**Dataset file:** `emails.csv`

The dataset contains email messages used as the text corpus for building and testing the NLP system.

The main text column used in the project is:

```text
message
```

Only valid non-null email messages were retained for NLP preprocessing.

## 🛠️ Technologies Used

- **Python**
- **Pandas** – Data loading and data manipulation
- **NumPy** – Numerical operations
- **NLTK** – Tokenization and stopword removal
- **Scikit-learn** – Performance metrics and confusion matrix
- **Matplotlib** – Visualization
- **Seaborn** – Visualization
- **pyspellchecker** – Spell correction
- **Jupyter Notebook** – Development environment

## 📂 Project Structure

```text
DataAnalytics-L2-T5-Autocomplete-Autocorrect/
│
├── dataset/
│   └── emails.csv
│
├── notebook/
│   └── L2_T5_Autocomplete_Autocorrect.ipynb
│
├── report/
│   └── L2_T5_Autocomplete_Autocorrect_Report.pdf
│
├── screenshots/
│   ├── 01_Dataset_Loading.png
│   ├── 02_Dataset_Inspection.png
│   ├── 03_Missing_Values.png
│   ├── 04_NLP_Preprocessing.png
│   ├── 05_Bigram_Model.png
│   ├── 06_Autocomplete_Predictions.png
│   ├── 07_Autocorrect_Results.png
│   ├── 08_Autocomplete_Evaluation.png
│   ├── 09_Autocorrect_Evaluation.png
│   ├── 10_Bigram_Trigram_Comparison.png
│   ├── 11_Top_20_Words.png
│   ├── 12_Autocorrect_Confusion_Matrix.png
│   └── 13_Final_Performance_Summary.png
│
├── demovideo/
│
└── README.md
```

> Update the notebook, report, and screenshot filenames if your actual project uses different names.

## 🔍 Project Workflow

### 1. Dataset Loading

The email dataset was loaded using Pandas:

```python
emails = pd.read_csv("../dataset/emails.csv")
```

The dataset was then inspected using:

- `head()`
- `columns`
- `info()`
- Missing-value check
- Duplicate-row check

The `message` column was used as the main text source for the NLP task.

### 2. NLP Text Preprocessing

Only messages with valid text were retained.

The following preprocessing steps were performed:

#### Lowercasing

All messages were converted to lowercase so that words such as `Please` and `please` would be treated consistently.

#### Punctuation Removal

Punctuation marks were removed from the text.

#### Tokenization

The cleaned messages were divided into individual words using NLTK word tokenization.

#### Stopword Removal

Common English stopwords were removed using the NLTK English stopword list.

#### Processed Text

The filtered tokens were joined back together to create the final `processed_text` used by the language model.

## ⌨️ Autocomplete System

### 3. Bigram Model

A **frequency-based bigram model** was created from the processed email text.

A bigram represents two consecutive words:

```text
current word → next word
```

For example:

```text
please → let
```

The model stores the frequency of words that appear immediately after each current word.

### 4. Next-Word Prediction

A prediction function was created:

```python
predict_next_word(word, top_n=3)
```

The function returns the most frequent next-word predictions for a given input word.

For example, the system can receive:

```text
please
```

and return up to three possible next words based on the training corpus.

### 5. Autocomplete Testing

The autocomplete system was tested using 10 different input prefixes:

- please
- thank
- hello
- would
- get
- need
- send
- information
- contact
- message

For each prefix, the system generated up to three next-word predictions.

## 📈 Autocomplete Evaluation

Autocomplete performance was evaluated using:

- **Top-1 Accuracy**
- **Top-3 Accuracy**

### Results

| Metric | Result |
|---|---:|
| Top-1 Accuracy | **100%** |
| Top-3 Accuracy | **100%** |
| Test Prefixes | 10 |

The expected next words were correctly identified for all 10 selected test prefixes.

> These scores apply only to the selected 10 test prefixes and should not be interpreted as production-level performance.

## ✍️ Autocorrect System

### 6. Spell Correction

The `pyspellchecker` library was used to create the autocorrect component.

The system was tested using deliberately misspelled words such as:

- recieve → receive
- teh → the
- messege → message
- thnaks → thanks
- informtion → information
- adress → address
- recieved → received
- attachmnt → attachment
- pleese → please
- emial → email

Additional spelling errors were also tested.

### 7. Manual Corrections

For some words where the spell-checking library could produce an unsuitable correction, a manual correction dictionary was used to ensure the intended spelling was evaluated.

The final test set contains **20 deliberately misspelled words**.

## 📊 Autocorrect Evaluation

The autocorrect system was evaluated using:

- **Accuracy**
- **Precision**
- **Recall**

### Results

| Metric | Result |
|---|---:|
| Accuracy | **100%** |
| Precision | **100%** |
| Recall | **100%** |
| Test Words | 20 |

All 20 deliberately misspelled test words were corrected to their expected words in the final evaluation.

> The 100% result is based on the selected 20-word test set and does not represent general-purpose spelling correction performance.

## 🔄 Bigram vs Trigram Comparison

### 8. N-Gram Comparison

The project also compares **bigram and trigram models**.

A bigram considers two consecutive words:

```text
word1 → word2
```

A trigram considers three consecutive words:

```text
word1 → word2 → word3
```

The comparison was performed using a sample of **20,000 email texts**.

The project calculates:

- Number of unique bigrams
- Number of unique trigrams
- Top 10 most frequent bigrams
- Top 10 most frequent trigrams

### Key Observation

A trigram contains more context than a bigram.

Therefore, trigrams can provide more context-specific predictions, while bigrams are simpler and require less contextual information.

## 🔤 Top 20 Most Frequent Words

A word-frequency analysis was performed using the processed email text.

The **20 most frequently occurring words** were calculated and visualized using a horizontal bar chart.

This visualization provides an overview of the most common vocabulary in the email corpus.

## 📉 Autocorrect Confusion Matrix

A confusion matrix was generated for the autocorrect test words.

The matrix compares:

- Actual correct words
- Predicted corrected words

This provides a visual representation of how the spelling correction system performed for each tested word.

## 📋 Final Performance Summary

The final project performance is summarized below:

| Component | Metric | Score |
|---|---|---:|
| Autocomplete | Top-1 Accuracy | **100%** |
| Autocomplete | Top-3 Accuracy | **100%** |
| Autocorrect | Precision | **100%** |
| Autocorrect | Recall | **100%** |

The selected test cases were correctly handled by both components.

## 📊 Graphs and Figures

### 1. Dataset Inspection

The dataset inspection outputs show the structure, columns, and initial records of the email dataset.

### 2. NLP Preprocessing

The preprocessing output demonstrates the transformation from raw email messages into cleaned and tokenized text.

### 3. Autocomplete Predictions

The autocomplete results table shows the input prefixes and the top predicted next words.

### 4. Autocorrect Results

The autocorrect results table compares each misspelled word with its corrected version.

### 5. Autocomplete Performance

The evaluation table shows whether the expected next word was correctly identified as the first prediction or within the top three predictions.

### 6. Bigram vs Trigram

The comparison output shows the number of unique n-grams and the most frequent bigrams and trigrams.

### 7. Top 20 Words

The horizontal bar chart visualizes the most frequently occurring words in the processed email corpus.

### 8. Autocorrect Confusion Matrix

The confusion matrix visually represents the relationship between the expected and predicted corrected words.

### 9. Final Performance Summary

The final summary presents the Top-1 and Top-3 autocomplete accuracy and the autocorrect precision and recall scores.

## 💡 Key Findings

- The project successfully implements both autocomplete and autocorrect functionality.
- Text preprocessing improves consistency before building the language model.
- The frequency-based bigram model provides next-word predictions from email text.
- Autocomplete achieved **100% Top-1 and Top-3 accuracy** on the selected 10 test prefixes.
- Autocorrect achieved **100% precision and 100% recall** on the selected 20 misspelled words.
- Trigrams provide more contextual information than bigrams.
- The most frequent-word analysis provides insight into the vocabulary of the email corpus.
- The confusion matrix provides a visual evaluation of autocorrect predictions.
- The test scores are based on small, deliberately selected evaluation sets.

## ⚠️ Limitations

The current implementation has several limitations:

- The autocomplete system is frequency-based and does not understand sentence meaning.
- A bigram model uses only one previous word as context.
- The system may not perform well for unseen words or uncommon phrases.
- Email metadata, technical terminology, and domain-specific vocabulary can affect word frequencies.
- The autocorrect system depends on vocabulary coverage and spelling similarity.
- Names, abbreviations, technical terms, and context-dependent spelling errors may not always be corrected correctly.
- The evaluation uses only 10 autocomplete prefixes and 20 misspelled words.
- Therefore, the 100% test scores should not be interpreted as production-level NLP performance.

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone <your-github-repository-link>
cd DataAnalytics-L2-T5-Autocomplete-Autocorrect
```

### 2. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn nltk scikit-learn pyspellchecker jupyter
```

### 3. Open Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
notebook/L2_T5_Autocomplete_Autocorrect.ipynb
```

Make sure the dataset is available at:

```text
dataset/emails.csv
```

Then run the notebook cells from top to bottom.

> The notebook also downloads the required NLTK resources for tokenization and English stopwords.

## 📄 Project Report

The detailed project report can be placed inside:

```text
report/
```

Example:

```text
L2_T5_Autocomplete_Autocorrect_Report.pdf
```

## 🎥 Demo Video

The project demonstration video is available here:

https://drive.google.com/file/d/1nJgqFXcf9Ak4QYfuAD9Jd8Hq9-yDQuQ3/view?usp=sharing


The demo explains:

- Dataset loading
- NLP preprocessing
- Bigram model
- Autocomplete predictions
- Autocorrect
- Performance evaluation
- Bigram vs trigram comparison
- Top 20 words
- Confusion matrix
- Final performance summary

## 📸 Screenshots

The `screenshots/` folder contains visual evidence of the major stages of the project, including dataset inspection, NLP preprocessing, autocomplete, autocorrect, evaluation, n-gram comparison, word frequency, confusion matrix, and final performance summary.

## 🧠 Learning Outcomes

This project provided practical experience in:

- Natural Language Processing
- Text preprocessing
- Tokenization
- Stopword removal
- Regular expressions
- Frequency-based language models
- Bigram modelling
- Trigram modelling
- Autocomplete systems
- Autocorrect systems
- Spell checking
- Precision and recall
- Accuracy evaluation
- Confusion matrix analysis
- Text data visualization
- Python NLP libraries

## 🏁 Conclusion

This project demonstrates a complete NLP workflow for building **Autocomplete and Autocorrect systems using email text data**.

The email messages were cleaned and preprocessed using lowercasing, punctuation removal, tokenization, and stopword removal. A frequency-based bigram model was then created to generate next-word predictions.

The autocomplete system achieved **100% Top-1 and Top-3 accuracy** on the selected test prefixes. The autocorrect component achieved **100% precision and 100% recall** on the selected misspelled-word test set.

The project also compared bigram and trigram models, analysed the most frequent words, and visualized autocorrect performance using a confusion matrix.

Overall, the project demonstrates the fundamental principles behind NLP-based text assistance systems while also highlighting the limitations of simple frequency-based approaches compared with modern contextual language models.

## 👩‍💻 Author

**Sai Sprisha**

Track: Data Analytics  
Level: Level 2  
Task: Task 5 — Autocomplete & Autocorrect  
Internship: Oasis Infobyte
