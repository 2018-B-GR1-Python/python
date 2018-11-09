# Histograms

```python
np.histograms([1,2,1], bins = [0,1,2,3])
# 1er parametros -> Datos
# 2do parametro -> contenedores (bins)
mu, sigma = 2, 0.5
# mu = centro de la desviacion estandar
# sigma = numero desde mu hasta donde cambia el punto de infleccion
data = np.random.normal(mu,sigma, 10000)
print(data)

(n, bin_edges) = np.histogram(data, bins = 50)
# n = occurrencias que caen en cada contenedor
# bin_edges = los valores de x que marcan los limites de los contenedores
plt.plot(bin_edges[1:],n)
plt.show()
```
