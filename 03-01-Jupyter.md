# Jupyter

## Plugins

```
https://github.com/ipython-contrib/jupyter_contrib_nbextensions
```

## Extension Manager
```
https://github.com/Jupyter-contrib/jupyter_nbextensions_configurator
```


## Pyplot

```python
from matplotlib import pyplot as plt
```

## Numpy

```python
import numpy as np
```

### Creating and Printing
```python
np.array([1,2,3])
np.zeros((3,4))
np.ones((3,4))
np.ones((3,4),  dtype=np.int16)
np.empty((3,4))
np.eye(4)
np.arange(3,50,3)
np.array([(1,2,3),(4,5,6)])
np.array([1,2,3]).shape
np.arange(6).reshape(3,2)
np.arange(6).reshape(3,3) # Error Need 9 elements
np.ones_like(np.arange(6).reshape(3,2))
np.arange(24).reshape(2,3,4)
np.arange(10000)

```

### Operations

#### Suma 

```python
a = np.array([10,10,10])
b = np.array([5,5,5])
a + b
```

#### Resta

```python
a = np.array([10,10,10])
b = np.array([5,5,5])
a - b
```

#### Multiplicacion

```python
a = np.array([10,10,10])
b = np.array([5,5,5])
a * b
```

#### Division

```python
a = np.array([10,10,10])
b = np.array([5,5,5])
a / b
```

#### Mod

```python
a = np.array([10,10,10])
a % 2
```

#### Expresiones

```python
a = np.array([10,10,10])
a < 15
```

#### Multiplicacion mas dimensiones

```python
A = np.array([[0,1],[2,3]])
print('A:\n', A)
B = np.array([[4,5],[6,7]])
print('B:\n', B)
A * B
```

#### Multiplicacion de Matrices


```python
A = np.array([[0,1],[2,3]])
print('A:\n', A)
B = np.array([[4,5],[6,7]])
print('B:\n', B)
A.dot(B)
# OR
np.dot(A,B)
```

#### Operaciones en python

```python
a = np.array([10,10,10])
a *= 3
print(a)
```

#### Operaciones conocidas en los arreglos

```python
arreglo_numeros = np.array([1,2,3,4,5,6,7,8,9,10])
arreglo_numeros.sum()
arreglo_numeros.min()
arreglo_numeros.max()
```

#### Operaciones por ejex (x y z, etc...)

```python
numeros = np.arange(12).reshape(3,4)
print(numeros)
print(numeros.sum(axis=0)) # X
print(numeros.sum(axis=1)) # Y
```

### Universal Functions

#### Radianes

```python
angulos = np.array([0,30,45,60,90])
print(angulos)
angulos_en_radianes = angulos * np.pi/180
print(angulos_en_radianes)
print(np.radians(angulos))
print(np.degrees(angulos_en_radianes))
```

#### Sen

```python
angulos = np.array([0,30,45,60,90])
# Funcion seno() en los angulos del arreglo
print(np.sin(angulos))
```
#### Cos

```python
angulos = np.array([0,30,45,60,90])
# Funcion coseno() en los angulos del arreglo
print(np.cos(angulos))
```

#### Tan

```python
angulos = np.array([0,30,45,60,90])
# Funcion tangente() en los angulos del arreglo
print(np.tan(angulos))
```

#### Media

```python
notas = np.array([1,3,5,7,6,5,3,4,6,7,8,3,1,5,6,8,9,10,10,6,5,6,7,8,9])
print(np.mean(notas))
```

#### Mediana

```python
notas = np.array([1,3,5,7,6,5,3,4,6,7,8,3,1,5,6,8,9,10,10,6,5,6,7,8,9])
print(np.median(notas))
```

#### Desviacion Estandar

```python
notas = np.array([1,3,5,7,6,5,3,4,6,7,8,3,1,5,6,8,9,10,10,6,5,6,7,8,9])
print(np.std(notas))
```

#### Varianza

```python
notas = np.array([1,3,5,7,6,5,3,4,6,7,8,3,1,5,6,8,9,10,10,6,5,6,7,8,9])
print(np.var(notas))
```

#### Generate from text

archivo `salaries.csv`:

