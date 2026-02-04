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
df2=pd.read_csv("heights.csv")
print(df2)
```
<img width="208" height="512" alt="image" src="https://github.com/user-attachments/assets/bd165ebc-a91a-41f8-8323-1b7e318be0eb" />

```
df2.dropna(inplace=True)
df2.to_csv("cleaned_data.csv")
```
```
sns.boxplot(data=df2['height'])
plt.show()
```
<img width="534" height="413" alt="image" src="https://github.com/user-attachments/assets/bea8ca41-d924-4e17-957a-24777a36134e" />

```
q1=df2['height'].quantile(0.25)
q2=df2['height'].quantile(0.5)
q3=df2['height'].quantile(0.75)
iqr=q3-q1
print('IQR:',iqr)
lb=q1-1.5*iqr
up=q3+1.5*iqr
print('lb',lb)
print('up',up)
l=df2['height'].tolist()
outl=[x for x in l if x<lb or x>up]
print("Outliers:",outl)
```

<img width="250" height="102" alt="image" src="https://github.com/user-attachments/assets/363428a4-2f52-4489-9d69-6e67c9e1891f" />

```
df2=df2[(df2['height']>lb)&(df2['height']<up)]
sns.boxplot(data=df2['height'])
plt.show()
```

<img width="547" height="413" alt="image" src="https://github.com/user-attachments/assets/98c9aced-2cfa-4bba-a47c-c83dad249d25" />

```
df2_z=pd.DataFrame(l,columns=['height'])
z_score=np.abs(stats.zscore(df2_z))
z_score
```

<img width="160" height="467" alt="image" src="https://github.com/user-attachments/assets/38e39f3e-bc72-4c78-b7cd-74cc736f324a" />

```
outl_z= df2_z[z_score>threshold]
cleaned_data=df2_z[z_score<=threshold]
print(cleaned_data)
```

<img width="120" height="436" alt="image" src="https://github.com/user-attachments/assets/fbe4598c-5d46-472c-b2da-71e1df659542" />

# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method. 
