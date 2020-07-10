# Introducción a Python

## Tipos de Datos y Operadores

En esta lección repasaremos acerca de:  

- Operadores
	- Aritméticos
	- De Asignación
	- De Comparación
	- Lógicos

- Tipos de Datos: Integers, Floats, Booleans, Strings

- Conversión de tipos de datos

- Funciones incorporadas (Built-in)

- Guías de estilo (Best Practices)

### Operadores

#### Aritméticos

-   `+` Suma
-   `-` Resta
-   `*` Multiplicación
-   `/` División
-   `%` Residuo (el remanente después de una división)
-   `**` Exponenciación
-   `//` Divide y redondea al entero más cercano

```python
100+200
```
  300

```python
150000-25000
```
  125000

```python
25*100
```
  2500  

```python
500/10
```
  50.0  

```python
9%2
```
  1  

```python
2**5
```
  32  

```python
1//3
```
  0  



#### Operadores de Asignación

![img_04_dt_01](images/img_04_dt_01.png)

```python
x = 3
x
```
  3  

```python
x += 2
x
```
  5  

```python
x -= 2
x
```
  3  

```python
x,y,z = 5,8,10
print(z,y,x)
```
  10 8 5  



### Operadores de Comparación

| Símbolo/Caso de Uso | Booleano | Operación |
|---|---|---|
| 5 < 3	| False	| Menor que 		|
| 5 > 3	| True	| Mayor que	|
| 3 <= 3| True	| Menor o igual a	|
| 3 >= 5| False	| Mayor o igual a	|
| 3 == 5| False	| Igual a 		|
| 3 != 5| True 	| No igual a 		|



### Operadores Lógicos

| Símbolo/Caso de Uso | Booleano | Operación |
|--|--|--|
| 5 < 3 `and` 5 == 5	| False	| `and` evalúa si todas las declaraciones son ciertas (True)|
| 5 < 3 `or` 5 == 5	| True	| `or` evalúa si alguna de las declaraciones es cierta (True)|
| `not` 5 < 3		| True	| `not` Invierte el valor del resultado|



### Tipos de Datos

#### Enteros y Flotantes (Integer, Float)

-   **int** - para valores enteros
-   **float** - para valores decimales o de punto flotante
-   **bool** - para valores lógicos
-   **str** - para cadenas de texto

```python
X = 50
X
```
  50  

```python
type(X)
```
  int  

```python
y=12.2
y
```
  12.2  

```python
type(y)
```
  float  

```python
z=(3<5)
z
```
  True  

```python
type(z)
```
  bool  

```python
v='texto'
v
```
  'texto'  

```python
type(v)
```
  str  



#### Cadena (String)

Las cadenas en Python se muestran como el tipo variable `str`. Se puede definir una cadena con comillas dobles `"` o comillas simples `'`  

Si la cadena que se está creando contiene uno de estos dos caracteres, se debe tener cuidado para asegurarse de que el código no genere un error.  

```python
mi_cadena = '¡esta es una cadena!'
mi_cadena2 = "¡esta también es un cadena!!!"
mi_cadena
mi_cadena2
```
  '¡esta también es un cadena!!!'  

```python
print(mi_cadena,mi_cadena2,sep='\n')
```
  ¡esta es una cadena!  
  ¡esta también es un cadena!!!  



