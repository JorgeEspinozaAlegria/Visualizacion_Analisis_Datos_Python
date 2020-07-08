# Procesamiento de Datos

## Combinar conjuntos de datos
Ahora aprenderemos cómo combinar conjuntos de datos relacionando renglones mediante llaves.

### Merge


```python
# Importar las librerías que ocuparemos
import numpy as np
import pandas as pd
from pandas import Series, DataFrame
```


```python
# Iniciemos creando dos dataframes
dframe1 = DataFrame({'llave':['X','Z','Y','Z','X','X'],'datos_1': np.arange(6)})
dframe2 = DataFrame({'llave':['Q','Y','Z'],'datos_2':[1,2,3]})
print(dframe1)
print(dframe2)
```

      llave   datos_1
    0     X         0
    1     Z         1
    2     Y         2
    3     Z         3
    4     X         4
    5     X         5
      llave   datos_2
    0     Q         1
    1     Y         2
    2     Z         3



```python
# Unamos los dataframes; merge establece una relación uno a muchos del campo llave
pd.merge(dframe1,dframe2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>llave</th>
      <th>dato_1</th>
      <th>dato_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Z</td>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Z</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Y</td>
      <td>2</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Hagamos la unión especificando el campo llave
pd.merge(dframe1,dframe2,on='llave')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>llave</th>
      <th>dato_1</th>
      <th>dato_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Z</td>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Z</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Y</td>
      <td>2</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Se puede especificar que se utilice un left join
pd.merge(dframe1,dframe2,on='llave',how='left')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>llave</th>
      <th>dato_1</th>
      <th>dato_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>X</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Z</td>
      <td>1</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Y</td>
      <td>2</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Z</td>
      <td>3</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>X</td>
      <td>4</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>X</td>
      <td>5</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Se puede especificar que se utilice un right join
pd.merge(dframe1,dframe2,on='llave',how='right')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>llave</th>
      <th>dato_1</th>
      <th>dato_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Z</td>
      <td>1.0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Z</td>
      <td>3.0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Y</td>
      <td>2.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Q</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Se puede especificar que se utilice un outer join
pd.merge(dframe1,dframe2,on='llave',how='outer')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>llave</th>
      <th>dato_1</th>
      <th>dato_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>X</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>X</td>
      <td>4.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>X</td>
      <td>5.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Z</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Z</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Y</td>
      <td>2.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Q</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Definamos otros conjuntos de datos, con relaciones muchos a muchos
dframe3 = DataFrame({'llave': ['X', 'X', 'X', 'Y', 'Z', 'Z'],
                 'dato_3': range(6)})
dframe4 = DataFrame({'llave': ['Y', 'Y', 'X', 'X', 'Z'],
                 'dato_4': range(5)})
print(dframe3)
print(dframe4)
```

      llave  dato_3
    0     X       0
    1     X       1
    2     X       2
    3     Y       3
    4     Z       4
    5     Z       5
      llave  dato_4
    0     Y       0
    1     Y       1
    2     X       2
    3     X       3
    4     Z       4



```python
pd.merge(dframe3,dframe4)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>llave</th>
      <th>dato_3</th>
      <th>dato_4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>X</td>
      <td>0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>X</td>
      <td>0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>X</td>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>X</td>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>X</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>5</th>
      <td>X</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Y</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Y</td>
      <td>3</td>
      <td>1</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Z</td>
      <td>4</td>
      <td>4</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Z</td>
      <td>5</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>



### Merge sobre indices


```python
# Veamos un ejemplo uniendo por varias llaves

# Definamos dos dataframes
df_izq = DataFrame({'llave1': ['SF', 'SF', 'LA'],
                  'llave2': ['uno', 'dos', 'uno'],
                  'dato_izq': [10, 20, 30]})

df_der = DataFrame({'llave1': ['SF', 'SF', 'LA', 'LA'],
                   'llave2': ['uno', 'uno', 'uno', 'dos'],
                   'dato_der': [40, 50, 60, 70]})
