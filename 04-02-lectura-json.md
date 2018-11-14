# Lectura

```python
import json
import pandas as pd
records = [
        ('Espresso','$5'),
        ('Capuccino','$10'),
]
data_frame = pd.DataFrame.from_records(
        records,
        columns= ['Coffe','Price']
        )

llaves_a_usarse =  ['id', 'all_artists', 'title', 'medium', 'dateText',
               'acquisitionYear', 'height', 'width', 'units']


def obtener_registros_de_archivos(path_archivo,keys_a_usarse):
    with open(path_archivo) as texto_json:
        contenido_json = json.load(texto_json)
    lista_valores_json_leido = []
    for llave in keys_a_usarse:
        lista_valores_json_leido.append(contenido_json[llave])
    return tuple(lista_valores_json_leido)

directorio_a_leer = 'C://Users//Adrian//Documents//Spyder//data//json'
ejemplo_json = directorio_a_leer + '//a//000//a00001-1035.json'

registro_ejemplo_json = obtener_registros_de_archivos(ejemplo_json,llaves_a_usarse)

registro_ejemplo_json_dt = pd.DataFrame.from_records([registro_ejemplo_json])

import os


def leer_registros_en_carpetas(keys_a_usarse):

    JSON_ROOT = 'C://Users//Adrian//Documents//Spyder//data//json'
    trabajos_de_arte_encontrados = []
    for path_raiz, lista_directorios, archivos in os.walk(JSON_ROOT):
        for archivo in archivos:
            if archivo.endswith('json'):
                registro_encontrado = obtener_registros_de_archivos(
                            os.path.join(path_raiz, archivo),
                            keys_a_usarse)
                trabajos_de_arte_encontrados.append(registro_encontrado)
            break
        
    df = pd.DataFrame.from_records(trabajos_de_arte_encontrados,
                                   columns=keys_a_usarse,
                                   index="id")
    return df


df = leer_registros_en_carpetas(llaves_a_usarse)

```
