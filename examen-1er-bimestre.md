# 1) Examen

## 2) Crear un vector de ceros de tamaño 10

```python
a = np.zeros(10)
print(a)
```

## 3) Crear un vector de ceros de tamaño 10 y el de la posicion 5 sea igual a 1

```python
a = np.zeros(10)
a[4] = 1
print(a)
```


## 4) Cambiar el orden de un vector de 50 elementos, el de la posicion 1 es el de la 50 etc.


```python
a = np.arange(50)
a = a[::-1]
```



## 5) Crear una matriz de 3 x 3 con valores del cero al 8


```python
a = np.arange(9).reshape(3,3)
print(a)
```


## 6) Encontrar los indices que no sean cero en un arreglo

```python
import numpy as np
arreglo = [1,2,0,0,4,0]
nz = np.nonzero(arreglo)
print(nz)
```

## 7) Crear una matriz de identidad 3 x 3 

```python
a = np.eye(3)
print(a)
```

## 8) Crear una matriz 3 x 3 x 3 con valores randomicos

```python
a = np.random.random((3,3,3))
print(a)
```


## 9) Crear una matriz 10 x 10 y encontrar el mayor y el menor

```python
a = np.random.random((10,10))
amin, amax = a.min(), a.max()
print(amin, amax)
```



## 10) Sacar los colores RGB unicos en una imagen (cuales rgb existen ej: 0, 0, 0 - 255,255,255 -> 2 colores)


```python
a = numpy.unique(img.reshape(-1, img.shape[2]), axis=0)
print(a)
```


## 11) ¿Como crear una serie de una lista, diccionario o arreglo?

```python
import numpy as np
mylist = list('abcedfghijklmnopqrstuvwxyz')
myarr = np.arange(26)
mydict = dict(zip(mylist, myarr))

ser1 = pd.Series(mylist)
ser2 = pd.Series(myarr)
ser3 = pd.Series(mydict)
print(ser3.head())

```

## 12) ¿Como convertir el indice de una serie en una columna de un DataFrame?

```python
mylist = list('abcedfghijklmnopqrstuvwxyz')
myarr = np.arange(26)
mydict = dict(zip(mylist, myarr))
ser = pd.Series(mydict)
df = ser.to_frame().reset_index()
print(df.head())
```

## 13) ¿Como combinar varias series para hacer un DataFrame?

```python
import numpy as np
ser1 = pd.Series(list('abcedfghijklmnopqrstuvwxyz'))
ser2 = pd.Series(np.arange(26))
df = pd.concat([ser1, ser2], axis=1)
df = pd.DataFrame({'col1': ser1, 'col2': ser2})
print(df.head())
```

## 14) ¿Como obtener los items que esten en una serie A y no en una serie B?

```python
ser1 = pd.Series([1, 2, 3, 4, 5])
ser2 = pd.Series([4, 5, 6, 7, 8])
ser1[~ser1.isin(ser2)]
```

## 15) ¿Como obtener los items que no son comunes en una serie A y serie B?

```python
ser1 = pd.Series([1, 2, 3, 4, 5])
ser2 = pd.Series([4, 5, 6, 7, 8])
ser_u = pd.Series(np.union1d(ser1, ser2))  # union
ser_i = pd.Series(np.intersect1d(ser1, ser2))  # intersect
ser_u[~ser_u.isin(ser_i)]
```

## 16) ¿Como obtener el numero de veces que se repite un valor en una serie?

```python
ser = pd.Series(np.take(list('abcdefgh'), np.random.randint(8, size=30)))
ser.value_counts()
```

## 17) ¿Como mantener los 2 valores mas repetidos de una serie, y a los demas valores cambiarles por 0 ?

```python
np.random.RandomState(100)
ser = pd.Series(np.random.randint(1, 5, [12]))
print(ser.value_counts())
ser[~ser.isin(ser.value_counts().index[:2])] = 0
ser

```

## 18) ¿Como transformar una serie de un arreglo de numpy a un DataFrame con un `shape` definido?


```python
ser = pd.Series(np.random.randint(1, 10, 35))
shape(7,5)
df = pd.DataFrame(ser.values.reshape(7,5))
print(df)

```

## 19) ¿Obtener los valores de una serie conociendo la posicion por indice?


```python
ser = pd.Series(list('abcdefghijklmnopqrstuvwxyz'))
pos = [0, 4, 8, 14, 20]
# a e i o u
ser.take(pos)
```

## 20) ¿Como anadir series vertical u horizontalmente a un DataFrame?


```python
ser1 = pd.Series(range(5))
ser2 = pd.Series(list('abcde'))
ser1.append(ser2)
df = pd.concat([ser1, ser2], axis=1)
print(df)
```


## 21)¿Obtener la media de una serie agrupada por otra serie?

`groupby` tambien esta disponible en series.


```python
frutas = pd.Series(np.random.choice(['manzana', 'banana', 'zanahoria'], 10))
pesos = pd.Series(np.linspace(1, 10, 10))
print(pesos.tolist())
print(frutas.tolist())
#> [1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0, 10.0]
#> ['banana', 'carrot', 'apple', 'carrot', 'carrot', 'apple', 'banana', 'carrot', 'apple', 'carrot']

# Los valores van a cambiar por ser random
# apple     6.0
# banana    4.0
# carrot    5.8
# dtype: float64

# Input
frutas = pd.Series(np.random.choice(['apple', 'banana', 'carrot'], 10))
pesos = pd.Series(np.linspace(1, 10, 10))

# Solution
pesos.groupby(frutas).mean()

```


## 22)¿Como importar solo columnas especificas de un archivo csv?

https://raw.githubusercontent.com/selva86/datasets/master/BostonHousing.csv.

```python
df = pd.read_csv('https://raw.githubusercontent.com/selva86/datasets/master/BostonHousing.csv', usecols=['crim', 'medv'])
print(df.head())

```





