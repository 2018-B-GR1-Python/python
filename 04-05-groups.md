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
# En este caso todos los valores existen, abrir el dataframe y seleccionar, editarle y cambiarle a "float"

def llenar_valores_vacios(series):
  valores_count = series.value_counts() # Sacar los valores
  if valores_count.empty:  # Revisar si algun valor esta vacio
    return series;  # Si ningun valor esta vacio, devolver la serie, no hay nada que hacer
  valores_mas_utilizados = valores_count.index[0]
  nuevo_valor_medium = series.fillna(valores_mas_utilizados)
  return nuevo_valor_medium

def transformar_todo_el_df_por_artista(df)
  group_dfs[]
  for name, group_df in df.groupby('artist'):
    df_lleno = group_df.copy()
    df_lleno.loc([ : , 'medium' ]) = llenar_valores_vacios(group_df['medium'])
    group_dfs.append(df_lleno)
  nuevo_df_llenado = pd.concat(group_dfs)
  return nuevo_df_llenado

# Probar la funcion
df_lleno_sin_valores_vacios = transformar_todo_el_df_por_artista(seccion_data_frame)


# Metodos de panda

medium_agrupados_por_artista = seccion_data_frame.groupby('artist')['medium']

seccion_data_frame.log[:,'medium'] = medium_agrupados_por_artista.transform(llenar_valores_vacios)

# Funcion de agregacion

df.groupby('artist').agg(np.min)  # Very Good performance 
df.groupby('artist').min()  # Best way in pandas

# Filtrados

agrupados_por_titulo = df.groupby('title')
titulos_contados = agrupados_por_titulo.size().sort_values(ascending = False)

condicion = lambda x: len(x.index)>1

dup_titles_df = agrupados_por_titulo.filter(condicion)

dup_titles_df.sort_values('title', inplace=True)




```