Podemos incluir el caracter `\` en una cadena para incluir comillas simples como parte de la misma cadena:  

```python
esta_cadena = 'El título del libro es \'Don Quijote\'.'
print(esta_cadena)
```
   El título del libro es 'Don Quijote'.  



### Operaciones con cadenas de texto
#### Concatenar cadenas

```python
primera_palabra = 'Hola'
segunda_palabra = 'Mundo'
print(primera_palabra + segunda_palabra)
```
   HolaMundo  

```python
print(primera_palabra + ' ' + segunda_palabra)
```
  Hola Mundo  


#### Acceder a un elemento de la cadena

```python
primera_palabra[0]
```
  'H'  

```python
primera_palabra[-1]
```
  'a'  


#### Multiplicar cadenas

```python
print(primera_palabra * 5)
```
  HolaHolaHolaHolaHola  


#### Longitud de cadenas

```python
L=len(primera_palabra)
L
```
  4  

```python
D=len(primera_palabra)/len(segunda_palabra)
D
```
  0.8  


#### Dividir una cadena de texto
El método `split()` divide una cadena en palabras y lo devuelve como una lista.  

```python
nueva_cadena = "La vaca saltó sobre la luna."
nueva_cadena.split()
```
  ['La', 'vaca', 'saltó', 'sobre', 'la', 'luna.']  


Especificando un separador y limitando el número de divisiones:  

```python
nueva_cadena.split(' ', 3)
```
  ['La', 'vaca', 'saltó', 'sobre la luna.']  


Para conocer todos los métodos que podemos usar, véase la [documentación de Python](https://docs.python.org/3.7/library/stdtypes.html#string-methods).  


#### Reemplazar o complementar partes de una cadena

El método cadena `format()` es uno de los métodos más útiles, que estaremos usando en el transcurso de nuestro curso. Este método reemplaza o complementa partes de una cadena, con los valores de otros objetos o variables.  

```python
print("Juan tiene {} globos".format(27))
```
  Juan tiene 27 globos  

```python
animal = "perro"
accion = "muerde"
print("¿Tu {} {}?".format(animal, accion))
```
  ¿Tu perro muerde?  

```python
maria_cadena = "A Maria le gustan {} y {}"
print(maria_cadena.format("las matemáticas", "la estadística"))
```
  A Maria le gustan las matemáticas y la estadística  

```python
print("¿Tu %s %s?" % (animal, accion))
```
  ¿Tu perro muerde?  


### Conversión de datos

Para poder convertir un tipo de datos a otro, podemos usar las siguientes funciones de conversión (cast):  

```python
print(str(14))
print(int(4.7))
print(float(5))
print(bool(1))
```
  14  
  4  
  5.0  
  True  


## Estructuras de Datos

En esta lección conoceremos los diferentes tipos de estructuras de datos usados en Python:  

- Tipos de estructuras de datos:
	- Listas
	- Tuplas
	- Conjuntos
	- Diccionarios
	- Estructuras de datos compuestas

- Operadores  de Identidad


### Listas

Las **estructuras de datos** son contenedores que organizan y agrupan los tipos de datos de diferentes formas, las **listas** son una de las estructuras de datos más comunes y básicas en Python.  
Las listas deben ser creadas usando **corchetes** y pueden contener cualquier combinación de los tipos de datos (numérico y alfanumérico).  

#### Crear una lista

```python
lista_de_elementos = [1, 3.4, 'una cadena', True]
lista_de_elementos
```
  [1, 3.4, 'una cadena', True]  


#### Acceder a un elemento de la lista

```python
lista_de_elementos[0]
```
  1  

```python
lista_de_elementos[-1]
```
  True  

```python
lista_de_elementos[len(lista_de_elementos)]
```
  ---------------------------------------------------------------------------

  IndexError                                Traceback (most recent call last)

  <ipython-input-40-dcf8dd71bbd3> in <module>
  ----> 1 lista_de_elementos[len(lista_de_elementos)]


  IndexError: list index out of range  


```python
lista_de_elementos[len(lista_de_elementos)-1]
```
  True  


#### Rebanar y cortar (Slice & Dice)

```python
lista_de_elementos = [1, 3.4, 'una cadena', True]
lista_de_elementos[1:2]
```
  [3.4]  

#### IN o NOT IN

```python
'esta' in 'esta es una cadena'
```
  True  

```python
'en' in 'esta es una cadena'
```
  True  

```python
'esuna' in 'esta es una cadena'
```
  False  

```python
5 not in [1, 2, 3, 4, 6]
```
  True  

```python
5 in [1, 2, 3, 4, 6]
```
  False  


## Mutabilidad y Orden

El concepto de **mutabilidad** en Python indica si podemos cambiar o no un objeto, una vez que se ha creado. Si un objeto (como una lista o cadena) se puede cambiar (como una lista), se considera **mutable**.  

Sin embargo, si un objeto no se puede cambiar, entonces el objeto se considera **inmutable**.  

```python
# Ejemplo de mutabilidad:
mi_lista = [1, 2, 3, 4, 5]
mi_lista[0] = 'uno'
print(mi_lista)
```
  ['uno', 2, 3, 4, 5]  

```python
# Ejemplo de un objeto inmutable:
mi_cadena = "Hola Mundo"
mi_cadena[0] = 'M'
print(mi_cadena)
```
  ---------------------------------------------------------------------------
  TypeError                                 Traceback (most recent call last)
  <ipython-input-49-f23bf4ad3a22> in <module>
        1 # Ejemplo de un objeto inmutable:
        2 mi_cadena = "Hola Mundo"
  ----> 3 mi_cadena[0] = 'M'
        4 print(mi_cadena)

  TypeError: 'str' object does not support item assignment  


El concepto de **orden** en Python indica, si la posición de un elemento en el objeto se puede utilizar para accederlo. Ambas cadenas y listas están ordenadas. Podemos usar el orden para acceder partes de una lista y cadena.  

En lecciones posteriores veremos que en diferentes tipos de datos, es importante tener en cuenta las propiedades de mutabilidad y ordenamiento, para poder accederlos y manipularlos.  


## Funciones básicas

1. `len()` devuelve el número de elementos que hay en una lista.

2. `max()` devuelve el elemento más grande de la lista. La forma en que se determina el elemento más grande, depende del tipo de objetos que estén en la lista.
	- El elemento máximo en una lista de números es el número más grande.
	- El máximo de elementos en una lista de cadenas es el último elemento ordenado alfabéticamente.
	- La función `max()` no está definida para listas que contienen elementos de diferentes tipos no compatibles.

3. `min()` devuelve el elemento más pequeño de una lista. `min()` es lo opuesto a `max()`, que devuelve el elemento más grande de una lista.

4. `sorted()` devuelve una copia de una lista en orden de menor a mayor, dejando la lista sin cambios.

5. `join()`. Es un método de cadena que toma una lista de cadenas como argumento y devuelve una cadena que consta de los elementos unidos por un separador.

6. `append()`. Este método agrega un elemento al final de una lista.

7. `pop()`. Este método elimina un elemento de una lista. Si no se especifica un valor, se elimina el último elemento (en otros tipos de estructuras, si no se define un valor puede eliminar el primer elemento).

8. `split()`. Divide una cadena y como resultado devuelve una lista.


```python
mi_lista_de_cadenas = ['Z', 'ALZ', 'B']
max(mi_lista_de_cadenas)
```
  'Z'  

```python
sorted(mi_lista_de_cadenas)
```
  ['ALZ', 'B', 'Z']  

```python
mi_separador= "\n"
mi_lista_de_cadenas = ["Este", "es", "mi", "curso", "Python"]
nueva_cadena = mi_separador.join(mi_lista_de_cadenas)
print(nueva_cadena)
```
  Este  
  es  
  mi  
  curso  
  Python  

```python
letras = ['a', 'b', 'c', 'd']
letras.append('z')
print(letras)
```
  ['a', 'b', 'c', 'd', 'z']  

```python
letras = ['a', 'b', 'c', 'd']
letras.pop(0)
print(letras)
```
  ['a', 'b', 'c', 'd', 'z']  

```python
verso = "si puedes mantener la cabeza en su sitio cuando todos a tu alrededor la pierden y te culpan a ti   si puedes seguir creyendo en ti mismo cuando todos dudan de ti     pero también aceptas que tengan dudas   si puedes esperar y no cansarte de la espera      o si siendo engañado no respondes con engaños   o si siendo odiado no incurres en el odio      Y aun así no te las das de bueno ni de sabio"
print(verso, "\n")
verso_lista = verso.split()
print(verso_lista, '\n')
```
  si puedes mantener la cabeza en su sitio cuando todos a tu alrededor la pierden y te culpan a ti   si puedes seguir creyendo en ti mismo cuando todos dudan de ti     pero también aceptas que tengan dudas   si puedes esperar y no cansarte de la espera      o si siendo engañado no respondes con engaños   o si siendo odiado no incurres en el odio      Y aun así no te las das de bueno ni de sabio  

  ['si', 'puedes', 'mantener', 'la', 'cabeza', 'en', 'su', 'sitio', 'cuando', 'todos', 'a', 'tu', 'alrededor', 'la', 'pierden', 'y', 'te', 'culpan', 'a', 'ti', 'si', 'puedes', 'seguir', 'creyendo', 'en', 'ti', 'mismo', 'cuando', 'todos', 'dudan', 'de', 'ti', 'pero', 'también', 'aceptas', 'que', 'tengan', 'dudas', 'si', 'puedes', 'esperar', 'y', 'no', 'cansarte', 'de', 'la', 'espera', 'o', 'si', 'siendo', 'engañado', 'no', 'respondes', 'con', 'engaños', 'o', 'si', 'siendo', 'odiado', 'no', 'incurres', 'en', 'el', 'odio', 'Y', 'aun', 'así', 'no', 'te', 'las', 'das', 'de', 'bueno', 'ni', 'de', 'sabio']  


### Tuplas

Una **tupla** es otro tipo de estructura útil. Es un tipo de datos para secuencias **inmutables, ordenadas** de elementos. A menudo se usan para almacenar información relacionada  


```python
ubicacion = (13.4125, 103.866667)
print("Latitud:", ubicacion[0])
print("Longitud:", ubicacion[1])
```
  Latitud: 13.4125  
  Longitud: 103.866667  

```python
ubicacion[0] = 12.1
print("Latitud:", ubicacion[0])
```
  ---------------------------------------------------------------------------
  TypeError                                 Traceback (most recent call last)
  <ipython-input-57-3de36f8b6071> in <module>
  ----> 1 ubicacion[0] = 12.1
        2 print("Latitud:", ubicacion[0])

  TypeError: 'tuple' object does not support item assignment  


### Conjunto

Un **conjunto** es un tipo de datos para colecciones **mutables, no ordenadas** de elementos **únicos**. Una aplicación de un conjunto es eliminar rápidamente los duplicados de una lista.  

```python
numeros = [1, 2, 6, 3, 1, 1, 6]
numeros_unicos = set(numeros)
print(numeros_unicos)
```
  {1, 2, 3, 6}  

```python
type(numeros_unicos)
```
  set  


## Diccionarios

Un diccionario es un tipo de dato **mutable** que almacena asignaciones de claves únicas a valores  

```python
elementos = {"hidrogeno": 1, "helio": 2, "carbono": 6}
print(elementos["helio"])
elementos["litio"] = 3  # Insertar "litio" con el valor 3 dentro del diccionario
print(elementos)
```
  2  
  {'hidrogeno': 1, 'helio': 2, 'carbono': 6, 'litio': 3}  

```python
print("carbono" in elementos)
print(elementos.get("litio"))
print(elementos.get("hidrogeno"))
print(elementos["hidrogeno"])
```
  True  
  3  
  1  
  1  


# Estructuras de datos compuestas

Una característica interesante en Python es el poder incluir contenedores dentro de otros contenedores, para crear estructuras de datos compuestas.  

```python
elementos = {"hidrogeno": {"numero": 1,
                         "peso": 1.00794,
                         "simbolo": "H"},
                 "helio": {"numero": 2,
                         "peso": 4.002602,
                         "simbolo": "He"}}
