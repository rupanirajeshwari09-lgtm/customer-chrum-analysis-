# Customer Churn Analysis Project

# Import Libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load Dataset
# Replace 'customer_churn.csv' with your dataset file
df = pd.read_csv("customer_churn.csv")

# Display First 5 Rows
print("First 5 Rows:")
print(df.head())

# Dataset Information
print("\nDataset Info:")
print(df.info())

# Check Missing Values
print("\nMissing Values:")
print(df.isnull().sum())

# Churn Distribution
plt.figure(figsize=(6,4))
sns.countplot(x='Churn', data=df)
plt.title("Customer Churn Distribution")
plt.show()

# Monthly Charges vs Churn
plt.figure(figsize=(8,5))
sns.boxplot(x='Churn', y='MonthlyCharges', data=df)
plt.title("Monthly Charges vs Churn")
plt.show()

# Tenure vs Churn
plt.figure(figsize=(8,5))
sns.histplot(data=df, x='tenure', hue='Churn', multiple='stack')
plt.title("Tenure Distribution by Churn")
plt.show()

# Contract Type Analysis
plt.figure(figsize=(7,5))
sns.countplot(x='Contract', hue='Churn', data=df)
plt.title("Contract Type vs Churn")
plt.show()

# Correlation Heatmap
numeric_df = df.select_dtypes(include=['int64', 'float64'])

plt.figure(figsize=(10,6))
sns.heatmap(numeric_df.corr(), annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.show()

# Churn Rate
churn_rate = df['Churn'].value_counts(normalize=True) * 100

print("\nChurn Rate:")
print(churn_rate)

# Key Insights
print("\nKey Insights:")
print("- Customers with higher monthly charges are more likely to churn.")
print("- Short-term contract users show higher churn rates.")
print("- Customers with low tenure tend to leave more frequently.")
print("- Engagement and long-term contracts improve retention.")# customer-chrum-analysis-