#Merge
pd.merge(df_left, df_right, on=['llave1', 'llave2'], how='outer')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>llave1</th>
      <th>llave2</th>
      <th>dato_izq</th>
      <th>dato_der</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SF</td>
      <td>uno</td>
      <td>10.0</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>SF</td>
      <td>uno</td>
      <td>10.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SF</td>
      <td>dos</td>
      <td>20.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>LA</td>
      <td>uno</td>
      <td>30.0</td>
      <td>60.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>LA</td>
      <td>dos</td>
      <td>NaN</td>
      <td>70.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Pandas agrega sufijos de forma automática
pd.merge(df_izq,df_der,on='llave1')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>llave1</th>
      <th>llave2_x</th>
      <th>dato_izq</th>
      <th>llave2_y</th>
      <th>dato_der</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SF</td>
      <td>uno</td>
      <td>10</td>
      <td>uno</td>
      <td>40</td>
    </tr>
    <tr>
      <th>1</th>
      <td>SF</td>
      <td>uno</td>
      <td>10</td>
      <td>uno</td>
      <td>50</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SF</td>
      <td>dos</td>
      <td>20</td>
      <td>uno</td>
      <td>40</td>
    </tr>
    <tr>
      <th>3</th>
      <td>SF</td>
      <td>dos</td>
      <td>20</td>
      <td>uno</td>
      <td>50</td>
    </tr>
    <tr>
      <th>4</th>
      <td>LA</td>
      <td>uno</td>
      <td>30</td>
      <td>uno</td>
      <td>60</td>
    </tr>
    <tr>
      <th>5</th>
      <td>LA</td>
      <td>uno</td>
      <td>30</td>
      <td>dos</td>
      <td>70</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Se pueden establecer sufijos personalizados
pd.merge(df_izq,df_der, on='llave1',suffixes=('_izq','_der'))
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>llave1</th>
      <th>llave2_izq</th>
      <th>dato_izq</th>
      <th>llave2_der</th>
      <th>dato_der</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SF</td>
      <td>uno</td>
      <td>10</td>
      <td>uno</td>
      <td>40</td>
    </tr>
    <tr>
      <th>1</th>
      <td>SF</td>
      <td>uno</td>
      <td>10</td>
      <td>uno</td>
      <td>50</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SF</td>
      <td>dos</td>
      <td>20</td>
      <td>uno</td>
      <td>40</td>
    </tr>
    <tr>
      <th>3</th>
      <td>SF</td>
      <td>dos</td>
      <td>20</td>
      <td>uno</td>
      <td>50</td>
    </tr>
    <tr>
      <th>4</th>
      <td>LA</td>
      <td>uno</td>
      <td>30</td>
      <td>uno</td>
      <td>60</td>
    </tr>
    <tr>
      <th>5</th>
      <td>LA</td>
      <td>uno</td>
      <td>30</td>
      <td>dos</td>
      <td>70</td>
    </tr>
  </tbody>
</table>
</div>



### Join


```python
# Definamos dos dataframes
df = pd.DataFrame({'llave': ['K0', 'K1', 'K2', 'K3', 'K4', 'K5'],
                   'A': ['A0', 'A1', 'A2', 'A3', 'A4', 'A5']})
df1 = pd.DataFrame({'llave': ['K0', 'K1', 'K2'],
                      'B': ['B0', 'B1', 'B2']})
print(df)
print(df1)
```

      llave   A
    0    K0  A0
    1    K1  A1
    2    K2  A2
    3    K3  A3
    4    K4  A4
    5    K5  A5
      llave   B
    0    K0  B0
    1    K1  B1
    2    K2  B2



