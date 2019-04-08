---
title: "Pandas Cheat Sheet"
date: 2019-04-08
---
---------------------
#### 1. Collect dataframe as dictionary
.set_index(['a','b']).T.to_dict('list')

#### 2. Read in csv file format(transpose) 
https://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html

#### 3. count rows with same value
df[col].value_counts()

#### 4. display columns unlimit ( equivalent to spark df, with limit=False)
```Python
pd.set_option('display.expand_frame_repr', False)

Other settings:
pd.set_option('display.height', 1000)
pd.set_option('display.max_rows', 500)
pd.set_option('display.max_columns', 500)
pd.set_option('display.width', 1000)
```

#### 5. remove all the rows with a value occur less than n times
```Python
df[df.groupby(value).uid.transform(len) > n]
or:
df.groupby(by=value).filter(lambda x: len(x) > n)
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgzNjY2MTkxNF19
-->