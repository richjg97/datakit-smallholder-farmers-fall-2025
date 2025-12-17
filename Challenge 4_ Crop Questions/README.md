# 🌾 Challenge 4: Crop-Specific vs. Crop-Independent Questions

**DataKind – Producers Direct DataKit**

---

## Project Background

This project was completed as part of the **DataKind Producers Direct DataKit** and focuses on understanding how smallholder farmers use peer-to-peer platforms to seek agricultural knowledge. Producers Direct inherited historical data from the **WeFarm** platform, an SMS-based agricultural knowledge-sharing system that operated for approximately seven years across multiple East African countries.

From the perspective of a **data analyst supporting Producers Direct**, the goal of this analysis is to determine whether farmer questions are primarily **crop- or livestock-specific** or whether they reflect **general agricultural concerns** that apply across crops, locations, and seasons. Understanding this balance helps inform how agricultural knowledge can be structured, reused, and scaled to better support farmers and advisory systems.

This analysis directly addresses **Challenge 4** of the DataKit.

---

## Intended Audience

This analysis is intended to support **Producers Direct product and content teams** in deciding how agricultural knowledge should be organized, reused, and delivered across different crops, regions, and seasonal contexts.

---

## Data Structure & Initial Checks

The analysis was conducted at the **question level**, using **distinct `question_id` values** to avoid inflating counts due to multiple responses per question.

**Key fields used:**

- `question_id`: Unit of analysis
- `question_topic`: Topic classification
- `question_user_country_code`: Geographic analysis
- `question_sent`: Temporal and seasonal analysis

A **topic classification mapping** was created to assign each question to one of the following categories:

- Crop-Specific
- Livestock-Specific
- General (crop-independent)

This classification was applied consistently across all analyses.

---

## Executive Summary

Across approximately **4.2 million unique questions**, most farmer questions focus on **specific crops or livestock**, while a smaller but persistent share addresses **general agricultural concerns**. General questions appear consistently across countries and years, indicating shared challenges regardless of crop choice. Although total question volume fluctuates over time, the **relative balance between crop-specific, livestock-specific, and general questions remains stable**, suggesting that general questions complement rather than replace specific ones.

---

## Insights Deep Dive

### Category 1: Question Type Balance (Crop-Specific vs. General)

- **Crop-specific questions dominate overall volume**, accounting for **51.06% of all questions (2,141,563 unique questions)** out of approximately **4.2 million** distinct question records.
- **Livestock-specific questions form a substantial secondary share**, representing **38.26% of all questions (1,604,681 unique questions)**, showing that animal-related concerns are nearly as prominent as crop-specific ones.
- **General (crop-independent) questions comprise a smaller but meaningful segment**, making up **10.63% of all questions (445,953 unique questions)**, indicating persistent demand for advice that applies across crops.
- **Unknown-topic questions are negligible**, accounting for only **0.04% of all questions (1,613 unique questions)** and therefore do not materially affect interpretation of category balance.
- **Overall, specificity dominates farmer inquiry**, with **89.32% of questions** focused on specific crops or livestock, compared with **10.68%** that are general or uncategorized.

![image.png](attachment:1c9024fd-c381-4fab-8255-7e48693c7e2a:image.png)

---

### Category 2: Temporal Trends and Seasonality

- **Crop-specific question volume increases sharply over time**, rising from approximately **5,000–15,000 questions per month** in late 2017 and early 2018 to sustained peaks of **80,000–90,000 questions per month** by late 2018.
- **Peak crop-specific activity reaches approximately 87,000–88,000 questions in a single month**, followed by repeated high-volume periods of **65,000–75,000 questions per month** throughout 2019 and 2020.
- **Crop-specific questions remain consistently high through mid-2021**, staying above **40,000 questions per month** for most months, which indicates sustained engagement rather than isolated seasonal spikes.
- **General question volume follows a similar trajectory**, increasing from roughly **1,000–3,000 questions per month** in late 2017 to peaks of **20,000–25,000 questions per month** by late 2018.
- **From 2019 through early 2021, general questions persist at scale**, typically ranging between **5,000 and 12,000 questions per month**, even as total platform volume fluctuates.
- **Both crop-specific and general questions decline sharply after mid-2021**, falling from tens of thousands per month to near zero by late 2021, which indicates a platform-wide decline rather than a seasonal pattern.

