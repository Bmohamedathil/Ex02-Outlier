# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

## AIM:

TO detect and remove the outliers in the given data set and save the final data.

## ALGORITHM:

### Step 1
Import the required packages(pandas,numpy,scipy)

### Step 2
Read the given csv file

### Step 3
Convert the file into a dataframe and get information of the data.

### Step 4
Remove the non numerical data columns using drop() method.

### Step 5
Detect the outliers in the data set using z scores method.

### Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

### Step 7
Check if the outliersare removed from data set using graphical methods.

### Step 8
Save the final data set into the file.

## PROGRAM:

### (1) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe
```
import pandas as pd
import seaborn as sns
df = pd.read_csv("/content/bhp.csv")
df
sns.boxplot(data=df)
sns.boxplot(x="price_per_sqft",data=df)
q1 = df['price_per_sqft'].quantile(0.35)
q3 = df['price_per_sqft'].quantile(0.65)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
high = q3+1.5*IQR
low = q1-1.5*IQR
df1 =df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]
df1
sns.boxplot(x="price_per_sqft",data=df1)
df1.shape
```
### (1) & (2) Examine price_per_sqft column and use zscore of 3 to remove outliers.
```
from scipy import stats
import numpy as np
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
df2.shape
sns.boxplot(x="price_per_sqft",data=df2)
```
### (4) (i)For the data set height_weight.csv detect weight outliers using IQR method
```
df3 = pd.read_csv("/content/height_weight.csv")
df3
sns.boxplot(x="weight",data=df3)
q1 = df3["weight"].quantile(0.25)
q3 = df3['weight'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df4 =df3[((df3['weight']>=low)&(df3['weight']<=high))]
df4
df4.shape
sns.boxplot(x="weight",data=df4)
```
### (4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
```
sns.boxplot(x="height",data=df3)
q1 = df3["height"].quantile(0.25)
q3 = df3['height'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df5 =df3[((df3['height']>=low)&(df3['height']<=high))]
df5
df5.shape
sns.boxplot(x="height",data=df5)
```

## OUTPUT:

### DATASET for bhp.csv
![image](https://user-images.githubusercontent.com/119560261/229770125-e32dc66c-5507-43a2-9be1-372f4eb66a96.png)

### bhp BOXPLOT
![image](https://user-images.githubusercontent.com/119560261/229770434-678f1372-c724-4d2a-a5db-04a97f9a3e24.png)

### DATASET BOXPLOT WITH OUTLIERS(BHP)
![image](https://user-images.githubusercontent.com/119560261/229770536-a6fffa52-590e-42e6-bb80-c8449c426e2b.png)

### DATASET WITHOUT OUTLIERS(BHP)
![image](https://user-images.githubusercontent.com/119560261/229770680-de2b39de-d751-49f7-95d2-14541e9dd651.png)
![image](https://user-images.githubusercontent.com/119560261/229770714-49accbb3-a0d6-41ad-b9ef-5c7ab4d379a4.png)

### DATASET BOXPLOT WITHOUT OUTLIERS(BHP)
![image](https://user-images.githubusercontent.com/119560261/229770809-38413194-25c5-491d-a792-0a52e5b31105.png)

### SHAPE
![image](https://user-images.githubusercontent.com/119560261/229770981-d524773e-4cce-4837-b889-3dd9a63ff126.png)

### DATASET AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)
![image](https://user-images.githubusercontent.com/119560261/229771080-8d986ce7-b5be-4fd9-826c-f8086b4fc204.png)

### SHAPE
![image](https://user-images.githubusercontent.com/119560261/229771223-9d321c20-9fa2-4356-b168-58407ad50f34.png)

### DATASET BOXPLOT AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)
![image](https://user-images.githubusercontent.com/119560261/229771303-75f1ebeb-fe89-4645-a308-641c3e35e847.png)

### DATASET FOR WEIGHT_HEIGHT_CSV
![image](https://user-images.githubusercontent.com/119560261/229843731-738e5616-6c91-4e07-b8c7-ad6560675057.png)

### DATASET BOXPLOT WITH OUTLIERS(WEIGHT_HEIGHT)
![image](https://user-images.githubusercontent.com/119560261/229843942-7e5ff627-fd27-4312-a971-309e6f3c36f0.png)

### DATASET AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)
![image](https://user-images.githubusercontent.com/119560261/229844187-d3776857-044e-49e4-b56d-056e0110f088.png)

![image](https://user-images.githubusercontent.com/119560261/229844355-e935a97d-889f-4081-8136-dc0d62a0f84e.png)

### SHAPE
![image](https://user-images.githubusercontent.com/119560261/229844552-18a9ab2f-4316-4e20-a103-1e9e026490a3.png)

### DATASET BOXPLOT AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)
![image](https://user-images.githubusercontent.com/119560261/229844730-1f7f1fdb-8eb5-4598-be02-847771bc44f9.png)

### FOR HEIGHT COLUMN WITH OUTLIERS
![image](https://user-images.githubusercontent.com/119560261/229844808-26dae7e4-4ac1-4735-8223-62e14115f852.png)

![image](https://user-images.githubusercontent.com/119560261/229846617-a61759bd-dcb5-4963-a8a1-4e5a0b76df5b.png)

![image](https://user-images.githubusercontent.com/119560261/229846647-51ffa4d6-2aa1-4cd5-af98-680a7704701a.png)

### SHAPE
![image](https://user-images.githubusercontent.com/119560261/229845028-053782dd-52c4-4161-89ad-84934d6e718a.png)

### AFTER REMOVING OUTLIERS BOXPLOT FOR HEIGHT
![image](https://user-images.githubusercontent.com/119560261/229845230-8e1a09b7-c695-4f6c-a75b-651e36ce70a3.png)

## Result:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
