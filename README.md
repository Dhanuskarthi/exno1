```
NAME-Dhanus karthi S
REG NO-24005701
```
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
exp=pd.read_csv("/content/SAMPLEIDS.csv")
exp.head()
```
![Screenshot 2025-03-05 231802](https://github.com/user-attachments/assets/32ec67df-be96-4881-aa87-637a202654da)
```
exp.head(5)
```
![image](https://github.com/user-attachments/assets/ebaddd51-3af8-4699-85e3-345eed65da01)
```
exp.tail(5)
```
![Screenshot 2025-03-05 232858](https://github.com/user-attachments/assets/37c4a53a-8821-466f-8a82-620d9936f999)
```
exp.isnull().sum()
```
![image](https://github.com/user-attachments/assets/bea9340c-dddb-44c9-be70-397928c134ea)
```
exp.isnull().any()
```
![image](https://github.com/user-attachments/assets/452dbd39-8d7d-480b-992e-6bd64535ef0b)
```
exp.dropna(axis=1)
```
![Screenshot 2025-03-05 233400](https://github.com/user-attachments/assets/055f6ada-99df-492b-843b-ec68182dbba2)

![image](https://github.com/user-attachments/assets/8201b377-a050-4454-84e6-bba700446ff6)
```
exp.fillna(50)
```
![image](https://github.com/user-attachments/assets/532c6840-d88e-4b5c-b464-0a578012bb2a)

![image](https://github.com/user-attachments/assets/2f5f314a-81f6-4f92-aad3-dcc84a613390)
```
exp.fillna(method='ffill')
```
![Screenshot 2025-03-05 234026](https://github.com/user-attachments/assets/01d2c157-9569-495b-a231-1fcbe0090a76)

![image](https://github.com/user-attachments/assets/4e5756b1-93cd-43c6-9242-f1f2ec759114)
```
exp.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/1746c3ad-aa3c-4deb-922d-909c20bf0934)
```
lab.fillna({'GENDER':'MALE','NAME':'PRAKASH','ADDRESS':'POONAMALEE','M1':'50','M2':'89','M3':'75','M4':'82','TOTAL':'896','AVG':'89.00000'})
```
![image](https://github.com/user-attachments/assets/00098235-4740-42d6-b274-76ea159edf63)
```
exp=pd.read_csv("/content/iris.csv")
exp
```
![image](https://github.com/user-attachments/assets/419d48f7-2780-41c1-9b23-68a23e33409c)
```
lab.describe()
```
![Screenshot 2025-03-05 235617](https://github.com/user-attachments/assets/88137c67-9ec4-4588-a061-7701379ee5c6)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=lab)
```
![image](https://github.com/user-attachments/assets/1831b014-f79e-4018-9bb5-dd63980abf77)
```
q1=lab.sepal_width.quantile(0.25)
q3=lab.sepal_width.quantile(0.75)
iq=q3-q1
print(iq)
```
![image](https://github.com/user-attachments/assets/cc06124b-b5a7-4b0c-a4e6-cf0e9a314b10)
```
rid=lab[((lab.sepal_width<(q1-1.5*iq))|(lab.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/9eb23533-eb45-4f7c-9900-f7cd3ae73010)
```
depo=lab[~((lab.sepal_width<(q1-1.5*iq))|(lab.sepal_width>(q3+1.5*iq)))]
depo
```
![Screenshot 2025-03-06 000143](https://github.com/user-attachments/assets/2567f354-3f43-4186-8ec2-82c13876f6e0)
```
sns.boxplot(x='sepal_width',data=depo)
```
![image](https://github.com/user-attachments/assets/7bd438cb-6ec1-4064-8139-b02fddcf7d46)
```
import numpy as np
import scipy.stats as stats
z = np.abs(stats.zscore(lab.sepal_width))
z
```
![image](https://github.com/user-attachments/assets/b0f4c4ed-219c-4da8-8b25-26f2ce74f629)
```
p=lab[z<2]
p
```
![Screenshot 2025-03-06 000730](https://github.com/user-attachments/assets/096994eb-b370-4213-a448-3bd8c1699b51)


# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
