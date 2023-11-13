# Ex02-Outlier Detection and Removal
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height.csv find the following

(i) Using IQR, detect height outliers and print them

## CODE:

```
### Developed by: Sabitha P
### Register number:212222040137
```
### bhp.csv:
```python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('bhp.csv')
df.info()
print(df.describe())
df.head()
#BEFORE REMOVING OUTLIER
sns.boxplot(y='price_per_sqft',data=df)

# PERFORMING IQR METHOD
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
IQR=q3-q1
low=q1-1.5*IQR
high=q3+1.5*IQR
new=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]

#AFTER REMOVING OUTLIER using IQR method
sns.boxplot(y='price_per_sqft',data=new)

# PERFORMING Zscore METHOD
z=np.abs(stats.zscore(df['price_per_sqft']))
new2=df[(z<3)]

#AFTER REMOVING OUTLIER using Zscore method
sns.boxplot(y="price_per_sqft",data=new2)
```
### height.csv:
```python
import pandas as pd
import seaborn as sns
import numpy as np

df=pd.read_csv("/content/heights.csv")
df
#BEFORE REMOVING OUTLIER in HEIGHT
sns.boxplot(data=df)

sns.scatterplot(data=df)

max=df['height'].quantile(0.75)
min=df['height'].quantile(0.25)

max

min

iqr

df=df[((df['height']>=min)&(df['height']<=max))]
df

iqr=max-min
low=min-1.5*iqr
high=max+1.5*iqr

low

high
#AFTER REMOVING OUTLIER in HEIGHT
sns.boxplot(data=df)

sns.scatterplot(data=df)
```

## OUTPUT:
### bhp.csv:
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/6684ba43-7640-4bcc-b847-ecd1efd89a91)
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/0cb19485-2662-431a-b896-7c0e74e180ee)
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/3a9ab1fb-60ed-4166-83a5-62e8bdd3c8a6)
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/77d0fe42-0318-4895-b2c9-914a7ed2f63d)
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/f9011279-0cc6-48a4-8602-23309f5819e4)

### height.csv
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/280eb03a-3b59-48bf-88ca-a86d0cbfffab)
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/0ee4078a-2fce-4f73-83c8-83c371b28664)
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/08c2ffca-b1f8-4689-bcc2-641149a4cb5d)
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/8b61ae05-285f-4679-912f-b24bb857badc)
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/4c8bb0d8-4c83-42c8-9f86-68b27fa1a8d8)
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/da0fd93a-bc44-4d2a-a209-8ab0b9d7e003)
![image](https://github.com/sabithapaulraj/ODD2023---Datascience---Ex-02/assets/118343379/10d0cf03-28af-452f-a14a-00143cded75f)

# RESULT:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.
