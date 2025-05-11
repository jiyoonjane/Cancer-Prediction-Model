# Data Description

**Source:** [Cancer Patients and Air Pollution](https://www.kaggle.com/datasets/thedevastator/cancer-patients-and-air-pollution-a-new-link/data)

## 1. Preprocessing Steps

* **Missing Values:** None present.
* **Outliers:** Not applicable for categorical and ordinal features.
* **Drop Columns:** `index`, `Patient Id`.
* **Encode Target:** Convert `Level` from `{'Low','Medium','High'}` to `{0,1,2}` respectively.

## 2. Post-Processing Dataset Structure

| Column                   | Type  | Description                                            |
| ------------------------ | ----- | ------------------------------------------------------ |
| Age                      | int64 | Patient age (years)                                    |
| Gender                   | int64 | Gender (1 = male, 2 = female)                          |
| Air pollution            | int64 | Air pollution exposure level (higher = more polluted)  |
| Alcohol use              | int64 | Alcohol consumption level                              |
| Dust Allergy             | int64 | Dust allergy sensitivity level                         |
| OccuPational Hazards     | int64 | Occupational hazard level                              |
| Genetic Risk             | int64 | Genetic cancer risk level                              |
| Chronic Lung Disease     | int64 | Chronic lung disease severity                          |
| Balanced Diet            | int64 | Balanced diet quality                                  |
| Obesity                  | int64 | Obesity level                                          |
| Smoking                  | int64 | Smoking intensity                                      |
| Passive Smoker           | int64 | Passive smoking exposure                               |
| Chest Pain               | int64 | Chest pain severity                                    |
| Coughing of Blood        | int64 | Hemoptysis frequency                                   |
| Fatigue                  | int64 | Fatigue severity                                       |
| Weight Loss              | int64 | Weight loss severity                                   |
| Shortness of Breath      | int64 | Dyspnea severity                                       |
| Wheezing                 | int64 | Wheezing severity                                      |
| Swallowing Difficulty    | int64 | Dysphagia severity                                     |
| Clubbing of Finger Nails | int64 | Digital clubbing severity                              |
| Frequent Cold            | int64 | Frequency of common cold episodes                      |
| Dry Cough                | int64 | Dry cough severity                                     |
| Snoring                  | int64 | Snoring severity                                       |
| Level                    | int64 | Lung cancer risk level (0 = Low, 1 = Medium, 2 = High) |

## 3. Preprocessing Code

```python
import pandas as pd

# 1. Load raw data
df = pd.read_csv('cancer_air_pollution.csv')  # replace with your file path

# 2. Drop unneeded columns
df = df.drop(columns=['index','Patient Id'], errors='ignore')

# 3. Encode target variable
level_map = {'Low': 0, 'Medium': 1, 'High': 2}
df['Level'] = df['Level'].map(level_map).astype('int64')

# 4. Check data types and missing values
print(df.info())
print(df.isnull().sum())

# 5. Save cleaned dataset
df.to_csv('lung_cancer_data_cleaned.csv', index=False)
```

