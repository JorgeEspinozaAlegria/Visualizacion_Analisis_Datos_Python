# Introducción a Pandas

Pandas proporciona estructuras y funciones de datos enriquecidas, diseñadas para trabajar con datos estructurados de forma fácil, rápida y eficiente.
Combina las características de computación de matrices de alto rendimiento de NumPy con las capacidades flexibles de manipulación de datos de hojas de Excel y bases de datos relacionales (como SQL). 

Los principales componentes de pandas son:
- Series
- Datraframes

## Instalar Pandas
### Anaconda
Para instalar Pandas realice los siguientes pasos:
1. Abrir anaconda
2. Elegir el ambiente de trabajo
3. Abrir un CMD.exe Prompt
4. Teclear `conda install pandas`

## Importar la libreria de Pandas
Para poder usar los componentes de Pandas es necesario importar la libreria, de la siguiente manera.


```python
import pandas as pd
import numpy as np
```

## El objeto de la serie Pandas 
Una `serie` de Pandas es una matriz unidimensional de datos indexados, la cual se puede crear a partir de una lista o matriz.


```python
data = pd.Series([0.25, 0.5, 0.75, 1.0])
data
```




    0    0.25
    1    0.50
    2    0.75
    3    1.00
    dtype: float64




```python
data.values
```




    array([0.25, 0.5 , 0.75, 1.  ])




```python
data.index
```




    RangeIndex(start=0, stop=4, step=1)




```python
# Para acceder a los datos usamos [] co o en numpy
data[0]
```




    0.25




```python
data[1:3]
```




    1    0.50
    2    0.75
    dtype: float64



## Series como matriz de NumPy
La diferencia esencial es la presencia del índice: mientras el Numpy Array tiene un índice entero definido implícitamente utilizado para acceder a los valores, las series de Pandas tienen un índice definido explícitamente asociado con los valores, que no necesariamente debe se númerico.


```python
data = pd.Series([0.25, 0.5, 0.75, 1.0],
                 index=['a', 'b', 'c', 'd'])
data
```




    a    0.25
    b    0.50
    c    0.75
    d    1.00
    dtype: float64




```python
data['b']
```




    0.5




```python
# Índices no secuenciales
data = pd.Series([0.25, 0.5, 0.75, 1.0],
                 index=[2, 5, 3, 7])
data
```




    2    0.25
    5    0.50
    3    0.75
    7    1.00
    dtype: float64




```python
data[5]
```




    0.5



## Serie como diccionario
Las series de Pandas son como una especialización de un diccionario de Python. Un diccionario es una estructura que asigna claves arbitrarias a un conjunto de valores arbitrarios, y en series de Pandas es una estructura que asigna claves a un conjunto de valores escritos. 


```python
population_dict = {'California': 38332521,
                   'Texas': 26448193,
                   'New York': 19651127,
                   'Florida': 19552860,
                   'Illinois': 12882135}
population = pd.Series(population_dict)
population
```




    California    38332521
    Texas         26448193
    New York      19651127
    Florida       19552860
    Illinois      12882135
    dtype: int64



Por defecto, se crea un índice de las claves ordenadas. Desde aquí, se puede realizar el acceso típico a elementos de estilo de diccionario


```python
population['California']
```




    38332521




```python
population['California':'Florida']
```




    California    38332521
    Texas         26448193
    New York      19651127
    Florida       19552860
    dtype: int64




```python
pd.Series(5, index=[100, 200, 300])
```




    100    5
    200    5
    300    5
    dtype: int64




```python
pd.Series({2:'a', 1:'b', 3:'c'})
```




    2    a
    1    b
    3    c
    dtype: object




```python
pd.Series({2:'a', 1:'b', 3:'c'}, index=[3, 2])
```




    3    c
    2    a
    dtype: object



## El objeto Pandas DataFrame
Un DataFrame es una estructura de datos 2D con columnas de diferentes tipos de datos y las filas se denominan índice. Se puede formar a partir de las siguientes estructuras de datos:

