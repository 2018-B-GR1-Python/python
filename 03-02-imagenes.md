# Images

![alt Imagen como un arreglo](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/Imagen%20como%20un%20arreglo.PNG "Imagen como un arreglo")

## Pixeles


Cada pixel -> valor  ! Dependiendo del tipo de imagen:

Ejemplo:

Pixel [0,0] es de color rojo, el rojo puede estar representado por el formato RGB ->  255,0,0

|0-255|0-255|0-255|
|--|--|--|
|Red|Green|Blue|

Cada **Red**, **Green** y **Blue** es conocido como un `Channel`. Por lo tanto la imagen es una imagen de **3** `Channel image`.

## Grayscale

Las imagenes en escalado de grises son representadas por una intensidad del color `negro` -> 0 - 1.

Ej:
Pixel [0,0] -> 0.2 intensidad

En este caso esta imagen seria una imagen de **1** `Channel image`

Basicamente existen dos tipos de imagenes, o de `representaciones` de imagenes. La primera es **Single Channel** y la segunda es **Multi Channel**

![alt Imagen representada en arreglo 3D](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/imagen%203D.PNG "Imagen representada en arreglo 3D")


## Ejemplo

```python
import numpy as np
# pip install scipy
from scipy import ndimage
from scipy import misc
# Get a 1024 x 768, color image of a raccoon face.
raccon_face_image = misc.face() 
raccon_face_image.shape  # (768, 1024, 3)
type(raccon_face_image)  # numpy.ndarray
import matplotlib.pyplot as plt
plt.imshow(raccon_face_image)
partial_raccon_face_image = raccon_face_image[384:,512:,:]
plt.imshow(partial_raccon_face_image)
plt.show()
```

## Split Horizontal

```python
raccon_uno, raccon_dos = np.split(raccon_face_image,2)  # Horizontal split
plt.imshow(raccon_uno)
plt.show()
plt.imshow(raccon_dos)
plt.show()
```

## Split Vertical

```python
raccon_uno_vertical, raccon_dos_vertical = np.split(raccon_face_image,2, axis=1)  # Vertical split
plt.imshow(raccon_uno_vertical)
plt.show()
plt.imshow(raccon_dos_vertical)
plt.show()
```

## Concatenate horizontal

```python
plt.imshow(np.concatenate((raccon_uno_vertical,raccon_dos_vertical)))
plt.show()
```

## Concatenate vertical

```python
plt.imshow(np.concatenate((raccon_uno_vertical,raccon_dos_vertical), axis=1))
plt.show()
```

# Creditos
[Pluralsight](https://app.pluralsight.com/player?course=numpy-working-with-multidimensional-data&author=janani-ravi&name=65a7bc5d-54ab-4b87-b966-67794e77d2d5&clip=10&mode=live)
