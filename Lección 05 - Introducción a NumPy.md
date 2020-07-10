# Introducción a Numpy

## ¿Qué es NumPy?
NumPy es el paquete fundamental para la computación científica en Python. Es una biblioteca de Python que proporciona un objeto de matriz multidimensional, varios objetos derivados (como matrices y matrices enmascaradas) y una variedad de rutinas para operaciones rápidas en matrices, incluidas la matemática, lógica, manipulación de formas, clasificación, selección, E / S , transformadas discretas de Fourier, álgebra lineal básica, operaciones estadísticas básicas, simulación aleatoria y mucho más.  

En el núcleo del paquete NumPy, está el objeto `ndarray`. Este encapsula matrices n-dimensionales de tipos de datos homogéneos, con muchas operaciones que se realizan en código compilado para el rendimiento.  

## ¿Por qué es rápido NumPy?
La vectorización describe la ausencia de cualquier bucle explícito, indexación, etc., en el código; estas cosas están ocurriendo, por supuesto, solo "detrás de escena" en un código C precompilado optimizado. El código vectorizado tiene muchas ventajas, entre las cuales se encuentran:  

- el código vectorizado es más conciso y más fácil de leer.
- menos líneas de código generalmente significa menos errores.
- el código se asemeja más a la notación matemática estándar (lo que facilita, por lo general, codificar correctamente construcciones matemáticas).
- la vectorización da como resultado más código tipo Python. Sin vectorización, nuestro código estaría lleno de bucles `for` ineficientes y difíciles de leer .

## Instalar Numpy
### Anaconda
Para instalar Numpy realiza los siguientes pasos:
1. Abrir anaconda
2. Elegir el ambiente de trabajo
3. Abrir un prompt en CMD.exe
4. Teclear `conda install numpy`

## Crear matrices a partir de listas de Python
Primero, podemos usar `np.array` para crear matrices de listas de Python:  


```python
import numpy as np
```

```python
# Matriz de tipo entero
np.array([1, 4, 2, 5, 3])
```
array([1, 4, 2, 5, 3])  

```python
# Matriz de tipo flotante
np.array([3.14, 4, 2, 3])
```
array([3.14, 4., 2., 3.])  

```python
# Establecer explícitamente el tipo de datos de la matriz
np.array([1, 2, 3, 4], dtype='float32')
```
array([1., 2., 3., 4.], dtype=float32)  

Recuerda que, a diferencia de las listas de Python, NumPy está restringido a matrices que contienen el mismo tipo. Si los tipos no coinciden, NumPy cambia los enteros a flotante.  
Finalmente, a diferencia de las listas de Python, las matrices de NumPy pueden ser explícitamente multidimensionales. Esta es una forma de inicializar una matriz multidimensional, utilizando una lista de listas  


```python
# listas anidadas dan como resultado matrices multidimensionales
np.array([range(i, i + 3)  for i in [2, 4, 6]])
```
array([[2, 3, 4],  
       [4, 5, 6],  
       [6, 7, 8]])  

```python
for i in [2, 4, 6]:
    print(i)
```
2  
4  
6  


Las listas internas se tratan como filas de la matriz bidimensional resultante.

## Crear matrices desde cero
Especialmente para matrices más grandes, es más eficiente crear matrices desde cero, utilizando rutinas integradas en NumPy. Algunos ejemplos:


```python
# Crear una matriz entera de longitud 10 llena de ceros
np.zeros(10, dtype=int)
```




    array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0])




```python
# Crear una matriz de punto flotante de 3x5 llena de unos
np.ones((3, 5), dtype=float)
```




    array([[1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1.]])




```python
# Crear una matriz de 3x5 con 3.14
np.full((3, 5), 3.14)
```




    array([[3.14, 3.14, 3.14, 3.14, 3.14],
           [3.14, 3.14, 3.14, 3.14, 3.14],
           [3.14, 3.14, 3.14, 3.14, 3.14]])