1. Numpy array
2. Listas
3. Diccionarios
4. Series


```python
#using numpy array
array = np.array([[0.8, 5.5], [3.7, 12.4]])
df1 = pd.DataFrame({'Column1': array[:, 0], 'Column2': array[:, 1]}, index=['A','B'])
print(df1)
```

       Column1  Column2
    A      0.8      5.5
    B      3.7     12.4
    


```python
#usando diccionario de listas
d = {'column_1': [1,2,3],
    'column_2': ['abc',10.5,'xy'],
    'column_3': [14,15,26]}
df = pd.DataFrame(d)
df
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
      <th>column_1</th>
      <th>column_2</th>
      <th>column_3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>abc</td>
      <td>14</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>10.5</td>
      <td>15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>xy</td>
      <td>26</td>
    </tr>
  </tbody>
</table>
</div>




```python
#usando diccionario de series
d = {'column_1': pd.Series([1,2,3]),
    'column_2': pd.Series(['abc',10.5,'xy'])}
df = pd.DataFrame(d)
df
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
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>10.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>xy</td>
    </tr>
  </tbody>
</table>
</div>



### Selección e Indexación


```python
# seleccionando una columna
df['column_1']

```




    0    1
    1    2
    2    3
    Name: column_1, dtype: int64




```python
# selecting more than one column
df[['column_1','column_2']]
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
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>10.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>xy</td>
    </tr>
  </tbody>
</table>
</div>



### <u>loc e iloc:</u>
#### -loc trabaja sobre etiquetas in el índice.
#### -iloc trabaja sobre la posición de los índices (solo toma enteros).


```python
#selecting rows
df1.loc['A']
```




    Column1    0.8
    Column2    5.5
    Name: A, dtype: float64




```python
df1.iloc[0]
```




    Column1    0.8
    Column2    5.5
    Name: A, dtype: float64




```python
type(df1['Column1'])
```




    pandas.core.series.Series



### Insertando una nueva columna


```python
df1['new'] = df1['Column1'] + df1['Column2']
df1
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
      <th>Column1</th>
      <th>Column2</th>
      <th>new</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>0.8</td>
      <td>5.5</td>
      <td>6.3</td>
    </tr>
    <tr>
      <th>B</th>
      <td>3.7</td>
      <td>12.4</td>
      <td>16.1</td>
    </tr>
  </tbody>
</table>
</div>



### Borrando una columna


```python
df1.drop('new',axis=1,inplace=True) # use inplace para hacer los cambios permanentes
df1
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
      <th>Column1</th>
      <th>Column2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>0.8</td>
      <td>5.5</td>
    </tr>
    <tr>
      <th>B</th>
      <td>3.7</td>
      <td>12.4</td>
    </tr>
  </tbody>
</table>
</div>



### Selecionando un subconjunto de un dataframe por filas y columnas


```python
df1.loc['A','Column1']
```




    0.8




```python
# reset los índices
df1.reset_index(inplace=True)
df1
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
      <th>index</th>
      <th>Column1</th>
      <th>Column2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>0.8</td>
      <td>5.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>B</td>
      <td>3.7</td>
      <td>12.4</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.loc[[0,1],['index','Column2']]
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
      <th>index</th>
      <th>Column2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>5.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>B</td>
      <td>12.4</td>
    </tr>
  </tbody>
</table>
</div>



### Selección por condición


```python
df1[df1['Column1']>1][['index','Column2']]
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
      <th>index</th>
      <th>Column2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>B</td>
      <td>12.4</td>
    </tr>
  </tbody>
</table>
</div>




```python
# condición AND
df1[(df1['Column1']>1) & (df1['Column2'] > 5)]
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
      <th>index</th>
      <th>Column1</th>
      <th>Column2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>B</td>
      <td>3.7</td>
      <td>12.4</td>
    </tr>
  </tbody>
</table>
</div>




