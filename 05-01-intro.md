# Plotting


## Basico configuracion 

[RcParams](https://matplotlib.org/api/matplotlib_configuration_api.html#matplotlib.RcParams)

```python
import numpy as np
import matplotlib.pyplot as plt

# Configuracion general de los plots revisar documentacion
plt.rcParams['figure.figsize'] = (4,3)
plt.rcParams['figure.dpi'] = 150

# Basico
xvals = np.arange(0,10,0.1)
plt.plot(xvals)

# Ejes
plt.plot(xvals, np.sin(xvals))

# Labels en ejes y varios graficos

plt.plot(xvals, np.sin(xvals))
plt.plot(xvals, np.cos(xvals))
plt.xlabel("$x$")
plt.ylabel(r"$y$")


# Labels en el grafico Color
plt.plot(xvals, np.sin(xvals), label=r"$y = \sin(x)$")
plt.plot(xvals, np.cos(xvals), label=r"$y = \cos(x)$")
plt.xlabel("$x$")
plt.ylabel(r"$y$")
plt.legend()


# Estilo de la linea
# linestyle
plt.plot(xvals, np.sin(xvals), label=r"$y = \sin(x)$", color='r')
plt.plot(xvals, np.cos(xvals), label=r"$y = \cos(x)$", marker='o')
plt.xlabel("$x$")
plt.ylabel(r"$y$")
plt.legend()


# Con el 3er argumento
plt.plot(xvals, np.sin(xvals), 'r--', label=r"$y = \sin(x)$")
plt.plot(xvals, np.cos(xvals), 'bo', label=r"$y = \cos(x)$")
plt.xlabel("$x$")
plt.ylabel(r"$y$")
plt.legend()

# Limitar el plot con ciertos valores
plt.ylim(0,1)
plt.xlim(0,1)



```




