# Introducción a Pandas

Pandas proporciona estructuras y funciones de datos enriquecidas, diseñadas para trabajar con datos estructurados de forma fácil, rápida y eficiente.
Combina las características de computación de matrices de alto rendimiento de NumPy, con las capacidades flexibles de manipulación de datos de hojas de Excel y bases de datos relacionales (como SQL).

Los principales componentes de Pandas son:
- Series
- Dataframes

## Instalar Pandas
### Anaconda
Para instalar Pandas realice los siguientes pasos:
1. Abrir anaconda
2. Elegir el ambiente de trabajo
3. Abrir un prompt de CMD.exe
4. Teclear `conda install pandas`

## Importar la libreria de Pandas
Para poder usar los componentes de Pandas, es necesario importar la libreria de la siguiente manera.


```python
import pandas as pd
import numpy as np
```

## El objeto Serie de Pandas
Una `Serie` de Pandas es una matriz unidimensional de datos indexados, la cual se puede crear a partir de una lista o matriz.


```python
datos = pd.Series([0.25, 0.5, 0.75, 1.0])
datos
```




    0    0.25
    1    0.50
    2    0.75
    3    1.00
    dtype: float64




```python
datos.values
```




    array([0.25, 0.5 , 0.75, 1.  ])




```python
datos.index
```




    RangeIndex(start=0, stop=4, step=1)




```python
# Para acceder a los datos usamos [] como en numpy
datos[0]
```




    0.25




```python
datos[1:3]
```




    1    0.50
    2    0.75
    dtype: float64



## Series como matriz de NumPy
La diferencia esencial es la presencia del índice: mientras que la matriz de Numpy tiene un índice entero, definido implícitamente para ser utilizado para acceder a los valores, las series de Pandas tienen un índice definido explícitamente asociado con los valores, que no necesariamente debe ser númerico.


```python
datos = pd.Series([0.25, 0.5, 0.75, 1.0],
                 index=['a', 'b', 'c', 'd'])
datos
```




    a    0.25
    b    0.50
    c    0.75
    d    1.00
    dtype: float64




```python
datos['b']
```




    0.5




```python
# Índices no secuenciales
datos = pd.Series([0.25, 0.5, 0.75, 1.0],
                 index=[2, 5, 3, 7])
datos
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
Las series de Pandas son como una especialización de un diccionario de Python. Un diccionario es una estructura que asigna claves arbitrarias, a un conjunto de valores arbitrarios y en series de Pandas, es una estructura que asigna claves a un conjunto de valores especificados.


```python
diccionario_poblacion = {'California': 38332521,
                   'Texas': 26448193,
                   'New York': 19651127,
                   'Florida': 19552860,
                   'Illinois': 12882135}
poblacion = pd.Series(diccionario_poblacion)
poblacion
```




    California    38332521
    Texas         26448193
    New York      19651127
    Florida       19552860
    Illinois      12882135
    dtype: int64



Por defecto, se crea un índice de las claves ordenadas. A partir de esto, se puede realizar el acceso típico a los elementos como si fuera un diccionario


```python
poblacion['California']
```




    38332521




```python
poblacion['California':'Florida']
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



## El objeto Dataframe de Pandas
Un `DataFrame` es una estructura de datos en 2 dimensiones, con columnas de diferentes tipos de datos y filas que se denominan índices. Se puede formar a partir de las siguientes estructuras de datos:

1. Matrices Numpy
2. Listas
3. Diccionarios
4. Series


```python
#Usando una matriz numpy
matriz = np.array([[0.8, 5.5], [3.7, 12.4]])
df1 = pd.DataFrame({'Columna1': array[:, 0], 'Columna2': array[:, 1]}, index=['A','B'])
print(df1)
```

       Columna1  Columna2
    A      0.8      5.5
    B      3.7     12.4



```python
#usando un diccionario de listas
d = {'columna_1': [1,2,3],
    'columna_2': ['abc',10.5,'xy'],
    'columna_3': [14,15,26]}
df = pd.DataFrame(d)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>columna_1</th>
      <th>columna_2</th>
      <th>columna_3</th>
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
#usando un diccionario de series
d = {'columna_1': pd.Series([1,2,3]),
    'columna_2': pd.Series(['abc',10.5,'xy'])}
df = pd.DataFrame(d)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>columna_1</th>
      <th>columna_2</th>
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
df['columna_1']

```




    0    1
    1    2
    2    3
    Name: columna_1, dtype: int64




