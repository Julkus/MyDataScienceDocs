```python
import pandas as pd
import numpy as np
```


```python
cities=['London','Belin','Warsaw','Paris']
```


```python
cities
```




    ['London', 'Belin', 'Warsaw', 'Paris']




```python
pd.Series(cities)
```




    0    London
    1     Belin
    2    Warsaw
    3     Paris
    dtype: object




```python
pip show pandas
```

    Name: pandas
    Version: 1.4.3
    Summary: Powerful data structures for data analysis, time series, and statistics
    Home-page: https://pandas.pydata.org
    Author: The Pandas Development Team
    Author-email: pandas-dev@python.org
    License: BSD-3-Clause
    Location: c:\users\julka\appdata\local\programs\python\python310\lib\site-packages
    Requires: numpy, python-dateutil, pytz
    Required-by: 
    Note: you may need to restart the kernel to use updated packages.
    


```python
import matplotlib.pyplot as plt
import math as math
```


    ---------------------------------------------------------------------------

    ModuleNotFoundError                       Traceback (most recent call last)

    Input In [9], in <cell line: 1>()
    ----> 1 import matplotlib.pyplot as plt
          2 import math as math
    

    ModuleNotFoundError: No module named 'matplotlib'



```python
!pip install matplotlib
```

    Requirement already satisfied: matplotlib in c:\users\julka\appdata\local\programs\python\python310\lib\site-packages (3.5.3)
    Requirement already satisfied: cycler>=0.10 in c:\users\julka\appdata\local\programs\python\python310\lib\site-packages (from matplotlib) (0.11.0)
    Requirement already satisfied: fonttools>=4.22.0 in c:\users\julka\appdata\local\programs\python\python310\lib\site-packages (from matplotlib) (4.34.4)
    Requirement already satisfied: packaging>=20.0 in c:\users\julka\appdata\local\programs\python\python310\lib\site-packages (from matplotlib) (21.3)
    Requirement already satisfied: kiwisolver>=1.0.1 in c:\users\julka\appdata\local\programs\python\python310\lib\site-packages (from matplotlib) (1.4.4)
    Requirement already satisfied: python-dateutil>=2.7 in c:\users\julka\appdata\local\programs\python\python310\lib\site-packages (from matplotlib) (2.8.2)
    Requirement already satisfied: pillow>=6.2.0 in c:\users\julka\appdata\local\programs\python\python310\lib\site-packages (from matplotlib) (9.2.0)
    Requirement already satisfied: numpy>=1.17 in c:\users\julka\appdata\local\programs\python\python310\lib\site-packages (from matplotlib) (1.23.2)
    Requirement already satisfied: pyparsing>=2.2.1 in c:\users\julka\appdata\local\programs\python\python310\lib\site-packages (from matplotlib) (3.0.9)
    Requirement already satisfied: six>=1.5 in c:\users\julka\appdata\local\programs\python\python310\lib\site-packages (from python-dateutil>=2.7->matplotlib) (1.16.0)
    
    [notice] A new release of pip available: 22.2 -> 22.2.2
    [notice] To update, run: python.exe -m pip install --upgrade pip
    


```python
import matplotlib.pyplot as plt
```


```python
primeNumbers=(2,3,5,7,9,11,13,17,19)
pd.Series(primeNumbers)
```




    0     2
    1     3
    2     5
    3     7
    4     9
    5    11
    6    13
    7    17
    8    19
    dtype: int64




```python
SpielbergFilmography={'Jaws':1975,'1941':1979,'Indiana Jones and the Raiders of the Lost Ark':1981,'E.T. the Extra-Terrestrial':1982}
```


```python
SpielbergFilmography
```




    {'Jaws': 1975,
     '1941': 1979,
     'Indiana Jones and the Raiders of the Lost Ark': 1981,
     'E.T. the Extra-Terrestrial': 1982}




```python
pd.Series(SpielbergFilmography)
```




    Jaws                                             1975
    1941                                             1979
    Indiana Jones and the Raiders of the Lost Ark    1981
    E.T. the Extra-Terrestrial                       1982
    dtype: int64




