## Multivariate_Analysis
## ODD2023-Datascience-Ex-04
# AIM
To perform Multivariate EDA on the given data set.

# Explanation:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

# ALGORITHM:
STEP 1
Import the built libraries required to perform EDA and outlier removal.

STEP 2
Read the given csv file

STEP 3
Convert the file into a dataframe and get information of the data.

STEP 4
Return the objects containing counts of unique values using (value_counts()).

STEP 5
Plot the counts in the form of Histogram or Bar Graph.

STEP 6
Use seaborn the bar graph comparison of data can be viewed.

STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

STEP 8
Save the final data set into the file

# PROGRAM
```
import pandas as pd
from scipy import stats
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from google.colab import files
uploaded = files.upload()
```

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/e97e8468-d7f0-477e-8ae1-279f1032f344)

```
df = pd.read_csv('diabetes.csv')
df
```

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/bba7f578-49c6-447f-90e8-839ba02853be)


df.isnull().sum()

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/03ba1132-fdf4-4e95-898c-59586e9411b9)

```
q1 = df.quantile(0.25)
q3 = df.quantile(0.75)
iqr = q3 - q1
iqr
```

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/eab51529-a702-4a1e-895c-7a5db6af4a6e)


sns.boxplot(df)

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/49458b40-3f9d-4a8a-9900-4a8ad0f3cd6a)

```
plt.figure(figsize = (14,6))
sns.scatterplot(x = 'Glucose',y='BloodPressure',data = df)
```

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/2418ec6f-5222-48ea-97cd-ca4b9d8123b5)


sns.scatterplot(x = 'Glucose',y='Insulin',data = df)

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/5735e80b-9674-4034-8d67-969f2ca91acd)


sns.scatterplot(x = 'Glucose',y='DiabetesPedigreeFunction',data = df)

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/91012442-b462-4c47-9969-88e0e7e3dae3)


sns.scatterplot(x = 'Glucose',y='Age',data = df)

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/80ffb308-3556-4320-a64c-37e6ac402ea5)


sns.heatmap(df.corr(),annot = True)

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/30679705-b470-4331-8990-1b0d5f2e2e3d)

```
from google.colab import files
uploaded = files.upload()
```

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/47f32187-80d5-4ace-98aa-26d93caa54b8)

```
df = pd.read_csv('employeesal.csv')
df
```

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/62ac0ba2-5201-4a34-b954-15ec12e5d8ba)


df.isnull().sum()

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/190cce55-ec3e-464f-9634-2b77f7fac572)

```
numeric_cols = df.select_dtypes(include=[int, float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
```

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/8bdd4389-7d67-4402-b936-a2e83969b257)

```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
numeric_cols.dropna()
```
![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/93ee58fe-5e5e-483d-bad0-2d790f7d9386)


sns.boxplot(numeric_cols)

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/b09bc1fc-a50e-4731-8051-e612d22f09ab)


sns.scatterplot(x = 'Salary',y='Age',data = numeric_cols)

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/5083d2ca-c7f8-47be-a9ef-254b80e54c26)


sns.scatterplot(x = 'Experience_Years',y='Salary',data = numeric_cols)

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/c3060a31-d13b-4618-b42b-970bca557006)


sns.scatterplot(x = 'Experience_Years',y='Age',data = numeric_cols)

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/8e69f4f6-1ba0-42e6-94d3-f5eff2bd688e)


sns.heatmap(numeric_cols.corr(),annot = True)

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/ced6e032-f532-4171-89e5-732a74e9c8d8)

```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/53b4c9e8-a393-482c-8c3e-1e38a6274513)


```
df = pd.read_csv('SuperStore.csv')
df
```
![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/dc25191a-eda5-45f2-bf87-5ae1320cbc1d)


df.isnull().sum()

![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/1fa575e0-3e25-4127-baa0-1a61e74716f6)


df.dropna()
![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/cd0b1203-69ce-45f0-b8e9-d0a781766d84)


df.dtypes
![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/40dd8644-eb8e-44f2-93f0-db5c999bb654)

```
numeric_cols = df.select_dtypes(include=[int,float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
```
![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/31f276c6-c0d9-4651-a426-7a77e984296c)

```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
sns.boxplot(numeric_cols)
```
![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/469b084d-00df-49fc-a428-34c07df5d959)


sns.heatmap(numeric_cols.corr(),annot = True)
![image](https://github.com/keerthysesha/ODD2023-Datascience-Ex-04/assets/125575936/dc6e254c-541e-4365-9be1-41fda3731d85)


## RESULT
Thus we have read the given data and performed the multivariate analysis with different types of plots.
