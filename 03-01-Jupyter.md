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