```python
# Hagamos la unión
df.join(df1, lsuffix='_izq', rsuffix='_der')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>llave_izq</th>
      <th>A</th>
      <th>llave_der</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>K0</td>
      <td>A0</td>
      <td>K0</td>
      <td>B0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>K1</td>
      <td>A1</td>
      <td>K1</td>
      <td>B1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>K2</td>
      <td>A2</td>
      <td>K2</td>
      <td>B2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>K3</td>
      <td>A3</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>K4</td>
      <td>A4</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>K5</td>
      <td>A5</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Si queremos unirlos usando las columnas llave, necesitamos especificar la llave, para que sea el índice tanto en df como en df1 .
df.set_index('llave').join(df1.set_index('llave'))
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
    <tr>
      <th>llave</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>K0</th>
      <td>A0</td>
      <td>B0</td>
    </tr>
    <tr>
      <th>K1</th>
      <td>A1</td>
      <td>B1</td>
    </tr>
    <tr>
      <th>K2</th>
      <td>A2</td>
      <td>B2</td>
    </tr>
    <tr>
      <th>K3</th>
      <td>A3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>K4</th>
      <td>A4</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>K5</th>
      <td>A5</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



## Concatenación de conjuntos de datos
Iniciemos con un ejemplo con Numpy


```python
# Generemos una matrix de 3x3
matriz1 = np.arange(9).reshape((3,3))
matriz1
```




    array([[0, 1, 2],
           [3, 4, 5],
           [6, 7, 8]])




```python
# Concatenemos la matriz por medio de las columnas
np.concatenate([matriz1,matriz1],axis=1)
```




    array([[0, 1, 2, 0, 1, 2],
           [3, 4, 5, 3, 4, 5],
           [6, 7, 8, 6, 7, 8]])




```python
# Concatenemos la matriz por medio de los renglones
np.concatenate([matriz1,matriz1],axis=0)
```




    array([[0, 1, 2],
           [3, 4, 5],
           [6, 7, 8],
           [0, 1, 2],
           [3, 4, 5],
           [6, 7, 8]])



Veamos ahora como funciona con Pandas


```python
# Creemos dos series independientes
ser1 = Series([0,1,2],index=['T','U','V'])
ser2 = Series([3,4],index=['X','Y'])

