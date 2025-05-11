# Lung-Cancer-Prediction-Model

# Introduction

## 1. Topic Selection & Analysis Objectives

### 1.1 Background

Cancer remains one of the leading causes of death globally, and early detection is critical for improving prognosis. Numerous studies have shown that lifestyle factors (smoking, alcohol consumption, physical activity), genetic predispositions, and medical history influence cancer risk. In this project, we aim to develop a machine learning model that predicts lung cancer diagnosis based on health-related variables and past medical history.

### 1.2 Storytelling

Lung cancer often presents without noticeable symptoms until advanced stages, resulting in delayed diagnosis and poorer outcomes. By analyzing individual health and lifestyle data through machine learning, this project seeks to identify high-risk individuals early, prompting timely screening and preventive care to improve treatment success and survival rates.

### 1.3 Project Goals

* **Build a risk prediction model** for lung cancer using personal health and lifestyle data.
* **Identify key risk factors** to inform preventive health strategies.

## 2. Analysis Approach

We prioritize both predictive performance and model interpretability, applying four classification methods:

### 2.1 Multinomial Logistic Regression

* **Use case:** Predicts risk level as High, Medium, or Low.
* **Interpretability:** Provides class-specific coefficients, allowing clear interpretation of each variable’s direction and magnitude of effect for each risk level.
* **Limitation:** Sensitive to class imbalance and multicollinearity.

### 2.2 Binary Logistic Regression

* **Use case:** Focuses on identifying the high-risk group (High vs. Medium/Low).
* **Advantage:** Simplifies interpretation for high-risk screening.
* **Limitation:** Loses granularity by merging Medium and Low risk categories.

### 2.3 Lasso Logistic Regression (L1 Regularization)

* **Use case:** Performs variable selection and modeling simultaneously.
* **Advantage:** Shrinks irrelevant coefficients to zero, reducing multicollinearity and simplifying the model.
* **Limitation:** May exclude moderately important variables if regularization is too strong.

### 2.4 Random Forest + Logistic Regression Hybrid

* **Use case:** Balances predictive power and interpretability.
* **Approach:** Use a Random Forest to rank variable importance and select top predictors, then fit a logistic regression model on those variables.
* **Advantage:** Retains interpretability of logistic regression while leveraging Random Forest’s feature selection.

By applying multiple models, ensure robust variable identification and deep insights, leveraging each method’s strengths to deliver an interpretable and effective lung cancer risk prediction framework.

# Conclusion

## 1. Model Performance Comparison

| Model                                         | Accuracy | Precision (Low/Med/High) | Recall (Low/Med/High) | F1-Score (Low/Med/High) | ROC-AUC  |
| --------------------------------------------- | -------- | ------------------------ | --------------------- | ----------------------- | -------- |
| Multiclass Logistic Regression                | 0.88     | 0.81 / 0.84 / 0.99       | 0.85 / 0.80 / 0.99    | 0.83 / 0.82 / 0.99      | —        |
| Binary Logistic Regression (High vs. Others)  | 0.87     | 0.81                     | 0.83                  | 0.82                    | 0.90     |
| Lasso Logistic Regression (L1 Regularization) | **1.00** | **1.00**                 | **1.00**              | **1.00**                | **1.00** |
| Tree-Based Feature ➔ Logistic Regression      | **1.00** | **1.00**                 | **1.00**              | **1.00**                | **1.00** |

* **Top Performers:** Lasso and the hybrid Tree-Based➔Logistic models achieve perfect scores across all metrics on the test set.
* **Baseline Models:** Multiclass and binary logistic regression achieve \~88% and \~87% accuracy, respectively.

**Note:** 100% performance suggests potential overfitting. External validation on independent cohorts is essential before clinical deployment.

---

## 2. Key Predictive Factors for Lung Cancer Risk

### Respiratory & Symptom-Related Variables

* **Coughing of Blood**: Very strong positive impact across all models.
* **Shortness of Breath**: Strong positive influence.
* **Fatigue**: Strong positive influence, reflects systemic disease.
* **Swallowing Difficulty**: Moderate positive signal.
* **Wheezing**: Mixed effect; requires combination with other symptoms.

### Environmental & Lifestyle Variables

* **Passive Smoker (Secondhand Smoke)**: Consistently strong predictor.
* **Air Pollution**: Strong positive association.
* **Alcohol Use**: Moderate positive association.
* **Balanced Diet**: Protective factor, especially in mid-risk group.
* **Obesity**: Variable effect across models (risk vs. protective).

---

## 3. Detailed Variable Insights by Model

**Multiclass Logistic Regression:** Highlights obesity, hemoptysis, alcohol use, dust allergy, and secondhand smoke as top predictors for high-risk classification.

**Binary Logistic Regression:** Emphasizes hemoptysis, fatigue, passive smoking, dyspnea, and dysphagia for distinguishing high-risk from others.

**Tree-Based➔Logistic Model:** Prioritizes fatigue, passive smoking, dysphagia, air pollution, and hemoptysis; also reveals protective roles for obesity, wheezing, clubbing, and snoring in certain contexts.

---

## 4. Clinical & Public Health Insights

1. **Common High-Risk Signals:** Hemoptysis, secondhand smoke, fatigue, and dyspnea should be prioritized in screening questionnaires and policymaking.
2. **Protective Factor:** Balanced diet reduces progression to higher risk categories—supporting nutritional interventions.
3. **Symptom Combinations:** Joint presence of multiple respiratory symptoms (e.g., hemoptysis + dyspnea + fatigue) greatly enhances predictive accuracy—suggesting multi-symptom checklists.
4. **Model Deployment:** Lasso and hybrid models offer interpretable feature sets for early-warning systems, but external validation is crucial to avoid overfitting.
5. **Binary Model Use:** The binary logistic regression is practical for simple high-risk screening in clinical settings.

**Next Steps:**

* Validate models on independent / prospective cohorts.
* Incorporate patient-reported outcomes and imaging biomarkers.
* Develop an integrated risk calculator or decision-support tool for clinicians.

