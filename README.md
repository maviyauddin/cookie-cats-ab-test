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

---


