# loc iloc

```python
import pandas as pd
import os
data_frame_guardado = pd.read_pickle('C://Users//Adrian//Documents//Spyder//data//artwork_data_frame.pickle')


Selecting data by row numbers (.iloc)
# Selecting data by label or by a conditional statment (.loc)

data_frame_guardado.loc[1035,'artist']
data_frame_guardado.iloc[0,0]
data_frame_guardado.iloc[0,:]
data_frame_guardado.iloc[0:2,0:2]

data_frame_guardado['height'] * data_frame_guardado['width']  # Error porque son de tipo objeto

data_frame_guardado['width'].sort_values().head()
data_frame_guardado['width'].sort_values().tail()


# Convertir a numero
pd.to_numeric(data_frame_guardado['width'])  # Error comun en procesamiento de datos
pd.to_numeric(data_frame_guardado['width'], errors = 'coerce')  # Si encuentra un valor que no es un numero le convierte a NaN
pd.to_numeric(data_frame_guardado['height'], errors = 'coerce')

# Convertir

data_frame_guardado.loc[:,'width'] = pd.to_numeric(data_frame_guardado['width'])
data_frame_guardado.loc[:,'height'] = pd.to_numeric(data_frame_guardado['height'], errors = 'coerce')

data_frame_guardado['height'] * data_frame_guardado['width']  # Funciona
data_frame_guardado['units'].value_counts()  # las unidades


area = data_frame_guardado['height'] * data_frame_guardado['width']

data_frame_guardado = data_frame_guardado.assign(area=area)

data_frame_guardado['area'].max()

id_mas_grande = data_frame_guardado['area'].idxmax()

data_frame_guardado.loc[id_mas_grande,:]

# Como buena practica usar iloc y loc en todos los casos.

```
