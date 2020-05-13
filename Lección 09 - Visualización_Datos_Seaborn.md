# Visualización de Datos con Seaborn

## Instalación Seaborn:
- pip install seaborn
- conda install seaborn


```python
# Importemos las librerias que vamos a ocupar
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
%matplotlib inline
```

## Carguemos los datos


```python
iris_ = pd.read_csv("../Python_Cursos/data/iris_dataset.csv")
iris_.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SepalLength</th>
      <th>SepalWidth</th>
      <th>PetalLength</th>
      <th>PetalWidth</th>
      <th>Class</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
  </tbody>
</table>
</div>



## Carguemos los datos con seaborn


```python
iris = sns.load_dataset("iris")
iris.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Violinplot
sns.violinplot(x = "sepal_length", data=iris)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22895fe16a0>




![png](/images/Seaborn/output_7_1.png)


## Estilos en Seaborn


```python
# Styles: darkgrid, whitegrid, dark, white, and ticks
sns.set_style("whitegrid")
sns.boxplot("species", "petal_length", data=iris)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x228961747f0>




![png](/images/Seaborn/output_9_1.png)


## Grids in Seaborn


```python
sns.set_style("whitegrid")
sns.boxplot("species", "petal_length", data=iris)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22a5859ec48>




![png](/images/Seaborn/output_11_1.png)



```python
sns.set_style("white")
sns.boxplot("species", "petal_length", data=iris)
sns.despine()
```


![png](/images/Seaborn/output_12_0.png)



```python
sns.set_style("whitegrid")
sns.boxplot("species", "petal_length", data=iris)
sns.despine(left=True, bottom=True)
```


![png](/images/Seaborn/output_13_0.png)


## set_context y set


```python
# Los contextos disponibles son: paper, notebook, talk and poster
sns.set_style("ticks")
sns.set_context("paper")
sns.boxplot("species", "petal_length", data=iris)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x2289640d2b0>




![png](/images/Seaborn/output_15_1.png)



```python
sns.set_style("ticks")
sns.set_context("poster")
sns.boxplot("species", "petal_length", data=iris)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x228962e1ba8>




![png](/images/Seaborn/output_16_1.png)



```python
sns.set_style("whitegrid")
sns.set_context("poster", font_scale = .5, rc={"grid.linewidth": 0.6})
sns.boxplot("species", "petal_length", data=iris)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22896519c88>




![png](/images/Seaborn/output_17_1.png)



```python
# podemos pasarle mas argumentos al set_context() 
sns.set_context("paper", font_scale=1.8, rc={"font.size":5,"axes.labelsize":1.0})
sns.boxplot("species", "petal_length", data=iris, palette="husl")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x228965a0ba8>




![png](/images/Seaborn/output_18_1.png)



```python
# Restablecer parámetros predeterminados
sns.set(rc={"font.size":6,"axes.labelsize":6})
sns.boxplot("species", "petal_length", data=iris, palette="husl")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22896628908>




![png](/images/Seaborn/output_19_1.png)



```python
# Restablecer parámetros predeterminados
sns.set(palette='Set2')
sns.set_context("notebook")
sns.boxplot("species", "petal_length", data=iris)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x228966ab080>




![png](/images/Seaborn/output_20_1.png)



```python
sns.plotting_context()
```




    {'font.size': 12.0,
     'axes.labelsize': 12.0,
     'axes.titlesize': 12.0,
     'xtick.labelsize': 11.0,
     'ytick.labelsize': 11.0,
     'legend.fontsize': 11.0,
     'axes.linewidth': 1.25,
     'grid.linewidth': 1.0,
     'lines.linewidth': 1.5,
     'lines.markersize': 6.0,
     'patch.linewidth': 1.0,
     'xtick.major.width': 1.25,
     'ytick.major.width': 1.25,
     'xtick.minor.width': 1.0,
     'ytick.minor.width': 1.0,
     'xtick.major.size': 6.0,
     'ytick.major.size': 6.0,
     'xtick.minor.size': 4.0,
     'ytick.minor.size': 4.0,
     'legend.title_fontsize': 12.0}



## Cómo establecer el tamaño de la figura en Seaborn