```python
# condición OR
df1[(df1['Column1']>1) | (df1['Column2'] <= 5.5)]
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
      <th>index</th>
      <th>Column1</th>
      <th>Column2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>0.8</td>
      <td>5.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>B</td>
      <td>3.7</td>
      <td>12.4</td>
    </tr>
  </tbody>
</table>
</div>




```python
# condición NOT
df1[~((df1['Column1']>1) | (df1['Column2'] <= 5.5))]
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
      <th>index</th>
      <th>Column1</th>
      <th>Column2</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>



### Propiedades de los índices


```python
# matriz de los valores de los índices
df1.index.values
```




    array([0, 1], dtype=int64)




```python
#Usando la función split para tener una lista de cadenas
a = '10 abc'.split()
print(a)
```

    ['10', 'abc']
    


```python
#Insertar una nueva columna desde una lista de valores
df1['Column3'] = a
df1
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
      <th>index</th>
      <th>Column1</th>
      <th>Column2</th>
      <th>Column3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>0.8</td>
      <td>5.5</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>B</td>
      <td>3.7</td>
      <td>12.4</td>
      <td>abc</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Insertar una nueva fila
df1.loc[2]=['C',32,11.8,'xyz']
df1
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
      <th>index</th>
      <th>Column1</th>
      <th>Column2</th>
      <th>Column3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>0.8</td>
      <td>5.5</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>B</td>
      <td>3.7</td>
      <td>12.4</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>2</th>
      <td>C</td>
      <td>32.0</td>
      <td>11.8</td>
      <td>xyz</td>
    </tr>
  </tbody>
</table>
</div>



### Propiedades de los índices


```python
df = pd.DataFrame({'col1':[10,20,30,40,50],'col2':[4,5,6,5,2],'col3':['abc','def','ghi','xyz','123']})
df.head()
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
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10</td>
      <td>4</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20</td>
      <td>5</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>30</td>
      <td>6</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>40</td>
      <td>5</td>
      <td>xyz</td>
    </tr>
    <tr>
      <th>4</th>
      <td>50</td>
      <td>2</td>
      <td>123</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['col2'].sum()
```




    22




```python
(df['col2']==5).sum()
```




    2




```python
df['col2'].count()
```




    5




```python
df['col2'].value_counts()
```




    5    2
    6    1
    4    1
    2    1
    Name: col2, dtype: int64




```python
df['col2'].values
```




    array([4, 5, 6, 5, 2], dtype=int64)




```python
a = df.columns.values
s = sorted(a)
print(s)
```

    ['col1', 'col2', 'col3']
    


```python
df.sort_values(by='col2')
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
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>50</td>
      <td>2</td>
      <td>123</td>
    </tr>
    <tr>
      <th>0</th>
      <td>10</td>
      <td>4</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20</td>
      <td>5</td>
      <td>def</td>
    </tr>
    <tr>
      <th>3</th>
      <td>40</td>
      <td>5</td>
      <td>xyz</td>
    </tr>
    <tr>
      <th>2</th>
      <td>30</td>
      <td>6</td>
      <td>ghi</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[5]=[np.nan,2,np.nan]
df
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
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10.0</td>
      <td>4.0</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20.0</td>
      <td>5.0</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>30.0</td>
      <td>6.0</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>40.0</td>
      <td>5.0</td>
      <td>xyz</td>
    </tr>
    <tr>
      <th>4</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>123</td>
    </tr>
    <tr>
      <th>5</th>
      <td>NaN</td>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.dropna(inplace=True)
df
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
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10.0</td>
      <td>4.0</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20.0</td>
      <td>5.0</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>30.0</td>
      <td>6.0</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>40.0</td>
      <td>5.0</td>
      <td>xyz</td>
    </tr>
    <tr>
      <th>4</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>123</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[5]=[np.nan,2,np.nan]
df.fillna('sin valor',inplace=True)
df
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
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10</td>
      <td>4.0</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20</td>
      <td>5.0</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>30</td>
      <td>6.0</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>40</td>
      <td>5.0</td>
      <td>xyz</td>
    </tr>
    <tr>
      <th>4</th>
      <td>50</td>
      <td>2.0</td>
      <td>123</td>
    </tr>
    <tr>
      <th>5</th>
      <td>sin valor</td>
      <td>2.0</td>
      <td>sin valor</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[6]=[np.nan,2,np.nan]