```python
# Crear una matriz llena de una secuencia lineal
# comenzando en 0, terminando en 20, con incrementos de 2
# (esto es similar a la función incorporada range ())
np.arange(0, 20, 2)
```




    array([0, 2, 4, 6, 8, 10, 12, 14, 16, 18])




```python
# Crear una matriz de cinco valores espaciados uniformemente entre 0 y 1
np.linspace(0, 1, 5)
```




    array([0., 0.25, 0.5, 0.75, 1.])




```python
# Crear una matriz de 3x3 con
# valores aleatorios distribuidos uniformemente entre 0 y 1
np.random.random((3, 3))
```




    array([[0.90734194, 0.51231763, 0.61351982],
           [0.65957916, 0.02313783, 0.60537601],
           [0.1986259 , 0.91136139, 0.82392216]])




```python
# Crear una matriz de 3x3 con valores aleatorios distribuidos normalmente
# con media 0 y desviación estándar 1
np.random.normal(0, 1, (3, 3))
```




    array([[-0.76479864, -0.63143219,  1.76515554],
           [ 0.83707982,  0.41462297, -0.25600685],
           [ 0.80167061,  0.05135109, -0.98455474]])




```python
# Crear una matriz de 3x3 con enteros aleatorios en el intervalo [0, 10)
np.random.randint(0, 10, (3, 3))
```




    array([[7, 3, 8],
           [3, 0, 1],
           [2, 3, 3]])




```python
# Crear una matriz de identidad 3x3
np.eye(3)
```




    array([[1., 0., 0.],
           [0., 1., 0.],
           [0., 0., 1.]])




```python
# Crear una matriz no inicializada de tres enteros
# Los valores contendrán lo que exista en esa ubicación de memoria
np.empty(3)
```




    array([1., 1., 1.])



## Atributos de las matrices de NumPy


```python
np.random.seed(0)  # semilla para poder reproducir los resultados
x1 = np.random.randint(10, size=6)  # matriz de 1 dimensión
x2 = np.random.randint(10, size=(3, 4))  # matriz de 2 dimensiones
x3 = np.random.randint(10, size=(3, 4, 5))  # matriz de 3 dimensiones
print("Dimensiones x3:", x3.ndim)
print("Forma x3:", x3.shape)
print("Tamaño x3:", x3.size)
print(x3)
```

    Dimensiones x3: 3
    Forma x3: (3, 4, 5)
    Tamaño x3: 60
    [[[8 1 5 9 8]
      [9 4 3 0 3]
      [5 0 2 3 8]
      [1 3 3 3 7]]

     [[0 1 9 9 0]
      [4 7 3 2 7]
      [2 0 0 4 5]
      [5 6 8 4 1]]

     [[4 9 8 1 1]
      [7 9 9 3 6]
      [7 2 0 3 5]
      [9 4 4 6 4]]]



```python
print("Tipo de dato:", x3.dtype)
```

    Tipo de dato: int32


Otros atributos incluyen `itemsize`, que muestra el tamaño (en bytes) de cada elemento de la matriz y `nbytes`, que muestra el tamaño total (en bytes) de la matriz


```python
print("itemsize:", x3.itemsize, "bytes")
print("nbytes:",  x3.nbytes, "bytes")
```

    itemsize: 4 bytes
    nbytes: 240 bytes


## Indexación de matrices: acceso a elementos individuales
Si estás familiarizado con la indexación de una lista estándar de Python, la indexación en NumPy te resultará bastante familiar.


```python
x1
```




    array([5, 0, 3, 3, 7, 9])




```python
x1[0]
```




    5




```python
x1[5]
```




    9



Para indexar desde el final de la matriz, se pueden usar índices negativos


```python
x1[-1]
```




    9




```python
x1[-2]
```




    7



En una matriz multidimensional, se puede acceder a los elementos utilizando una tupla de índices separados por comas


```python
x2
```




    array([[3, 5, 2, 4],
           [7, 6, 8, 8],
           [1, 6, 7, 7]])