# Usemos concat; por default realiza la concatenación sobre los renglones
pd.concat([ser1,ser2])
```




    T    0
    U    1
    V    2
    X    3
    Y    4
    dtype: int64




```python
# Si se realiza por columnas, se genera un dataframe
pd.concat([ser1,ser2],axis=1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>T</th>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>U</th>
      <td>1.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>V</th>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>X</th>
      <td>NaN</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Y</th>
      <td>NaN</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Para generar un indice jerárquico por renglones
pd.concat([ser1,ser2],keys=['cat1','cat2'])
```




    cat1  T    0
          U    1
          V    2
    cat2  X    3
          Y    4
    dtype: int64




```python
# Para generar un encabezado por columnas
pd.concat([ser1,ser2],axis=1,keys=['cat1','cat2'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cat1</th>
      <th>cat2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>T</th>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>U</th>
      <td>1.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>V</th>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>X</th>
      <td>NaN</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Y</th>
      <td>NaN</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Veamos que para dataframes funciona de la misma forma
dframe1 = DataFrame(np.random.randn(4,3), columns=['X', 'Y', 'Z'])
dframe2 = DataFrame(np.random.randn(3, 3), columns=['Y', 'Q', 'X'])
print(dframe1)
print(dframe2)
```

              X         Y         Z
    0  0.860753 -0.045343  0.258483
    1 -0.073737 -1.269831  0.587107
    2 -1.968844  1.103597 -0.418956
    3 -0.502007 -0.544690 -0.940953
              Y         Q         X
    0  0.334562 -0.497145 -1.468054
    1  1.046430 -1.290066  0.776600
    2  0.874220 -0.735185 -0.194975



```python
# Se puede realizar un concat sobre dataFrames
pd.concat([dframe1,dframe2])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>X</th>
      <th>Y</th>
      <th>Z</th>
      <th>Q</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.860753</td>
      <td>-0.045343</td>
      <td>0.258483</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.073737</td>
      <td>-1.269831</td>
      <td>0.587107</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-1.968844</td>
      <td>1.103597</td>
      <td>-0.418956</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-0.502007</td>
      <td>-0.544690</td>
      <td>-0.940953</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0</th>
      <td>-1.468054</td>
      <td>0.334562</td>
      <td>NaN</td>
      <td>-0.497145</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.776600</td>
      <td>1.046430</td>
      <td>NaN</td>
      <td>-1.290066</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.194975</td>
      <td>0.874220</td>
      <td>NaN</td>
      <td>-0.735185</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Si los indices no son necesarios, podemos omitirlos
pd.concat([dframe1,dframe2],ignore_index=True)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>X</th>
      <th>Y</th>
      <th>Z</th>
      <th>Q</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.860753</td>
      <td>-0.045343</td>
      <td>0.258483</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.073737</td>
      <td>-1.269831</td>
      <td>0.587107</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-1.968844</td>
      <td>1.103597</td>
      <td>-0.418956</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-0.502007</td>
      <td>-0.544690</td>
      <td>-0.940953</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-1.468054</td>
      <td>0.334562</td>
      <td>NaN</td>
      <td>-0.497145</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.776600</td>
      <td>1.046430</td>
      <td>NaN</td>
      <td>-1.290066</td>
    </tr>
    <tr>
      <th>6</th>
      <td>-0.194975</td>
      <td>0.874220</td>
      <td>NaN</td>
      <td>-0.735185</td>
    </tr>
  </tbody>
</table>
</div>



## Combinar dataframes


```python
# Generemos dos series
ser1 = Series([2,np.nan,4,np.nan,6,np.nan],
           index=['Q','R','S','T','U','V'])
ser2 = Series(np.arange(len(ser1), dtype=np.float64),
           index=['Q','R','S','T','U','V'])
ser2[-1] = np.nan
print(ser1,ser2)
```

    Q    2.0
    R    NaN
    S    4.0
    T    NaN
    U    6.0
    V    NaN
    dtype: float64 Q    0.0
    R    1.0
    S    2.0
    T    3.0
    U    4.0
    V    NaN
    dtype: float64



```python
# Obtengamos una serie en donde el valor de ser2 es seleccionado si ser1 es NAN
# De lo contrario, se selecciona el valor de ser1
Series(np.where(pd.isnull(ser1),ser2,ser1),index=ser1.index)
```




    Q    2.0
    R    1.0
    S    4.0
    T    3.0
    U    6.0
    V    NaN
    dtype: float64



Analicemos a detalle el proceso anterior


```python
# Ahora hagamos lo mismo con el comando 'combine_first' con Pandas
ser1.combine_first(ser2)
```




    Q    2.0
    R    1.0
    S    4.0
    T    3.0
    U    6.0
    V    NaN
    dtype: float64




```python
# Ahora veamos como trabaja con dataframes
# Generemos dos dataframes
dframe_non = DataFrame({'X': [1., np.nan, 3., np.nan],
                     'Y': [np.nan, 5., np.nan, 7.],
                     'Z': [np.nan, 9., np.nan, 11.]})
dframe_par = DataFrame({'X': [2., 4., np.nan, 6., 8.],
                     'Y': [np.nan, 10., 12., 14., 16.]})
print(dframe_non)
print(dframe_par)
```

         X    Y     Z
    0  1.0  NaN   NaN
    1  NaN  5.0   9.0
    2  3.0  NaN   NaN
    3  NaN  7.0  11.0
         X     Y
    0  2.0   NaN
    1  4.0  10.0
    2  NaN  12.0
    3  6.0  14.0
    4  8.0  16.0



```python
dframe_non.combine_first(dframe_par)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>X</th>
      <th>Y</th>
      <th>Z</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.0</td>
      <td>5.0</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>12.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>6.0</td>
      <td>7.0</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>8.0</td>
      <td>16.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Veamos como funciona stack y unstack
# Generemos un dataframe
dframe1 = DataFrame(np.arange(8).reshape((2, 4)),
                 index=pd.Index(['LA', 'SF'], name='ciudad'),
                 columns=pd.Index(['A', 'B', 'C','D'], name='letra'))
dframe1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>letra</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>ciudad</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>LA</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>SF</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Usemos stack para pivotear las columnas a renglones
dframe_st = dframe1.stack()
dframe_st
```




    ciudad  letra
    LA      A         0
            B         1
            C         2
            D         3
    SF      A         4
            B         5
            C         6
            D         7
    dtype: int32




```python
# Podemos regresar a un dataframe
dframe_st.unstack()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>letra</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>ciudad</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>LA</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>SF</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Podemos elegir el nivel sobre cual se aplica unstack
dframe_st.unstack(0)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>ciudad</th>
      <th>LA</th>
      <th>SF</th>
    </tr>
    <tr>
      <th>letra</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>B</th>
      <td>1</td>
      <td>5</td>
    </tr>
    <tr>
      <th>C</th>
      <td>2</td>
      <td>6</td>
    </tr>
    <tr>
      <th>D</th>
      <td>3</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
dframe_st.unstack('letra')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>letra</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>ciudad</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>LA</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>SF</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
dframe_st.unstack('ciudad')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>ciudad</th>
      <th>LA</th>
      <th>SF</th>
    </tr>
    <tr>
      <th>letra</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>B</th>
      <td>1</td>
      <td>5</td>
    </tr>
    <tr>
      <th>C</th>
      <td>2</td>
      <td>6</td>
    </tr>
    <tr>
      <th>D</th>
      <td>3</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Ahora veamos como funciona stack y unstack sobre los Nan

# Generemos dos series
ser1 = Series([0, 1, 2], index=['Q', 'X', 'Y'])
ser2 = Series([4, 5, 6], index=['X', 'Y', 'Z'])

# Usemos Concat para generar un dataframe
dframe = pd.concat([ser1, ser2], keys=['Alpha', 'Beta'])

print(dframe)
```

    Alpha  Q    0
           X    1
           Y    2
    Beta   X    4
           Y    5
           Z    6
    dtype: int64



```python
# Apliquemos unstack sobre el dataframe
dframe.unstack()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Q</th>
      <th>X</th>
      <th>Y</th>
      <th>Z</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Alpha</th>
      <td>0.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Beta</th>
      <td>NaN</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Veamos como stack filtra los NAN por default
dframe.unstack().stack()
```




    Alpha  Q    0.0
           X    1.0
           Y    2.0
    Beta   X    4.0
           Y    5.0
           Z    6.0
    dtype: float64




```python
# Si necesitamos considerar los NAN
dframe.unstack().stack(dropna=False)
```




    Alpha  Q    0.0
           X    1.0
           Y    2.0
           Z    NaN
    Beta   Q    NaN
           X    4.0
           Y    5.0
           Z    6.0
    dtype: float64



## Pivoting


```python
# Generemos un dataframe simple como ejemplo
df = pd.DataFrame({'foo': ['uno', 'uno', 'uno', 'dos', 'dos','dos'],
                   'bar': ['A', 'B', 'C', 'A', 'B', 'C'],
                   'baz': [1, 2, 3, 4, 5, 6],
                   'zoo': ['x', 'y', 'z', 'q', 'w', 't']})
print(df)
```

       foo bar  baz zoo
    0  uno   A    1   x
    1  uno   B    2   y
    2  uno   C    3   z
    3  dos   A    4   q
    4  dos   B    5   w
    5  dos   C    6   t



```python
# Apliquemos la función "pivot"
df.pivot(index='foo', columns='bar', values='baz')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>foo</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
    <tr>
      <th>bar</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>uno</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>dos</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Otra forma de hacer el pivot a la tabla
df.pivot(index='foo', columns='bar')['baz']
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>bar</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
    <tr>
      <th>foo</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>uno</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>dos</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.pivot(index='foo', columns='bar', values=['baz', 'zoo'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="3" halign="left">baz</th>
      <th colspan="3" halign="left">zoo</th>
    </tr>
    <tr>
      <th>bar</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
    <tr>
      <th>foo</th>
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
      <th>uno</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
      <td>x</td>
      <td>y</td>
      <td>z</td>
    </tr>
    <tr>
      <th>dos</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>q</td>
      <td>w</td>
      <td>t</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Generemos otro dataframe, para mostrar el error por duplicados
df = pd.DataFrame({"foo": ['uno', 'uno', 'dos', 'dos', 'dos'],
                   "bar": ['A', 'A', 'B', 'C', 'C'],
                   "baz": [1, 1, 3, 4, 5]})
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>foo</th>
      <th>bar</th>
      <th>baz</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>uno</td>
      <td>A</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>uno</td>
      <td>A</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>dos</td>
      <td>B</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>dos</td>
      <td>C</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>dos</td>
      <td>C</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Error por duplicados
df.pivot(index='foo', columns='bar', values='baz')
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-46-193a26d1bfbc> in <module>
          1 # Error por duplicados
    ----> 2 df.pivot(index='foo', columns='bar', values='baz')


    ~\.conda\envs\PYRDEV\lib\site-packages\pandas\core\frame.py in pivot(self, index, columns, values)
       5921         from pandas.core.reshape.pivot import pivot
       5922
    -> 5923         return pivot(self, index=index, columns=columns, values=values)
       5924
       5925     _shared_docs[


    ~\.conda\envs\PYRDEV\lib\site-packages\pandas\core\reshape\pivot.py in pivot(data, index, columns, values)
        448         else:
        449             indexed = data._constructor_sliced(data[values].values, index=index)
    --> 450     return indexed.unstack(columns)
        451
        452


    ~\.conda\envs\PYRDEV\lib\site-packages\pandas\core\series.py in unstack(self, level, fill_value)
       3548         from pandas.core.reshape.reshape import unstack
       3549
    -> 3550         return unstack(self, level, fill_value)
       3551
       3552     # ----------------------------------------------------------------------


    ~\.conda\envs\PYRDEV\lib\site-packages\pandas\core\reshape\reshape.py in unstack(obj, level, fill_value)
        417             level=level,
        418             fill_value=fill_value,
    --> 419             constructor=obj._constructor_expanddim,
        420         )
        421         return unstacker.get_result()


    ~\.conda\envs\PYRDEV\lib\site-packages\pandas\core\reshape\reshape.py in __init__(self, values, index, level, value_columns, fill_value, constructor)
        139
        140         self._make_sorted_values_labels()
    --> 141         self._make_selectors()
        142
        143     def _make_sorted_values_labels(self):


    ~\.conda\envs\PYRDEV\lib\site-packages\pandas\core\reshape\reshape.py in _make_selectors(self)
        177
        178         if mask.sum() < len(self.index):
    --> 179             raise ValueError("Index contains duplicate entries, cannot reshape")
        180
        181         self.group_index = comp_index


    ValueError: Index contains duplicate entries, cannot reshape


## Duplicados en el dataframe


```python
# Usemos la función "duplicated" para identificar los duplicados
df.duplicated()
```


```python
# Se eliminan los duplicados con la función "drop duplicates"
df.drop_duplicates()
```


```python
#You can filter which duplicates to drop by a single column
df.drop_duplicates(['bar'])
```


```python
# Por default el valor es 'first' y toma el primer valor, pero podemos modificarlo con 'last'
df.drop_duplicates(['foo'],'last')
```

## Mapeo


```python
# generemos el dataframe para ejemplificar
dframe = DataFrame({'city':['Alma','Brian Head','Fox Park'],
                    'altitude':[3158,3000,2762]})
dframe
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
      <th>city</th>
      <th>altitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alma</td>
      <td>3158</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Brian Head</td>
      <td>3000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Fox Park</td>
      <td>2762</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Se necesita agregar una columna para los estados.
state_map={'Alma':'Colorado','Brian Head':'Utah','Fox Park':'Wyoming'}
state_map
```




    {'Alma': 'Colorado', 'Brian Head': 'Utah', 'Fox Park': 'Wyoming'}




```python
# Ahora utilicemos la función "map" para mapear los datos del diccionario con el dataframe
dframe['state'] = dframe['city'].map(state_map)
dframe
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
      <th>city</th>
      <th>altitude</th>
      <th>state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alma</td>
      <td>3158</td>
      <td>Colorado</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Brian Head</td>
      <td>3000</td>
      <td>Utah</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Fox Park</td>
      <td>2762</td>
      <td>Wyoming</td>
    </tr>
  </tbody>
</table>
</div>



El mapeo es una excelente forma de hacer transformación de elementos y otras operaciones de limpieza de datos¡¡

## Reemplazar datos


```python
# Iniciemos sobre las series
ser1 = Series([1,2,3,4,1,2,3,4])
ser1
```




    0    1
    1    2
    2    3
    3    4
    4    1
    5    2
    6    3
    7    4
    dtype: int64




```python
# Usemos la función "replace" de la siguiente forma (valor a reemplazar, nuevo valor)
ser1.replace(1,np.nan)
```




    0    NaN
    1    2.0
    2    3.0
    3    4.0
    4    NaN
    5    2.0
    6    3.0
    7    4.0
    dtype: float64




```python
# podemos poner reemplazar con una lista
ser1.replace([1,4],[100,400])
```




    0    100
    1      2
    2      3
    3    400
    4    100
    5      2
    6      3
    7    400
    dtype: int64




```python
#tambien con diccionario
ser1.replace({4:np.nan})
```




    0    1.0
    1    2.0
    2    3.0
    3    NaN
    4    1.0
    5    2.0
    6    3.0
    7    NaN
    dtype: float64




```python
# Ahora hagamos lo mismo con un dataframe
df = pd.DataFrame({'A': [0, 1, 2, 3, 4],
                   'B': [5, 6, 7, 8, 9],
                   'C': ['a', 'b', 'c', 'd', 'e']})
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>5</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>6</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>7</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>9</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Reemplazar un valor
df.replace(5, 7)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>7</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>6</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>7</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>9</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Reemplazar con lista
df.replace([0, 1, 2, 3], 4)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4</td>
      <td>5</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>6</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>7</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>8</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>9</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.replace([0, 1, 2, 3], [4, 3, 2, 1])
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4</td>
      <td>5</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>6</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>7</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>8</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>9</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Reemplazar con diccionarios
df.replace({0: 10, 1: 100})
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10</td>
      <td>5</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>100</td>
      <td>6</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>7</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>9</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Reemplazar sobre columnas
df.replace({'A': 0, 'B': 5}, 100)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>100</td>
      <td>100</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>6</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>7</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>9</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.replace({'A': {0: 100, 4: 400}})
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>100</td>
      <td>5</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>6</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>7</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>8</td>
      <td>d</td>
    </tr>
    <tr>
      <th>4</th>
      <td>400</td>
      <td>9</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>



## Renombrar indices


```python
# Generemos un dataframe para ejemplificar

dframe= DataFrame(np.arange(12).reshape((3, 4)),
                 index=['NY', 'LA', 'SF'],
                 columns=['A', 'B', 'C', 'D'])
dframe
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>NY</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>LA</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>SF</th>
      <td>8</td>
      <td>9</td>
      <td>10</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Si se necesita cambiar a minúsculas
dframe.index = dframe.index.map(str.lower)
dframe
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>ny</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>la</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>sf</th>
      <td>8</td>
      <td>9</td>
      <td>10</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```python
dframe.rename(index={'ny': 'NEW YORK'},
            columns={'A': 'ALPHA', 'B': 'BETA'})
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
      <th>ALPHA</th>
      <th>BETA</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>NEW YORK</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>la</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>sf</th>
      <td>8</td>
      <td>9</td>
      <td>10</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```python
# si se requiere persitir las modificaciones se utiliza inplace=True
dframe.rename(index={'ny': 'NEW YORK'}, inplace=True)
dframe
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>NEW YORK</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>la</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>sf</th>
      <td>8</td>
      <td>9</td>
      <td>10</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>



## Valores Atípicos


```python
# Veamos como encontrar valores atípicos en un dataset

# Primero sembremos una semilla para generar los números aleatorios
np.random.seed(12345)

# Ahora vreemos el dataframe
dframe = DataFrame(np.random.randn(1000,4))
dframe.head()
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-0.204708</td>
      <td>0.478943</td>
      <td>-0.519439</td>
      <td>-0.555730</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.965781</td>
      <td>1.393406</td>
      <td>0.092908</td>
      <td>0.281746</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.769023</td>
      <td>1.246435</td>
      <td>1.007189</td>
      <td>-1.296221</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.274992</td>
      <td>0.228913</td>
      <td>1.352917</td>
      <td>0.886429</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-2.001637</td>
      <td>-0.371843</td>
      <td>1.669025</td>
      <td>-0.438570</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Para sacar estaíisticos básicos
dframe.describe()
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1000.000000</td>
      <td>1000.000000</td>
      <td>1000.000000</td>
      <td>1000.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>-0.067684</td>
      <td>0.067924</td>
      <td>0.025598</td>
      <td>-0.002298</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.998035</td>
      <td>0.992106</td>
      <td>1.006835</td>
      <td>0.996794</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-3.428254</td>
      <td>-3.548824</td>
      <td>-3.184377</td>
      <td>-3.745356</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>-0.774890</td>
      <td>-0.591841</td>
      <td>-0.641675</td>
      <td>-0.644144</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>-0.116401</td>
      <td>0.101143</td>
      <td>0.002073</td>
      <td>-0.013611</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.616366</td>
      <td>0.780282</td>
      <td>0.680391</td>
      <td>0.654328</td>
    </tr>
    <tr>
      <th>max</th>
      <td>3.366626</td>
      <td>2.653656</td>
      <td>3.260383</td>
      <td>3.927528</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Seleccionemos la primer columna
col = dframe[0]
```


```python
# Ahora verifiquemos cuales valores son mayores a 3
col[np.abs(col)>3]
```




    523   -3.428254
    900    3.366626
    Name: 0, dtype: float64




```python
# Ahora usemos el metodo "any" para hacer el análisis sobre todas las columnas
dframe[(np.abs(dframe)>3).any(1)]
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>-0.539741</td>
      <td>0.476985</td>
      <td>3.248944</td>
      <td>-1.021228</td>
    </tr>
    <tr>
      <th>97</th>
      <td>-0.774363</td>
      <td>0.552936</td>
      <td>0.106061</td>
      <td>3.927528</td>
    </tr>
    <tr>
      <th>102</th>
      <td>-0.655054</td>
      <td>-0.565230</td>
      <td>3.176873</td>
      <td>0.959533</td>
    </tr>
    <tr>
      <th>305</th>
      <td>-2.315555</td>
      <td>0.457246</td>
      <td>-0.025907</td>
      <td>-3.399312</td>
    </tr>
    <tr>
      <th>324</th>
      <td>0.050188</td>
      <td>1.951312</td>
      <td>3.260383</td>
      <td>0.963301</td>
    </tr>
    <tr>
      <th>400</th>
      <td>0.146326</td>
      <td>0.508391</td>
      <td>-0.196713</td>
      <td>-3.745356</td>
    </tr>
    <tr>
      <th>499</th>
      <td>-0.293333</td>
      <td>-0.242459</td>
      <td>-3.056990</td>
      <td>1.918403</td>
    </tr>
    <tr>
      <th>523</th>
      <td>-3.428254</td>
      <td>-0.296336</td>
      <td>-0.439938</td>
      <td>-0.867165</td>
    </tr>
    <tr>
      <th>586</th>
      <td>0.275144</td>
      <td>1.179227</td>
      <td>-3.184377</td>
      <td>1.369891</td>
    </tr>
    <tr>
      <th>808</th>
      <td>-0.362528</td>
      <td>-3.548824</td>
      <td>1.553205</td>
      <td>-2.186301</td>
    </tr>
    <tr>
      <th>900</th>
      <td>3.366626</td>
      <td>-2.372214</td>
      <td>0.851010</td>
      <td>1.332846</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Podríamos limitar los datos a 3 Sign -1 - <0 , 0 x=0, 1 x>0

dframe[np.abs(dframe)>3] = np.sign(dframe) *3
```


```python
dframe.describe()
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1000.000000</td>
      <td>1000.000000</td>
      <td>1000.000000</td>
      <td>1000.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>-0.067623</td>
      <td>0.068473</td>
      <td>0.025153</td>
      <td>-0.002081</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.995485</td>
      <td>0.990253</td>
      <td>1.003977</td>
      <td>0.989736</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-3.000000</td>
      <td>-3.000000</td>
      <td>-3.000000</td>
      <td>-3.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>-0.774890</td>
      <td>-0.591841</td>
      <td>-0.641675</td>
      <td>-0.644144</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>-0.116401</td>
      <td>0.101143</td>
      <td>0.002073</td>
      <td>-0.013611</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.616366</td>
      <td>0.780282</td>
      <td>0.680391</td>
      <td>0.654328</td>
    </tr>
    <tr>
      <th>max</th>
      <td>3.000000</td>
      <td>2.653656</td>
      <td>3.000000</td>
      <td>3.000000</td>
    </tr>
  </tbody>
</table>
</div>



## Reordenamiento


```python
# Veamos como podemos reordenar una serie o las filas en un dataframe
# Generemos un dataframe
dframe = DataFrame(np.arange(4 * 4).reshape((4, 4)))
print(dframe)
# Generemos un arreglo con reordenamientos aleatorios de 0,1,2,3
blender = np.random.permutation(4)
print(blender)
```


```python
# Ahora reordenemos los datos en base a blender
dframe.take(blender)
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>3</th>
      <td>12</td>
      <td>13</td>
      <td>14</td>
      <td>15</td>
    </tr>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>9</td>
      <td>10</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




 [**Siguiente Lección**](Lecci%C3%B3n%2008%20-%20Procesamiento_Datos_2.md)    
