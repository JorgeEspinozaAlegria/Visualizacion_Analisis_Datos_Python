# NumPy Ejercicios

Ahora que hemos aprendido sobre NumPy, analicemos sus conocimientos. Comenzaremos con algunas tareas simples y luego se le harán algunas preguntas más complicadas.

#### Import NumPy as np


```python

```

#### Crear un arreglo de 10 ceros 


```python

```




    array([0., 0., 0., 0., 0., 0., 0., 0., 0., 0.])



#### Crear un arreglo de 10 unos


```python

```




    array([1., 1., 1., 1., 1., 1., 1., 1., 1., 1.])



#### Crear un arreglo de 10 cincos


```python

```




    array([5., 5., 5., 5., 5., 5., 5., 5., 5., 5.])



#### Crear un arreglo del 1 al 50


```python

```




    array([10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26,
           27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43,
           44, 45, 46, 47, 48, 49, 50])



#### Crear un arreglo de todos los números pares que exiten entre 10 y 50


```python

```




    array([10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 42,
           44, 46, 48, 50])



#### Crear una matriz 3X3 con valores entre 0 y 8


```python

```




    array([[0, 1, 2],
           [3, 4, 5],
           [6, 7, 8]])



#### Crear una matriz identidad de tamaño 3X3


```python

```




    array([[1., 0., 0.],
           [0., 1., 0.],
           [0., 0., 1.]])



#### Use Numpy para generar numeros aleatorios entre 0 y 1


```python

```




    array([0.51787234])



#### Use Numpy para generar un arreglo de 25 números aleatorios de una distribución normal.


```python

```




    array([-2.46589453,  0.14707011, -0.53265965,  0.30686099, -0.60930594,
            0.20645672,  1.29034172, -0.07439634,  0.52803155, -0.49322622,
           -0.4360668 ,  0.57065503, -0.59265004, -0.49789408,  0.36926571,
           -0.68648866,  0.80196731, -0.33418613,  1.4950219 ,  0.54421291,
           -2.39465423, -0.75977582,  1.1345078 , -1.34949657, -0.76403495])



#### Cree la siguiente matriz:


```python

```




    array([[0.01, 0.02, 0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09, 0.1 ],
           [0.11, 0.12, 0.13, 0.14, 0.15, 0.16, 0.17, 0.18, 0.19, 0.2 ],
           [0.21, 0.22, 0.23, 0.24, 0.25, 0.26, 0.27, 0.28, 0.29, 0.3 ],
           [0.31, 0.32, 0.33, 0.34, 0.35, 0.36, 0.37, 0.38, 0.39, 0.4 ],
           [0.41, 0.42, 0.43, 0.44, 0.45, 0.46, 0.47, 0.48, 0.49, 0.5 ],
           [0.51, 0.52, 0.53, 0.54, 0.55, 0.56, 0.57, 0.58, 0.59, 0.6 ],
           [0.61, 0.62, 0.63, 0.64, 0.65, 0.66, 0.67, 0.68, 0.69, 0.7 ],
           [0.71, 0.72, 0.73, 0.74, 0.75, 0.76, 0.77, 0.78, 0.79, 0.8 ],
           [0.81, 0.82, 0.83, 0.84, 0.85, 0.86, 0.87, 0.88, 0.89, 0.9 ],
           [0.91, 0.92, 0.93, 0.94, 0.95, 0.96, 0.97, 0.98, 0.99, 1.  ]])



#### Crear un arreglo linealmente espaciado entre 0 y 1:


```python

```




    array([0.        , 0.05263158, 0.10526316, 0.15789474, 0.21052632,
           0.26315789, 0.31578947, 0.36842105, 0.42105263, 0.47368421,
           0.52631579, 0.57894737, 0.63157895, 0.68421053, 0.73684211,
           0.78947368, 0.84210526, 0.89473684, 0.94736842, 1.        ])



## Numpy Selección e Indíces
Ahora se le darán algunas matrices y se le pedirá que replique los resultados de la matriz resultante:


```python
mat = np.arange(1,26).reshape(5,5)
mat
```




    array([[ 1,  2,  3,  4,  5],
           [ 6,  7,  8,  9, 10],
           [11, 12, 13, 14, 15],
           [16, 17, 18, 19, 20],
           [21, 22, 23, 24, 25]])




```python
# ESCRIBA EL CÓDIGO AQUÍ QUE REPRODUCE LA SALIDA DE LA CELDA ABAJO
# TEN CUIDADO DE NO EJECUTAR LA CELDA A CONTINUACIÓN, DE LO CONTRARIO NO
# PUEDE VER LA PRODUCCIÓN MÁS
```


```python

```




    array([[12, 13, 14, 15],
           [17, 18, 19, 20],
           [22, 23, 24, 25]])




```python
# ESCRIBA EL CÓDIGO AQUÍ QUE REPRODUCE LA SALIDA DE LA CELDA ABAJO
# TEN CUIDADO DE NO EJECUTAR LA CELDA A CONTINUACIÓN, DE LO CONTRARIO NO
# PUEDE VER LA PRODUCCIÓN MÁS
```


```python

```




    20




```python
# ESCRIBA EL CÓDIGO AQUÍ QUE REPRODUCE LA SALIDA DE LA CELDA ABAJO
# TEN CUIDADO DE NO EJECUTAR LA CELDA A CONTINUACIÓN, DE LO CONTRARIO NO
# PUEDE VER LA PRODUCCIÓN MÁS
```


```python

```




    array([[ 2],
           [ 7],
           [12]])




```python
# ESCRIBA EL CÓDIGO AQUÍ QUE REPRODUCE LA SALIDA DE LA CELDA ABAJO
# TEN CUIDADO DE NO EJECUTAR LA CELDA A CONTINUACIÓN, DE LO CONTRARIO NO
# PUEDE VER LA PRODUCCIÓN MÁS
```


```python

```




    array([21, 22, 23, 24, 25])




```python
# ESCRIBA EL CÓDIGO AQUÍ QUE REPRODUCE LA SALIDA DE LA CELDA ABAJO
# TEN CUIDADO DE NO EJECUTAR LA CELDA A CONTINUACIÓN, DE LO CONTRARIO NO
# PUEDE VER LA PRODUCCIÓN MÁS
```


```python

```




    array([[16, 17, 18, 19, 20],
           [21, 22, 23, 24, 25]])



### Ahora haga lo siguiente

#### Obtenga la suma de todos los valores en mat


```python

```




    325



#### Obtenga la desviación estándar de los valores en mat


```python

```




    7.211102550927978



#### Obtenga la suma de todas las columnas en mat


```python

```




    array([55, 60, 65, 70, 75])



# Buen trabajo¡¡

   
[**Ejercicios Resueltos**](Numpy%20Ejercicios%20-%20Soluci%C3%B3n.md)    
 