```python
monotonicList = (1,2,4,67,99)
monotonicSeries = pd.Series(monotonicList)
monotonicSeries
```




    0     1
    1     2
    2     4
    3    67
    4    99
    dtype: int64



## METHODS


```python
monotonicSeries.sum()
```




    173




```python
monotonicSeries.min()
```




    1




```python
monotonicSeries.max()
```




    99




```python
monotonicSeries.mean()
```




    34.6




```python
monotonicSeries.count()
```




    5




```python
monotonicSeries.size
```




    5




```python
monotonicSeries.product()
```




    53064




```python
monotonicSeries.index
```




    RangeIndex(start=0, stop=5, step=1)




```python
monotonicSeries.keys()
```




    RangeIndex(start=0, stop=5, step=1)




```python
monotonicSeries.values
```




    array([ 1,  2,  4, 67, 99], dtype=int64)




```python
monotonicSeries.to_json()
```




    '{"0":1,"1":2,"2":4,"3":67,"4":99}'




```python
monotonicSeries.add(10)
```




    0     11
    1     12
    2     14
    3     77
    4    109
    dtype: int64




```python
currencies = ['USD','EUR','PLN','EUR','EUR']
countries = ['USA','Spain','Poland','Portugal','Italy']
```


```python
curSeries = pd.Series(countries,currencies)
curSeries
```




    USD         USA
    EUR       Spain
    PLN      Poland
    EUR    Portugal
    EUR       Italy
    dtype: object




```python
countrySeries = pd.Series(currencies,countries)
countrySeries
```




    USA         USD
    Spain       EUR
    Poland      PLN
    Portugal    EUR
    Italy       EUR
    dtype: object




```python
curSeries = pd.Series(data=countries,index=currencies)
curSeries
```




    USD         USA
    EUR       Spain
    PLN      Poland
    EUR    Portugal
    EUR       Italy
    dtype: object



## FILTRATION


```python
numbers = [1,2,3,11,12,13]
```


```python
numbers
```




    [1, 2, 3, 11, 12, 13]




```python
# numbers > 10 #error
```


```python
numSeries = pd.Series(numbers)
numSeries
```




    0     1
    1     2
    2     3
    3    11
    4    12
    5    13
    dtype: int64




```python
numSeries > 10
```




    0    False
    1    False
    2    False
    3     True
    4     True
    5     True
    dtype: bool




```python
numSeries.where(numSeries > 10)
```




    0     NaN
    1     NaN
    2     NaN
    3    11.0
    4    12.0
    5    13.0
    dtype: float64




```python
numSeries.where(numSeries > 10, other=-1)
```




    0    -1
    1    -1
    2    -1
    3    11
    4    12
    5    13
    dtype: int64




```python
numSeries.where(numSeries > 10).dropna()
```




    3    11.0
    4    12.0
    5    13.0
    dtype: float64




```python
numSeries.where(numSeries > 10, inplace=True)
```


```python
numSeries
```




    0     NaN
    1     NaN
    2     NaN
    3    11.0
    4    12.0
    5    13.0
    dtype: float64




```python
numSeries.dropna(inplace=True)
```


```python
numSeries
```




    3    11.0
    4    12.0
    5    13.0
    dtype: float64




```python
numSeries = pd.Series(numbers)
numSeries
```




    0     1
    1     2
    2     3
    3    11
    4    12
    5    13
    dtype: int64




```python
numSeries.where(numSeries > 10, inplace=True)
numSeries.dropna(inplace=True)
```


```python
numSeries
```




    3    11.0
    4    12.0
    5    13.0
    dtype: float64




```python
numSeries = pd.Series(numbers)
numSeries
```




    0     1
    1     2
    2     3
    3    11
    4    12
    5    13
    dtype: int64




```python
numSeries.filter(items=[0,2,4])
```




    0     1
    2     3
    4    12
    dtype: int64




```python

```