```csv
1,2,3,4,5,6,7,8,9,10,11,12,13,14,15
15,14,13,12,11,10,9,8,7,6,5,4,3,2,1
```

Codigo: 

```python
salarios = np.genfromtxt('data/salaries.csv', delimiter=',')
print(salarios)
```

#### Shape

```python
arreglo_una_d =  np.array([1,2,3])
print(arreglo_una_d)
print(arreglo_una_d.shape)
arreglo_dos_d =  np.array([[1,2],[2,3],[3,4]])
print(arreglo_dos_d)
print(arreglo_dos_d.shape)
```

#### Slicing & Dicing

```python
arreglo_al_cuadrado = np.arange(11)**2
print(arreglo_al_cuadrado)
print(arreglo_al_cuadrado[0])
print(arreglo_al_cuadrado[0:3])
print(arreglo_al_cuadrado[-2])
print(arreglo_al_cuadrado[2:-3])
print(arreglo_al_cuadrado[-3:-1])
print(arreglo_al_cuadrado[2:])
print(arreglo_al_cuadrado[:4])
print(arreglo_al_cuadrado[2:8:4]) # Pasos de 4 en 4  desde el 2 hasta el 8
print(arreglo_al_cuadrado[::-1]) # De atras para adelante
```

## Iteracion

### for

```python
estudiantes = np.array([['Adrian','Vicente','Eguez','Sarzosa'],
                      [1,2,3,4],
                      [5,6,7,8]])
for i in estudiantes:
    print(f"Dimension uno: {i}")
for i in estudiantes.flatten():
    print(f"Todos en una dimension: {i}")
for i in estudiantes.flatten(order='F'):
    print(f"Todos en una dimension ordenados por 'First': {i}")
```

### nditer

```python
arreglo_tres_cuatro = np.arange(12).reshape(3,4)
print(arreglo_tres_cuatro)
for i in np.nditer(arreglo_tres_cuatro):
    print(i)
for i in np.nditer(arreglo_tres_cuatro, order='F'):
    print(i)
for i in np.nditer(arreglo_tres_cuatro, order='F', flags = ['external_loop']):
    print(i)
#  for i in np.nditer(arreglo_tres_cuatro):  # ReadOnly
#      i[...] = i*i
for i in np.nditer(arreglo_tres_cuatro, op_flags = ['readwrite']):  # ReadOnly
    i[...] = i*i
arreglo_tres_cuatro
```

## Reshaping

```python
paises_tuplas = np.array([('Ecuador','USA','Cuba','Venezuela'),
              ('Brazil','China','Japon','Mexico')])
print(paises_tuplas)
print(paises_tuplas.shape)
print(paises_tuplas.flatten())  # 1D Array
print(paises_tuplas.T)  # Transposes Matrix
print(paises_tuplas.T.flatten())  # 1D Array
print(paises_tuplas.reshape(4,2))  # 1D Array
paises = np.array(['Ecuador','USA','Cuba','Venezuela','Brazil','China'])
print(paises)
print(paises.reshape(-1,3))  # -1 significa que no se el numero de esa dimension
print(paises.reshape(2,-1))  # -1 significa que no se el numero de esa dimension
```

## Splitting

### Split

```python
arreglo_split = np.array([1,2,3,4,5,6,7,8,9,10,11,12])
print(np.split(arreglo_split,2))
print(np.split(arreglo_split,3))
print(np.split(arreglo_split,4))
#  print(np.split(arreglo_split,5)) ## Error
print(np.split(arreglo_split,[2,3,5,8,9]))
```

### Horizontal split

```python
paises = np.array(['Ecuador','USA','Cuba','Venezuela','Brazil','China'])
print(np.hsplit(paises,2))
print(np.hsplit(paises,3))
print(np.hsplit(paises,6))
# print(np.hsplit(paises,4))  # Error
print('*******************************************\n\n\n\n\n')

print('*******************************************')
paises_tuplas = np.array([('Ecuador','USA','Cuba','Venezuela'),
              ('Brazil','China','Japon','Mexico')])
print(paises_tuplas)
xa, xb, xc, xd = np.hsplit(paises_tuplas,4)
print(xa)
print(xb)
print(xc)
print(xd)
```

### Vertical split

```python

```
