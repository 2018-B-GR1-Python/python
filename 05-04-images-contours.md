# Images and Contours

```python
import numpy as np
import matplotlib.pyplot as plt

%matplotlib inline
# Set up figure size and DPI for screen demo
plt.rcParams['figure.figsize'] = (4,3)
plt.rcParams['figure.dpi'] = 150


from scipy.ndimage.filters import gaussian_filter
rands2d = gaussian_filter(np.random.normal(size=(512,512)), sigma=10)

# Basico
plt.imshow(rands2d)
plt.colorbar()

# Limites del grafico
plt.imshow(rands2d, extent=[-200,100,-100,])

# Minimo y maximo valor de la escala
plt.imshow(rands2d, vmax=0.3, vmin= -0.05) 
plt.colorbar()

# Aspect ratio
plt.imshow(rands2d, aspect=0.2) # 0.... 1 horizontal, vertical

# Interpolacion
small = np.arange(0,4,1).reshape(2,2)
print(small)
plt.imshow(small, interpolation='mitchell')

plt.matshow(small)  # helper function, deshabilita la interpolacion y usa los valores en el centro

"""
[None, 'none', 'nearest', 'bilinear', 'bicubic', 'spline16',
           'spline36', 'hanning', 'hamming', 'hermite', 'kaiser', 'quadric',
           'catrom', 'gaussian', 'bessel', 'mitchell', 'sinc', 'lanczos']
"""

# CONTORNOS

# Basico
srands2d = gaussian_filter(rands2d, sigma=100)
plt.imshow(srands2d)
plt.colorbar()

# Contorno
plt.contour(srands2d)
plt.colorbar()

# Niveles (3D)
plt.contour(srands2d, levels=[0,0.003])

# Numero de contornos
plt.contour(srands2d, 5)

# Colores del contorno
plt.contour(srands2d, 4, colors=['r','b'])

# Contornos llenos
plt.contourf(srands2d, 5)

# Rejillas
plt.contourf(srands2d, 3, colors='none', hatches=['*','-'])

# Estilo de la linea
plt.contour(srands2d, linestyles=[':','--','-'])

# labels
contours = plt.contour(srands2d, 5)
plt.clabel(contours)

# Multiple
plt.contour(srands2d, colors=['k']) # levels=[0],
plt.imshow(srands2d)


```
