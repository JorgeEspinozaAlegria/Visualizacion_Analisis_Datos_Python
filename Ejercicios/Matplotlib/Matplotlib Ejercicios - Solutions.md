# Ejercicios Matplotlib

¡Bienvenido a los ejercicios para revisar matplotlib! Tómate tu tiempo, Matplotlib puede ser difícil de entender al principio. Estas son gráficas relativamente simples, pero pueden ser difíciles si esta es tu primera vez con Matplotlib; no dudes en consultar las soluciones a medida que avanzas.

** * NOTA: TODOS LOS COMANDOS PARA GRAFICAR UNA FIGURA DEBEN IR EN LA MISMA CÉLULA. SEPARARLAS EN CÉLULAS MÚLTIPLES PUEDE CAUSAR QUE NO SE MUESTRE NADA. * **

# Ejercicios

Sigue las instrucciones para recrear los gráficos con estos datos:

## Datos


```python
import numpy as np
x = np.arange(0,100)
y = x*2
z = x**2
```


** Importa matplotlib.pyplot como plt y establece % matplotlib en línea si estás utilizando el cuaderno jupyter. ¿Qué comando utilizas si no estás usando el cuaderno jupyter? **


```python
import matplotlib.pyplot as plt
%matplotlib inline
# plt.show() for non-notebook users
```

## Ejercicio 1

** Sigue estos pasos: **
* ** Crea una figura llamada fig usando plt.figure () **
* ** Usa add_axes para agregar un eje al lienzo de la figura en [0,0,1,1]. Llama a este nuevo eje "eje". **
* ** Traza (x, y) en esos ejes y configura las etiquetas y títulos para que coincidan con el siguiente diagrama: **


```python
fig = plt.figure()
ax = fig.add_axes([0,0,1,1])
ax.plot(x,y)
ax.set_xlabel('x')
ax.set_ylabel('y')
ax.set_title('title')
```




    Text(0.5, 1.0, 'title')




![png](images/output_5_1.png)


## Ejercicio 2
** Crea una figura llamada fig y coloca dos ejes sobre él, ax1 y ax2. Ubica los ejes en [0,0,1,1] y [0.2,0.5, .2, .2] respectivamente. **


```python
fig = plt.figure()
ax1 = fig.add_axes([0,0,1,1])
ax2 = fig.add_axes([0.2,0.5,.2,.2])
```


![png](images/output_7_0.png)


** Ahora dibuja (x, y) en ambos ejes. Y llama a tu figura para mostrarla. **


```python
ax1.plot(x,y)
ax1.set_xlabel('x')
ax1.set_ylabel('y')


ax2.plot(x,y)
ax2.set_xlabel('x')
ax2.set_ylabel('y')

fig
```




![png](images/output_9_0.png)



## Ejercicio 3

** Crea el siguiente diagrama, agregando dos ejes a una figura en [0,0,1,1] y [0.2,0.5, .4, .4] **


```python
fig = plt.figure()

ax = fig.add_axes([0,0,1,1])
ax2 = fig.add_axes([0.2,0.5,.4,.4])
```


![png](images/output_11_0.png)


** Ahora usa las matrices x, y, z para recrear el siguiente diagrama. Considera los límites de x, y en el diagrama: **


```python
ax.plot(x,z)
ax.set_xlabel('X')
ax.set_ylabel('Z')


ax2.plot(x,y)
ax2.set_xlabel('X')
ax2.set_ylabel('Y')
ax2.set_title('zoom')
ax2.set_xlim(20,22)
ax2.set_ylim(30,50)

fig
```




![png](images/output_13_0.png)



## Ejercicio 4

** Usa plt.subplots (nrows=1, ncols=2), para crear la gráfica siguiente. **


```python
# Lienzo vacío de 1 por 2 subgrafo
fig, axes = plt.subplots(nrows=1, ncols=2)
```


![png](images/output_15_0.png)



** Ahora traza (x, y) y (x, z) en los ejes. Juega con el ancho de línea y el estilo **


```python
axes[0].plot(x,y,color="blue", lw=3, ls='--')
axes[1].plot(x,z,color="red", lw=3, ls='-')
fig
```




![png](images/output_17_0.png)




** Revisa si puedes cambiar el tamaño del gráfico, agregando el argumento figsize () en plt.subplots ().
Copia y pega tu código anterior. **


```python
fig, axes = plt.subplots(nrows=1, ncols=2,figsize=(12,2))

axes[0].plot(x,y,color="blue", lw=5)
axes[0].set_xlabel('x')
axes[0].set_ylabel('y')

axes[1].plot(x,z,color="red", lw=3, ls='--')
axes[1].set_xlabel('x')
axes[1].set_ylabel('z')
```




    Text(0, 0.5, 'z')




![png](images/output_19_1.png)


# !Excelente trabajo!
