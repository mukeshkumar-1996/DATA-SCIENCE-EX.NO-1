#EX.NO:1
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

    import pandas as pd
    data=pd.read_csv("Data_set.csv")
    df=pd.DataFrame(data)
    print(df)
    
![516605032-31b73eb9-a220-43bb-89d1-3aa5e3867a9d](https://github.com/user-attachments/assets/21c47f9b-ece7-4137-90ac-1aa29709eb65)
   
    df.info()
    df.describe()
    
![516605740-d6be4298-987c-462a-9aad-84b3f3611f8d](https://github.com/user-attachments/assets/12d47072-4e51-4b21-b315-bd501c28a927)

    df.isna().sum()
![516606283-6e15a867-09ce-466b-9c24-0a7c8010e4ff](https://github.com/user-attachments/assets/2885c3ec-3473-4152-8251-0b1316b74684)

    df.fillna(0)
<img width="1276" height="861" alt="519955315-6363a95c-9621-4cd3-8567-97fd971ebe94" src="https://github.com/user-attachments/assets/fa8b2498-9c87-4b24-96b4-737c16ff44fe" />

    df.fillna(method="ffill

<img width="1353" height="865" alt="519955483-cfa963a2-5a45-4ed4-80db-4acc1a259223" src="https://github.com/user-attachments/assets/7ba9fda5-ed33-4c35-a473-f44bda2369f5" />

    f.fillna(method="bfill")
<img width="1306" height="857" alt="519955585-024931da-bcb0-4b10-a7d4-053427b597e6" src="https://github.com/user-attachments/assets/604b8a7e-d4d3-4f62-9abc-42870b037dbc" />

    df.dropna(axis=0,inplace=True)df["TOTAL"].fillna(df["TOTAL"].mean())
<img width="1323" height="849" alt="519955807-3f56bde5-8764-459c-836c-90783d338568" src="https://github.com/user-attachments/assets/8625215b-70b1-49d1-bec7-adcd3f9f4674" />

![516607060-03954226-f6a0-4404-8515-c60213200d72](https://github.com/user-attachments/assets/2108c920-31db-4f08-934f-2a368ba73464)

    df.to_csv('newdata1.csv', index-False)
    data1=pd.read_csv("newdata1.csv")
    df=pd.DataFrame(data1)
    df
    
![516607666-12ccbb30-366a-41eb-9855-3e606bcd1cbd](https://github.com/user-attachments/assets/c8824d57-c3d2-428c-a681-e933b93c6c5f)

   
    df.["num_episodes")
![516608086-136239e4-7f01-4d4d-9836-d61a3862cda8](https://github.com/user-attachments/assets/30d4321f-0ccd-4127-86db-6a17ea6e6fe3)
   
    import seaborn as sns
    import numpy as np
    sns.boxplot(data=df["num_episodes"])

![516609054-a52254ee-d072-4734-83a3-e7be0bca72f6](https://github.com/user-attachments/assets/25d4bbc9-074a-4fb9-85bf-9722da537d96)

    sns.scatterplot(data=df["num_episodes"])
    
![516609887-163fa1bd-cff0-4506-8ba3-dd0542d600ad](https://github.com/user-attachments/assets/e9b9c54d-6bd7-4eef-80d4-360f627f9e49)

    q1=df["num_episodes"].quantile(0.25)
    q3=df["num_episodes"].quantile(0.75)
    IQR=q3-q1
    up_bound=q3+(1.5*IQR)
    low_bound=q1-(1.5*IQR)
    outliers=[x for x in df["num_episodes"] if x<low_bound or x>up_bound]
    print("q1:",q1)
    print("q3:",q3)
    print("IQR:",IQR)
    print("upper bound:",up_bound," and lower bound:",low_bound)
    print("Outliers:",outliers)   

![516611321-667ab2ea-e435-4d39-8f45-ecafe7111874](https://github.com/user-attachments/assets/d7811974-bbd7-46ab-b72d-f84af06b499a)

    mean=np.mean(df["num_episodes"])
    std=np.std(df["num_episodes"])
    threshold=3
    outliers=[]
    for i in df["num_episodes"]:
    z=(i-mean)/std
    if np.abs(z)>threshold:
    outliers.append(i)
    print("Mean:",mean)
    print("Standard deviation:",std)
    print("Outliers:",outliers)

![516612125-ec935f5f-2115-457d-ae10-fdba4e1bcd0e](https://github.com/user-attachments/assets/56304cfe-9bff-4c71-af67-0c13a1d5fd6b)

   index_to_delete = df[df["num_episodes"] ==50].index df.drop(index_to_delete, inplace=True)
   
![516613375-39e962a4-5d21-4504-8f5f-569b5938310b](https://github.com/user-attachments/assets/fc84d55b-f99d-4935-b5c0-7ed8ebace57b)

   sns.scatterplot(data=df["num_episodes"])
   
![516613855-10ed2296-6c69-483d-966c-d2826c80f7b4](https://github.com/user-attachments/assets/9bef157a-cd40-4bd8-9366-93540d81f54d)
![516614168-e01fae05-050b-499f-8a9a-ccaa252f0383](https://github.com/user-attachments/assets/e5a432b7-c9a8-4d2d-b7b4-63d3d19437b8)


# Result
                Thus the program to read the given data and perform data cleaning and save the cleaned data to a file and removing outliers using IQR
