# Introducción a Python

## Sentencias Condicionales

### IF

Una sentencia `if` es una declaración condicional que ejecuta u omite código en función de si una condición es verdadera o falsa.


```python
saldo_telefono=0
saldo_bancario=0
if saldo_telefono < 5:
    saldo_telefono += 10
    saldo_bancario -= 10
print(saldo_telefono)
print(saldo_bancario)
```

10
-10


Analicemos esto:

- Una instrucción `if` comienza con la palabra clave `if`, seguida de la condición a evaluar, en este caso `saldo_telefono < 5`, y luego **dos puntos**. La condición se especifica en una expresión booleana que se evalúa como Verdadero (`True`) o Falso (`False`).  

- Después de esta línea hay un bloque de código **indentado** que se ejecutará si esa condición es verdadera. Si no, el código en este bloque simplemente se omite.

### ELSE IF

Además de la cláusula `if`, hay otras dos cláusulas opcionales que a menudo se usan con una declaración: `else` y `elif`. Veamos un ejemplo


```python
estacion = 'primavera'
if estacion == 'primavera':
    print('¡planta el jardín!')
elif estacion == 'verano':
    print('¡riega el jardín!')
elif estacion == 'otoño':
    print('¡cosecha el jardín!')
elif estacion == 'invierno':
    print('¡quédate en casa!')
else:
    print('estación no reconocida')
```
¡planta el jardín!


### Expresiones Booleanas complejas

Para condiciones complejas podemos usar los operadores lógicos `and`, `or` y `not`.

```python
no_inscrito = 0
ubicacion = 'USA'
if (not no_inscrito) and (ubicacion == "USA" or ubicacion == "CAN"):
    print("mandar correo electrónico")
```
mandar correo electrónico

```python
if True:
    print("Este código indentado siempre será ejecutado.")
```
Este código indentado siempre será ejecutado.

```python
# Un mal ejemplo
hace_frio=1
if hace_frio == True:
    print("¡El clima está frio!")
```
¡El clima está frio!

```python
# Un buen ejemplo
if hace_frio:
    print("¡El clima está frio!")
```
¡El clima está frio!


## Bucles
Un objeto **iterable** es un objeto que puede devolver uno de sus elementos a la vez. Estos objetos pueden incluir tipos de secuencia, como cadenas, listas y tuplas, así como tipos que no son de secuencia, como diccionarios y archivos.


### Bucles For

```python
ciudades = ['CDMX', 'Monterrey', 'Guadalajara', 'Aguascalientes']
for ciudad in ciudades:
    print(ciudad)
print("¡Listo!")
```
CDMX
Monterrey
Guadalajara
Aguascalientes
¡Listo!


#### Usando la función `range()` con bucles `for`

`range ()` es una función incorporada, utilizada para crear una secuencia iterativa de números. Con frecuencia usará `range ()` con un bucle `for` para repetir una acción un cierto número de veces.


```python
for i in range(3):
    print("¡Hola!")
```
¡Hola!
¡Hola!
¡Hola!


#### range(start=0, stop, step=1)

La función `range()` toma **tres argumentos enteros**, el primero y el tercero son opcionales:  

- `start`. Es el primer número de la secuencia. Si no se especifica, `start` por defecto es 0.  

- `stop`. Es 1 más que el último número de la secuencia. Este argumento debe ser especificado.  

- `step`. Es la diferencia entre cada número en la secuencia. Si no se especifica, el `step` predeterminado es 1.

#### Creando y modificando listas


```python
ciudades = ['cdmx', 'monterrey', 'guadalajara', 'aguascalientes']
ciudades_mayusculas = []

for ciudad in ciudades:
    ciudades_mayusculas.append(ciudad.title())
print(ciudades_mayusculas)
```
['Cdmx', 'Monterrey', 'Guadalajara', 'Aguascalientes']

```python
ciudades = ['cdmx', 'monterrey', 'guadalajara', 'aguascalientes']

for indice in range(len(ciudades)):
    ciudades[indice] = ciudades[indice].title()

ciudades
```
['Cdmx', 'Monterrey', 'Guadalajara', 'Aguascalientes']



#### Construyendo Diccionarios


```python
titulo_libro =  ['don', 'quijote', 'de', 'la', 'mancha', 'cien', 'años', 'de', 'soledad','crimen','y','castigo','el','conde','de','montecristo','el','principito']
```

```python
contador_palabras = {}
```


```python
for palabra in titulo_libro:
    if palabra not in contador_palabras:
        contador_palabras[palabra] = 1
    else:
        contador_palabras[palabra] += 1
print(contador_palabras)
```
{'don': 1, 'quijote': 1, 'de': 3, 'la': 1, 'mancha': 1, 'cien': 1, 'años': 1, 'soledad': 1, 'crimen': 1, 'y': 1, 'castigo': 1, 'el': 2, 'conde': 1, 'montecristo': 1, 'principito': 1}


#### Usando el método `get()`


```python
titulo_libro =  ['don', 'quijote', 'de', 'la', 'mancha', 'cien', 'años', 'de', 'soledad','crimen','y','castigo','el','conde','de','montecristo','el','principito']
```


```python
contador_palabras = {}
for palabra in titulo_libro:
    contador_palabras[palabra] = contador_palabras.get(palabra, 0) + 1
print(contador_palabras)
```
{'don': 1, 'quijote': 1, 'de': 3, 'la': 1, 'mancha': 1, 'cien': 1, 'años': 1, 'soledad': 1, 'crimen': 1, 'y': 1, 'castigo': 1, 'el': 2, 'conde': 1, 'montecristo': 1, 'principito': 1}