```python
x2[0,0]
```




    3




```python
x2[2, 0]
```




    1




```python
x2[2, -1]
```




    7



Los valores también se pueden modificar, utilizando cualquiera de las anotaciones de índice anteriores


```python
x2[0, 0] = 12
x2
```




    array([[12,  5,  2,  4],
           [ 7,  6,  8,  8],
           [ 1,  6,  7,  7]])



Nota: Ten en cuenta que, a diferencia de las listas de Python, las matrices NumPy tienen un tipo fijo. Esto significa, por ejemplo, que si intentas insertar un valor de punto flotante en una matriz entera, el valor se truncará sin mandar algún tipo de notificación. ¡No te dejes sorprender por este comportamiento!


```python
x1[0] = 3.14159   # ¡esto se truncará!
x1
```




    array([3, 0, 3, 3, 7, 9])



## Rebanadas de matrices: acceso a subarreglos

Del mismo modo que podemos usar corchetes, para acceder a elementos de la matriz individualmente, también podemos usarlos para acceder a submatrices con la notación de corte , marcada con el carácter de dos puntos ( :). La sintaxis de segmentación NumPy utiliza la misma de la lista estándar de Python; para acceder a una porción de una matriz x, usa esto:   
`x [inicio : fin : incremento]`

Si cualquiera de estos no se especifican, por defecto se utilizarán los valores `inicio = 0`, `fin = tamaño de la dimensión`, `incremento = 1`. A continuación se muestra el acceso a sub-matrices en una dimensión y en múltiples dimensiones.

### Subarreglos unidimensionales


```python
x = np.arange(10)
x
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
x[:5]  # primeros 5 elementos
```




    array([0, 1, 2, 3, 4])




```python
x[5:] # últimos 5 elementos
```




    array([5, 6, 7, 8, 9])




```python
x[4:7]   # subarreglo intermedio
```




    array([5, 6, 7, 8, 9])




```python
x[::2]  # cada dos elementos
```




    array([0, 2, 4, 6, 8])




```python
x[1::2]   # cada dos elementos, comenzando en el índice 1
```




    array([1, 3, 5, 7, 9])



Un caso potencialmente confuso es cuando el valor del `incremento` es negativo. En este caso, los valores predeterminados `inicio` y `fin` se intercambian. Esto proporciona una forma conveniente de invertir una matriz


```python
x[::-1]   # todos los elementos, invertidos
```




    array([9, 8, 7, 6, 5, 4, 3, 2, 1, 0])




```python
x[5::-2]   # invertido desde el índice 5 con incrementos de 2
```




    array([5, 3, 1])



### Subarreglos multidimensionales
Los sectores multidimensionales funcionan de la misma manera, con múltiples sectores separados por comas.


```python
x2
```




    array([[12,  5,  2,  4],
           [ 7,  6,  8,  8],
           [ 1,  6,  7,  7]])




```python
x2[:2, :3]   # dos filas, tres columnas
```




    array([[12,  5,  2],
           [ 7,  6,  8]])




```python
x2[:3, ::2]   # todas las filas, cada dos columnas
```




    array([[12,  2],
           [ 7,  8],
           [ 1,  7]])




```python
#Finalmente, las dimensiones de la submatriz pueden incluso invertirse juntas
x2 [::-1, ::-1]
```




    array([[ 7,  7,  6,  1],
           [ 8,  8,  6,  7],
           [ 4,  2,  5, 12]])



### Accediendo a filas y columnas de una matriz
Una rutina comúnmente utilizada es acceder a filas o columnas individuales de una matriz. Esto se puede hacer combinando indexación y segmentación, utilizando una división vacía marcada con solo dos puntos (`:`)


```python
print(x2[:, 0])   # primera columna de x2
```

    [12  7  1]



```python
print(x2[0, :])  # primera fila de x2
```

    [12  5  2  4]


### Subarreglos como vistas sin copia
Una cosa importante, y extremadamente útil, que debes saber sobre los segmentos de matriz, es que devuelven vistas en lugar de copias de los datos de la matriz.


