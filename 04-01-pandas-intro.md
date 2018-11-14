# Series Data Frames intro

```python
import numpy as np
import pandas as pd
arreglo = np.random.rand(3)
arreglo2D = np.random.rand(3,2)

serie = pd.Series(arreglo)
serie2 = pd.Series(arreglo, index = ['uno','Dos','TRES'])
serie2.index
print(serie)  # Arreglo con indices 0 -> 1 , 1 -> 2 etc...

data_frame = pd.DataFrame(arreglo2D)
print(serie)  # Arreglo con indices 0,0 -> 1 , 0,1 -> 2 etc...
data_frame[0,0]  # Error
data_frame.columns = ['Uno','Dos']
data_frame['Uno']  # Serie
data_frame['Uno'][0]  # ok
```

# Tipos de datos

1. Text Files
   1. CSV
   2. JSON
   3. HTML
2. Binary Files
3. Relational Databases

## Leer csv
```python
# f9 para compilar en la terminal
import pandas as pd
import os

CSV_PATH = 'C://Users//Adrian//Documents//Spyder//data//artwork_data.csv'
df = pd.read_csv(CSV_PATH, nrows=5)
df

df = pd.read_csv(CSV_PATH, nrows=5, index_col = 'id')
df

df = pd.read_csv(CSV_PATH, 
                 nrows=5, 
                 index_col = 'id',
                 usecols = ['id','artist'])
df


columnas_a_usar = ['id','artist','title','medium',
                   'year','acquisitionYear','height',
                   'width','units']

df = pd.read_csv(CSV_PATH, 
                 index_col = 'id',
                 usecols = columnas_a_usar)
# Warning
# C:\ProgramData\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py:2785: DtypeWarning: Columns (9,13) have mixed types. Specify dtype option on import or set low_memory=False.
#   interactivity=interactivity, compiler=compiler, result=result)
df.shape

# Serializar los datos en un archivo y poder usarlos despues
df.to_pickle('C://Users//Adrian//Documents//Spyder//data//artwork_data_frame.pickle')


```
