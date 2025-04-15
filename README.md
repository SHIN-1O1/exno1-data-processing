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
Pyhton codes: 

            import pandas as pd import numpy as np df=pd.read_csv("/content/SAMPLEIDS.csv") df
            df.shape
            df.describe()
            df.info()
            df.head(10)
            df.tail(5)
            df.isna()
            df.isna().sum()
            df.dropna(how="any").shape
            x=df.dropna(how="any") x
            mn=df.TOTAL.mean() mn
            df.TOTAL.fillna(mn,inplace=True) df
            df.isnull().sum()
            df.M1.fillna(method="ffill",inplace=True) df
            df.isna().sum()
            df.M2.fillna(method='ffill',inplace=True) df
            df.isna().sum()
            df.M3.fillna(method='ffill',inplace=True) df
            df.isna().sum()
            df.duplicated()
            df.drop_duplicates(inplace=True) df
            df.duplicated()
            df['DOB']
            import seaborn as sns sns.heatmap(df.isnull(),yticklabels=False,annot=True)
            df.dropna(inplace=True) sns.heatmap(df.isnull(),yticklabels=False,annot=True)

"""OutLiers Detection and removal Using IQR"""

            age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94] df=pd.DataFrame(age) df
            sns.boxplot(data=df)
            sns.scatterplot(data=df)
            q1=df.quantile(0.25) q3=df.quantile(0.75) iqr=q3-q1 iqr
            Q1=np.percentile(df,25) Q3=np.percentile(df,75) IQR=Q3-Q1 IQR
            lower_bound=Q1-1.5IQR upper_bound=Q3+1.5IQR lower_bound
            upper_bound
            outliers=[x for x in age if x<lower_bound or x>upper_bound] print("Q1:",Q1) print("Q3:",Q3) print("IQR:",IQR) print("Lower Bound:",lower_bound) print("Upper Bound:",upper_bound) print("Outliers:",outliers)
            df=df[((df>=lower_bound)&(df<=upper_bound))] df
            df=df.dropna() df
            sns.boxplot(data=df)
            sns.scatterplot(data=df)
            data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2] mean=np.mean(data) std=np.std(data) print('mean of the dataset is',mean) print('std.deviation is',std)
            threshold=3 outlier=[] for i in data: z=(i-mean)/std if z>threshold: outlier.append(i) print('outlier in dataset is',outlier);
            from scipy import stats data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63, 66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]} df=pd.DataFrame(data) df
            z=np.abs(stats.zscore(df)) print(df[z['weight']>3])
            slope: -1.1064189189189189
            Y-intercept: 14.08108108108108
            Predicted values: [ 5.22972973 11.86824324  1.91047297  7.44256757  8.54898649  9.65540541 0.80405405  4.12331081  7.44256757 12.97466216]
## Screenshots of the codes with Outputs:

![image](https://github.com/user-attachments/assets/2ab3a216-6f05-4686-a7ed-6ebfe32f5cf7)

![image](https://github.com/user-attachments/assets/83733944-aafa-4f40-9614-018e94b530de)

![image](https://github.com/user-attachments/assets/d6d9d981-bd8f-4a38-a752-c54610c95b7c)

![image](https://github.com/user-attachments/assets/97d6ef24-3e24-4a99-b37b-2bd42624621f)

![image](https://github.com/user-attachments/assets/4f0e66b6-58dc-4b33-bf27-d0cd3dbc4dd4)

![image](https://github.com/user-attachments/assets/189a5cb8-a4f5-45d5-bb1b-cc415fab7ba0)

![image](https://github.com/user-attachments/assets/ae050ff5-c3c5-49d4-88bf-9fe389d602a0)

![image](https://github.com/user-attachments/assets/ab1339c1-8b7c-4b57-bf24-6c064e96166c)

![image](https://github.com/user-attachments/assets/d42d0f22-9344-41de-9ca6-8f5dce0dd6c3)

![image](https://github.com/user-attachments/assets/79fcb10f-edd7-4ce8-b364-7860a164e329)

![image](https://github.com/user-attachments/assets/ab331983-b954-46ca-a9ab-b481f470ccd7)

![image](https://github.com/user-attachments/assets/934c0613-fed7-403a-842a-0c0b96f324ca)

![image](https://github.com/user-attachments/assets/9ac5b543-cab0-4bb7-9bef-662e7aaa0ba2)

![image](https://github.com/user-attachments/assets/5bdd5840-e4b3-45d1-9043-c6296193263b)

![image](https://github.com/user-attachments/assets/cdc3c8a3-1f0a-4a28-956e-d6f90994ccf9)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score
