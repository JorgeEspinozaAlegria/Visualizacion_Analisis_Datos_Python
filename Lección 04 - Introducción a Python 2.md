# Introducción a Python

## Sentencias Condicionales

### IF

Una sentencia `if` es una declaración condicional que ejecuta u omite código en función de si una condición es verdadera o falsa.


```python
phone_balance=0
bank_balance=0
if phone_balance < 5:
    phone_balance += 10
    bank_balance -= 10
print(phone_balance)
print(bank_balance)
```

    10
    -10
    

Analicemos esto:

- Una instrucción `if` comienza con la palabra clave `if`, seguida de la condición a evaluar, en este caso `phone_balance <5`, y luego **dos puntos**. La condición se especifica en una expresión booleana que se evalúa como Verdadero (`True`) o Falso (`False`).  

- Después de esta línea hay un bloque de código **identado** que se ejecutará si esa condición es verdadera. Si no, el código en este bloque si simplemente se omite.

### ELSE IF

Además de la cláusula `if`, hay otras dos cláusulas opcionales que a menudo se usan con una declaración: `else` y `elif`. Veamos un ejemplo


```python
season = 'spring'
if season == 'spring':
    print('plant the garden!')
elif season == 'summer':
    print('water the garden!')
elif season == 'fall':
    print('harvest the garden!')
elif season == 'winter':
    print('stay indoors!')
else:
    print('unrecognized season')
```

    plant the garden!
    

### Expresiones Booleanas complejas

Para condiciones complejas podemos usar los operadores lógicos `and`, `or` y `not`.


```python
unsubscribed = 0
location = 'USA'
if (not unsubscribed) and (location == "USA" or location == "CAN"):
    print("send email")
```

    send email
    


```python
if True:
    print("This indented code will always get run.")
```

    This indented code will always get run.
    


```python
# Un mal ejemplo
is_cold=1
if is_cold == True:
    print("The weather is cold!")
```

    The weather is cold!
    


```python
# Un buen ejemplo
if is_cold:
    print("The weather is cold!")
```

    The weather is cold!
    

## Bucles
Un objeto **iterable** es un objeto que puede devolver uno de sus elementos a la vez. Estos objetos pueden incluir tipos de secuencia, como cadenas, listas y tuplas, así como tipos que no son de secuencia, como diccionarios y archivos.
### Bucles For


```python
cities = ['new york city', 'mountain view', 'chicago', 'los angeles']
for city in cities:
    print(city)
print("Done!")
```

    new york city
    mountain view
    chicago
    los angeles
    Done!
    

#### Usando la función `range()` con bucles `for`

`range ()` es una función incorporada utilizada para crear una secuencia iterativa de números. Con frecuencia usará range () con un bucle for para repetir una acción un cierto número de veces.


```python
for i in range(3):
    print("Hello!")
```

    Hello!
    Hello!
    Hello!
    

#### range(start=0, stop, step=1)

La función `range()` toma **tres argumentos enteros**, el primero y el tercero son opcionales:  

- `start`. Es el primer número de la secuencia. Si no se especifica, `start` por defecto es 0.  

- `stop`. Es 1 más que el último número de la secuencia. Este argumento debe ser especificado.  

- `step`. Es la diferencia entre cada número en la secuencia. Si no se especifica, el `step` predeterminado es 1.

#### Creando y modificando listas


```python
cities = ['new york city', 'mountain view', 'chicago', 'los angeles']
capitalized_cities = []

for city in cities:
    capitalized_cities.append(city.title())
print(capitalized_cities)
```

    ['New York City', 'Mountain View', 'Chicago', 'Los Angeles']
    


```python
cities = ['new york city', 'mountain view', 'chicago', 'los angeles']

for index in range(len(cities)):
    cities[index] = cities[index].title()
    
cities
```




    ['New York City', 'Mountain View', 'Chicago', 'Los Angeles']



#### Construyendo Diccionarios


```python
book_title =  ['great', 'expectations','the', 'adventures', 'of', 'sherlock','holmes','the','great','gasby','hamlet','adventures','of','huckleberry','fin']
```


```python
word_counter = {}
```


```python
for word in book_title:
    # print(word)
    if word not in word_counter:
        word_counter[word] = 1
        # print("número 2 ", word_counter)
    else:
        word_counter[word] += 1
print(word_counter)
```

    {'great': 2, 'expectations': 1, 'the': 2, 'adventures': 2, 'of': 2, 'sherlock': 1, 'holmes': 1, 'gasby': 1, 'hamlet': 1, 'huckleberry': 1, 'fin': 1}
    

#### Usando el método `get()`


```python
book_title =  ['great', 'expectations','the', 'adventures', 'of', 'sherlock','holmes','the','great','gasby','hamlet','adventures','of','huckleberry','fin']
```


```python
word_counter = {}
for word in book_title:
    word_counter[word] = word_counter.get(word, 0) + 1
print(word_counter)
```

    {'great': 2, 'expectations': 1, 'the': 2, 'adventures': 2, 'of': 2, 'sherlock': 1, 'holmes': 1, 'gasby': 1, 'hamlet': 1, 'huckleberry': 1, 'fin': 1}
    

#### Iterando a través de Diccionarios


```python
cast = {
           "Jerry Seinfeld": "Jerry Seinfeld",
           "Julia Louis-Dreyfus": "Elaine Benes",
           "Jason Alexander": "George Costanza",
           "Michael Richards": "Cosmo Kramer"
       }
```


