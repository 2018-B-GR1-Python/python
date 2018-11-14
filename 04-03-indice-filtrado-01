# Basics

```python
import pandas as pd
import os
data_frame_guardado = pd.read_pickle('C://Users//Adrian//Documents//Spyder//data//artwork_data_frame.pickle')

# Obtener solo artistas

artistas_data_frame_con_repetidos = data_frame_guardado['artist']

artistas_object_sin_repetidos = pd.unique(artistas_data_frame_con_repetidos)

artistas_object_sin_repetidos

len(artistas_object_sin_repetidos)

serie_artistas_con_nombre_bacon_francis = data_frame_guardado['artist'] == 'Bacon, Francis'

# Devuelve el numero de falsos y verdaderos, el nombre del indice
# y el tipo de dato
serie_artistas_con_nombre_bacon_francis.value_counts()

# Otra forma

serie_artistas = data_frame_guardado['artist'].value_counts()
serie_artistas['Bacon, Francis']

data_frame_bacon_francis = data_frame_guardado[serie_artistas_con_nombre_bacon_francis]

len(data_frame_bacon_francis)

```
