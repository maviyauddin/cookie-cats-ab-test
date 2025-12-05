<p align="center">
  <img src="https://github.com/maviyauddin/cookie-cats-ab-test/blob/main/Image%20Dec%205,%202025,%2008_53_08%20AM.png?raw=true" width="90%">
</p>



# Cookie Cats A/B Testing: Retention Impact Analysis

## 1. Overview

This project analyzes the results of an A/B experiment conducted on *Cookie Cats*, a popular mobile puzzle game.  
The game includes gates—progression blockers that players must wait for or pay to bypass.  
The development team tested whether moving the first gate from level 30 to level 40 would improve user retention.

This analysis evaluates the experiment using statistical hypothesis testing, bootstrapping, and effect size measurement.  
The primary outcomes assessed are **Day-1 retention** and **Day-7 retention**.

---

## 2. Business Objective

The objective of this experiment is to determine whether shifting the first gate from level 30 (control) to level 40 (treatment) increases short-term or long-term player retention.

Retention is a key business metric in mobile gaming:
- Higher retention leads to higher engagement.
- Increased engagement generally results in improved ad revenue and in-app purchase opportunities.
- Early-game experience is critical in shaping long-term player behavior.

The business question:

> **Does moving the first gate from level 30 to level 40 improve Day-1 or Day-7 retention?**

---

## 3. Dataset Description

The dataset contains 90,189 player records with the following fields:

| Column | Description |
|--------|-------------|
| `userid` | Unique player identifier |
| `version` | Experimental group (`gate_30` = control, `gate_40` = treatment) |
| `sum_gamerounds` | Number of rounds played during the first week |
| `retention_1` | Whether the player returned one day after installation (binary) |
| `retention_7` | Whether the player returned one week after installation (binary) |

The dataset contains no missing values and is suitable for statistical testing directly.

---

## 4. Methodology

### 4.1 Exploratory Data Analysis
- Verified balance between control and treatment groups.
- Calculated observed Day-1 and Day-7 retention rates.
- Examined gameplay distribution through descriptive statistics.

### 4.2 Statistical Testing
Retention metrics are binary proportions.  
Given the large sample size (>45k per group), the **two-proportion z-test** is the appropriate statistical method.

Performed:
- Z-test for Day-1 retention
- Z-test for Day-7 retention

### 4.3 Bootstrapping
Generated 5,000 bootstrap samples to estimate the confidence interval for the difference in Day-7 retention between groups.

### 4.4 Effect Size (Cohen’s h)
Calculated Cohen’s h to measure practical significance in addition to statistical significance.

---

## 5. Results

### 5.1 Observed Retention Rates

| Metric | gate_30 (Control) | gate_40 (Treatment) |
|--------|--------------------|----------------------|
| **Day-1 Retention** | 44.82% | 44.23% |
| **Day-7 Retention** | 19.02% | 18.20% |

---

### 5.2 Hypothesis Test Results

**Day-1 Retention**  
- z = 1.784  
- p-value = 0.074  
- Interpretation: *Not statistically significant*

**Day-7 Retention**  
- z = 3.164  
- p-value = 0.00155  
- Interpretation: *Statistically significant difference*

Retention in the treatment group (gate_40) is significantly lower after seven days.

---

### 5.3 Bootstrap Confidence Interval (Day-7 Retention)

95% CI for (gate_30 − gate_40):

**[0.0031, 0.01336]**

The entire interval is positive, confirming that gate_30 consistently outperforms gate_40 in long-term retention.

---

### 5.4 Effect Size (Cohen’s h)

| Metric | Cohen’s h | Interpretation |
|--------|-----------|----------------|
| **Day-1 Retention** | 0.0119 | Very small effect |
| **Day-7 Retention** | 0.0211 | Very small effect |

Although the effect size is small, the large sample size ensures statistical reliability.  
In mobile gaming, even a 1% retention decrease can significantly impact revenue and player lifetime value.

---

## 6. Interpretation and Discussion

- Moving the gate to level 40 **does not improve short-term retention** (Day-1).  
- The change **reduces long-term retention** (Day-7) in a statistically significant and consistent manner.
- Despite a small effect size, the direction and significance of impact are unfavorable for the business.
- Reduced long-term retention indicates fewer returning players, lower engagement, and diminished monetization potential.

---

## 7. Recommendation

Based on statistical evidence, bootstrap analysis, and effect size evaluation:

> **Do not implement the gate_40 change.  
Revert to the original gate position at level 30.**

The treatment negatively impacts long-term retention and may reduce overall revenue.

---

## 8. Suggested Follow-Up Experiments

1. Test intermediate gate levels (e.g., 32, 35) to measure sensitivity.  
2. Experiment with reward-based progression instead of gate movement.  
3. Segment users by engagement level or geographic region for differential impact analysis.  
5. Build predictive retention models to identify at-risk players.

---

## 9. Project Structure