```python
for key in cast:
    print(key)
```

    Jerry Seinfeld
    Julia Louis-Dreyfus
    Jason Alexander
    Michael Richards
    


```python
print(cast.items())
for key, value in cast.items():
    print("Actor: {}    Role: {}".format(key, value))
```

    dict_items([('Jerry Seinfeld', 'Jerry Seinfeld'), ('Julia Louis-Dreyfus', 'Elaine Benes'), ('Jason Alexander', 'George Costanza'), ('Michael Richards', 'Cosmo Kramer')])
    Actor: Jerry Seinfeld    Role: Jerry Seinfeld
    Actor: Julia Louis-Dreyfus    Role: Elaine Benes
    Actor: Jason Alexander    Role: George Costanza
    Actor: Michael Richards    Role: Cosmo Kramer
    

### Bucles While

Los bucles `for` son un ejemplo de "**iteración definida**", lo que significa que el cuerpo del bucle se ejecuta un número predeterminado de veces. Esto difiere de una "**iteración indefinida**", que es cuando un ciclo se repite un número desconocido de veces y termina cuando se cumple alguna condición, que es lo que sucede en un bucle `while`.


```python
card_deck = [4, 11, 8, 5, 13, 2, 8, 10]
hand = []
while sum(hand) < 40:
    hand.append(card_deck.pop())
    print(hand)
    print(sum(hand))
```

    [10]
    10
    [10, 8]
    18
    [10, 8, 2]
    20
    [10, 8, 2, 13]
    33
    [10, 8, 2, 13, 5]
    38
    [10, 8, 2, 13, 5, 8]
    46
    

### Break & Continue

A veces necesitamos más control sobre cuándo debe terminar un buble, o saltar una iteración. En estos casos, usamos las palabras clave `break` y `continue`, que se pueden usar tanto en bucles `for` como `while`.  

- `break` termina un bucle  

- `continue` omite una iteración de un bucle  



```python
headlines = ["Local Bear Eaten by Man",
             "Legislature Announces New Laws",
             "Peasant Discovers Violence Inherent in System",
             "Cat Rescues Fireman Stuck in Tree",
             "Brave Knight Runs Away",
             "Papperbok Review: Totally Triffic"]

news_ticker = ""
for headline in headlines:
    news_ticker += headline + " "
    if len(news_ticker) >= 140:
        news_ticker = news_ticker[:140]
        break

print(news_ticker)
```

    Local Bear Eaten by Man Legislature Announces New Laws Peasant Discovers Violence Inherent in System Cat Rescues Fireman Stuck in Tree Brave
    

## Funciones

Una Función permite reutilizar código para usarlo una y otra de forma fácil.

### Definir una Función


```python
def cylinder_volume(height, radius):
    pi = 3.14159
    return height * pi * radius ** 2
```


```python
cylinder_volume(10, 3)
```




    282.7431



### Argumentos por Default

Podemos agregar argumentos predeterminados en una función para tener valores por defecto para argumentos o parámetros que no están especificados en una llamada a la función.


```python
def cylinder_volume(height, radius=5):
    pi = 3.14159
    return height * pi * radius ** 2
```


```python
cylinder_volume(10, 7)  # por posición
cylinder_volume(height=10, radius=7)  # por nombre de argumento
```




    1539.3791



### Alcance de Variables

El alcance de una variable se refiere a aquellas partes de un programa que pueden hacer referencia a una variable.

Es importante tener en cuenta el alcance cuando se usan variables en funciones. Si se crea una variable dentro de una función, solo se puede usar dentro de esa función. No es posible acceder a él fuera de esa función.


```python
# Esto provocará un error
def some_function():
    word = "hello"
print(word)
```

    fin
    


```python
some_function()
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-77-6a01c81cb036> in <module>
    ----> 1 some_function()
    

    TypeError: 'str' object is not callable



```python
word = "hello"

def some_function():
    print(word)

some_function()
```

    hello
    

## Expresiones Lambda

Podemos usar expresiones lambda para crear funciones anónimas. Es decir, funciones que no tienen nombre.

Son útiles para crear funciones rápidas que no se necesitan más adelante en el código. Esto puede ser especialmente útil para funciones de orden superior o funciones que toman otras funciones como argumentos.

Una función normal:



```python
def multiply1(x, y):
    return x * y
```

puede ser reducida a:


```python
multiply = lambda x, y: x * y
multiply(2,10)


```




    20




```python
numbers = [
              [34, 63, 88, 71, 29],
              [90, 78, 51, 27, 45],
              [63, 37, 85, 46, 22],
              [51, 22, 34, 11, 18]
           ]

averages = list(map(lambda x: sum(x) / len(x), numbers))
print(averages)
```

    [57.0, 58.2, 50.6, 27.2]
    


```python
cities = ["New York City", "Los Angeles", "Chicago", "Mountain View", "Denver", "Boston"]

short_cities = list(filter(lambda x: len(x) < 10, cities))
print(short_cities)
```

    ['Chicago', 'Denver', 'Boston']
    

## ¡¡¡Felicidades ahora ya tienes los conceptos basicos de Python!!!

#<div style="text-align: right">    
 [**Ejercicios**](Ejercicios/Python/Python%20Ejercicios.ipynb)    
<div/>#  
    
