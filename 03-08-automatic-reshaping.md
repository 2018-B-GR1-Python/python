# Automatic Reshaping

```python
a = np.arange(30)
a.shape = 2,-1,3  # El '-1' es la dimension que no sabemos cuanto va a tomar, numpy se encarga de eso
# En este caso es 2 * 3 * X    ->  X = 30 / (2 * 3)  -> X = 5
print(a)
a.shape = 2,3,-1
print(a)
```
