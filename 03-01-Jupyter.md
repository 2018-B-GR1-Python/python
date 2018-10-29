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

```
from matplotlib import pyplot as plt
```

## Numpy

```
import numpy as np
```

### Creating and Printing
```
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

```
a = np.array([10,10,10])
b = np.array([5,5,5])
a + b
```

#### Resta

```
a = np.array([10,10,10])
b = np.array([5,5,5])
a - b
```

#### Multiplicacion

```
a = np.array([10,10,10])
b = np.array([5,5,5])
a * b
```

#### Division

```
a = np.array([10,10,10])
b = np.array([5,5,5])
a / b
```

#### Mod

```
a = np.array([10,10,10])
a % 2
```

#### Expresiones

```
a = np.array([10,10,10])
a < 15
```

#### Multiplicacion mas dimensiones

```
A = np.array([[0,1],[2,3]])
print('A:\n', A)
B = np.array([[4,5],[6,7]])
print('B:\n', B)
A * B
```

#### Multiplicacion de Matrices


```
A = np.array([[0,1],[2,3]])
print('A:\n', A)
B = np.array([[4,5],[6,7]])
print('B:\n', B)
A.dot(B)
# OR
np.dot(A,B)
```

#### Operaciones en python

```
a = np.array([10,10,10])
a *= 3
print(a)
```

#### Operaciones conocidas en los arreglos

```
arreglo_numeros = np.array([1,2,3,4,5,6,7,8,9,10])
arreglo_numeros.sum()
arreglo_numeros.min()
arreglo_numeros.max()
```

#### Operaciones por ejex (x y z, etc...)

```
numeros = np.arange(12).reshape(3,4)
print(numeros)
print(numeros.sum(axis=0)) # X
print(numeros.sum(axis=1)) # Y
```

### Universal Functions

#### Radianes

```
angulos = np.array([0,30,45,60,90])
print(angulos)
angulos_en_radianes = angulos * np.pi/180
print(angulos_en_radianes)
print(np.radians(angulos))
```

#### Sen

```
angulos = np.array([0,30,45,60,90])
# Funcion seno() en los angulos del arreglo
print(np.sin(angulos))
```
#### Cos

```
angulos = np.array([0,30,45,60,90])
# Funcion coseno() en los angulos del arreglo
print(np.cos(angulos))
```
