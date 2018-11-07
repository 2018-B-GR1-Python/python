# Indices

## Indices 1D

```python
import numpy as np
import csv
cuadrados_uno_once = np.arange(11)**2
cuadrados_uno_once[2],cuadrados_uno_once[4],cuadrados_uno_once[6]
indices = [2,6,8]
cuadrados_uno_once[indices]
```

## Indices 2D

```python
indice_dos = np.array([[2,4],[8,10]])
print(cuadrados_uno_once[indice_dos])
frutas = np.array([
    ['Pera','Manzana','Banano','Mango'],
    ['Coco','Naranja','Mandarina','Piña'],
    ['Frutilla','Mora','Papaya','Melon']
])
arreglo_filas = np.array([[0,0],[2,2]])  # 0,0 - 0,3 - 2,0 - 2,3
arreglo_columnas = np.array([[0,3],[0,3]])
print(frutas[arreglo_filas, arreglo_columnas])
frutas[arreglo_filas, arreglo_columnas] = 'HHHH'
print(frutas)
```

## Ejemplo GDP

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
gdp_2016 = pd.read_csv("data/gdp_pc.csv")["2016"].values  # Producto interno bruto
gdp_2016.shape  # 1D array
plt.plot(gdp_2016)
plt.show()
np.median(gdp_2016)  # Entradas con valores "nan" Que no son numeros Not A Number
gdp_2016_sin_nan = gdp_2016[~np.isnan(gdp_2016)]  # Entradas sin valores "nan" Que no son numeros Not A Number
gdp_2016_sin_nan
gdp_2016_sin_nan.shape
np.median(gdp_2016_sin_nan)
np.mean(gdp_2016_sin_nan)
np.count_nonzero(gdp_2016_sin_nan[gdp_2016_sin_nan > 10000])
np.count_nonzero(gdp_2016_sin_nan[(gdp_2016_sin_nan > 10000) & (gdp_2016_sin_nan < 20000)])
np.sort(gdp_2016_sin_nan)
np.sort(gdp_2016_sin_nan)[:10]
```
