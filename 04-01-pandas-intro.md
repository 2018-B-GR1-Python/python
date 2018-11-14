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

