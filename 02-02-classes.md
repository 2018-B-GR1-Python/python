# Classes
  
```python
class Usuario:
    pass
    
usuario = Usuario()

print(usuario)
```


```python
class Usuario:

    def __init__(self):
        print("Inicializando")

    def saludar(self, nombre):
        print(f"Hola {nombre}")

    def __str__(self):
        return "To string"


usuario = Usuario()

usuario.saludar("Adrian")
print(usuario)
```


```python
class Usuario:

    nacionalidad = "Ecuatoriano"

    def __init__(self, nombre, apellido=""):
        self.nombre = nombre
        self.apellido = apellido
        print("Inicializando")

    def saludar(self, nombre):
        print(f"Hola {nombre}")

    def __str__(self):
        return f"Soy {self.nombre} {self.apellido}"


usuario = Usuario("Adrian", "Eguez")

usuario.saludar("Vicente")

print(usuario)

print(Usuario.nacionalidad)
```


```python
class Usuario:

    nacionalidad = "Ecuatoriano"

    def __init__(self, nombre, apellido=""):
        self.nombre = nombre
        self.apellido = apellido
        print("Inicializando")

    def saludar(self, nombre):
        print(f"Hola {nombre}")

    def capitalizar(self):
        return self.nombre.upper()

    def __str__(self):
        return f"Soy {self.nombre} {self.apellido}"


usuario = Usuario("Adrian", "Eguez")

usuario.saludar("Vicente")

print(usuario)

print(Usuario.nacionalidad)
print(usuario.capitalizar())

class Vendedor(Usuario):
    nacionalidad = "Colombiano"

    def capitalizar(self):
        capitalizado = super().capitalizar()
        return "CAP " + capitalizado


richard = Vendedor("Richard")

print(richard, Vendedor.nacionalidad)
print(richard.capitalizar())
```












