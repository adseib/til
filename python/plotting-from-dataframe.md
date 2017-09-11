# Plotting from a Dataframe

A few simple datavisuals using Seaborn and Matplotlib.

```python
import numpy as np
import pandas as pd
from pandas import Series, DataFrame

from pandas.tools.plotting import scatter_matrix

import matplotlib.pyplot as plt
from pylab import rcParams
import seaborn as sb

#Set parameters and style
%matplotlib inline
rcParams['figure.figsize'] = 10, 10
sb.set_style('whitegrid')

address = 'C:/filename.csv'
data = pd.read_csv(address)

data.columns = ['column1', 'column2', 'column3', 'column4']

plot1 = data['column1']

#plot as histogram
plot1.plot(kind'hist')

#histogram with seaborn
sb.distplot(plot1)

#scatter plot
data.plot(kind ='scatter', X='cloumn1', y='column2', c=['red'], s=20)

#scatter plot matrix
sb.pairplot(data)

#boxplot
data.boxplot('column1', by='column2')
```
