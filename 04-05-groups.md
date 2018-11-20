# Groups

![Groups](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/Captura%20de%20pantalla%202018-11-20%20a%20la(s)%2017.37.55.png "Groups")

![Empty](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/Captura%20de%20pantalla%202018-11-20%20a%20la(s)%2017.41.46.png "Empty")

1. Agreggation
2. Transformation
3. Filtering

```python

import pandas as pd
import os
import numpy as np

data_frame_guardado = pd.read_pickle('C://Users//Adrian//Documents//Spyder//data//artwork_data_frame.pickle')

seccion_data_frame = data_frame_guardado.iloc[49980:50019,:].copy()

sdf_agrupado = seccion_data_frame.groupby('artist')

type(sdf_agrupado)

for name, group_fd in sdf_agrupado:
  print(name)
  print(group_fd)
  break


# Agregacion Minimo
for name, group_fd in sdf_agrupado:
  anio_minimo = group_fd['acquisitionYear'].min()
  print("{}:{}").format(name,anio_minimo)

# Transform
# -> Editar a mano
# Un caso donde no exista datos a inferir
# seccion_data_frame.loc[[11838:16441],'medium']





```
