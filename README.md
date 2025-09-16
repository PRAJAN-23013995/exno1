PRAJAN P - 212223240121
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

# Coding and Output:
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="1060" height="758" alt="image" src="https://github.com/user-attachments/assets/ae6807d6-65f1-4a6c-93d0-076a80f8be3a" />

```
df.head()
```
<img width="1092" height="257" alt="image" src="https://github.com/user-attachments/assets/545d3bce-116d-4871-adc4-7b23dee80d3f" />

```
df.tail()
```
<img width="1026" height="215" alt="image" src="https://github.com/user-attachments/assets/522834d4-5d31-437b-b096-c1663036e04b" />

```
df.isnull()
```
<img width="897" height="758" alt="image" src="https://github.com/user-attachments/assets/2ae19ac3-f290-4e0f-8b46-2f3bfcea568b" />

```
df.isnull().sum()
```
<img width="262" height="426" alt="image" src="https://github.com/user-attachments/assets/83c27323-ee75-4566-a988-80c602d78102" />

```
df.isnull().any()
```
<img width="230" height="420" alt="image" src="https://github.com/user-attachments/assets/8d2703db-387b-43e4-adba-00efd3908d7b" />

```
df.dropna(axis=0)
```
<img width="1042" height="562" alt="image" src="https://github.com/user-attachments/assets/b9a3c6c0-b632-4c28-b22a-b71ff420be61" />

```
df.dropna(axis=1)
```
<img width="382" height="796" alt="image" src="https://github.com/user-attachments/assets/2fd3163b-e81a-4424-8f70-66a0811a7565" />

```
df.fillna(2)
```
<img width="1027" height="750" alt="image" src="https://github.com/user-attachments/assets/7ca75738-621b-4365-8973-ae62f69c019e" />

```
df.fillna(method = 'ffill')
```
<img width="1047" height="820" alt="image" src="https://github.com/user-attachments/assets/78a5b26a-c50c-47c6-96ce-497dc8c0b88f" />

```
df.fillna(method = 'bfill')
```
<img width="1057" height="851" alt="image" src="https://github.com/user-attachments/assets/f123736a-9d56-4ea7-9d1d-99fe42d92c2a" />

```
df.fillna({'GENDER':'MALE','NAME':'DONGLY','ADDRESS':'ARNI','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
<img width="1057" height="783" alt="image" src="https://github.com/user-attachments/assets/983c766a-9dd7-4e34-b14c-0aa7fb555ed6" />

```
ir=pd.read_csv('iris.csv')
ir
```
<img width="680" height="436" alt="image" src="https://github.com/user-attachments/assets/359b9ace-9df8-4a65-be02-d3518cd35ace" />

```
ir.describe()
```
<img width="591" height="387" alt="image" src="https://github.com/user-attachments/assets/2aa5ced5-59d1-49bd-af93-5479e3b0fc41" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="528" height="433" alt="e1572101-c079-4597-8fff-14bb375d3a28" src="https://github.com/user-attachments/assets/64c026ca-4e70-4d2d-ad26-05fa421a3d03" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="195" height="65" alt="image" src="https://github.com/user-attachments/assets/8bc8ee25-1850-4f62-a31f-19a488000ef6" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="461" height="155" alt="image" src="https://github.com/user-attachments/assets/5b0dfe56-ed24-403b-9ab3-92ea1c650642" />

```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
<img width="642" height="427" alt="image" src="https://github.com/user-attachments/assets/6590fd86-b14a-4c01-bf06-09c01440f2bb" />

```
sns.boxplot(x='sepal_width',data=delid)
```
<img width="520" height="433" alt="3622832f-31b0-4efb-9f65-3bbcf4c39c62" src="https://github.com/user-attachments/assets/f978af61-11f3-403f-a062-35ec545f7506" />

```
import numpy as np
import scipy.stats as stats
z = np.abs(stats.zscore(delid['sepal_width']))
z
```
<img width="486" height="313" alt="image" src="https://github.com/user-attachments/assets/97f6ee7c-00ca-4178-9081-c944d8296968" />

```
df =delid[z<3]
df
```
<img width="653" height="433" alt="image" src="https://github.com/user-attachments/assets/28cea338-4e55-4e15-afe2-fbbb6e6da6f9" />

## Result
Thus the functions are executed successfully !!!