elementos
```
  {'hidrogeno': {'numero': 1, 'peso': 1.00794, 'simbolo': 'H'},
   'helio': {'numero': 2, 'peso': 4.002602, 'simbolo': 'He'}}  

```python
helio = elementos["helio"]
hidrogeno_peso = elementos["hidrogeno"]["peso"]
print(helio)
print(hidrogeno_peso)
```
  {'numero': 2, 'peso': 4.002602, 'simbolo': 'He'}  
  1.00794  

```python
oxigeno = {"numero":8,"peso":15.999,"simbolo":"O"}  # crear un diccionario
elementos["oxigeno"] = oxigeno  # asignar el diccionario al diccionario compuesto
print('elementos = ', elementos)
```
  elementos =  {'hidrogeno': {'numero': 1, 'peso': 1.00794, 'simbolo': 'H'}, 'helio': {'numero': 2, 'peso': 4.002602, 'simbolo': 'He'}, 'oxigeno': {'numero': 8, 'peso': 15.999, 'simbolo': 'O'}}  


En resumen se tiene:  

| Estructura de Datos | Ordenado | Mutable | Constructor | Ejemplo |
|--|--|--|--|--|
| Lista 	| Si | Si | `[ ]` o `list()`	| `[5.7, 4, 'si', 5.7]` |
| Tupla 	| Si | No | `( )` o `tuple()`	| `(5.7, 4, 'si', 5.7)` |
| Conjunto	| No | Si | `{}`* o `set()`	| `{5.7, 4, 'si'}`	 |
| Diccionario 	| No | No | `{ }` o `dict()`	| `{'Jun': 75, 'Jul': 89}` |


 [**Siguiente Lección**](Lecci%C3%B3n%2004%20-%20Introducci%C3%B3n%20a%20Python%202.md)    
