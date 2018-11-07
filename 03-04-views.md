# Views

## id

```python
import numpy as np
frutas = np.array(['Pera','Manzana','Banano','Mango','Piña'])
cesta_uno = frutas.view()
cesta_dos = frutas.view()
print(cesta_uno)
print(cesta_dos)
print(id(frutas))
print(id(cesta_uno))
print(id(cesta_dos))
```

## is

```python
print(cesta_uno is frutas)
print(cesta_dos is frutas)
print(cesta_uno.base is frutas)  # Base object es el arreglo de frutas
print(cesta_dos.base is frutas)  # Base object es el arreglo de frutas
```


## Asignacion

```python
frutas = np.array(['Pera','Manzana','Banano','Mango','Piña'])
cesta_uno = frutas.view()
cesta_dos = frutas.view()

cesta_uno[0]= 'Frutillaaass'  # El valor mas grande en el arreglo original es de 7 elementos, por eso se corta la palabra
print(cesta_uno) 
print(frutas) 
print(cesta_dos)  # Se actualizaron todos los arreglos
```

## Shape

```python
frutas = np.array(['Pera','Manzana','Banano','Mango','Piña','Melon'])
cesta_uno = frutas.view()
cesta_dos = frutas.view()

cesta_uno = np.array(['Coco','Mora','Mortiño','Limon'])
print(cesta_dos)
print(cesta_uno)
cesta_dos.shape = 3,2
print(cesta_dos)
print(frutas)
```
