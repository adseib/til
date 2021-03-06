# Creating and Modifying a Data Frame from a CSV file

Grab the file and name columns.

```python
import numpy as np
import pandas as pd
from pandas import Series, DataFrame

address = 'files/filename.csv'
data = pd.read_csv(address)

data.columns = ['column1', 'column2', 'column3', 'column4']

#Output head of Data Frame
data.head()
```
![alt text](images/data-head.png "data.head output")

```python
#Check for missing values
data.isnull()

#Count missing values
data.isnull().sum()
```
![alt text](images/dataframe-nulls.PNG "dataframe nulls output")

```python
#Use fillna to replace null values if required
data_nonull = data.fillna(0)
data_nonull
```

Group by any column:

```python
data_group = data.groupby(data['column1'])
#Print out the average, min, max, or median value for each group.
data_group.mean()
```
![alt text](images/dataframe-grouped.PNG "dataframe grouped output")

[Pandas Documentation on Data Frame](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html)