```python
fig, ax = plt.subplots(figsize=(10,4))
sns.stripplot(x="species", y="petal_length", data=iris, ax=ax)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22896744be0>




![png](/images/Seaborn/output_23_1.png)



```python
sns.catplot("species", "petal_length", data=iris, kind="bar", height=5, aspect=2, palette="muted", legend=False)
```




    <seaborn.axisgrid.FacetGrid at 0x22893cf9cc0>




![png](/images/Seaborn/output_24_1.png)


## Cómo rotar el texto de la etiqueta en Seaborn


```python
sns.set_context("poster",font_scale = .5,)
g = sns.catplot("species", "petal_length", data=iris, kind="bar", height=4, aspect=2, palette="Paired")
g.set_xticklabels(rotation=90)
```




    <seaborn.axisgrid.FacetGrid at 0x2289671f9e8>




![png](/images/Seaborn/output_26_1.png)


## Configuración de xlim e ylim en Seaborn


```python
g = sns.catplot("species", "petal_length", data=iris, kind="bar", height=4, aspect=2, palette="Set2", legend=False)
g.set_xticklabels(rotation=90)
g.set(ylim=(0, 12)) # alternative you can use : ax.set_ylim(0,10)
```




    <seaborn.axisgrid.FacetGrid at 0x22896874748>




![png](/images/Seaborn/output_28_1.png)


## Agregar un titulo


```python
b = sns.boxplot("species", "petal_length", data=iris, palette="muted")
b.set_title('Bar graph for species')
```




    Text(0.5, 1.0, 'Bar graph for species')




![png](/images/Seaborn/output_30_1.png)


## Gráficos de Datos Categóricos

### Gráficos de barras


```python
iris.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
fig, ax = plt.subplots(figsize=(6,4))
sns.barplot(x=iris["species"], y=iris["sepal_length"], palette="pastel",data=iris,ax=ax,estimator=lambda x: sum(x)/len(x))
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22897a7a630>




![png](/images/Seaborn/output_34_1.png)


### Puedes usar una función de estimador.


```python
fig, ax = plt.subplots(1,2,figsize=(6,4))
sns.barplot(x=iris["species"], y=iris["sepal_length"], palette="Paired",data=iris,ax=ax[0],estimator=np.count_nonzero)
sns.barplot(x=iris["species"], y=iris["petal_length"], palette="Set2",data=iris,ax=ax[1],estimator=np.mean)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22897c367b8>




![png](/images/Seaborn/output_36_1.png)


## Grafico de caja


```python
planets = sns.load_dataset('planets')
planets.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>method</th>
      <th>number</th>
      <th>orbital_period</th>
      <th>mass</th>
      <th>distance</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Radial Velocity</td>
      <td>1</td>
      <td>269.300</td>
      <td>7.10</td>
      <td>77.40</td>
      <td>2006</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Radial Velocity</td>
      <td>1</td>
      <td>874.774</td>
      <td>2.21</td>
      <td>56.95</td>
      <td>2008</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Radial Velocity</td>
      <td>1</td>
      <td>763.000</td>
      <td>2.60</td>
      <td>19.84</td>
      <td>2011</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Radial Velocity</td>
      <td>1</td>
      <td>326.030</td>
      <td>19.40</td>
      <td>110.62</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Radial Velocity</td>
      <td>1</td>
      <td>516.220</td>
      <td>10.50</td>
      <td>119.47</td>
      <td>2009</td>
    </tr>
  </tbody>
</table>
</div>




```python
sns.set(style="ticks", palette="muted")
ax = sns.boxplot(x="distance", y="method", data=planets)
ax.set_xscale("log")
```


![png](/images/Seaborn/output_39_0.png)


## Gráfico de Violin


```python
tips = sns.load_dataset('tips')
tips.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
sns.set(style="whitegrid")
sns.violinplot(x="time",y="total_bill", data=tips, palette="rainbow", hue='time')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22897bfa978>




![png](/images/Seaborn/output_42_1.png)



```python
sns.violinplot(x="day",y="total_bill", data=tips, palette="rainbow", hue='sex')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22897a65a20>




![png](/images/Seaborn/output_43_1.png)


#### Violines agrupados con violines divididos