├── data/
│ └── cookie_cats.csv
├── notebooks/
│ └── cookie_cats_ab_test.ipynb
├── images/
│ ├── retention_day1.png
│ ├── retention_day7.png
│ └── bootstrap_distribution.png
├── README.md

yaml
Copy code

---

## 10. Technologies Used

- Python 3  
- Pandas  
- NumPy  
- Matplotlib  
- Statsmodels  
- Scikit-learn (optional exploratory modeling)  
- Jupyter / Google Colab  

## Executive Summary

This project analyzes an A/B experiment conducted on the mobile puzzle game Cookie Cats, where the development team tested whether shifting the first progression gate from level 30 to level 40 would improve player retention. Using 90,189 user records, the analysis applies statistical hypothesis testing, bootstrap confidence intervals, and effect size measurement to determine the impact of this design change.

Results show that while Day-1 retention remains statistically unchanged, Day-7 retention decreases significantly for players exposed to the new gate at level 40. The bootstrap confidence interval confirms that this effect is consistently negative, and even small changes in retention can have meaningful implications for player lifetime value in mobile gaming.

Based on these findings, the recommendation is to maintain the original gate at level 30, as the modification negatively affects long-term engagement. This project demonstrates a full analytics workflow—from experiment evaluation to actionable business insight—and highlights my ability to apply data science techniques to real product decisions.
---

## Purpose of This Project

The purpose of this project is to evaluate the impact of a gameplay design change on user retention through a controlled A/B experiment.  
Specifically, the mobile game Cookie Cats moved its first progression gate from level 30 to level 40, and the company needed to determine whether this change improved or harmed player engagement.

This project applies statistical hypothesis testing, bootstrapping, and effect size analysis to quantify the effect of the experiment and provide a clear, data-driven recommendation for product decision-making.

## Project Motivation

A/B testing is one of the most essential tools in data-driven product development.  
Understanding how to design, evaluate, and interpret controlled experiments is a core skill for data scientists, product analysts, and machine learning practitioners.

This project was selected to strengthen my ability to:

- Analyze real behavioral data at scale  
- Apply statistical methods to quantify treatment effects  
- Validate results using bootstrapping and effect size metrics  
- Translate analytical findings into clear product recommendations  

By working through this end-to-end experiment, I aimed to develop a deeper understanding of how data science directly influences product decisions, user engagement, and business outcomes.

## Skills Demonstrated

- **A/B Testing & Experimentation**
  - Designed and evaluated a controlled A/B experiment
  - Applied two-proportion z-tests to compare treatment and control groups
  - Interpreted statistical significance and practical significance

- **Statistical Analysis**
  - Conducted hypothesis testing for retention metrics
  - Generated bootstrap confidence intervals (5,000+ samples)
  - Calculated effect sizes (Cohen’s h) to quantify impact

- **Data Exploration & Visualization**
  - Cleaned and analyzed user gameplay data
  - Built clear retention plots and distribution visualizations
  - Summarized insights into interpretable tables and charts

- **Machine Learning**
  - Built a logistic regression model to predict Day-7 retention
  - Performed feature engineering and model evaluation (AUC metric)
  - Interpreted model coefficients to support decision-making

- **Business Decision-Making**
  - Translated statistical findings into actionable recommendations
  - Assessed the impact of game mechanics on user engagement
  - Formulated product insights and experiment follow-up strategies

- **Technical Stack**
  - Python, Pandas, NumPy  
  - Matplotlib for visualizations  
  - Scikit-learn for modeling  
  - Statsmodels for statistical testing  

This project demonstrates my ability to combine analytical rigor, statistical methods, and business thinking to deliver insights that guide product development.

## Final Summary

This project presents a complete A/B testing workflow applied to real game analytics data.  
Through statistical hypothesis testing, bootstrap validation, effect size measurement, and machine learning modeling, the analysis demonstrates that moving the first game gate from level 30 to level 40 negatively affects long-term retention.

The results provide a clear, data-driven recommendation for product decision-making and highlight the importance of combining statistical rigor with business context.  
This work reflects my ability to execute end-to-end analytical projects, communicate insights effectively, and apply data science methods to meaningful real-world scenarios.



## 👤 About Me

Hi, I'm **Khaja Maviya Uddin** — a Data Science student passionate about building end-to-end ML systems, data analysis, and real-world projects.  
I'm actively seeking opportunities as a **Data Scientist / ML Engineer**.
I’m currently applying for **(Data Scientist,ML,AI) roles** and actively growing my skills in:
- Machine Learning  
- Data Engineering  
- SQL & Python  
- Deep Learning  
- Recommender Systems
I love building projects that go beyond basic ML models — focusing on **clean pipelines**, **real-world datasets**, and **scalable techniques** like collaborative filtering and matrix factorization.

📫 **Email:** [khajamaviyauddin@gmail.com]  
🔗 **LinkedIn:** (https://www.linkedin.com/in/khaja-maviya-uddin-018995309/)  
💻 **GitHub:** (https://github.com/maviyauddin)

