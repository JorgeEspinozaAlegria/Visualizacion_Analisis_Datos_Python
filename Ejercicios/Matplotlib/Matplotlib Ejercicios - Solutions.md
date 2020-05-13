# Ejercicios Matplotlib

¡Bienvenido a los ejercicios para revisar matplotlib! Tómese su tiempo con estos, Matplotlib puede ser difícil de entender al principio. Estas son tramas relativamente simples, pero pueden ser difíciles si esta es su primera vez con matplotlib, no dude en consultar las soluciones a medida que avanza.

** * NOTA: TODOS LOS COMANDOS PARA GRAFICAR UNA FIGURA DEBEN IR EN LA MISMA CÉLULA. SEPARARLAS EN CÉLULAS MÚLTIPLES PUEDE CAUSAR QUE NADA SE MOSTRARÁ. * **

# Ejercicios

Siga las instrucciones para recrear los gráficos con estos datos:

## Datos


```python
import numpy as np
x = np.arange(0,100)
y = x*2
z = x**2
```


** Importe matplotlib.pyplot como plt y establezca% matplotlib en línea si está utilizando el cuaderno jupyter. ¿Qué comando utilizas si no estás usando el cuaderno jupyter? **


```python
import matplotlib.pyplot as plt
%matplotlib inline
# plt.show() for non-notebook users
```

## Ejercicio 1

** Siga estos pasos: **
* ** Crea una figura llamada fig usando plt.figure () **
* ** Use add_axes para agregar un eje al lienzo de la figura en [0,0,1,1]. Llame a este nuevo eje "eje". **
* ** Trace (x, y) en esos ejes y configure las etiquetas y títulos para que coincidan con el siguiente diagrama: **


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
** Crea un objeto figura y coloca dos ejes sobre él, ax1 y ax2. Ubicado en [0,0,1,1] y [0.2,0.5, .2, .2] respectivamente. **


```python
fig = plt.figure()
ax1 = fig.add_axes([0,0,1,1])
ax2 = fig.add_axes([0.2,0.5,.2,.2])
```


![png](images/output_7_0.png)


** Ahora dibuje (x, y) en ambos ejes. Y llame a su figura objeto para mostrarlo. **


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

** Cree el siguiente diagrama agregando dos ejes a un objeto de figura en [0,0,1,1] y [0.2,0.5, .4, .4] **


```python
fig = plt.figure()

ax = fig.add_axes([0,0,1,1])
ax2 = fig.add_axes([0.2,0.5,.4,.4])
```


![png](images/output_11_0.png)


** Ahora use las matrices x, y, y z para recrear el diagrama a continuación. Observe los límites xlimits e y en el diagrama insertado: **


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

** Use plt.subplots (nrows = 1, ncols = 2) para crear la gráfica a continuación. **


```python
# Lienzo vacío de 1 por 2 subgrafo
fig, axes = plt.subplots(nrows=1, ncols=2)
```


![png](images/output_15_0.png)



** Ahora trace (x, y) y (x, z) en los ejes. Juega con el ancho de línea y el estilo **


```python
axes[0].plot(x,y,color="blue", lw=3, ls='--')
axes[1].plot(x,z,color="red", lw=3, ls='-')
fig
```




![png](images/output_17_0.png)




** Vea si puede cambiar el tamaño del gráfico agregando el argumento figsize () en plt.subplots () están copiando y pegando su código anterior. **


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
