
# Prep Challenge: Bridging Languages – Translating Farmer Conversations

## 1. Background and Goal

Producers Direct supports smallholder farmers across East Africa. Farmers use digital tools to ask questions about crops, livestock, pests, diseases, soil, fertilizer and markets. Many of these questions are written in Swahili, Luganda and Runyankore or Rukiga.

The goal of this Prep Challenge is to prepare these multilingual questions for later DataKit challenges by translating them into clear English and creating simple language resources that can support topic modeling, clustering and other NLP work.

This submission focuses on the specific Prep Challenge goal:

* Translate non English farmer questions into English
* Build a glossary of how farmers talk about key agricultural terms
* Create a keyword dataset that can be used for training future models

---

## 2. Data Used

This work uses a sample from the Producers Direct farmer question dataset.

For the Prep Challenge I worked with:

* 5 000 non English questions
* Languages in this sample

  * Swahili
  * Luganda
  * Runyankore or Rukiga

Key fields include

* question_id
* question_language
* question_content
* question_topic
* question_user_country_code
* question_sent

All questions are anonymized and come from the WeFarm platform history that Producers Direct now stewards.

---

## 3. Approach Overview

The work is organized into four main steps.

1. Select and clean the 5 000 non English questions
2. Translate all 5 000 questions into English using the NLLB 200 model
3. Check translation quality with simple automated checks plus manual review
4. Produce the two suggested Prep Challenge outputs

   * A farmer glossary for key agricultural terms
   * A keyword and category dataset that can be used for training or clustering

The README focuses on the high level logic and insights. All code and notebooks are stored separately in this folder.

---

## 4. Translation and Quality Checks

All 5 000 non English questions were translated into English.

To check whether the translation was successful I used three types of checks.

**Completeness checks**

* Confirm there are no missing translations
* Confirm there are no empty strings after translation

**Repetition and machine error checks**

* Look for unusual repetition patterns in the English text
* Flag very long or noisy outputs for inspection

**Manual spot checks**

* Manually review a small sample of translations from Swahili, Luganda and Runyankore or Rukiga
* Confirm that key farming concepts such as maize, beans, soil, pests, chickens, cows, goats and fertilizer are preserved

Overall result

* All 5 000 rows have a non empty English translation
* Only a small number of rows show clear machine repetition or awkward phrasing
* For most rows the meaning is clear enough for clustering, keyword extraction and later modeling

---

## 5. Output 1 – Farmer Glossary

**Suggested output**

> A glossary about how farmers refer to key agriculture terms

### How the glossary was created

* I scanned the translated English text for high frequency agricultural words
* I focused on terms that match the Prep Challenge theme
  such as crops, livestock, inputs, soil, pests, disease and weather
* For each term I pulled up to three real example questions from farmers
* I added a simple category for each term, such as

  * crops
  * livestock
  * inputs
  * soil
  * weather
  * disease or pests

The final glossary file is

* `farmer_glossary_enhanced.csv`

It contains

* term
* frequency
* example_1
* example_2
* example_3
* category

### Insights from the glossary

* Livestock appears very often in the data. Terms like chicken, hen, cow, goat and chicks show that animal health is a major concern.
* Crop terms such as maize, beans, potato and sunflower are also frequent, often paired with questions about pests, fertilizer and yield.
* Farmers use simple and informal phrasing instead of technical language. For example they ask why plants are turning yellow or why beans are not growing, rather than talking about nutrient deficiency.
* Inputs like seed and fertilizer and actions like spraying are repeated themes across many questions.
* Weather and soil terms appear in many contexts, hinting at climate and soil challenges even when they are not the main focus of the question.

This glossary captures how farmers actually talk about agriculture and can be used to support annotation, labeling and model design in later challenges.

---

## 6. Output 2 – Keyword and Category Dataset

**Suggested output**

> Cluster or keyword analysis for key terms in local languages that will provide a datasets for training

In this Prep Challenge I interpreted this as creating a dataset where each translated question is tagged with agricultural keywords and their categories. This gives a simple training ready signal that later models can use.

### How the keyword dataset was created

* I used the glossary terms as the core vocabulary
* For each translated question I searched for occurrences of these terms in the English text
* I stored the matched terms in a keywords_found field
* I mapped each term to its category from the glossary and stored those in a keyword_categories field

The main file is

* `farmer_keyword_dataset_with_categories.csv`

Each row includes

* the translated question text
* a list of keywords found in that question
* a list of the categories those keywords belong to

### Insights from the keyword analysis

* Many questions focus on livestock and crops together, for example chickens and maize in the same question. This suggests that future models should expect multi topic questions.
* Inputs and treatments such as fertilizer, spray and medicine appear across both crop and livestock questions. This points to a strong need for advice on how much to apply, when to apply and how to treat disease.
* Disease and pest related keywords show up frequently, supporting the idea that plant and animal health are core pain points for farmers.
* Weather related terms are less frequent as direct topics but often appear in combination with pests, soil or yield, which suggests that weather is an important underlying factor.

This keyword dataset can be used as a starting point for clustering, supervised training, or rule based labeling in later DataKit challenges.

---

## 7. Caveats and Assumptions

* The glossary and keyword dataset are based on the 5 000 row sample, not the full 7.6 million questions. Patterns may change at full scale.
* Machine translation can be imperfect, especially for low resource languages. Some nuance and local expressions may be lost.
* The keyword list is not exhaustive. Farmers may use many other expressions that are not yet captured by the current terms.
* Some questions mix many topics or are unclear, which can make category assignment noisy.

These caveats should be kept in mind when using this Prep Challenge work in later analysis.

---

## 8. Use of Generative AI

I used ChatGPT to help with

* Drafting and refining the README text
* Clarifying how to describe methods and insights in plain language
* Brainstorming how to structure the glossary and keyword outputs

All code and final decisions about data cleaning, translation steps and outputs were reviewed by me.
