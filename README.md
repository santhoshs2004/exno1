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
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![Screenshot 2024-08-25 142713](https://github.com/user-attachments/assets/6cb3ec9e-906c-404a-bd5e-c315cb9f9694)
```
df.head(3)
df.tail(3)
```
![Screenshot 2024-08-25 142842](https://github.com/user-attachments/assets/741cfd68-34f4-4081-8082-ace812d43e0b)
```
df.isnull().sum()
```
![Screenshot 2024-08-25 142938](https://github.com/user-attachments/assets/32e9ad57-f3cb-451d-b41c-ed224a1eaae6)
```
df.dropna(how='any').shape
```
![Screenshot 2024-08-25 143033](https://github.com/user-attachments/assets/5c5e8c1a-9ce0-4be6-9174-cf160c8aa622)
```
df.shape
```
![Screenshot 2024-08-25 143140](https://github.com/user-attachments/assets/32df084c-f32c-4813-8d3a-470f85def69e)
```
mn=df.TOTAL.mean()
mn
```
![Screenshot 2024-08-25 143235](https://github.com/user-attachments/assets/d99ee149-b9cd-4796-8b04-36c4fe6ff9b6)
```
df.TOTAL.fillna(mn,inplace=True)
df
```
![Screenshot 2024-08-25 143327](https://github.com/user-attachments/assets/9ecc8009-d7e9-49aa-8ccf-84541282c4ba)
```
df.drop_duplicates(inplace=True)
df
```
![Screenshot 2024-08-25 143435](https://github.com/user-attachments/assets/2042f677-8252-40f0-b22b-5546e0caa2db)
```
df.duplicated()
```
![Screenshot 2024-08-25 143521](https://github.com/user-attachments/assets/6e65f9cf-c048-40bb-9ba5-e7bc8283243c)
```
df['DOB']
```
![Screenshot 2024-08-25 143610](https://github.com/user-attachments/assets/04795d23-1db4-43c3-8d3d-2091594ce12f)
```
df['DOB'] = pd.to_datetime(df['DOB'], format='%Y-%m-%d',errors='coerce')
df['DOB']
```
![Screenshot 2024-08-25 143656](https://github.com/user-attachments/assets/12a11132-1b9c-4ce2-a85f-23105c87edbf)
```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![Screenshot 2024-08-25 143756](https://github.com/user-attachments/assets/0d579748-e8dc-4f83-adac-7b20e033e44c)
```
import pandas as pd
import seaborn as sns
import numpy as np
```
```
age = [1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af= pd.DataFrame(age)
af
```
![Screenshot 2024-08-25 143859](https://github.com/user-attachments/assets/92635e20-2570-4d62-ac03-441f8aaac4ca)
```
sns.boxplot(data=af)
```
![Screenshot 2024-08-25 143944](https://github.com/user-attachments/assets/590b1f90-66d3-4dbd-9d3c-c69d6db386b7)
```
sns.scatterplot(data=af)
```
![Screenshot 2024-08-25 144028](https://github.com/user-attachments/assets/53619c20-ffa2-40f8-9bbb-570bd78af7c1)
```
q1=af.quantile(0.25)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![Screenshot 2024-08-25 144108](https://github.com/user-attachments/assets/d9df5a19-ba5f-456f-ab2d-ce208e3323ed)
```
Q1 = np.quantile(af, 0.25)
Q3 = np.quantile(af, 0.75)
IQR = Q3 - Q1
IQR
```
![Screenshot 2024-08-25 144147](https://github.com/user-attachments/assets/72290d72-0bbb-4062-b37c-cc9513a30e8b)
```
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR
```
```
lower_bound
```
![Screenshot 2024-08-25 144230](https://github.com/user-attachments/assets/438f2a91-a3c8-4d8d-85d4-361f4b916839)
```
upper_bound
```
![Screenshot 2024-08-25 144313](https://github.com/user-attachments/assets/d9a1b6b0-beff-4fe6-81fe-f03411a7c7ee)
```
outliers = [x for x in age if x < lower_bound or x > upper_bound]
```
```
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/d41fcfbd-d8ce-4787-8324-6b634cdc1175)
```
af=af[((af >= lower_bound)&(af <= upper_bound))]
af
```
![Screenshot 2024-08-25 144442](https://github.com/user-attachments/assets/b9502d6f-4d9c-43e3-a95f-fab6c373f2e9)
```
af.dropna()
```
![Screenshot 2024-08-25 144559](https://github.com/user-attachments/assets/1a14c6e1-0672-460b-905a-9f164b1004a4)
```
sns.boxplot(data=af)
```
![Screenshot 2024-08-25 144643](https://github.com/user-attachments/assets/9f9011a4-49a3-4aca-9233-d4133217ce00)
```
data = [1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean = np.mean(data)
std = np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
```
![Screenshot 2024-08-25 144731](https://github.com/user-attachments/assets/cdb8a60a-6394-4b10-91e1-00b0fc0cdd82)
```
threshold = 3
outlier = []
for i in data:
  z_score = (i-mean)/std
  if np.abs(z_score) > threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)
```
![Screenshot 2024-08-25 144807](https://github.com/user-attachments/assets/a7944aec-7056-4439-91a7-fd3a8616ddce)
```
import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats
```
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![Screenshot 2024-08-25 145008](https://github.com/user-attachments/assets/15994396-c2a6-4daf-86df-6b576281ddd5)

# Result:
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
