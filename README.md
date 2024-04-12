## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
  ```
     import pandas as pd
     df=pd.read_csv("/content/Encoding Data.csv")
     df
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/08159a16-5072-4902-949e-011407ca138c)
```
  from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
  pm=['Hot','Warm','Cold']
  e1=OrdinalEncoder(categories=[pm])
  e1.fit_transform(df[["ord_2"]])
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/b9646ad0-c411-4ce8-adc6-eb0b5dc637db)
```
    df['bo2']=e1.fit_transform(df[["ord_2"]])
    df
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/56cc0310-7165-4f61-9218-835ab2692659)
```
    le=LabelEncoder()
    dfc=df.copy()
    dfc['ord_2']=le.fit_transform(dfc['ord_2'])
    dfc
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/d1faf1c0-405b-480b-9035-d3e088455dd5)
```
  from sklearn.preprocessing import OneHotEncoder
  ohe=OneHotEncoder(sparse=False)
  df2=df.copy()
  enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
  df2=pd.concat([df2,enc],axis=1)
  df2
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/cff58462-c9eb-49be-9d95-c229291bdb08)
```
  pd.get_dummies(df2,columns=["nom_0"])
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/84474ce4-5d49-425d-bffe-37001baa86c0)
```
  pip install --upgrade category_encoders
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/a8b9ddd6-2a48-4e2e-b33b-64857d78d4a9)
```
    from category_encoders import BinaryEncoder
    df=pd.read_csv("/content/data.csv")
    be=BinaryEncoder()
    nd=be.fit_transform(df['Ord_2'])
    fb=pd.concat([df,nd],axis=1)
    dfb1=df.copy()
    dfb
 
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/56e304af-9663-4c4d-acbf-98a0cd0801fc)
```
   from category_encoders import TargetEncoder
   te=TargetEncoder()
   cc=df.copy()
   new=te.fit_transform(X=cc["City"],y=cc["Target"])
   cc=pd.concat([cc,new],axis=1)
   cc
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/597e0747-510c-4fc4-9007-4ababc8d5ca4)
```
    import pandas as pd
    from scipy import stats
    import numpy as np
    df=pd.read_csv("/content/Data_to_Transform.csv")
    df
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/f1e5bbe6-f3e8-4f9c-a1e9-f1ebb228fb1f)
```
    df.skew()
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/58cc61e7-f65f-4c28-b0cb-d172fc856d57)
```
    np.log(df["Highly Positive Skew"])
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/94561f69-eb9a-483b-95ef-c7e899d4c051)
```
    np.reciprocal(df["Moderate Positive Skew"])
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/166ac97d-4946-4058-92b7-6376e3bbd3e8)
```
    np.sqrt(df["Highly Positive Skew"])
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/4308b16d-1e0f-4f19-8004-f48fe0ffab17)
```
    np.square(df["Highly Positive Skew"])
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/394f23c9-98f1-4b09-b1e4-cd93776b9aad)
```
   df["Highly Positive Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
   df
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/0f716938-b938-4231-8cc7-40762f75e73c)
```
    df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])
    df.skew()
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/6ce1d000-f587-4fc5-9741-5c59d4c54f2b)
```
    df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
    df.skew()

```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/f1204c70-da2b-4616-98e5-63a4d0ccb856)
```
   import matplotlib.pyplot as plt
   import seaborn as sns
   import statsmodels.api as sm
   import scipy.stats as stats

   sm.qqplot(df["Moderate Negative Skew"],line='45')

   plt.show()
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/3b729a7e-60fb-4b51-a438-fe7a31325f73)

```
    sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/600538f2-697e-47e9-9d56-09977931e28b)
```
    from sklearn.preprocessing import QuantileTransformer
    qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

    df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])

    sm.qqplot(df["Moderate Negative Skew"],line='45')
    plt.show()
```
![image](https://github.com/Vanitha-SM/EXNO-3-DS/assets/119557985/36aa6277-64af-40a4-8ce8-5043b817d802)

# RESULT:
      Hence performing Feature Encoding and Transformation process was Successful.


       