```python
print(x2)
```

    [[12  5  2  4]
     [ 7  6  8  8]
     [ 1  6  7  7]]



```python
x2_sub  =  x2[:2, :2]
print(x2_sub)
```

    [[12  5]
     [ 7  6]]


Ahora, si modificamos esta submatriz, ¡veremos que se modifica la matriz original! Por ejemplo:


```python
x2_sub [0, 0] = 99
print(x2_sub)
```

    [[99  5]
     [ 7  6]]



```python
print(x2)
```

    [[99  5  2  4]
     [ 7  6  8  8]
     [ 1  6  7  7]]


Este comportamiento predeterminado es realmente bastante útil: significa que cuando trabajamos con grandes conjuntos de datos, podemos acceder y procesar partes de estos conjuntos de datos. sin la necesidad de copiar el búfer de datos correspondiente.

### Crear copias de matrices
A pesar de las buenas características de las vistas de matriz, a veces es útil copiar explícitamente los datos dentro de una matriz o una submatriz. Esto se puede hacer más fácilmente con el método `copy()`.


```python
x2_sub_copia = x2[:2, :2].copy()
print(x2_sub_copia)
```

    [[99  5]
     [ 7  6]]


Si ahora modificamos esta submatriz, la matriz original no se modifica


```python
x2_sub_copia[0, 0] = 42
print(x2_sub_copia)
```

    [[42  5]
     [ 7  6]]



```python
print(x2)
```

    [[99  5  2  4]
     [ 7  6  8  8]
     [ 1  6  7  7]]


## Reestructuración de matrices

Ten en cuenta que para que esto funcione, el tamaño de la matriz inicial debe coincidir con el tamaño de la matriz modificada. Cuando sea posible, el método `reshape` utilizará una vista sin copia de la matriz inicial, pero con memorias intermedias de memoria no contiguas, aunque este no es siempre el caso.


```python
grid = np.arange(0, 10).reshape((2, 5))
print(grid)
```

    [[0 1 2 3 4]
     [5 6 7 8 9]]



```python
x = np.array([1, 2, 3])
x
# vector de renglones mediante reshape
x.reshape((3, 1))
```




    array([[1],
           [2],
           [3]])



## Concatenación y división de matrices
Todas las rutinas anteriores funcionaron en matrices individuales. También es posible combinar múltiples matrices en una y, por el contrario, dividir una matriz en múltiples matrices

### Concatenación de matrices
La concatenación o unión de dos matrices en NumPy, se logra principalmente utilizando las rutinas `np.concatenate`, `np.vstacky`, `np.hstack`.


```python
x = np.array([1, 2, 3])
y = np.array([3, 2, 1])
np.concatenate([x, y])
```




    array([1, 2, 3, 3, 2, 1])




```python
#También se puede concatenar más de dos matrices a la vez
z = [99, 99, 99]
print(np.concatenate([x, y, z]))
```

    [ 1  2  3  3  2  1 99 99 99]



```python
# También se puede usar para matrices bidimensionales
cuadricula = np.array([[1, 2, 3], [4, 5, 6]])

```


```python
# Concatenar a lo largo del primer eje
np.concatenate([cuadricula, cuadricula])
```




    array([[1, 2, 3],
           [4, 5, 6],
           [1, 2, 3],
           [4, 5, 6]])




```python
# Concatenar a lo largo del segundo eje (indexado a cero)
np.concatenate([cuadricula, cuadricula], axis = 1)
```




    array([[1, 2, 3, 1, 2, 3],
           [4, 5, 6, 4, 5, 6]])



Para trabajar con matrices de dimensiones mixtas, puede ser más claro usar las funciones np.vstack(pila vertical) y np.hstack(pila horizontal):


```python
x = np.array([1, 2, 3])
cuadricula = np.array([[9, 8, 7], [6, 5, 4]])

# apila verticalmente las matrices
np.vstack([x, cuadricula])
```




    array([[1, 2, 3],
           [1, 2, 3],
           [4, 5, 6]])