#### Iterando a través de Diccionarios


```python
elenco = {
           "Jerry Seinfeld": "Jerry Seinfeld",
           "Julia Louis-Dreyfus": "Elaine Benes",
           "Jason Alexander": "George Costanza",
           "Michael Richards": "Cosmo Kramer"
         }
```


```python
for llave in elenco:
    print(llave)
```
Jerry Seinfeld
Julia Louis-Dreyfus
Jason Alexander
Michael Richards

```python
print(elenco.items())
for llave, valor in elenco.items():
    print("Actor: {}    Personaje: {}".format(llave, valor))
```

dict_items([('Jerry Seinfeld', 'Jerry Seinfeld'), ('Julia Louis-Dreyfus', 'Elaine Benes'), ('Jason Alexander', 'George Costanza'), ('Michael Richards', 'Cosmo Kramer')])
Actor: Jerry Seinfeld    Personaje: Jerry Seinfeld
Actor: Julia Louis-Dreyfus    Personaje: Elaine Benes
Actor: Jason Alexander    Personaje: George Costanza
Actor: Michael Richards    Personaje: Cosmo Kramer


### Bucles While

Los bucles `for` son un ejemplo de "**iteración definida**", lo que significa que el cuerpo del bucle se ejecuta un número predeterminado de veces. Esto difiere de una "**iteración indefinida**", que es cuando un ciclo se repite un número desconocido de veces y termina cuando se cumple alguna condición, que es lo que sucede en un bucle `while`.


```python
baraja = [4, 11, 8, 5, 13, 2, 8, 10]
mano = []
while sum(mano) < 17:
    mano.append(baraja.pop())
    print(mano)
    print(sum(mano))
```

    [10]
    10
    [10, 8]
    18


### Break & Continue

A veces necesitamos más control sobre cuándo debe terminar un bucle, o saltar una iteración. En estos casos, usamos las palabras clave `break` y `continue`, que se pueden usar tanto en bucles `for` como `while`.  

- `break` termina un bucle  

- `continue` omite una iteración de un bucle  



```python
titulares = ["Oso Comido por un Hombre",
             "Legisladores Anuncian Nuevas Leyes",
             "Ciudadano Descubre Violencia Inherente en el Sistema",
             "Gato Rescata a Bombero Atorado en Arbol",
             "Valiente Caballero Huye del Dragón",
             "Libro del Mes: Totalmente Horrible"]

teletipo_noticias = ""
for titular in titulares:
    teletipo_noticias += titular + " "
    if len(teletipo_noticias) >= 140:
        teletipo_noticias = teletipo_noticias[:140]
        break

print(teletipo_noticias)
```
Oso Comido por un Hombre Legisladores Anuncian Nuevas Leyes Ciudadano Descubre Violencia Inherente en el Sistema Gato Rescata a Bombero Ator


## Funciones

Una Función permite reutilizar código para usarlo una y otra vez, de forma fácil.

### Definir una Función


```python
def volumen_cilindro(altura, radio):
    pi = 3.14159
    return altura * pi * radio ** 2
```

```python
volumen_cilindro(10, 3)
```
282.7431


### Argumentos por Default

Podemos agregar argumentos predeterminados en una función, para tener valores por defecto para argumentos o parámetros que no están especificados en una llamada a la función.


```python
def volumen_cilindro(altura, radio=5):
    pi = 3.14159
    return altura * pi * radio ** 2
```

```python
volumen_cilindro(10, 7)  # por posición
volumen_cilindro(altura=10, radio=7)  # por nombre de argumento
```
1539.3791


### Alcance de Variables

El alcance de una variable se refiere a aquellas partes de un programa que pueden hacer referencia a una variable.

Es importante tener en cuenta el alcance cuando se usan variables en funciones. Si se crea una variable dentro de una función, solo se puede usar dentro de esa función. No es posible acceder a él fuera de esa función.


```python
# Esto provocará un error
def una_funcion():
    palabra = "hola"
print(palabra)
```

---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-1-3328aca760a1> in <module>
      2     palabra = "hola"
      3
----> 4 print(palabra)

NameError: name 'palabra' is not defined


```python
palabra = "hola"

def una_funcion():
    print(palabra)

una_funcion()
```
hola


## Expresiones Lambda

Podemos usar expresiones lambda para crear funciones anónimas. Es decir, funciones que no tienen nombre.

Son útiles para crear funciones rápidas que no se necesitan más adelante en el código. Esto puede ser especialmente útil para funciones de orden superior o funciones que toman otras funciones como argumentos.

Una función normal:

```python
def multiplica(x, y):
    return x * y
```

puede ser reducida a:

```python
multiplica = lambda x, y: x * y
multiplica(2,10)
```
20

```python
numeros = [
              [34, 63, 88, 71, 29],
              [90, 78, 51, 27, 45],
              [63, 37, 85, 46, 22],
              [51, 22, 34, 11, 18]
           ]

promedios = list(map(lambda x: sum(x) / len(x), numeros))
print(promedios)
```
[57.0, 58.2, 50.6, 27.2]

```python
ciudades = ["CDMX", "Monterrey", "Guadalajara", "Aguascalientes", "Oaxaca", "Cancún"]

ciudades_menores = list(filter(lambda x: len(x) < 10, ciudades))
print(ciudades_menores)
```
['CDMX', 'Monterrey', 'Oaxaca', 'Cancún']


## ¡¡¡Felicidades ahora ya tienes los conceptos basicos de Python!!!


 [**Ejercicios**](Ejercicios/Python/Python%20Ejercicios.md)    
