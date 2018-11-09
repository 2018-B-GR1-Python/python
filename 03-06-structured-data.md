# Structured Data

![Datos structurados](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/structured_data.PNG "Datos structurados")

![Datos structurados parte 2](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/structured_data2.PNG "Datos structurados parte 2")


```python
nombres = ['Adrian','Vicente','Andres','Carlos']
ids = [1,2,3,4]
notas = np.random.rand(4)*100

datos_estudiante = np.zeros(4, dtype= { 'names' : ('nombre','id','nota'), 'formats':('U10','i4','f8') })

print(datos_estudiante)

datos_estudiante['nombre'] = nombres
datos_estudiante['id'] = ids
datos_estudiante['nota'] = notas

print(datos_estudiante)
print(datos_estudiante['nombre'])
print(datos_estudiante[0])
print(datos_estudiante[1])
print(datos_estudiante[2])
print(datos_estudiante[3])
print(datos_estudiante[-1]['nombre'])
print(datos_estudiante[datos_estudiante['nota'] > 70 ]['nombre'])
```
