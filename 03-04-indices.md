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
