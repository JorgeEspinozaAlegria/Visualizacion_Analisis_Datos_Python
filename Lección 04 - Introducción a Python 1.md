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

![img_04_dt_01](data/img_04_dt_01.png)



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
    

<div style="text-align: left"> 
    
### Operadores de Comparación


| Símbolo/Caso de Uso | Booleano | Operación |
|---|---|---|
| 5 < 3	| False	| Menor que 		|
| 5 > 3	| True	| Más grande que	|
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
```


```python
type(v)
```




    str



#### Cadena (String)

Las cadenas en Python se muestran como el tipo variable `str`. Se puede definir una cadena con comillas dobles `"` o comillas simples `'`

Si la cadena que está creando contiene uno de estos dos caracteres, se debe tener cuidado para asegurarse que el código no genere un error.



```python
my_string = 'this is a string!'
my_string2 = "this is also a string!!!"
my_string
my_string2
```




    'this is also a string!!!'




```python
print(my_string,my_string2,sep='\n')
```

    this is a string!
    this is also a string!!!
    

Podemos incluir el caracter `\` en una cadena para incluir comillas simples como parte de la misma cadena:


```python
this_string = 'Simon\'s skateboard is in the garage.'
print(this_string)

```

    Simon's skateboard is in the garage.
    

### Operaciones con cadenas de texto
#### Concatenar cadenas


```python
first_word = 'Hello'
second_word = 'There'
print(first_word + second_word)
```

    HelloThere
    


```python
print(first_word + ' ' + second_word)
```

    Hello There
    

#### Acceder a un elemento de la cadena


```python
first_word[0]
```




    'H'




```python
first_word[-1]
```




    'o'



#### Multiplicar cadenas


```python
print(first_word * 5)
```

    HelloHelloHelloHelloHello
    

#### Longitud de cadenas


```python
L=len(first_word)
L
```




    5




```python
D=len(first_word)/len(second_word)
D
```




    1.0



#### Dividir una cadena de texto
El método `split()` divide una cadena en palabras y lo devuelve como una lista.


```python
new_str = "The cow jumped over the moon."
new_str.split()
```




    ['The', 'cow', 'jumped', 'over', 'the', 'moon.']



Especificando un separador y limitando el número de divisiones:


```python
new_str.split(' ', 3)
```




    ['The', 'cow', 'jumped', 'over the moon.']



Para conocer todos los métodos que podemos usar, véase la [documentación de Python](https://docs.python.org/3.7/library/stdtypes.html#string-methods).

#### Reemplazar o complementar partes de una cadena

El método cadena `format()` es uno de los métodos más útiles y que estaremos usando en el transcurso de nuestro curso. Este método reemplaza o complementa partes de una cadena con los valores de otros objetos o variables.


```python
print("Mohammed has {} balloons".format(27))
```

    Mohammed has 27 balloons
    


```python
animal = "dog"
action = "bite"
print("Does your {} {}?".format(animal, action))
```

    Does your dog bite?
    


```python
maria_string = "Maria loves {} and {}"
print(maria_string.format("math", "statistics"))
```

    Maria loves math and statistics
    


```python
print("Does your %s %s?" % (animal, action)) 
```

    Does your dog bite?
    

### Conversión de datos

Para poder convertir un tipo de datos a otro podemos usar las siguientes funciones de conversión (cast):



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
list_of_elements = [1, 3.4, 'a string', True]
list_of_elements
```




    [1, 3.4, 'a string', True]



#### Acceder a un elemento de la lista


```python
list_of_elements[0]
```




    1




```python
list_of_elements[-1]
```




    True




```python
list_of_elements[len(list_of_elements)]
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-40-dcf8dd71bbd3> in <module>
    ----> 1 list_of_elements[len(list_of_elements)]
    

    IndexError: list index out of range



```python
list_of_elements[len(list_of_elements)-1]
```




    True



#### Rebanar y cortar (Slice & Dice)


```python
list_of_elements = [1, 3.4, 'a string', True]
list_of_elements[1:2]

```


```python
list_of_elements = [1, 3.4, 'a string', True]
list_of_elements[1:2]
```


```python
#### IN o NOT IN

'this' in 'this is a string'
True
>>> 'in' in 'this is a string'
True
>>> 'isa' in 'this is a string'
False
>>> 5 not in [1, 2, 3, 4, 6]
True
>>> 5 in [1, 2, 3, 4, 6]
False
```


```python
'this' in 'this is a string'
```


```python
'in' in 'this is a string'
```


```python
'isa' in 'this is a string'
```


```python
5 not in [1, 2, 3, 4, 6]
```


```python
5 in [1, 2, 3, 4, 6]
```

## Mutabilidad y Orden

El concepto de **mutabilidad** en Python indica si podemos o no cambiar un objeto una vez que se ha creado. Si un objeto (como una lista o cadena) se puede cambiar (como una lista), se considera **mutable**.

Sin embargo, si un objeto no se puede cambiar, entonces el objeto se considera **inmutable**.



```python
# Ejemplo de mutabilidad:

