# Exno:1
Data Cleaning Process

##### NAME: MARINO SARISHA T
#### REG NO: 212223240084

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
###                           Data Cleaning Process 
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![Screenshot 2025-03-04 104705](https://github.com/user-attachments/assets/6da8bbe2-9a98-4db9-b5c3-5c2ad0c0a5bd)

```
df.head()
```
![Screenshot 2025-03-04 104719](https://github.com/user-attachments/assets/8d189142-972b-4391-93e0-eef62b1dbc3f)

```
df.tail()
```
![Screenshot 2025-03-04 104729](https://github.com/user-attachments/assets/d1c6eb0a-2441-47cf-8039-d66133f5cb26)
```
df.isnull().sum()
```
![Screenshot 2025-03-04 105432](https://github.com/user-attachments/assets/b3e96148-d532-4f8a-b66d-b4dde2454ee1)

```
df.isnull().any()
```
![Screenshot 2025-03-04 105444](https://github.com/user-attachments/assets/c87bdd64-cec2-4200-a652-289721672c42)

```
df.dropna()
```
![Screenshot 2025-03-04 105456](https://github.com/user-attachments/assets/d6bf5b73-1bef-4742-98f8-07ec7f65034e)

```
df.fillna(0)
```
![Screenshot 2025-03-04 105512](https://github.com/user-attachments/assets/d676cd45-92ea-4872-9b6a-74bd46c02236)

```
df.fillna(method="ffill")
```
![Screenshot 2025-03-04 105753](https://github.com/user-attachments/assets/569528b8-0e83-470e-9484-b5b9ae432c71)

```
df.fillna(method="bfill")
```
![Screenshot 2025-03-04 105807](https://github.com/user-attachments/assets/df976a75-f0f2-4ad8-adb0-eacf1440a8a3)

```
 df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![Screenshot 2025-03-04 105820](https://github.com/user-attachments/assets/57370298-23cb-4c60-8471-c95684eb4e97)

### IQR(Inter Quartile Range)
```
ir=pd.read_csv('/content/iris.csv')
ir
```
![Screenshot 2025-03-04 111002](https://github.com/user-attachments/assets/fd15f8c9-4cfd-458f-b0e9-b52d9147b54f)

```
ir.describe()
```
![Screenshot 2025-03-04 111013](https://github.com/user-attachments/assets/ff516a9c-1733-4d8a-a167-6cf9ddf91a5b)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![Screenshot 2025-03-04 111027](https://github.com/user-attachments/assets/e85d347b-2c0b-4783-b41b-0d8cebc8b9cb)

```
 q1=ir.sepal_width.quantile(0.25)
 q3=ir.sepal_width.quantile(0.75)
 iqr=q3-q1
 print(iqr)
```

![Screenshot 2025-03-04 111037](https://github.com/user-attachments/assets/95e6e9e1-d6d5-4377-895f-308a15d51b46)

```
 rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 rid['sepal_width']
```

![Screenshot 2025-03-04 111045](https://github.com/user-attachments/assets/3147e931-83ab-45a7-a9e1-710a1536c8cb)
```
 delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 delid
 ```

![Screenshot 2025-03-04 111117](https://github.com/user-attachments/assets/f03b253c-d1b9-4c13-bda3-34634832426c)

```
 sns.boxplot(x='sepal_width',data=delid)
 ```

![Screenshot 2025-03-04 111127](https://github.com/user-attachments/assets/bfc414f9-5949-47d4-83ac-fa20d9fc0655)

###                    Z-Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
dataset=pd.read_csv("/content/heights.csv")
dataset
```

![Screenshot 2025-03-04 111929](https://github.com/user-attachments/assets/f6a794c1-1f4a-4ea8-b15c-2d8e222aeb49)

```
import scipy.stats as stats
z=np.abs(stats.zscore(dataset["height"]))
z
```

![Screenshot 2025-03-04 111938](https://github.com/user-attachments/assets/d54778d8-bd82-48ab-95b0-e0499e28b259)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
