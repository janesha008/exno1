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
#Read the Given Data
df2=pd.read_csv("heights.csv")
#Get the Information about the data
print(df2)
print(df2.info())
print(df2.describe())
#Remove null values from the data
df2.dropna(inplace=True)
#Save the Clean data to the file
df2.to_csv("cleaned_data.csv")
#Remove Outliers Using IQR
sns.boxplot(data=df2['height'])
plt.show()
q1=df2['height'].quantile(0.25)
q2=df2['height'].quantile(0.5)
q3=df2['height'].quantile(0.75)
iqr=q3-q1
print(iqr)
lb=q1-1.5*iqr
up=q3+1.5*iqr
print(lb)
print(up)
l=df2['height'].tolist()
outl=[x for x in l if x<lb or x>up]
print("Outliers:",outl)
df2=df2[(df2['height']>lb)&(df2['height']<up)]
sns.boxplot(data=df2['height'])
plt.show()
```

            <<include your coding and its corressponding output screen shots here>>
# Result
          <<include your Result here>>
