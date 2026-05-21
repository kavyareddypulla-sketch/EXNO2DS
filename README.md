# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
data = pd.read_csv("C:/Users/acer/Downloads/titanic_dataset.csv")
 
print("\nDataset Loaded Successfully\n")

```

<img width="306" height="75" alt="image" src="https://github.com/user-attachments/assets/02bc9bc3-3cac-4f60-bf1d-c9e5a1c474a8" />

```
data.head()
```

<img width="815" height="185" alt="image" src="https://github.com/user-attachments/assets/d4b8d680-74b4-4d76-ab29-9cc51fbdf19d" />

```
print("\nDataset Info:\n")
data.info()
```
<img width="337" height="375" alt="image" src="https://github.com/user-attachments/assets/2ba4bab6-bba8-49b0-ad46-ba21eb2149cd" />
```
print("\nStatistical Summary:\n")
data.describe()
```
<img width="640" height="271" alt="image" src="https://github.com/user-attachments/assets/bd667225-01ba-4735-9b7e-8f9a9bb1516f" />
```
for column in data.columns:
if data[column].dtype == 'object':
data[column] = data[column].fillna(data[column].mode()[0])
else:
data[column] = pd.to_numeric(data[column], errors='coerce')
data[column] = data[column].fillna(data[column].median())
print("Missing Values Handled Successfully")
```
<img width="311" height="25" alt="image" src="https://github.com/user-attachments/assets/a82bbd50-f963-4c28-8673-f033371698b0" />
```
plt.figure(figsize=(6,4))
sns.boxplot(x=data["Age"])
plt.title("Boxplot - Age")
plt.show()
```
<img width="470" height="371" alt="image" src="https://github.com/user-attachments/assets/2dbfffdd-15d5-4db5-b855-1704f9c4ac6d" />
```
def remove_outliers_iqr(df, column):
Q1 = df[column].quantile(0.25)
Q3 = df[column].quantile(0.75)
IQR = Q3 - Q1
lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR
return df[
        (df[column] >= lower) &
        (df[column] <= upper)
    ]
```
```
print("Shape after removing Age outliers:")
print(remove_outliers_iqr(data, "Age").shape)
print("\nShape after removing Fare outliers:")
print(remove_outliers_iqr(data, "Fare").shape)
print("\nOutliers Removed Using IQR Method")
```
<img width="326" height="140" alt="image" src="https://github.com/user-attachments/assets/6213a87a-ef35-45d4-985e-636adda9e88a" />
```

plt.figure(figsize=(6,4))
sns.countplot(x="Survived", data=data)
plt.title("Countplot - Survival Distribution")
plt.show()
```
<img width="455" height="334" alt="image" src="https://github.com/user-attachments/assets/0299893b-8f5a-42ca-8298-edb68d485c60" />
```
plt.figure(figsize=(6,4))
sns.countplot(x="SibSp", data=data)
plt.title("Countplot - Sibling/Spouse Distribution")
plt.show()
```
<img width="534" height="358" alt="image" src="https://github.com/user-attachments/assets/8ca5792c-0f3e-4446-84e2-c75f87d45a51" />
```
plt.figure(figsize=(6,4))
sns.countplot(x="Pclass", data=data)
plt.title("Countplot - Passenger Class Distribution")
plt.show()
```
<img width="511" height="367" alt="image" src="https://github.com/user-attachments/assets/e560ef25-0294-436a-845a-20ca552b7bbd" />
```

sns.displot(data["Age"], kde=True, height=4, aspect=1.5)
plt.title("Displot - Age Distribution")
plt.show()
```
<img width="513" height="351" alt="image" src="https://github.com/user-attachments/assets/c43cdf31-eda7-4205-98cc-5398e00e02a4" />
```
sns.displot(data["Fare"], kde=True, height=4, aspect=1.5)
plt.title("Displot - Fare Distribution")
plt.show()
```
<img width="538" height="341" alt="image" src="https://github.com/user-attachments/assets/282c3be1-2979-4812-beb5-9bfa3f39485d" />
```


# RESULT
        <<INCLUDE YOUR RESULT HERE>>
