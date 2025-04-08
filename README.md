# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/06273c00-16cf-4cbb-a8fb-51466ec6e853)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/5ca8b790-0ec3-4271-b33f-ed0971429e05)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/0bab2dd0-7658-42b3-a00d-8623b9f0fc2b)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/0aaa6325-9ac5-4026-b2f1-d1a783e3d8c5)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/be64527d-c7f4-4e5a-901e-25b009cb877b)
```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/1b1c240d-17af-4e2a-bfb9-29c82c60e634)
```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/ff314a24-4b91-4e43-b1c2-4622808ff628)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/52116da4-e2dd-47a9-bf09-82ec5dbad4dd)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/df324dba-dbbe-4434-91f1-0764bd29a4a4)
```
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/9a5d79a2-c201-4583-abc3-1f12d766634b)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/1368e355-4ce7-4a85-ad86-95f2ab6f8006)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/0b536965-0526-421a-8e8e-0e8ad50c1235)
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```
![image](https://github.com/user-attachments/assets/fa24c854-b7a4-4d54-99c6-fbbc9d1165ce)
```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/7a0fa550-a716-49ce-9a40-b9a37771e292)
```
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/c73e5dd8-2901-4e93-8563-ef0b5a8829d8)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/91649573-ab34-4482-96ff-715ae2a7e476)
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats


dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/2f972139-0efb-4a5b-bbab-be19d4c9b635)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)


iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/d1539124-5ff2-493a-8a72-96135930d8b7)
```
low = q1- 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/4c2a64ac-9d9c-4031-b9d5-802500e7e083)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/f4260ebb-ceb6-4f5c-8393-fd4973df4423)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/5f07be42-fed9-48de-ba55-b3067bea3ccc)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/bd8bfdfe-747c-40a8-9e87-1d455c8fc929)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/9e8be010-d3d9-4b24-9430-259ce1686940)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
