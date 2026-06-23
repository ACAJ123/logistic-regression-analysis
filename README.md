# Project Title: 

## Airline Passenger Satisfaction Analysis: Logistic Regression Framework

## Executive Summary
This project implements a binomial Logistic Regression model to classify and predict airline passenger satisfaction using a comprehensive tracking dataset of 129,880 rows. The primary objective is to move beyond high-level accuracy to derive actionable, data-backed operational improvements for airline stakeholders based on feature weights and odd ratios.

---

## Data Pipeline & Preparation
* **Handling Missing Values:** Rows containing missing or null fields (`NaN`) were dropped entirely to ensure numeric continuity.
* **Categorical Feature Encoding:** The 4 structural string columns (`Customer Type`, `Type of Travel`, `Class`) were safely transformed into numerical arrays using `LabelEncoder`.
* **Feature Scaling:** Since parameters span heavily differing numerical limits, `StandardScaler` was applied to normal distribution spreads, preventing algorithmic weight bias.
* **Validation Structure:** An 80/20 train/test partition was executed using stratification rules to maintain perfect baseline target proportions.

---

## Model Evaluation Metrics
By scaling our test partitions explicitly before evaluation, our validation framework yields highly stable, symmetrical performance characteristics.

* **Overall Classification Accuracy:** 82.55%
* **Macro Average F1-Score:** 0.82

### Complete Classification Report Summary
* **Dissatisfied Class:** Precision = 0.81 | Recall = 0.81 | F1-Score = 0.81
* **Satisfied Class:** Precision = 0.84 | Recall = 0.84 | F1-Score = 0.84

### Confusion Matrix Breakdowns
* **True Negatives (Correctly Identified Dissatisfied):** 9,441
* **True Positives (Correctly Identified Satisfied):** 11,938
* **False Positives (False Alarms - Unhappy predicted as Happy):** 2,280
* **False Negatives (Missed Cases - Happy predicted as Unhappy):** 2,239

---

## Technical Insights & Coefficient Interpretations
Rather than relying on uninterpretable log-odds coordinates, model outputs were transformed into **Odds Ratios** via mathematical exponents ($e^{\beta}$) to clarify exact operational leverage points.

1. **Inflight Entertainment (Coefficient: 0.9810 | Odds Ratio: 2.6672)**
   * *Interpretation:* This is the absolute strongest predictor of positive satisfaction. For every one unit increase on the standardized rating scale, a passenger's baseline odds of being satisfied increase by **166.7%** (giving them 2.66x higher odds of satisfaction). 
   * *Probability Shift:* Upgrading an average traveler's inflight entertainment experience yields an isolated satisfaction probability surge of **23.23%**.
2. **On-board Service & Seat Comfort (Odds Ratios: ~1.49)**
   * *Interpretation:* Physical comfort benchmarks maintain massive statistical dependencies. Improving standard cabin design seats or service quality metrics expands satisfaction likelihood structures by roughly **49%** per unit increase.
3. **Customer Type (Coefficient: -0.7594 | Odds Ratio: 0.4679)**
   * *Interpretation:* First-time or disloyal consumer segments show a major negative coefficient mapping. This category experiences **53.21% lower odds** of evaluating their flight experience as satisfactory compared to the standard loyalty tier benchmarks.

---

## Data-Backed Strategic Recommendations
* **Direct Resource Reallocation:** Physical experience pillars like *Seat Comfort* (1.49 Odds Ratio) significantly outperform digital properties like *Inflight Wifi Service* (0.88 Odds Ratio). Capital expenditure budgets should prioritize seat geometry and crew soft-skill training over expensive satellite internet infrastructure expansions.
* **Targeted Retentional Infrastructure:** Address the severe satisfaction drop among first-time flyers indicated by the negative Customer Type weight. Implement rapid automated post-flight recovery vouchers and introductory frequent-flyer bonuses to flatten this critical churn vector.

---

## Limitations & Project Scaling Next Steps
* **Linear Constraint Limitations:** Logistic regression fits a hard linear boundary. It cannot natively capture multi-dimensional interaction terms, such as how flight distance heavily alters the comfort expectations of varying age cohorts.
* **Future Optimization Protocols:** To step past our current 82.55% accuracy benchmark, future iterations will transition from basic label maps to **One-Hot Encoding** vectors, alongside deploying non-parametric ensemble models such as **Random Forests** and **XGBoost**.



### Confusion Matrix
True Negative (Correctly caught Dissatisfied): 9493
False Positive (Wrongly guessed Satisfied):     2266
False Negative (Wrongly guessed Dissatisfied): 2149
True Positive (Correctly caught Satisfied):    12068
