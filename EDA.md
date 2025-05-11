#  Exploratory Data Analysis (EDA)

Use the cleaned lung cancer dataset (`lung_cancer_data_cleaned.csv`) to explore distributions, relationships, and identify patterns.

```python
# Imports & Data Load
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load cleaned data
df = pd.read_csv('lung_cancer_data_cleaned.csv')

# Create figures directory if not exists
import os
os.makedirs('figures', exist_ok=True)

#  Quick Overview
print(df.head())
print(df.info())
print(df.describe())

# Target Distribution
plt.figure(figsize=(6,4))
sns.countplot(x='Level', data=df, palette='magma')
plt.xticks([0,1,2], ['Low','Medium','High'])
plt.title('Lung Cancer Risk Level Distribution')
plt.savefig('figures/level_distribution.png', bbox_inches='tight')

#  Gender vs. Risk Level
plt.figure(figsize=(6,4))
sns.countplot(x='Gender', hue='Level', data=df, palette='pastel')
plt.xticks([1,2], ['Male','Female'])
plt.title('Risk Level by Gender')
plt.savefig('figures/gender_vs_level.png', bbox_inches='tight')

#  Correlation Heatmap
plt.figure(figsize=(12,10))
corr = df.corr()
sns.heatmap(corr, cmap='coolwarm', center=0, fmt='.2f')
plt.title('Feature Correlation Matrix')
plt.savefig('figures/correlation_heatmap.png', bbox_inches='tight')

#  Histograms of Key Features
features = ['Age','Air pollution','Smoking','Genetic Risk','Obesity']
for feat in features:
    plt.figure(figsize=(6,4))
    sns.histplot(df[feat], kde=True)
    plt.title(f'Distribution of {feat}')
    plt.savefig(f'figures/hist_{feat.lower().replace(" ","_")}.png', bbox_inches='tight')

#  Boxplots of Continuous Features by Risk Level
cont_feats = ['Age','Air pollution','Smoking','Alcohol use']
for feat in cont_feats:
    plt.figure(figsize=(6,4))
    sns.boxplot(x='Level', y=feat, data=df, palette='Set3')
    plt.xticks([0,1,2], ['Low','Medium','High'])
    plt.title(f'{feat} by Risk Level')
    plt.savefig(f'figures/box_{feat.lower().replace(" ","_")}.png', bbox_inches='tight')

#  Pairplot of Top Features
sns.pairplot(df, vars=features, hue='Level', palette='bright')
plt.savefig('figures/pairplot_top_features.png', bbox_inches='tight')

#  Save encoded dataset summary
df.to_csv('lung_cancer_data_eda_summary.csv', index=False)
```

