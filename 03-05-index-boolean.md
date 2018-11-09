# Index with boolean

```python
arreglo_diez_seis = np.arange(16).reshape(4,4)
indice_booleano = arreglo_diez_seis > 9
print(indice_booleano)
print(arreglo_diez_seis[indice_booleano])
print(np.count_non_zero(indice_booleano))
print(np.sum(indice_booleano))  # Cuantos 
print(np.sum(indice_booleano, axis = 1))  # Cuantos por eje ([0,0,2,4])
print(np.any(indice_booleano))
print(np.all(indice_booleano))
print(np.all(indice_booleano, axis = 1))  # Cuantos por todo el eje ([False, False, False, True]) 
```
