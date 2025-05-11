# Lung-Cancer-Prediction-Model

# I. Introduction

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

By applying multiple models, we ensure robust variable identification and deep insights, leveraging each method’s strengths to deliver an interpretable and effective lung cancer risk prediction framework.
