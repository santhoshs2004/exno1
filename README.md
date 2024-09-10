## Exno:1
### Data Cleaning Process
### AIM
To read the given data and perform data cleaning and save the cleaned data to a file.
### Explanation
##### Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.
### Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

### Coding and Output:
#### Data cleaning process:

```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```

![image](https://github.com/user-attachments/assets/93401c95-bb10-41fd-879e-4969a5f7ee4f)

```
df.head()
```

![image](https://github.com/user-attachments/assets/1a447fe0-a978-4c92-87b7-a98c6c1d7d84)

```
df.tail(5)
```

![image](https://github.com/user-attachments/assets/5cda549c-de93-45b7-ba82-b7f5f5e686af)

```
df.isnull()
```

![image](https://github.com/user-attachments/assets/77005ab8-affc-49a0-94bb-e85103cdba08)

```
df.notnull()
```

![image](https://github.com/user-attachments/assets/01585993-3e36-4f64-b635-bec23b09a13a)

```
df.dropna(axis=0)
```

![image](https://github.com/user-attachments/assets/2f67b824-36bd-4f8b-9b45-e101d99f273c)

```
df.dropna(axis=1)
```

![image](https://github.com/user-attachments/assets/6a6d8a81-5109-4079-aa55-9de0774f7a66)

```
df.fillna(0)
```

![image](https://github.com/user-attachments/assets/366417b2-0fd6-4a00-b2d8-99bdb7c62661)

```
print(df.shape)
```

![image](https://github.com/user-attachments/assets/bef54714-c7f9-48a6-89f7-71feb365d436)

### IQR:

```
import pandas as pd
import seaborn as sns
ir=pd.read_csv('/content/iris.csv')
ir
```

![359434303-5f92ae1d-167b-4412-8e99-312c878199d7](https://github.com/user-attachments/assets/41fc23ee-ac24-4c9d-b9cf-ce683d86d862)

```
ir.describe()
```

![image](https://github.com/user-attachments/assets/c0540501-73de-4ecc-9d1f-ead4961372cd)

```
sns.boxplot(x='sepal_width',data=ir)
```

![image](https://github.com/user-attachments/assets/452705a2-1d41-45ed-9897-1fd921770faa)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```

![image](https://github.com/user-attachments/assets/1c9ec84f-e759-4185-a6a8-c6d9ad763747)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

![image](https://github.com/user-attachments/assets/0e6ce3cc-3d98-44bb-b68d-5fb8d1ac666b)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```

![image](https://github.com/user-attachments/assets/6a133748-77c2-4dca-8f77-8b278b5d4505)

```
sns.boxplot(x='sepal_width',data=delid)
```

![image](https://github.com/user-attachments/assets/064fc55c-0136-4e32-af0f-f47b2d6e9f86)

### Z SQUARE

```
import matplotlib.pyplot as plt
import pandas as pd
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```

![image](https://github.com/user-attachments/assets/91aaebae-9883-4d8b-8973-ca9062d26978)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```

![image](https://github.com/user-attachments/assets/0bdd0dd4-c5ae-4427-b52a-80d79f3207f7)

```
low = q1 - 1.5*iqr
low
```

![image](https://github.com/user-attachments/assets/5ad613c6-415a-4fd5-9a6b-56d97e1ca47a)

```
high = q3 + 1.5*iqr
high
```

![image](https://github.com/user-attachments/assets/d9389aa7-e169-42df-aed4-037dd72cb08d)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![image](https://github.com/user-attachments/assets/8b3080a2-d1b8-4a38-98d1-1f141bdacbd4)

```
z = np.abs(stats.zscore(df['height']))
z
```

![image](https://github.com/user-attachments/assets/20e5a03a-23e3-448b-bbb7-11f5fce6bbad)

```
 df1 = df[z<3]
 df1
```

![image](https://github.com/user-attachments/assets/b0dc52f3-9a89-4a0d-b598-9ece1cda054b)

### Result
Thus the Data Cleaning Process and Detecting and Removal of Outliers is executed successfully.     