![image.png](attachment:89dddfb5-e742-4608-aed1-e0ce6d46c205:image.png)

---

### Category 3: Geographic Variation by Country

- **Crop-specific questions constitute the majority of questions in every country analyzed**, ranging from **70.49% in Ghana**, **63.80% in Tanzania**, **54.17% in Uganda**, to **41.88% in Kenya**, measured as the share of distinct question IDs within each country.
- **The proportion of crop-specific questions varies by nearly 29 percentage points across countries**, indicating meaningful geographic differences in how narrowly farmers frame their questions.
- **General questions represent a consistent secondary share in most countries**, accounting for **12.8% in Kenya**, **11.8% in Uganda**, and **11.4% in Ghana**.
- **Tanzania differs notably from other countries**, with general questions accounting for only **approximately 5.1%** of all questions, which is **6–8 percentage points lower** than in Kenya, Uganda, and Ghana.
- **Countries with higher crop-specific shares tend to have lower general-question shares**, suggesting differing balances between specific and general information needs by location.

![image.png](attachment:d3b63b65-76c2-450f-b363-e4e4aa8ce7da:image.png)

![image.png](attachment:eda61793-7043-4e44-a2da-caa2ff7e7ff1:image.png)

### Category 4: Cross-Cutting Topics and Response Specificity

### Cross-Cutting Topics (General Questions)

- **Planting is the most common cross-cutting topic**, accounting for **133,089 unique questions**, which represents **29.84% of all general questions**.
- **Disease-related topics appear consistently across crops**, with **19,172 unique questions (4.30% of general questions)**.
- **Pest-related concerns are widespread**, accounting for **14,099 unique questions (3.16%)** among general questions.
- **Soil management questions recur across crops**, totaling **10,604 unique questions (2.38%)**.
- **Fertilizer-related topics occur less frequently**, with **4,236 unique questions (0.95%)**.
- **Weather-related questions appear across crops and regions**, totaling **3,326 unique questions (0.75%)**.
- **A large residual group of other topics accounts for the majority of general questions**, totaling **261,430 unique questions (58.62%)**, reflecting a wide variety of less frequent themes.

![image.png](attachment:49b57fca-1b48-4eb7-8c09-cfc1a4bd51e5:image.png)

### Response Specificity

- **General questions receive the highest rate of topic-matched responses**, with **35.52% of general questions (158,385 out of 445,953)** having at least one response that explicitly references the question topic.
- **Crop-specific questions receive topic-matched responses far less often**, with only **14.54% (311,456 out of 2,141,561)** containing at least one topic-matched response.
- **Livestock-specific questions show the lowest response specificity**, with **11.00% (176,506 out of 1,604,683)** receiving a topic-matched response.
- **Across all question types, most responses remain general in wording**, with **78.81% of responses to general questions**, **90.60% of responses to crop-specific questions**, and **94.36% of responses to livestock-specific questions** not explicitly restating the topic.

---

## What This Analysis Does Not Address

- Agronomic correctness or usefulness of responses
- Response length, tone, or quality
- Farmer outcomes or behavioral change

This analysis focuses strictly on **question patterns and response topic alignment**.

---

## Assumptions and Caveats

- Analysis is conducted at the question level to avoid duplication from multiple responses.
- Repetition and text-based analyses are limited to English-language questions.
- Topic classification relies on predefined topic labels and may not capture all semantic nuance.

---

## Future Work

- Deeper NLP-based clustering of question text to uncover latent themes
- Evaluation of response quality and usefulness
- Linking question patterns to downstream farmer outcomes

---

## Transparency on GenAI Use

Generative AI tools were used to assist with code debugging, visualization refinement, and documentation drafting. All outputs were reviewed and validated to ensure accuracy, transparency, and alignment with DataKind’s values.

---
