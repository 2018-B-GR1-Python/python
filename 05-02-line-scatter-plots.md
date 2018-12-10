# Line scatter

## Plots

```python
import numpy as np
import matplotlib.pyplot as plt
# https://stackoverflow.com/questions/43027980/purpose-of-matplotlib-inline/43028034
%matplotlib inline
# Set up figure size and DPI for screen demo
plt.rcParams['figure.figsize'] = (4,3)
plt.rcParams['figure.dpi'] = 150


# Basic plot seno
xvals = np.arange(0,10,0.1)
plt.plot(xvals, np.sin(xvals))
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')

# Tipos de imagenes para el simple plot
# Solido
# Guiones 
# Puntos
# Guion Punto

idx = 0
for marker in ('-', '--', ':', '-.'):
    plt.plot(xvals, np.sin(xvals)+idx, ''.join(('k',marker)))
    idx += 1

# Marcadores
plt.plot(xvals, np.sin(xvals), 'k.')  # .-- Se puede combinar
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')


# Marcadores frecuencia 'markevery'
xvals2 = np.arange(0,10,0.01)
plt.plot(xvals2, np.sin(xvals2), 'k.') # , markevery=10 
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')


# Marcadores tamano y color
plt.plot(xvals, np.sin(xvals), 'r.' markersize=20) # 30 40   # r = red k = black b = blue etc...
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')

# Tipos de marcadores
idx = 0
for marker in ('.', ',', 'o', 'v', '^', '>', '<', '1', '2', '3', '4', 's', 'p', 
               '*', 'h', 'H', '+', 'x', 'D', 'd', '|', '_'):
    plt.plot(idx, 0, ''.join(('r',marker)))
    idx += 1
plt.xlim(-0.5,idx+0.5)


#  Customizados
plt.plot(xvals, np.sin(xvals), color='k', linestyle='none', marker=r'$\Sigma$')  # $sin$   o sigma = \Sigma 
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')

#  Tamano de la linea
plt.plot(xvals, np.sin(xvals), linewidth=10)  # Default 1 o puede hacerse mas pequeña 0.1
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')

# Orden de la linea

#zorder
plt.plot(xvals, np.sin(xvals), lw=8, zorder=0)  # 1
plt.plot(xvals + 1, np.sin(xvals), lw=8, zorder=1)  # 0
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')


# Transparencia

plt.plot(xvals, np.sin(xvals), alpha=0.2)
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')

# El orden importa!
# El arreglo si no se muestra con puntos hace
# 'trazos' con los puntos en el orden que esta
# si esta desordenado se dibuja una 'telaraña'
shuffled_xvals = np.random.permutation(xvals)
plt.plot(shuffled_xvals, np.sin(shuffled_xvals), 'k.')  # k-
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')

###### Scatter

# Basic
xvals = np.arange(0,10,0.1)
plt.scatter(xvals, np.sin(xvals))
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')

# Colores
plt.scatter(xvals, np.sin(xvals), c=np.cos(xvals)) #, c='r -> rojo
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')

# Colores con cmap
plt.scatter(xvals, np.sin(xvals), c=np.cos(xvals), cmap='inferno')
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')



# Color del borde
plt.scatter(xvals, np.sin(xvals), c=np.cos(xvals), edgecolor='k')  # b, r, g
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')


# Tamaño
plt.scatter(xvals, np.sin(xvals), c=np.cos(xvals), edgecolor='none', size=1)  # b, r, g
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')

# Tamaños distintos enviando un arreglo
plt.scatter(xvals, np.sin(xvals), c=np.cos(xvals), edgecolor='k', s=np.power(xvals,3))
plt.xlabel(r'$x$')
plt.ylabel(r'$\sin(x)$')

# Velocidad importa

%%timeit -n3 -r3 plt.plot(np.random.uniform(size=int(1e6)), np.random.uniform(size=int(1e6)), 'k,')
plt.clf()

%%timeit -n3 -r3 plt.scatter(np.random.uniform(size=int(1e6)), np.random.uniform(size=int(1e6)), c='k', marker=',')
plt.clf()

# plot > scatter (scatter cuando se necesite colores y demas)

```
