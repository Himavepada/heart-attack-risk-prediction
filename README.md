# Heart Attack Risk Prediction — Machine Learning

**Tools:** SAS Enterprise Miner · Logistic Regression · Decision Tree · Gradient Boosting · Neural Networks  
**Domain:** Preventive Healthcare  
**Timeline:** Fall 2024 (DSCI 5240 — Data Mining, University of North Texas)

---

## Problem statement

Heart disease is one of the leading causes of death globally. Healthcare providers need to identify high-risk patients early to allocate resources effectively and intervene before emergencies occur. This project applies data mining techniques to a large patient dataset to predict heart attack risk and surface the most critical contributing factors.

---

## Dataset

- **Size:** 40,000+ patient records
- **Source:** CDC-style population health survey dataset
- **Features:** Demographics (age, sex, race), health conditions (angina, stroke, diabetes), lifestyle factors (smoking, alcohol), BMI, general health ratings, preventive care indicators
- **Target variable:** `HadHeartAttack` (binary: Yes / No)

---

## Methodology — CRISP-DM lifecycle

### 1. Business understanding
Define success criteria: build a model that accurately identifies high-risk patients to support targeted screening, preventive programs, and insurance risk stratification.

### 2. Data understanding
- Generated descriptive statistics and distributions for all variables
- Identified skewed variables requiring transformation (BMI, Age)
- Calculated chi-square statistics to assess association between predictors and the target

### 3. Data preparation
| Step | Action |
|---|---|
| Missing values | Replaced with mean (interval) or mode (categorical) via Replacement Node |
| Outlier handling | Winsorization — capped extreme values at standard deviation thresholds |
| Normalization | Standardized interval variables to mean=0, SD=1 |
| Encoding | Dummy coded all categorical variables (AgeCategory, RaceEthnicityCategory, SmokerStatus, etc.) |
| Data split | 70% training / 30% validation |

### 4. Modeling — 4 models compared

| Model | Train Accuracy | Validation Accuracy | ASE (Train) | ASE (Val) |
|---|---|---|---|---|
| Logistic Regression | ~95% | ~95% | 0.04 | 0.04 |
| Decision Tree | ~95% | ~95% | 0.04 | 0.04 |
| **Gradient Boosting** | **~95%** | **~95%** | **0.04** | **0.04** |
| Neural Network | ~95% | ~95% | 0.04 | 0.04 |

**Winner: Gradient Boosting** — highest and most consistent lift in the top decile, best balance of sensitivity and specificity, and most interpretable variable importance rankings.

### 5. Evaluation

**Top predictors identified:**

| Predictor | Odds Ratio | Interpretation |
|---|---|---|
| History of Angina | 1.79 | Patients with angina are ~1.8x more likely to have a heart attack |
| Sex (Male) | 2.02 | Males are ~2x more likely than females |
| Age Category | Up to 5.86 | Younger age categories with other risk factors show elevated risk |
| General Health (Poor) | Significant | Self-reported poor health strongly predicts risk |
| Chest Scan | 1.33 | Patients who had chest scans show higher likelihood (proxy for existing concerns) |

---

## Key findings & business recommendations

**For healthcare providers:**
- Prioritize angina patients and males over 50 for proactive cardiovascular screenings
- Build preventive care programs targeting top decile risk patients identified by the model
- Integrate model output into EHR systems to flag high-risk patients at point of care

**For insurance companies:**
- Use risk scores to design tiered, risk-adjusted premiums
- Incentivize preventive behaviors (exercise, non-smoking) with premium discounts

---

## Skills demonstrated

`SAS Enterprise Miner` `Logistic Regression` `Decision Tree` `Gradient Boosting` `Neural Networks` `Feature Engineering` `Data Preprocessing` `Chi-Square Analysis` `Lift Charts` `CRISP-DM` `Healthcare Analytics` `Predictive Modeling`
# heart-attack-risk-prediction
