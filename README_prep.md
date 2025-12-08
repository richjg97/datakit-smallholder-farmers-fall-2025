# **Prep Challenge – Translating Farmer Questions (richjg97)**

## **Overview**

This folder contains my work for the Prep Challenge of the DataKit Fall 2025 program. The goal of this challenge is to translate farmer questions written in Swahili, Luganda, and Runyankore/Rukiga into clear English, and to create simple keyword and glossary outputs from the translations.

The purpose of this preprocessing step is to make farmer messages easier to analyze in later challenges.



## **1. Objectives**

In this challenge, I focused on:

* Translating non-English farmer questions into English
* Cleaning and preparing text for keyword extraction
* Generating term-frequency lists and a small agricultural glossary
* Documenting data quality issues that affected translation
* Producing structured CSV files and a notebook showing the full workflow



## **2. Dataset Summary**

**Source file used:** `farmer_questions.csv`

**Important columns:**

* `question_id`
* `question_language`
* `question_content`
* `question_topic`
* `question_user_country_code`

**Key notes:**

* The dataset contains **over 20 million rows** because each question can have multiple responses.
* I reduced this to a **question-level dataset** (one row per question) so translation would not repeat the same text.
* `question_sent` was not included, but translation was still possible.
* Around **25 percent** of questions had missing topic labels.



## **3. Translation Workflow**

I used **Meta’s NLLB-200 (600M)** translation model to translate all non-English questions.

### **Steps:**

1. Filter out English questions
2. Translate remaining rows in batches
3. Save each translation batch as a CSV file
4. Append all results into a DuckDB table
5. Track `question_id` to avoid re-translating duplicates

Each translated row includes:

* Original text
* Cleaned/tokenized text
* English translation
* Source language code



## **4. Keyword and Glossary Outputs**

After translation, I extracted frequently used agricultural terms.

### **Process:**

* Lowercasing and removing punctuation
* Tokenizing text into individual words
* Counting term frequencies
* Keeping words that appeared at least 5 times
* Exporting keyword lists and glossary files as CSV

These outputs help reveal how farmers describe pests, crops, weather patterns, and other agricultural concerns.



## **5. Data Quality Issues Found**

### **Duplicate `question_id` values**

Occurred because the raw dataset contains multiple responses per question.

### **Missing topic labels**

About one-quarter of entries had an empty topic field.

### **Inconsistent language codes**

Some were mislabeled or not recognized, requiring filtering.

These issues were documented because they affect translation accuracy and later analysis.



## **6. Files Included in This Folder**

* **Prep_Challenge.ipynb - Colab.pdf**
  Full notebook showing the translation workflow

* **translated_batch_000.csv**
  Example translation output

* **prep_challenge_glossary_batch000.csv**
  Extracted agricultural glossary sample

* **prep_challenge_keyword_analysis.csv**
  Term-frequency keyword analysis



## **7. Summary**

The Prep Challenge prepares a cleaner and more structured version of farmer questions by:

* Removing duplicates
* Translating all non-English content
* Producing keyword lists and glossaries
* Identifying quality issues for future reference

This enables more accurate modeling, classification, and trend analysis in later challenges.