```python
# apila horizontalmente las matrices
y = np.array([[99],
              [99]])
np.hstack([cuadricula, y])
```




    array([[1, 2, 3, 99],
           [4, 5, 6, 99]])



### División de matrices
Lo contrario a la concatenación es la división, que es implementada por las funciones `np.split`, `np.hsplit`, y `np.vsplit`. Para cada uno de estas, podemos pasar una lista de índices que indican los puntos de división.


```python
x = [1, 2, 3, 99, 99, 3, 2, 1]
x1, x2, x3 = np.split(x, [2, 6])
print(x1, x2, x3)
```

    [1 2] [ 3 99 99  3] [2 1]



```python
cuadricula = np.arange(16).reshape((4, 4))
cuadricula
```




    array([[ 0,  1,  2,  3],
           [ 4,  5,  6,  7],
           [ 8,  9, 10, 11],
           [12, 13, 14, 15]])




```python
superior, inferior = np.vsplit(grid, [2])
print(superior)
print(inferior)
```

    [[0 1 2 3]
     [4 5 6 7]]
    [[ 8  9 10 11]
     [12 13 14 15]]



```python
izquierda, derecha = np.hsplit(grid, [2])
print(izquierda)
print(derecha)
```

    [[ 0  1]
     [ 4  5]
     [ 8  9]
     [12 13]]
    [[ 2  3]
     [ 6  7]
     [10 11]
     [14 15]]


## Agregaciones: Sum, Max y Min.
NumPy tiene funciones de agregación integradas, que son rápidas para trabajar en matrices; discutiremos y demostraremos algunos de ellos a continuación.

### Sumar los valores en una matriz


```python
# función sum de Python
L = np.random.random(100)
sum(L)
```




    52.13902574466732




```python
# función sum de NumPy
np.sum(L)
```




    52.139025744667336




```python
matriz_grande = np.random.rand(1000000)
%timeit sum(matriz_grande)

```

    133 ms ± 2.19 ms per loop (mean ± std. dev. of 7 runs, 10 loops each)



```python
%timeit np.sum(matriz_grande)
```

    862 µs ± 43.8 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)


### Mínimo y Máximo


```python
# funciones de python
min(matriz_grande), max(matriz grande)
```




    (1.8636745751088313e-06, 0.9999994002429613)




```python
# funciones de NumPy
np.min(matriz_grande), np.max(matriz_grande)
```




    (1.8636745751088313e-06, 0.9999994002429613)




```python
%timeit min(matriz_grande)
%timeit np.min(matriz_grande)
```

    87.5 ms ± 482 µs per loop (mean ± std. dev. of 7 runs, 10 loops each)
    355 µs ± 11.1 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)


### Agregaciones multi dimensionales
Un tipo común de operación de agregación, es un agregado a lo largo de una fila o columna


```python
M = np.random.random((3, 4))
print(M)
```

    [[0.94328606 0.57763174 0.10886194 0.95241469]
     [0.58188473 0.89675217 0.84964017 0.31060344]
     [0.02786824 0.65963817 0.0554205  0.51732046]]


Por defecto, cada función de agregación NumPy devolverá el agregado sobre toda la matriz.


```python
M.sum ()
```




    6.481322324204545



Las funciones de agregación toman un argumento adicional, que especifica el eje a lo largo del cual se calcula el agregado. Por ejemplo, podemos encontrar el valor mínimo dentro de cada columna especificando `axis=0`.


```python
M.min(axis=0)
```




    array([0.02786824, 0.57763174, 0.0554205 , 0.31060344])




```python
M.max(axis=1)
```




    array([0.95241469, 0.89675217, 0.65963817])



### Otras funciones de agregación
NumPy proporciona muchas otras funciones de agregación, pero no las discutiremos en detalle aquí.   
La siguiente tabla proporciona una lista de funciones de agregación útiles disponibles en NumPy:

|Nombre de la función|Versión NaN-safe|Descripción|
|---|---|---|
|np.sum	np.nansum|Calcula la suma de elementos|
|np.prod|np.nanprod|Calcula el producto de elementos|
|np.mean|np.nanmean|Calcula la media de elementos|
|np.std|np.nanstd|Calcula la desviación estándar|
|np.var|np.nanvar|Calcula la varianza|
|np.min|np.nanmin|Encuentra el valor mínimo|
|np.max|np.nanmax|Encuentra el valor máximo|
|np.argmin|np.nanargmin|Encuentra el índice de valor mínimo|
|np.argmax|np.nanargmax|Encuentra el índice de valor máximo|
|np.median|np.nanmedian|Calcula la mediana de los elementos|
|np.percentile|np.nanpercentile|Calcula estadísticas basadas en rangos de elementos|
|np.any|N / A|Evalua si algún elemento es verdadero|
|np.all|N / A|Evalua si todos los elementos son verdaderos|

## Operaciones numéricas sobre arreglos
#### Escalares


```python
a = np.array([1, 2, 3, 4])
a + 1
```




    array([2, 3, 4, 5])




```python
2**a
```




    array([2, 4, 8,16], dtype=int32)



#### Aritméticas


```python
b = np.ones(4) # otra función generadora de arreglos
b = b + 1
b
```




    array([2., 2., 2., 2.])




```python
b - a
```




    array([ 1.,  0., -1., -2.])




```python
a * b
```




    array([2., 4., 6., 8.])




```python
c = np.ones((3, 3))
c*c # ¡ojo! esto es una multiplicación elemento por elemento.
```




    array([[1., 1., 1.],
           [1., 1., 1.],
           [1., 1., 1.]])




```python
c.dot(c) # multiplicación matricial
```




    array([[3., 3., 3.],
           [3., 3., 3.],
           [3., 3., 3.]])



#### Lógicas


```python
a = np.array([1, 2, 3, 4])
b = np.array([4, 2, 2, 4])
```


```python
a == b
```




    array([False,  True, False,  True])




```python
a > b
```




    array([False, False,  True, False])




```python
a = np.array([1, 1, 0, 0], dtype=bool)
b = np.array([1, 0, 1, 0], dtype=bool)
```


```python
a | b # or, np.logical_or
```




    array([ True,  True,  True, False])




```python
a & b # and, np.logical_and
```




    array([ True, False, False, False])




```python
a ^ b # xor, np.logical_xor
```




    array([False,  True,  True, False])




```python
not_a = ~ a # not, np.logical_not
not_a
```




    array([False, False,  True,  True])



#### Álgebra lineal básica
##### Multiplicación de matrices


```python
a = np.triu(np.ones((3, 3)), 1)   # ver ayuda de (np.triu)
a
```




    array([[0., 1., 1.],
           [0., 0., 1.],
           [0., 0., 0.]])




```python
b = np.diag([1, 2, 3])
b
```




    array([[1, 0, 0],
           [0, 2, 0],
           [0, 0, 3]])




```python
a.dot(b)
```




    array([[0., 2., 3.],
           [0., 0., 3.],
           [0., 0., 0.]])



##### Transposición


```python
a.T
```




    array([[0., 0., 0.],
           [1., 0., 0.],
           [1., 1., 0.]])



##### Cálculo de eigenvalores


```python
np.linalg.eigvals(b)
```




    array([1., 2., 3.])



## ¡¡¡Felicidades, ahora ya conoces la funcionalidad básica de NumPy!!!


 [**Ejercicios**](Ejercicios/Numpy/Numpy%20Ejercicos.md)    



#### Referencias:
- https://docs.scipy.org/doc/numpy/search.html?q=split%28%29&check_keywords=yes&area=default
- https://damianavila.github.io/Python-Cientifico-HCC/3_NumPy.html
- https://jakevdp.github.io/PythonDataScienceHandbook/