```python
# seleccionando más de una columna
df[['columna_1','columna_2']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>columna_1</th>
      <th>columna_2</th>
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
#### -loc trabaja sobre etiquetas en el índice.
#### -iloc trabaja sobre la posición de los índices (solo toma enteros).


```python
#seleccionando renglones
df1.loc['A']
```




    Columna1    0.8
    Columna2    5.5
    Name: A, dtype: float64




```python
df1.iloc[0]
```




    Columna1    0.8
    Columna2    5.5
    Name: A, dtype: float64




```python
type(df1['Columna1'])
```




    pandas.core.series.Series



### Insertando una nueva columna


```python
df1['nueva'] = df1['Columna1'] + df1['Columna2']
df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Columna1</th>
      <th>Columna2</th>
      <th>nueva</th>
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
df1.drop('nueva',axis=1,inplace=True) # usar inplace para hacer los cambios permanentes
df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Columna1</th>
      <th>Columna2</th>
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
df1.loc['A','Columna1']
```




    0.8




```python
# resetear los índices
df1.reset_index(inplace=True)
df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Columna1</th>
      <th>Columna2</th>
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
df1.loc[[0,1],['index','Columna2']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Columna2</th>
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
df1[df1['Columna1']>1][['index','Columna2']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Columna2</th>
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
df1[(df1['Columna1']>1) & (df1['Columna2'] > 5)]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Columna1</th>
      <th>Columna2</th>
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
df1[(df1['Columna1']>1) | (df1['Columna2'] <= 5.5)]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Columna1</th>
      <th>Columna2</th>
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
df1[~((df1['Columna1']>1) | (df1['Columna2'] <= 5.5))]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Columna1</th>
      <th>Columna2</th>
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
df1['Columna3'] = a
df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Columna1</th>
      <th>Columna2</th>
      <th>Columna3</th>
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
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Columna1</th>
      <th>Columna2</th>
      <th>Columna3</th>
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
#Resetear el índice
df.reset_index(inplace=True)
df
```




<div>
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
#ordenar por índice
df.sort_index(ascending=False,inplace=True)
df
```




<div>
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
# establece los índices con alguna columna
df.set_index('col3',inplace=True)
df
```




<div>
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
dfhot = pd.DataFrame({'genero':['masculino','femenino','masculino','femenino','masculino'],'edad':['joven','adulto','adulto_mayor','joven','adulto']})
dfhot
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>genero</th>
      <th>age_range</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>masculino</td>
      <td>joven</td>
    </tr>
    <tr>
      <th>1</th>
      <td>femenino</td>
      <td>adulto</td>
    </tr>
    <tr>
      <th>2</th>
      <td>masculino</td>
      <td>adulto_mayor</td>
    </tr>
    <tr>
      <th>3</th>
      <td>femenino</td>
      <td>joven</td>
    </tr>
    <tr>
      <th>4</th>
      <td>masculino</td>
      <td>adulto</td>
    </tr>
  </tbody>
</table>
</div>




```python
dummies = pd.get_dummies(dfhot)
dummies
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>genero_femenino</th>
      <th>genero_masculino</th>
      <th>edad_adulto</th>
      <th>edad_adulto_mayor</th>
      <th>edad_joven</th>
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



## Aplicando funciones


```python
df = pd.DataFrame({'col1':[1,2,3,4,5],'col2':[0.8,55,44,25,4],'col3':['abc','det','gxx','wer','udf']})
df
```




<div>
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
def obtenerSoporte(X,datos):
    N = len(datos)
    soporte = (datos==X).sum() / N
    return soporte
```


```python
obtenerSoporte(55,df['col2'])
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
df['col2'].apply(lambda x: 'grande' if x > 20 else 'pequeño')
```




    0    pequeño
    1     grande
    2     grande
    3     grande
    4    pequeño
    Name: col2, dtype: object




```python
df['col4']= df['col3'].str[0:2].apply(lambda x: 1 if x==('de') else 0)
df
```




<div>
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




 [**Ejercicios**](Ejercicios/Pandas/Pandas%20Ejercicio.md)    



#### Referencias
- https://pandas.pydata.org/pandas-docs/stable/dsintro.html  
- https://pandas.pydata.org/pandas-docs/stable/getting_started/basics.html  
- https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.apply.html  
- https://jakevdp.github.io/PythonDataScienceHandbook/