df.isnull()
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
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>5</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>6</th>
      <td>True</td>
      <td>False</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Reset índice
df.reset_index(inplace=True)
df
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
      <th>index</th>
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>10</td>
      <td>4.0</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>20</td>
      <td>5.0</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>30</td>
      <td>6.0</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>40</td>
      <td>5.0</td>
      <td>xyz</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>50</td>
      <td>2.0</td>
      <td>123</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>sin valor</td>
      <td>2.0</td>
      <td>sin valor</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
#ordenar por index
df.sort_index(ascending=False,inplace=True)
df
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
      <th>index</th>
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>sin valor</td>
      <td>2.0</td>
      <td>sin valor</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>50</td>
      <td>2.0</td>
      <td>123</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>40</td>
      <td>5.0</td>
      <td>xyz</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>30</td>
      <td>6.0</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>20</td>
      <td>5.0</td>
      <td>def</td>
    </tr>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>10</td>
      <td>4.0</td>
      <td>abc</td>
    </tr>
  </tbody>
</table>
</div>




```python
# establece los índices con con alguna columna
df.set_index('col3',inplace=True)
df
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
      <th>index</th>
      <th>col1</th>
      <th>col2</th>
    </tr>
    <tr>
      <th>col3</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>NaN</th>
      <td>6</td>
      <td>NaN</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>sin valor</th>
      <td>5</td>
      <td>sin valor</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>123</th>
      <td>4</td>
      <td>50</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>xyz</th>
      <td>3</td>
      <td>40</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>ghi</th>
      <td>2</td>
      <td>30</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>def</th>
      <td>1</td>
      <td>20</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>abc</th>
      <td>0</td>
      <td>10</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Restablece los índices
df.reset_index(inplace=True)
df
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
      <th>col3</th>
      <th>index</th>
      <th>col1</th>
      <th>col2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>6</td>
      <td>NaN</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>sin valor</td>
      <td>5</td>
      <td>sin valor</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>123</td>
      <td>4</td>
      <td>50</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>xyz</td>
      <td>3</td>
      <td>40</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ghi</td>
      <td>2</td>
      <td>30</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>def</td>
      <td>1</td>
      <td>20</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>abc</td>
      <td>0</td>
      <td>10</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>



### Operaciones con cadenas


```python
df['col3'].str.extract('(\w+)',expand=False)
```




    0    NaN
    1    sin
    2    123
    3    xyz
    4    ghi
    5    def
    6    abc
    Name: col3, dtype: object



### Filtrando


```python
df[df['col3']=='abc']
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
      <th>col3</th>
      <th>index</th>
      <th>col1</th>
      <th>col2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6</th>
      <td>abc</td>
      <td>0</td>
      <td>10</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>



### Convierte a mayúsculas/Minúsculas


```python
df['col3'].str.upper()#lower()
```




    0          NaN
    1    SIN VALOR
    2          123
    3          XYZ
    4          GHI
    5          DEF
    6          ABC
    Name: col3, dtype: object



### Separar cadenas


```python
df['col3'].str.split('b')
```




    0            NaN
    1    [sin valor]
    2          [123]
    3          [xyz]
    4          [ghi]
    5          [def]
    6         [a, c]
    Name: col3, dtype: object



### Reemplazar


```python
df['col3'].str.replace(' ','__')
```




    0           NaN
    1    sin__valor
    2           123
    3           xyz
    4           ghi
    5           def
    6           abc
    Name: col3, dtype: object



### Contener


```python
c=df['col3'].str.contains('a')
c
```




    0      NaN
    1     True
    2    False
    3    False
    4    False
    5    False
    6     True
    Name: col3, dtype: object



### ONE HOT ENCONDING


