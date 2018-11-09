# Broadcasting

![Broadcasting](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/broadcasting.PNG "Broadcasting")

## Scalars

![Broadcasting Scalars](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/broadcasting_scalars.PNG "Broadcasting Scalars")

![Broadcasting Scalars](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/broadcasting_scalars_2.PNG "Broadcasting Scalars")

## Arrays

![Broadcasting Arrays](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/broadcasting_2.PNG "Broadcasting Arrays")

![Broadcasting Constraints](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/broadcasting_constgraints.PNG "Broadcasting Constraints")

![Broadcasting Constraints 2](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/broadcasting_constgraints_2.PNG "Broadcasting Constraints 2")

## Broadcasting Rules

```python
a = np.array([1,2,3,4,5])
b = np.array([10,10,10,10,10])
print(a * b)
c = 10
print(a * c)
d = np.ones((4,3))
alturas = [1.60,1.79,1.80]  # Centimetros
pesos = [180,166,190]  # Libras
datos_estudiante = np.array([alturas, pesos])
transformacion_1 = np.array([0.03,2.2])
transformacion_1.shape
datos_estudiante.shape
datos_estudiante * transformacion_1   # Error
transformacion_2 = np.array([[0.03],[2.2]])
datos_estudiante * transformacion_2  # Ok
transformacion_2.shape
datos_estudiante.shape

```




