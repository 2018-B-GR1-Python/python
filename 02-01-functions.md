# Functions

```python
def sumar_dos_numeros(numUno,numDos):
    return numUno + numDos
```

```python
def imprimir_nombre_y_apellido(nombre, apellido="Eguez"):
    print(f"{nombre} {apellido}")
```

```python
imprimir_nombre_y_apellido(apellido="Eguez", nombre="Vicente")
```

```python
def sumar_varios_numeros(*numeros):
    acumulado = 0
    for numero in numeros:
        acumulado = acumulado + numero
    return acumulado
```

```python
def imprimir_nombre_apellido(**key_word_arguments): # **kwargs
    print(key_word_arguments["nombre"])
    print(key_word_arguments["apellido"])
```

```python
imprimir_nombre_apellido(nombre="Adrian", apellido="Eguez")
```

```python
nombre = input("Ingresa tu nombre")
```


```python
def imprimirNombre(nombre):
    def imprimirEnMayuscula():
        return nombre.upper()  # Tiene acceso al closure, a la variable nombre en su funcion contenedora 
    print(imprimirEnMayuscula())
    
    
imprimirNombre("Vicente")
```

```python
def read_file(path):
    try:
        file_opened = open(path, "r") # r -> read
        print(file_opened)
        # print(file_opened.readlines()) // no se puede leer dos veces
        lines = file_opened.readlines()
        print(lines)
        for line in lines:
            print("Line content: ", line)
        file_opened.close()
    except Exception:
        print("No se pudo leer el archivo")



def write_file(path):
    try:
        file_opened = open(path, "a") # a -> append w -> overwrite rb ->  reading binary wn -> writing binary
        file_opened.write("nuevo contenido\n")
        file_opened.close()
    except Exception:
        print("No se pudo leer el archivo")


read_file("students.txt")

write_file("students.txt")

```

