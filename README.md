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
x=pd.read_csv("/content/Data_set.csv")
x
```
![image](https://github.com/user-attachments/assets/03c9c35e-a60b-4735-b4f0-ae1c1c14801b)

```
x.head(7)
```
![image](https://github.com/user-attachments/assets/59ae6795-433e-4122-887f-d18541b6434c)

```
x.tail(5)
```
![image](https://github.com/user-attachments/assets/696fcd74-fad1-4052-93db-9fb402c0d620)

```
x.isnull()
```
![image](https://github.com/user-attachments/assets/9ee64001-417f-43cb-9743-5c44a74ce4e9)

```
x.notnull()
```
![image](https://github.com/user-attachments/assets/41b9e847-5bbc-4b11-a5b2-f635d8fa2d7d)

```
x.fillna(5)
```
![image](https://github.com/user-attachments/assets/47294ee7-3e7a-4ad7-ab47-e4359053b329)

```
x.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/8cd44836-e3fc-4fb4-92d0-f59739292012)

```
x.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/d7b9660e-ff4f-49d5-97c5-26909ee65b69)

```
x.shape
```
![image](https://github.com/user-attachments/assets/ad37fe69-ada4-44dd-989c-28a2d7675f5f)

```
x.isnull().sum()
```
![image](https://github.com/user-attachments/assets/587677b4-25e3-4784-b64c-707e273aaf58)

```
x.isnull().any()
```
![image](https://github.com/user-attachments/assets/a36647d3-4b65-46df-96e4-fd7ee536c642)

```
x.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/539b95ac-066b-44c9-808a-8eb685c9a3e7)

```
x.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/c55dfd92-7845-413d-a6ee-2d9023d595b6)

```
import pandas as pd
x=pd.read_csv('iris.csv')
x
```
![image](https://github.com/user-attachments/assets/5195eba1-638a-4c36-a53c-c8b6187747e6)

```
x.describe()
```
![image](https://github.com/user-attachments/assets/ecda6844-de3a-489a-86c6-6b2d27ebbe23)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=x)
```
![image](https://github.com/user-attachments/assets/85ec522b-392d-4708-a2d9-b2429be2eda2)

```
c1=x.sepal_width.quantile(0.25)
c3=x.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/2f76c166-ecbc-45a3-9b2d-7caf86fdfbf7)

```
rid=x[((x.sepal_width<(c1-1.5*iq))|(x.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/5b94eaf5-dbd7-426e-8f9d-527a9b2e3dc2)

```
delid=x[~((x.sepal_width<(c1-1.5*iq))|(x.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/7bb429bf-b186-4e8e-8ddb-5459079d6a38)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/d99d6bec-f86a-4c79-bfcf-0b0bcd88fdab)


# Z SCORE

```
import pandas as pd
import scipy.stats as stats
import numpy as np
hp=pd.read_csv("/content/heights.csv")
hp
```
![image](https://github.com/user-attachments/assets/5a7a1872-8ae2-46ba-b462-701718474fe3)
```
z=np.abs(stats.zscore(hp["height"]))
z
```
![image](https://github.com/user-attachments/assets/203ab38b-e07a-4c9f-9039-b43268238c81)

```
hp1=hp[z<3]
hp1
```
![image](https://github.com/user-attachments/assets/dda80ae9-7c99-4754-85b7-114d80ca960d)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```

![image](https://github.com/user-attachments/assets/0d2ab6c9-60d6-48b2-b595-501a9f1e9a9e)
```

low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/88be17ce-6b37-481e-8c26-9c4fc7761df1)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/28c26dad-d7d1-4eff-a6db-7c997dac06ee)
```
df1 = df[((df['height'] >=low)& (df['height']<=high))]
df1
```
![image](https://github.com/user-attachments/assets/03523138-fe73-4062-8b92-ceb873b04732)


# Result

Hence the data was cleaned and the outliers are detected.