```python
dfhot = pd.DataFrame({'gender':['male','female','male','female','male'],'age_range':['young','adult','senior','young','adult']})
dfhot
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
      <th>gender</th>
      <th>age_range</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>male</td>
      <td>young</td>
    </tr>
    <tr>
      <th>1</th>
      <td>female</td>
      <td>adult</td>
    </tr>
    <tr>
      <th>2</th>
      <td>male</td>
      <td>senior</td>
    </tr>
    <tr>
      <th>3</th>
      <td>female</td>
      <td>young</td>
    </tr>
    <tr>
      <th>4</th>
      <td>male</td>
      <td>adult</td>
    </tr>
  </tbody>
</table>
</div>




```python
data_dummies = pd.get_dummies(dfhot)
data_dummies
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
      <th>gender_female</th>
      <th>gender_male</th>
      <th>age_range_adult</th>
      <th>age_range_senior</th>
      <th>age_range_young</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



## Aplicando a funciones


```python
df = pd.DataFrame({'col1':[1,2,3,4,5],'col2':[0.8,55,44,25,4],'col3':['abc','det','gxx','wer','udf']})
df
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
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0.8</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>55.0</td>
      <td>det</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>44.0</td>
      <td>gxx</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>25.0</td>
      <td>wer</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>4.0</td>
      <td>udf</td>
    </tr>
  </tbody>
</table>
</div>




```python
def log(x):
    return np.log(x)
```


```python
log(df['col2'])
```




    0   -0.223144
    1    4.007333
    2    3.784190
    3    3.218876
    4    1.386294
    Name: col2, dtype: float64




```python
def getsupport(X,data):
    N = len(data)
    support = (data==X).sum() / N
    return support
```


```python
getsupport(55,df['col2'])
```




    0.2




```python
df['col2'].apply(log)
```




    0   -0.223144
    1    4.007333
    2    3.784190
    3    3.218876
    4    1.386294
    Name: col2, dtype: float64



## Función Lambda

#### Expresión general: lambda arg1, arg2, ...argN : expresión usando argumentos


```python
df['col2'].apply(lambda x: np.log(x))
```




    0   -0.223144
    1    4.007333
    2    3.784190
    3    3.218876
    4    1.386294
    Name: col2, dtype: float64




```python
df['col1'].apply(lambda x: x**2)
```




    0     1
    1     4
    2     9
    3    16
    4    25
    Name: col1, dtype: int64




```python
# lambda con condicionales
df['col2'].apply(lambda x: 'big' if x > 20 else 'small')
```




    0    small
    1      big
    2      big
    3      big
    4    small
    Name: col2, dtype: object




```python
df['col4']= df['col3'].str[0:2].apply(lambda x: 1 if x==('de') else 0)
df
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
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
      <th>col4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0.8</td>
      <td>abc</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>55.0</td>
      <td>det</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>44.0</td>
      <td>gxx</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>25.0</td>
      <td>wer</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>4.0</td>
      <td>udf</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



## Usando la función `map` y `lambda`


```python
df['col5'] = list(map(lambda x : x * 5, df['col1']))
df
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
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
      <th>col4</th>
      <th>col5</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0.8</td>
      <td>abc</td>
      <td>0</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>55.0</td>
      <td>det</td>
      <td>1</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>44.0</td>
      <td>gxx</td>
      <td>0</td>
      <td>15</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>25.0</td>
      <td>wer</td>
      <td>0</td>
      <td>20</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>4.0</td>
      <td>udf</td>
      <td>0</td>
      <td>25</td>
    </tr>
  </tbody>
</table>
</div>



#<div style="text-align: right">    
 [**Ejercicios**](Ejercicios/Pandas/Pandas%20Ejercicio.ipynb)    
<div/>#


#### Referencias
- https://pandas.pydata.org/pandas-docs/stable/dsintro.html  
- https://pandas.pydata.org/pandas-docs/stable/getting_started/basics.html  
- https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.apply.html  
- https://jakevdp.github.io/PythonDataScienceHandbook/
