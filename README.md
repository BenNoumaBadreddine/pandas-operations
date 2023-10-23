# Pandas operations

``` python
import pandas as pd
``` 
## Create dataframe

``` python
data = {'customer_id': [1,2,3], 'name': ['Joe', 'Marc', 'Jasmine']}
df = pd.dataframe(data=data)
``` 
## Select columns
``` python
df['name']
``` 
## Filter rows
``` python
df[df['name]=='Marc']
``` 
## Get unique values of a given column
``` python
df.name.unique()
```
## Count unique values
``` python
len(df.name.unique())
# or
df.name.nunique()
```
## Count all records, shape, info, statistic
``` python
# count records
df.size
# shape
df.shape
# info: column types
df.info()
# statistics
df.describe()
```
## Group by a column to calculate sum, avg, ...
``` python
data = {'gender':['M', 'F', 'M', 'F'], 'population':[1,1,0,1]}
df = pd.DataFrame(data=data)
df.groupby('gender').sum()
```
## Sort by a column 
``` python
df.sort_values(by=['customer_id'])
```
## Count unique values
``` python
df.value_counts()
```
## Drop duplicated rows
``` python
df.drop_duplicates()
# drop rows having duplicated values in a subset of columns
df.drop_duplicates(subset['customer_id'])
```
## Join
``` python
pd.merge(df1, df2, on=customer_id, how=inner)
pd.merge(df1, df2, on=customer_id, how=left)
pd.merge(df1, df2, on=customer_id, how=right)
pd.merge(df1, df2, on=customer_id, how=outer)
pd.merge(df1, df2, on=customer_id, how=cross)
```
## Concatenate dataframes
``` python
# concat will add all the rows of df2 at the bottom of df1
# ignore index will reindex the dataframe
#only one column 
pd.concat(df1['name'], df2['name'], ignore_index= True)
# all columns
pd.concat(df1, df2, ignore_index= True)
```
## Add column
``` python
df['age'] = [33, 35, 36]
```
## Drop column
``` python
df.drop(columns=['age'], inplace=True)
```
## Rename column
``` python
df.rename(columns={'name': 'customer_name'}, inplcae=True)
```
## Iterate over dataframe
``` python
# method 1
for i in range(len(df)):
    print(df.loc[i, "Name"], df.loc[i, "Age"])
# method 2
for ind in df.index:
    print(df['Name'][ind], df['Stream'][ind])
# method 3
for i in range(len(df)):
    print(df.iloc[i, 0], df.iloc[i, 1])
# method 4
for index, row in df.iterrows():
    print(row["Name"], row["Age"])    
# method 5
df.apply(lambda row: row["Name"] + " " +
         str(row["Age"]), axis=1)
```