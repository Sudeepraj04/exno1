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

NAME : SUDEEP RAJ C R

REG  : 212224040333

import pandas as pd

df=pd.read_csv("/content/SAMPLEIDS.csv")

df

<img width="1018" height="864" alt="Screenshot 2025-08-26 173240" src="https://github.com/user-attachments/assets/72461a54-1a03-4c7b-9090-7d134344d4c7" />

df.isnull().sum()

<img width="661" height="532" alt="Screenshot 2025-08-26 173431" src="https://github.com/user-attachments/assets/35d94ff1-96f9-48fb-bbcf-f24fca1c6080" />

df.head()

<img width="990" height="252" alt="Screenshot 2025-08-26 173537" src="https://github.com/user-attachments/assets/5d5b9fbc-b6a3-407d-96a9-bf92bc40ea13" />

df.tail()

<img width="1013" height="261" alt="Screenshot 2025-08-26 173638" src="https://github.com/user-attachments/assets/ea5123a0-b532-4a4f-915b-fc7a7e904cfc" />

df.isnull()

<img width="822" height="871" alt="Screenshot 2025-08-26 173736" src="https://github.com/user-attachments/assets/0c68fd14-5902-44d1-953b-f63e1752cda8" />

df.notnull()

<img width="810" height="875" alt="Screenshot 2025-08-26 173822" src="https://github.com/user-attachments/assets/92d51f64-b505-4be9-9a93-c11f25eaaf84" />

df.isnull().any()

<img width="624" height="525" alt="Screenshot 2025-08-26 174008" src="https://github.com/user-attachments/assets/9428eb48-76a0-43bd-9785-0f85ac632bcd" />

df.dropna()

<img width="1023" height="566" alt="Screenshot 2025-08-26 174055" src="https://github.com/user-attachments/assets/7e33f2ee-e5cf-4ed3-8ad1-cc3b7fc38ba1" />

df.dropna(axis=0)

<img width="1022" height="571" alt="Screenshot 2025-08-26 174143" src="https://github.com/user-attachments/assets/fc2cad3e-fcfa-43af-af20-645ffe23510c" />

df.dropna(axis=1)

<img width="654" height="875" alt="Screenshot 2025-08-26 174232" src="https://github.com/user-attachments/assets/22090099-aca0-42eb-b44e-f3eea48784fa" />

df.fillna(0)

<img width="1024" height="880" alt="Screenshot 2025-08-26 174410" src="https://github.com/user-attachments/assets/a8d2f5f3-ce06-436d-af03-4c11685019ba" />

df.fillna(method='ffill')

<img width="1013" height="864" alt="Screenshot 2025-08-26 174535" src="https://github.com/user-attachments/assets/f99763da-7727-482e-82d0-16364ccdcc96" />

df.fillna(method='bfill')

<img width="1019" height="873" alt="Screenshot 2025-08-26 174620" src="https://github.com/user-attachments/assets/3dffc0fd-2e74-4b44-bd80-7890c45fe5d3" />

df.fillna({'GENDER': 'MALE','ADDRESS':'LADAKH','M1': '100','M2': '200', 'M3': '300','M4': '400','TOTAL':'568.5', 'AVERAGE':'66678.09'})

<img width="1014" height="877" alt="Screenshot 2025-08-26 174755" src="https://github.com/user-attachments/assets/d544ecda-30e4-47b3-ad8d-af7f585ae843" />

ir=pd.read_csv('/content/iris.csv')

ir

<img width="969" height="693" alt="Screenshot 2025-08-26 174845" src="https://github.com/user-attachments/assets/c97a5b01-ad22-4c75-b7f6-0d18fbc24ab1" />

ir.describe()

<img width="945" height="681" alt="Screenshot 2025-08-26 174925" src="https://github.com/user-attachments/assets/f8a9ba22-1573-461d-b8c9-c1e7bd1e14d7" />

import seaborn as sns

sns.boxplot(x='sepal_width',data=ir)

<img width="703" height="646" alt="Screenshot 2025-08-26 175018" src="https://github.com/user-attachments/assets/5bbc5f19-06cd-4803-8ae8-661f00ea59fe" />

ir=pd.read_csv('/content/iris.csv')

q1=ir.sepal_width.quantile(0.25)

q3=ir.sepal_width.quantile(0.75)

iqr=q3-q1

print(iqr)

<img width="747" height="81" alt="Screenshot 2025-08-26 175133" src="https://github.com/user-attachments/assets/c3d66305-4bfd-4524-8404-9307def05493" />

upper = q3+1.5*iqr

lower = q1-1.5*iqr

print(upper)

print(lower)

<img width="707" height="67" alt="Screenshot 2025-08-26 175253" src="https://github.com/user-attachments/assets/d153034d-d389-4881-9303-29fd6fecbcb1" />

rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]

rid['sepal_width']

<img width="614" height="445" alt="Screenshot 2025-08-26 175353" src="https://github.com/user-attachments/assets/65fead09-09d9-480c-ba53-30e1b97e9676" />

delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]

delid

<img width="801" height="562" alt="Screenshot 2025-08-26 175439" src="https://github.com/user-attachments/assets/a579a024-8de5-4e83-a12e-151175cddd61" />

sns.boxplot(x='sepal_width',data=delid)

<img width="695" height="612" alt="Screenshot 2025-08-26 175523" src="https://github.com/user-attachments/assets/eda788ad-2be8-483c-b6d4-ad0fefb7bb9f" />

import numpy as np

import scipy.stats as stats

z=np.abs(stats.zscore(ir['sepal_width']))

z

<img width="764" height="740" alt="Screenshot 2025-08-26 175609" src="https://github.com/user-attachments/assets/7df2bfe8-9ade-4800-87cc-9662caf4addb" />

# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score