```python
sns.violinplot(x="day", y="total_bill", hue="sex", data=tips, split=True,inner="quart",
               palette={"Male": "#33FFF8", "Female": "#FDFF33"})
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22897b040b8>




![png](/images/Seaborn/output_45_1.png)


#### Matriz de diagrama de dispersión: función Pairplot ()


```python
sns.pairplot(iris, hue="species", palette='cubehelix')
```




    <seaborn.axisgrid.PairGrid at 0x22897a3e5f8>




![png](/images/Seaborn/output_47_1.png)


### Cat Plot: es la forma general de una trama


```python
sns.set(style="ticks")
g = sns.catplot("day", "total_bill", "sex", data=tips, kind="box", palette='cubehelix')
g.set_axis_labels("Day", "Total Bill")
```




    <seaborn.axisgrid.FacetGrid at 0x22897b47ac8>




![png](/images/Seaborn/output_49_1.png)


### FaceGrid
Se utiliza para dibujar trazados con varios ejes en los que cada eje muestra la misma relación condicionada a diferentes niveles de alguna variable. Es posible condicionar hasta tres variables asignando variables a las filas y columnas de la cuadrícula y usando diferentes colores para los elementos de la trama. El flujo de trabajo básico es inicializar el objeto FacetGrid con el conjunto de datos y las variables que se utilizan para estructurar la cuadrícula. Luego, se pueden aplicar una o más funciones de trazado a cada subconjunto llamando a FacetGrid.map () o FacetGrid.map_dataframe (). Finalmente, la trama se puede ajustar con otros métodos para hacer cosas como cambiar las etiquetas de los ejes, usar diferentes marcas o agregar una leyenda.


```python
sns.set(style="ticks")
g = sns.FacetGrid(tips, col="time", row="smoker",height=2)
```


![png](/images/Seaborn/output_51_0.png)



```python
g = sns.FacetGrid(tips, col="time",  row="smoker")
g = g.map(plt.hist, "total_bill", color='red')
```


![png](/images/Seaborn/output_52_0.png)


### Cambie el tamaño y la relación del aspecto de cada faceta:


```python
g = sns.FacetGrid(tips, col="smoker", col_order=["Yes", "No"], height=4, aspect=1)
g.map(plt.hist, "total_bill", color="green")
```




    <seaborn.axisgrid.FacetGrid at 0x22899da0fd0>




![png](/images/Seaborn/output_54_1.png)


### Configuración de la paleta de colores:


```python
kws = dict(s=40, linewidth=.5, edgecolor="w")
g = sns.FacetGrid(tips, col="sex", hue="time", palette="Set2", hue_order=["Dinner", "Lunch"])
g = (g.map(plt.scatter, "total_bill", "tip", **kws).add_legend())
```


![png](/images/Seaborn/output_56_0.png)


### Use un marcador diferente para los niveles de tono:


```python
palette = dict(Lunch="blue", Dinner="red")
g = sns.FacetGrid(tips, col="sex", hue="time", palette=palette,
                  hue_order=["Dinner", "Lunch"],
                  hue_kws=dict(marker=["^", "v"]))
g = (g.map(plt.scatter, "total_bill", "tip", **kws).add_legend())
```


![png](/images/Seaborn/output_58_0.png)


### Use diferentes etiquetas de ejes después de trazar:


```python
g = sns.FacetGrid(tips, col="smoker", row="sex")
g = (g.map(plt.scatter, "total_bill", "tip", color="g", **kws)
     .set_axis_labels("Total bill (USD)", "TIP"))
```


![png](/images/Seaborn/output_60_0.png)


## Datos Númericos

### Distribuciones univariadas:


```python
# Función displot
x = np.random.normal(size=100)
sns.distplot(x, color='red')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22899f97128>




![png](/images/Seaborn/output_63_1.png)


### Histogramas


- Un histograma representa la distribución de datos formando contenedores a lo largo del rango de datos y luego dibujando barras para mostrar el número de observaciones que caen en cada contenedor. También podemos trazar un diagrama de alfombra, que dibuja una pequeña marca vertical en cada observación.


```python
sns.distplot(x, kde=False, rug=True, color='green', label='Histogram')
plt.legend(loc='best')
```




    <matplotlib.legend.Legend at 0x22899f9d7f0>




![png](/images/Seaborn/output_66_1.png)


### Estimación de densidad de los datos:


```python
sns.distplot(x, hist=False, rug=True)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22899dd6828>




![png](/images/Seaborn/output_68_1.png)



```python
sns.kdeplot(x, color='orange',shade=True)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x22899c6af98>




![png](/images/Seaborn/output_69_1.png)


### Uniendo gráficos


```python
# Gráficos de barras
sns.set(style="white")
tips = sns.load_dataset("tips")
sns.jointplot(x="total_bill", y="tip", data=tips, color='red')
```




    <seaborn.axisgrid.JointGrid at 0x228998c91d0>




![png](/images/Seaborn/output_71_1.png)