my_list = [1, 2, 3, 4, 5]
my_list[0] = 'one'
print(my_list)
```


```python
# Ejemplo de un objeto inmutable:
my_string = "Hello World"
my_string[0] = 'M'
```

El concepto de **orden** en Python indica si la posición de un elemento en el objeto se puede utilizar para accederlo. Ambas cadenas y listas están ordenadas. Podemos usar el orden para acceder a partes de una lista y cadena.

En lecciones posteriores veremos que, diferentes tipos de datos, cuyas propiedades de mutabilidad y ordenamiento, son importantes de tener en cuenta para poder acceder a ellos y manipularlos.

## Funciones básicas

1. `len()` devuelve el número de elementos que hay en una lista.

2. `max()` devuelve el elemento más grande de la lista. La forma en que se determina el elemento más grande depende del tipo de objetos que estén en la lista.
	- El elemento máximo en una lista de números es el número más grande.
	- El máximo de elementos en una lista de cadenas es el último elemento ordenado alfabéticamente.
	- La función `max()` no está definida para listas que contienen elementos de diferentes tipos no compatibles.

3. `min()` devuelve el elemento más pequeño de una lista. `min()` es lo opuesto a `max()`, que devuelve el elemento más grande de una lista.

4. `sorted()` devuelve una copia de una lista en orden de menor a mayor, dejando la lista sin cambios.

5. `join()`. Es un método de cadena que toma una lista de cadenas como argumento y devuelve una cadena que consta los elementos unidos por un separador.

6. `append()`. Este método agrega un elemento al final de una lista.

7. `pop()`. Este método elimina un elemento de una lista. Si no se especifica un valor, se elimina el último elemento (en otros tipos de estructuras si no se define un valor puede eliminar el primer elemento).

8. `split()`. Divide una cadena y como resultado devuelve una lista.


```python
my_string_list = ['Z', 'ALZ', 'B']
max(my_string_list)
```


```python
sorted(my_string_list)
```


```python
my_separator= "\n"
my_string_list = ["This", "is", "my", "Python", "course"]
new_string = my_separator.join(my_string_list)
print(new_string)
```


```python
letters = ['a', 'b', 'c', 'd']
letters.append('z')
print(letters)
```


```python
letters = ['a', 'b', 'c', 'd']
letters.pop(0)
print(letters)
```

verse = "if you can keep your head when all about you are losing theirs and blaming it on you   if you can trust yourself when all men doubt you     but make allowance for their doubting too   if you can wait and not be tired by waiting      or being lied about  don’t deal in lies   or being hated  don’t give way to hating      and yet don’t look too good  nor talk too wise"
print(verse, "\n")
verse_list = verse.split()
print(verse_list, '\n')

### Tuplas

Una **tupla** es otro tipo de estructura útil. Es un tipo de datos para secuencias de elementos ordenadas **inmutables**. A menudo se usan para almacenar información relacionada.


```python
location = (13.4125, 103.866667)
print("Latitude:", location[0])
print("Longitude:", location[1])
```


```python
location[0] = 12.1
```

### Conjunto

Un **conjunto** es un tipo de datos para colecciones **mutables no ordenadas** de elementos **únicos**. Una aplicación de un conjunto es eliminar rápidamente los duplicados de una lista.


```python
numbers = [1, 2, 6, 3, 1, 1, 6]
unique_nums = set(numbers)
print(unique_nums)
```


```python
type(unique_nums)
```

## Diccionarios

Un diccionario es un tipo de dato **mutable** que almacena asignaciones de claves únicas a valore


```python
elements = {"hydrogen": 1, "helium": 2, "carbon": 6}
print(elements["helium"])
elements["lithium"] = 3  # Insertar "lithium" con el valor 3 dentro del diccionario
print(elements)
```


```python
print("carbon" in elements)
print(elements.get("dilithium"))
print(elements.get("hydrogen"))
print(elements["hydrogen"])
```

# Estructuras de datos compuestas
Una característica interesante en Python es el poder incluir contenedores dentro de otros contenedores para crear estructuras de datos compuestos.


```python
elements = {"hydrogen": {"number": 1,
                         "weight": 1.00794,
                         "symbol": "H"},
              "helium": {"number": 2,
                         "weight": 4.002602,
                         "symbol": "He"}}
elements
```


```python
helium = elements["helium"]
hydrogen_weight = elements["hydrogen"]["weight"]
print(helium)
print(hydrogen_weight)
```


```python
oxygen = {"number":8,"weight":15.999,"symbol":"O"}  # crear un diccionario
elements["oxygen"] = oxygen  # asignar el diccionario al diccionario compuesto
print('elements = ', elements)
```

En resumen se tiene:


| Estructura de Datos | Ordenado | Mutable | Constructor | Ejemplo |
|--|--|--|--|--|
| Lista 	| Si | Si | `[ ]` or `list()`	| `[5.7, 4, 'yes', 5.7]` |
| Tupla 	| Si | No | `( )` or `tuple()`	| `(5.7, 4, 'yes', 5.7)` |
| Conjunto	| No | Si | `{}`* or `set()`	| `{5.7, 4, 'yes'}`	 |
| Diccionario 	| No | No | `{ }` or `dict()`	| `{'Jun': 75, 'Jul': 89}` |


#<div style="text-align: right">    
 [**Siguiente Lección**](Lecci%C3%B3n%2004%20-%20Introducci%C3%B3n%20a%20Python%202.ipynb)    
<div/>#  