### Gráficos de hexbin:
muestra los recuentos de observaciones que se encuentran dentro de los contenedores hexagonales


```python
sns.jointplot("total_bill", "tip", data=tips, color='green', kind="hex")
```




    <seaborn.axisgrid.JointGrid at 0x2289a1f44e0>




![png](/images/Seaborn/output_73_1.png)



```python
# kde gráfico 2D
sns.jointplot("total_bill", "tip", data=tips, kind="kde", space=0, color="green")
```




    <seaborn.axisgrid.JointGrid at 0x228998661d0>




![png](/images/Seaborn/output_74_1.png)



```python
iris = sns.load_dataset("iris")
iris.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Gráfico de dispersión
sns.jointplot("petal_length", "sepal_length", data=iris,
                  marginal_kws=dict(bins=15, rug=True),
                  s=40, color='blue', edgecolor="w", linewidth=1,
                 height=5, ratio=5)
```




    <seaborn.axisgrid.JointGrid at 0x2289b2a2630>




![png](/images/Seaborn/output_76_1.png)


#### Ajustar regresión lineal a datos:


```python
sns.jointplot("sepal_length", "sepal_width", data=iris,color='purple', kind="reg", height=6)
```




    <seaborn.axisgrid.JointGrid at 0x2289b419c50>




![png](/images/Seaborn/output_78_1.png)



```python
# regresión lineal pora múltiples variables
sns.pairplot(iris, kind="reg", height=2, aspect=1.2)
```




    <seaborn.axisgrid.PairGrid at 0x2289b5539b0>




![png](/images/Seaborn/output_79_1.png)



```python
sns.pairplot(iris, kind="reg", hue="species", palette="coolwarm", height=2, aspect=1.2)
```




    <seaborn.axisgrid.PairGrid at 0x2289bbe0ac8>




![png](/images/Seaborn/output_80_1.png)


### Mapa de calor:


```python
iris.corr()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>sepal_length</th>
      <td>1.000000</td>
      <td>-0.117570</td>
      <td>0.871754</td>
      <td>0.817941</td>
    </tr>
    <tr>
      <th>sepal_width</th>
      <td>-0.117570</td>
      <td>1.000000</td>
      <td>-0.428440</td>
      <td>-0.366126</td>
    </tr>
    <tr>
      <th>petal_length</th>
      <td>0.871754</td>
      <td>-0.428440</td>
      <td>1.000000</td>
      <td>0.962865</td>
    </tr>
    <tr>
      <th>petal_width</th>
      <td>0.817941</td>
      <td>-0.366126</td>
      <td>0.962865</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# si no se necesita la colorbar cbar=false
plt.figure(figsize=(8,6))
ax = sns.heatmap(iris.corr(), annot=True, linecolor='white',linewidths=.3, fmt='.2f', cbar=True, cmap=(sns.color_palette("Blues")))
bottom, top = ax.get_ylim()
ax.set_ylim(bottom + 0.5, top - 0.5)
```




    (4.5, -0.5)




![png](/images/Seaborn/output_83_1.png)


### Conjunto de datos de vuelos:


```python
flights = sns.load_dataset("flights")
flights.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>month</th>
      <th>passengers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1949</td>
      <td>January</td>
      <td>112</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1949</td>
      <td>February</td>
      <td>118</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1949</td>
      <td>March</td>
      <td>132</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1949</td>
      <td>April</td>
      <td>129</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1949</td>
      <td>May</td>
      <td>121</td>
    </tr>
  </tbody>
</table>
</div>




```python
f = flights.pivot_table(index='month', columns='year', values='passengers')
f
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>year</th>
      <th>1949</th>
      <th>1950</th>
      <th>1951</th>
      <th>1952</th>
      <th>1953</th>
      <th>1954</th>
      <th>1955</th>
      <th>1956</th>
      <th>1957</th>
      <th>1958</th>
      <th>1959</th>
      <th>1960</th>
    </tr>
    <tr>
      <th>month</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>January</th>
      <td>112</td>
      <td>115</td>
      <td>145</td>
      <td>171</td>
      <td>196</td>
      <td>204</td>
      <td>242</td>
      <td>284</td>
      <td>315</td>
      <td>340</td>
      <td>360</td>
      <td>417</td>
    </tr>
    <tr>
      <th>February</th>
      <td>118</td>
      <td>126</td>
      <td>150</td>
      <td>180</td>
      <td>196</td>
      <td>188</td>
      <td>233</td>
      <td>277</td>
      <td>301</td>
      <td>318</td>
      <td>342</td>
      <td>391</td>
    </tr>
    <tr>
      <th>March</th>
      <td>132</td>
      <td>141</td>
      <td>178</td>
      <td>193</td>
      <td>236</td>
      <td>235</td>
      <td>267</td>
      <td>317</td>
      <td>356</td>
      <td>362</td>
      <td>406</td>
      <td>419</td>
    </tr>
    <tr>
      <th>April</th>
      <td>129</td>
      <td>135</td>
      <td>163</td>
      <td>181</td>
      <td>235</td>
      <td>227</td>
      <td>269</td>
      <td>313</td>
      <td>348</td>
      <td>348</td>
      <td>396</td>
      <td>461</td>
    </tr>
    <tr>
      <th>May</th>
      <td>121</td>
      <td>125</td>
      <td>172</td>
      <td>183</td>
      <td>229</td>
      <td>234</td>
      <td>270</td>
      <td>318</td>
      <td>355</td>
      <td>363</td>
      <td>420</td>
      <td>472</td>
    </tr>
    <tr>
      <th>June</th>
      <td>135</td>
      <td>149</td>
      <td>178</td>
      <td>218</td>
      <td>243</td>
      <td>264</td>
      <td>315</td>
      <td>374</td>
      <td>422</td>
      <td>435</td>
      <td>472</td>
      <td>535</td>
    </tr>
    <tr>
      <th>July</th>
      <td>148</td>
      <td>170</td>
      <td>199</td>
      <td>230</td>
      <td>264</td>
      <td>302</td>
      <td>364</td>
      <td>413</td>
      <td>465</td>
      <td>491</td>
      <td>548</td>
      <td>622</td>
    </tr>
    <tr>
      <th>August</th>
      <td>148</td>
      <td>170</td>
      <td>199</td>
      <td>242</td>
      <td>272</td>
      <td>293</td>
      <td>347</td>
      <td>405</td>
      <td>467</td>
      <td>505</td>
      <td>559</td>
      <td>606</td>
    </tr>
    <tr>
      <th>September</th>
      <td>136</td>
      <td>158</td>
      <td>184</td>
      <td>209</td>
      <td>237</td>
      <td>259</td>
      <td>312</td>
      <td>355</td>
      <td>404</td>
      <td>404</td>
      <td>463</td>
      <td>508</td>
    </tr>
    <tr>
      <th>October</th>
      <td>119</td>
      <td>133</td>
      <td>162</td>
      <td>191</td>
      <td>211</td>
      <td>229</td>
      <td>274</td>
      <td>306</td>
      <td>347</td>
      <td>359</td>
      <td>407</td>
      <td>461</td>
    </tr>
    <tr>
      <th>November</th>
      <td>104</td>
      <td>114</td>
      <td>146</td>
      <td>172</td>
      <td>180</td>
      <td>203</td>
      <td>237</td>
      <td>271</td>
      <td>305</td>
      <td>310</td>
      <td>362</td>
      <td>390</td>
    </tr>
    <tr>
      <th>December</th>
      <td>118</td>
      <td>140</td>
      <td>166</td>
      <td>194</td>
      <td>201</td>
      <td>229</td>
      <td>278</td>
      <td>306</td>
      <td>336</td>
      <td>337</td>
      <td>405</td>
      <td>432</td>
    </tr>
  </tbody>
</table>
</div>



### Mapa de clúster

Dendograma: relación jerárquica entre objetos.  
La clave para interpretar un dendrograma es centrarse en la altura en el que dos objetos se unen.


```python
sns.clustermap(f,figsize=(8, 10), cmap='coolwarm', linecolor='white', linewidths=1)
```




    <seaborn.matrix.ClusterGrid at 0x2289c6a5f60>




![png](/images/Seaborn/output_89_1.png)



  
 [**Siguiente Lección**](Lecci%C3%B3n%2009%20-%20Visualizaci%C3%B3n_Datos_Seaborn.ipynb)    


## Referencias:
- https://seaborn.pydata.org/installing.html
- https://seaborn.pydata.org/
- https://seaborn.pydata.org/generated/seaborn.color_palette.html
- https://seaborn.pydata.org/tutorial/color_palettes.html
- http://seaborn.pydata.org/tutorial/categorical.html
- https://seaborn.pydata.org/tutorial/color_palettes.html
- https://seaborn.pydata.org/
