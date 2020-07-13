# Procesamiento de Datos

## Agrupaciones en DataFrames


```python
# Importar las librerias de trabajo
import numpy as np
import pandas as pd
from pandas import DataFrame, Series
from io import StringIO
```


```python
# Generar el dataframe de trabajo
dframe = DataFrame({'k1':['X','X','Y','Y','Z'],
                    'k2':['alpha','beta','alpha','beta','alpha'],
                    'datos1':np.random.randn(5),
                    'datos2':np.random.randn(5)})
dframe
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>k1</th>
      <th>k2</th>
      <th>datos1</th>
      <th>datos2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>X</td>
      <td>alpha</td>
      <td>1.141619</td>
      <td>0.737260</td>
    </tr>
    <tr>
      <th>1</th>
      <td>X</td>
      <td>beta</td>
      <td>-0.430231</td>
      <td>0.170866</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Y</td>
      <td>alpha</td>
      <td>0.570391</td>
      <td>1.114514</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Y</td>
      <td>beta</td>
      <td>-2.175396</td>
      <td>0.447751</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Z</td>
      <td>alpha</td>
      <td>-0.084418</td>
      <td>1.589869</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Ver como se usa la función "groupby"
grupo1 = dframe['datos1'].groupby(dframe['k1'])
grupo1
```

    <pandas.core.groupby.generic.SeriesGroupBy object at 0x000001EAA18F5550>



```python
# Realizar operaciones sobre este grupo
grupo1.mean()
```




    k1
    X    0.355694
    Y   -0.802503
    Z   -0.084418
    Name: datos1, dtype: float64




```python
# Podemos pasar el nombre de la columna como llave de agrupación
dframe.groupby('k1').mean()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>datos1</th>
      <th>datos2</th>
    </tr>
    <tr>
      <th>k1</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>X</th>
      <td>0.355694</td>
      <td>0.454063</td>
    </tr>
    <tr>
      <th>Y</th>
      <td>-0.802503</td>
      <td>0.781133</td>
    </tr>
    <tr>
      <th>Z</th>
      <td>-0.084418</td>
      <td>1.589869</td>
    </tr>
  </tbody>
</table>
</div>




```python
# o multiples columnas
dframe.groupby(['k1','k2']).mean()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>datos1</th>
      <th>datos2</th>
    </tr>
    <tr>
      <th>k1</th>
      <th>k2</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">X</th>
      <th>alpha</th>
      <td>1.141619</td>
      <td>0.737260</td>
    </tr>
    <tr>
      <th>beta</th>
      <td>-0.430231</td>
      <td>0.170866</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">Y</th>
      <th>alpha</th>
      <td>0.570391</td>
      <td>1.114514</td>
    </tr>
    <tr>
      <th>beta</th>
      <td>-2.175396</td>
      <td>0.447751</td>
    </tr>
    <tr>
      <th>Z</th>
      <th>alpha</th>
      <td>-0.084418</td>
      <td>1.589869</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Podemos utilizar groupby para contar elementos
dframe.groupby(['k1']).size()
```




    k1
    X    2
    Y    2
    Z    1
    dtype: int64




```python
# Podemos iterar sobre los grupos
# por ejemplo:
for nombre, grupo in dframe.groupby('k1'):
    print ("Este es el grupo %s" %nombre)
    print (grupo)
    print ('\n')
```

    Este es el grupo X
      k1     k2  dataset1  dataset2
    0  X  alpha  1.141619  0.737260
    1  X   beta -0.430231  0.170866


    Este es el grupo Y
      k1     k2  dataset1  dataset2
    2  Y  alpha  0.570391  1.114514
    3  Y   beta -2.175396  0.447751


    Este es el grupo Z
      k1     k2  dataset1  dataset2
    4  Z  alpha -0.084418  1.589869





```python
# Podemos iterar sobre varias llaves
for (k1,k2), grupo in dframe.groupby(['k1','k2']):
    print ("Llave1 = %s Llave2 = %s" %(k1,k2))
    print (grupo)
    print ('\n')
```

    Llave1 = X Llave2 = alpha
      k1     k2  dato1      dato2
    0  X  alpha  1.141619   0.73726


    Llave1 = X Llave2 = beta
      k1    k2  dato1     dato2
    1  X  beta -0.430231  0.170866


    Llave1 = Y Llave2 = alpha
      k1     k2  dato1     dato2
    2  Y  alpha  0.570391  1.114514


    Llave1 = Y Llave2 = beta
      k1    k2  dato1     dato2
    3  Y  beta -2.175396  0.447751


    Llave1 = Z Llave2 = alpha
      k1     k2  dato1     dato2
    4  Z  alpha -0.084418  1.589869





```python
# Una táctica usada es crear un diccionario de los datos
grupo_d = dict(list(dframe.groupby('k1')))
grupo_d
```




    {'X':   k1     k2  dato1  dato2
     0  X  alpha  1.141619  0.737260
     1  X   beta -0.430231  0.170866,
     'Y':   k1     k2  dato1  dato2
     2  Y  alpha  0.570391  1.114514
     3  Y   beta -2.175396  0.447751,
     'Z':   k1     k2  dato1  dato2
     4  Z  alpha -0.084418  1.589869}




```python
grupo_d['Y']
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>k1</th>
      <th>k2</th>
      <th>dato1</th>
      <th>dato2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Y</td>
      <td>alpha</td>
      <td>0.570391</td>
      <td>1.114514</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Y</td>
      <td>beta</td>
      <td>-2.175396</td>
      <td>0.447751</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Por ejemplo, si solo necesitamos agrupar la columna dato2 por ambos conjuntos de llaves
grupo_dato2 = dframe.groupby(['k1','k2'])[['datos2']]
grupo_dato2.mean()
```




<div>
<table border="1" class="dataframe">
<thead>
  <tr style=\"text-align: right;\">
    <th></th>
    <th></th>
    <th>datos2</th>
  </tr>
  <tr>
    <th>k1</th>
    <th>k2</th>
    <th></th>
  </tr>
</thead>
<tbody>
  <tr>
    <th rowspan=\"2\" valign=\"top\">X</th>
    <th>alpha</th>
    <td>0.538815</td>
  </tr>
  <tr>
    <th>beta</th>
    <td>0.871757</td>
  </tr>
  <tr>
    <th rowspan=\"2\" valign=\"top\">Y</th>
    <th>alpha</th>
    <td>-0.107305</td>
  </tr>
  <tr>
    <th>beta</th>
    <td>0.123704</td>
  </tr>
  <tr>
    <th>Z</th>
    <th>alpha</th>
    <td>0.008294</td>
  </tr>
</tbody>
</table>
</div>



## Agrupar series y diccionarios


```python
# Aprendamos a usar diccionarios o series con groupby
# Hagamos un dataframe con diferentes animales
animales = DataFrame(np.arange(16).reshape(4, 4),
                   columns=['W', 'X', 'Y', 'Z'],
                   index=['Perro', 'Gato', 'Pajaro', 'Raton'])
print(animales)
```

            W   X   Y   Z
    Perro   0   1   2   3
    Gato    4   5   6   7
    Pajaro  8   9  10  11
    Raton  12  13  14  15


```python
# Agreguemos algunos datos NAN
# animales.ix[1:2, ['W', 'Y']] = np.nan
animales.loc[1:2, ['W', 'Y']]  = np.nan
print(animales)
```
              W   X     Y   Z
    Perro   0.0   1   2.0   3
    Gato    NaN   5   NaN   7
    Pajaro  8.0   9  10.0  11
    Raton  12.0  13  14.0  15



```python
# Ahora supongamos que tenemos un diccionario con valores de comportamiento
comportamiento_m = {'W': 'bien', 'X': 'mal', 'Y': 'bien','Z': 'mal'}

# Ahora podemos agrupar a los animales usando este mapeo
animales_col = animales.groupby(comportamiento_m, axis=1)

# Mostremos la suma, de acuerdo a la agrupación por el mapeo
animales_col.sum()

# por ejemplo [Perro][bien] = [Perro][Y]+[Perro][W]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mal</th>
      <th>bien</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Perro</th>
      <td>4.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>Gato</th>
      <td>12.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Pajaro</th>
      <td>20.0</td>
      <td>18.0</td>
    </tr>
    <tr>
      <th>Raton</th>
      <td>28.0</td>
      <td>26.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Ahora intentemos lo mismo con una serie
comportamiento_s = Series(comportamiento_m)
comportamiento_s
```




    W    bien
    X     mal
    Y    bien
    Z     mal
    dtype: object




```python
# Agrupemos la serie
animales.groupby(comportamiento_s, axis=1).count()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mal</th>
      <th>bien</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Perro</th>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Gato</th>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Pajaro</th>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Raton</th>
      <td>2</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
print(animales)
```

              W   X     Y   Z
    Perro   0.0   1   2.0   3
    Gato    NaN   5   NaN   7
    Pajaro  8.0   9  10.0  11
    Raton  12.0  13  14.0  15



```python
# Supongamos que queremos agrupar por la longitud de los nombres de los animales, ¡podemos pasar la función len a groupby!
animales.groupby(len).sum()

# Nota: el índice ahora es el número de letras en el nombre del animal
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>W</th>
      <th>X</th>
      <th>Y</th>
      <th>Z</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>0.0</td>
      <td>5</td>
      <td>0.0</td>
      <td>7</td>
    </tr>
    <tr>
      <th>5</th>
      <td>12.0</td>
      <td>14</td>
      <td>16.0</td>
      <td>18</td>
    </tr>
    <tr>
      <th>6</th>
      <td>8.0</td>
      <td>9</td>
      <td>10.0</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```python
# También podemos mezclar funciones con matrices, diccionarios y series para métodos groupby
# Se define una lista de llaves
llaves = ['A', 'B', 'A', 'B']

# Se agrupa la longitud del nombre y las llaves para mostrar los valores máximos
animales.groupby ([len, llaves]). max ()
```




<div>
<table border="1" class="dataframe">
<thead>
  <tr style=\"text-align: right;\">
    <th></th>
    <th></th>
    <th>W</th>
    <th>X</th>
    <th>Y</th>
    <th>Z</th>
  </tr>
</thead>
<tbody>
  <tr>
    <th rowspan=\"2\" valign=\"top\">4</th>
    <th>B</th>
    <td>NaN</td>
    <td>5</td>
    <td>NaN</td>
    <td>7</td>
  </tr>
</tbody>
</table>
</div>




```python
# También podemos usar groupby con niveles de índice jerárquico

# Crear un índice de columna jerárquica
jerarq_col = pd.MultiIndex.from_arrays([['MX','MX','MX','US','US'],[1,2,3,1,2]],nombres=['Ciudad','Valor'])

# Crear un dataframe con índice jerárquico
dframe = DataFrame(np.arange(25).reshape(5,5),columns=jerarq_col)

# Valores múltiples por 100 para mayor claridad
dframe = dframe*100
dframe
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th>Ciudad</th>
      <th colspan="3" halign="left">MX</th>
      <th colspan="2" halign="left">US</th>
    </tr>
    <tr>
      <th>Valor</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>100</td>
      <td>200</td>
      <td>300</td>
      <td>400</td>
    </tr>
    <tr>
      <th>1</th>
      <td>500</td>
      <td>600</td>
      <td>700</td>
      <td>800</td>
      <td>900</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1000</td>
      <td>1100</td>
      <td>1200</td>
      <td>1300</td>
      <td>1400</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1500</td>
      <td>1600</td>
      <td>1700</td>
      <td>1800</td>
      <td>1900</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2000</td>
      <td>2100</td>
      <td>2200</td>
      <td>2300</td>
      <td>2400</td>
    </tr>
  </tbody>
</table>
</div>



## Agregación


```python
# La agregación de datos consiste en operaciones que resultan en un escalar (por ejemplo, mean(), sum(), count(), etc.)
# Se guarda el archivo winquality.csv en la misma carpeta que los notebooks Python, tenga en cuenta el delimitador utilizado ;
# El archivo contiene medidas de características de diferentes vinos, como acidez, azúcar, densidad, etc.
# La columna de calidad (quality) es una calificación asignada a cada vino
dframe_vino = pd.read_csv('/data/winequality-red.csv',sep=';')
dframe_vino
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>fixed acidity</th>
      <th>volatile acidity</th>
      <th>citric acid</th>
      <th>residual sugar</th>
      <th>chlorides</th>
      <th>free sulfur dioxide</th>
      <th>total sulfur dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
      <th>quality</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7.4</td>
      <td>0.700</td>
      <td>0.00</td>
      <td>1.9</td>
      <td>0.076</td>
      <td>11.0</td>
      <td>34.0</td>
      <td>0.99780</td>
      <td>3.51</td>
      <td>0.56</td>
      <td>9.4</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7.8</td>
      <td>0.880</td>
      <td>0.00</td>
      <td>2.6</td>
      <td>0.098</td>
      <td>25.0</td>
      <td>67.0</td>
      <td>0.99680</td>
      <td>3.20</td>
      <td>0.68</td>
      <td>9.8</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7.8</td>
      <td>0.760</td>
      <td>0.04</td>
      <td>2.3</td>
      <td>0.092</td>
      <td>15.0</td>
      <td>54.0</td>
      <td>0.99700</td>
      <td>3.26</td>
      <td>0.65</td>
      <td>9.8</td>
      <td>5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11.2</td>
      <td>0.280</td>
      <td>0.56</td>
      <td>1.9</td>
      <td>0.075</td>
      <td>17.0</td>
      <td>60.0</td>
      <td>0.99800</td>
      <td>3.16</td>
      <td>0.58</td>
      <td>9.8</td>
      <td>6</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7.4</td>
      <td>0.700</td>
      <td>0.00</td>
      <td>1.9</td>
      <td>0.076</td>
      <td>11.0</td>
      <td>34.0</td>
      <td>0.99780</td>
      <td>3.51</td>
      <td>0.56</td>
      <td>9.4</td>
      <td>5</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1594</th>
      <td>6.2</td>
      <td>0.600</td>
      <td>0.08</td>
      <td>2.0</td>
      <td>0.090</td>
      <td>32.0</td>
      <td>44.0</td>
      <td>0.99490</td>
      <td>3.45</td>
      <td>0.58</td>
      <td>10.5</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1595</th>
      <td>5.9</td>
      <td>0.550</td>
      <td>0.10</td>
      <td>2.2</td>
      <td>0.062</td>
      <td>39.0</td>
      <td>51.0</td>
      <td>0.99512</td>
      <td>3.52</td>
      <td>0.76</td>
      <td>11.2</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1596</th>
      <td>6.3</td>
      <td>0.510</td>
      <td>0.13</td>
      <td>2.3</td>
      <td>0.076</td>
      <td>29.0</td>
      <td>40.0</td>
      <td>0.99574</td>
      <td>3.42</td>
      <td>0.75</td>
      <td>11.0</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1597</th>
      <td>5.9</td>
      <td>0.645</td>
      <td>0.12</td>
      <td>2.0</td>
      <td>0.075</td>
      <td>32.0</td>
      <td>44.0</td>
      <td>0.99547</td>
      <td>3.57</td>
      <td>0.71</td>
      <td>10.2</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1598</th>
      <td>6.0</td>
      <td>0.310</td>
      <td>0.47</td>
      <td>3.6</td>
      <td>0.067</td>
      <td>18.0</td>
      <td>42.0</td>
      <td>0.99549</td>
      <td>3.39</td>
      <td>0.66</td>
      <td>11.0</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
<p>1599 rows × 12 columns</p>
</div>




```python
# ¿Qué tal si descubrimos el contenido promedio de alcohol para el vino?
dframe_vino['alcohol'].mean()
```




    10.422983114446529




```python
# Ese fue un ejemplo de agregación, ¿qué tal si hacemos el nuestro mediante una función?
def max_a_min(matriz):
    return matriz.max() - matriz.min()

# Agrupemos los vinos por su calidad (quality)
vino = dframe_vino.groupby('quality')
vino.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="8" halign="left">fixed acidity</th>
      <th colspan="2" halign="left">volatile acidity</th>
      <th>...</th>
      <th colspan="2" halign="left">sulphates</th>
      <th colspan="8" halign="left">alcohol</th>
    </tr>
    <tr>
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
      <th>count</th>
      <th>mean</th>
      <th>...</th>
      <th>75%</th>
      <th>max</th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
    <tr>
      <th>quality</th>
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
      <th>3</th>
      <td>10.0</td>
      <td>8.360000</td>
      <td>1.770875</td>
      <td>6.7</td>
      <td>7.15</td>
      <td>7.50</td>
      <td>9.875</td>
      <td>11.6</td>
      <td>10.0</td>
      <td>0.884500</td>
      <td>...</td>
      <td>0.615</td>
      <td>0.86</td>
      <td>10.0</td>
      <td>9.955000</td>
      <td>0.818009</td>
      <td>8.4</td>
      <td>9.725</td>
      <td>9.925</td>
      <td>10.575</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>53.0</td>
      <td>7.779245</td>
      <td>1.626624</td>
      <td>4.6</td>
      <td>6.80</td>
      <td>7.50</td>
      <td>8.400</td>
      <td>12.5</td>
      <td>53.0</td>
      <td>0.693962</td>
      <td>...</td>
      <td>0.600</td>
      <td>2.00</td>
      <td>53.0</td>
      <td>10.265094</td>
      <td>0.934776</td>
      <td>9.0</td>
      <td>9.600</td>
      <td>10.000</td>
      <td>11.000</td>
      <td>13.1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>681.0</td>
      <td>8.167254</td>
      <td>1.563988</td>
      <td>5.0</td>
      <td>7.10</td>
      <td>7.80</td>
      <td>8.900</td>
      <td>15.9</td>
      <td>681.0</td>
      <td>0.577041</td>
      <td>...</td>
      <td>0.660</td>
      <td>1.98</td>
      <td>681.0</td>
      <td>9.899706</td>
      <td>0.736521</td>
      <td>8.5</td>
      <td>9.400</td>
      <td>9.700</td>
      <td>10.200</td>
      <td>14.9</td>
    </tr>
    <tr>
      <th>6</th>
      <td>638.0</td>
      <td>8.347179</td>
      <td>1.797849</td>
      <td>4.7</td>
      <td>7.00</td>
      <td>7.90</td>
      <td>9.400</td>
      <td>14.3</td>
      <td>638.0</td>
      <td>0.497484</td>
      <td>...</td>
      <td>0.750</td>
      <td>1.95</td>
      <td>638.0</td>
      <td>10.629519</td>
      <td>1.049639</td>
      <td>8.4</td>
      <td>9.800</td>
      <td>10.500</td>
      <td>11.300</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>199.0</td>
      <td>8.872362</td>
      <td>1.992483</td>
      <td>4.9</td>
      <td>7.40</td>
      <td>8.80</td>
      <td>10.100</td>
      <td>15.6</td>
      <td>199.0</td>
      <td>0.403920</td>
      <td>...</td>
      <td>0.830</td>
      <td>1.36</td>
      <td>199.0</td>
      <td>11.465913</td>
      <td>0.961933</td>
      <td>9.2</td>
      <td>10.800</td>
      <td>11.500</td>
      <td>12.100</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>18.0</td>
      <td>8.566667</td>
      <td>2.119656</td>
      <td>5.0</td>
      <td>7.25</td>
      <td>8.25</td>
      <td>10.225</td>
      <td>12.6</td>
      <td>18.0</td>
      <td>0.423333</td>
      <td>...</td>
      <td>0.820</td>
      <td>1.10</td>
      <td>18.0</td>
      <td>12.094444</td>
      <td>1.224011</td>
      <td>9.8</td>
      <td>11.325</td>
      <td>12.150</td>
      <td>12.875</td>
      <td>14.0</td>
    </tr>
  </tbody>
</table>
<p>6 rows × 88 columns</p>
</div>




```python
# Ahora podemos aplicar nuestra propia función de agregación; esta función toma el valor máximo de la columna y resta el valor mínimo de la columna
vino.agg(max_a_min)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>fixed acidity</th>
      <th>volatile acidity</th>
      <th>citric acid</th>
      <th>residual sugar</th>
      <th>chlorides</th>
      <th>free sulfur dioxide</th>
      <th>total sulfur dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
    </tr>
    <tr>
      <th>quality</th>
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
      <th>3</th>
      <td>4.9</td>
      <td>1.140</td>
      <td>0.66</td>
      <td>4.5</td>
      <td>0.206</td>
      <td>31.0</td>
      <td>40.0</td>
      <td>0.00609</td>
      <td>0.47</td>
      <td>0.46</td>
      <td>2.6</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7.9</td>
      <td>0.900</td>
      <td>1.00</td>
      <td>11.6</td>
      <td>0.565</td>
      <td>38.0</td>
      <td>112.0</td>
      <td>0.00760</td>
      <td>1.16</td>
      <td>1.67</td>
      <td>4.1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>10.9</td>
      <td>1.150</td>
      <td>0.79</td>
      <td>14.3</td>
      <td>0.572</td>
      <td>65.0</td>
      <td>149.0</td>
      <td>0.01059</td>
      <td>0.86</td>
      <td>1.61</td>
      <td>6.4</td>
    </tr>
    <tr>
      <th>6</th>
      <td>9.6</td>
      <td>0.880</td>
      <td>0.78</td>
      <td>14.5</td>
      <td>0.381</td>
      <td>71.0</td>
      <td>159.0</td>
      <td>0.01362</td>
      <td>1.15</td>
      <td>1.55</td>
      <td>5.6</td>
    </tr>
    <tr>
      <th>7</th>
      <td>10.7</td>
      <td>0.795</td>
      <td>0.76</td>
      <td>7.7</td>
      <td>0.346</td>
      <td>51.0</td>
      <td>282.0</td>
      <td>0.01256</td>
      <td>0.86</td>
      <td>0.97</td>
      <td>4.8</td>
    </tr>
    <tr>
      <th>8</th>
      <td>7.6</td>
      <td>0.590</td>
      <td>0.69</td>
      <td>5.0</td>
      <td>0.042</td>
      <td>39.0</td>
      <td>76.0</td>
      <td>0.00800</td>
      <td>0.84</td>
      <td>0.47</td>
      <td>4.2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# También podemos pasar métodos de cadena a través del agregado
vino.agg('mean')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>fixed acidity</th>
      <th>volatile acidity</th>
      <th>citric acid</th>
      <th>residual sugar</th>
      <th>chlorides</th>
      <th>free sulfur dioxide</th>
      <th>total sulfur dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
    </tr>
    <tr>
      <th>quality</th>
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
      <th>3</th>
      <td>8.360000</td>
      <td>0.884500</td>
      <td>0.171000</td>
      <td>2.635000</td>
      <td>0.122500</td>
      <td>11.000000</td>
      <td>24.900000</td>
      <td>0.997464</td>
      <td>3.398000</td>
      <td>0.570000</td>
      <td>9.955000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7.779245</td>
      <td>0.693962</td>
      <td>0.174151</td>
      <td>2.694340</td>
      <td>0.090679</td>
      <td>12.264151</td>
      <td>36.245283</td>
      <td>0.996542</td>
      <td>3.381509</td>
      <td>0.596415</td>
      <td>10.265094</td>
    </tr>
    <tr>
      <th>5</th>
      <td>8.167254</td>
      <td>0.577041</td>
      <td>0.243686</td>
      <td>2.528855</td>
      <td>0.092736</td>
      <td>16.983847</td>
      <td>56.513950</td>
      <td>0.997104</td>
      <td>3.304949</td>
      <td>0.620969</td>
      <td>9.899706</td>
    </tr>
    <tr>
      <th>6</th>
      <td>8.347179</td>
      <td>0.497484</td>
      <td>0.273824</td>
      <td>2.477194</td>
      <td>0.084956</td>
      <td>15.711599</td>
      <td>40.869906</td>
      <td>0.996615</td>
      <td>3.318072</td>
      <td>0.675329</td>
      <td>10.629519</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8.872362</td>
      <td>0.403920</td>
      <td>0.375176</td>
      <td>2.720603</td>
      <td>0.076588</td>
      <td>14.045226</td>
      <td>35.020101</td>
      <td>0.996104</td>
      <td>3.290754</td>
      <td>0.741256</td>
      <td>11.465913</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8.566667</td>
      <td>0.423333</td>
      <td>0.391111</td>
      <td>2.577778</td>
      <td>0.068444</td>
      <td>13.277778</td>
      <td>33.444444</td>
      <td>0.995212</td>
      <td>3.267222</td>
      <td>0.767778</td>
      <td>12.094444</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Agreguemos una proporción entre la calidad (quality) y el contenido alcoholico (alcohol)
dframe_vino['qual/alc ratio'] = dframe_vino['quality']/dframe_wine['alcohol']
dframe_vino.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>fixed acidity</th>
      <th>volatile acidity</th>
      <th>citric acid</th>
      <th>residual sugar</th>
      <th>chlorides</th>
      <th>free sulfur dioxide</th>
      <th>total sulfur dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
      <th>quality</th>
      <th>qual/alc ratio</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7.4</td>
      <td>0.70</td>
      <td>0.00</td>
      <td>1.9</td>
      <td>0.076</td>
      <td>11.0</td>
      <td>34.0</td>
      <td>0.9978</td>
      <td>3.51</td>
      <td>0.56</td>
      <td>9.4</td>
      <td>5</td>
      <td>0.531915</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7.8</td>
      <td>0.88</td>
      <td>0.00</td>
      <td>2.6</td>
      <td>0.098</td>
      <td>25.0</td>
      <td>67.0</td>
      <td>0.9968</td>
      <td>3.20</td>
      <td>0.68</td>
      <td>9.8</td>
      <td>5</td>
      <td>0.510204</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7.8</td>
      <td>0.76</td>
      <td>0.04</td>
      <td>2.3</td>
      <td>0.092</td>
      <td>15.0</td>
      <td>54.0</td>
      <td>0.9970</td>
      <td>3.26</td>
      <td>0.65</td>
      <td>9.8</td>
      <td>5</td>
      <td>0.510204</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11.2</td>
      <td>0.28</td>
      <td>0.56</td>
      <td>1.9</td>
      <td>0.075</td>
      <td>17.0</td>
      <td>60.0</td>
      <td>0.9980</td>
      <td>3.16</td>
      <td>0.58</td>
      <td>9.8</td>
      <td>6</td>
      <td>0.612245</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7.4</td>
      <td>0.70</td>
      <td>0.00</td>
      <td>1.9</td>
      <td>0.076</td>
      <td>11.0</td>
      <td>34.0</td>
      <td>0.9978</td>
      <td>3.51</td>
      <td>0.56</td>
      <td>9.4</td>
      <td>5</td>
      <td>0.531915</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Tambien podemos usar pivot_table en lugar groupby

# Pivotear la calidad (quality) en la tabla
dframe_vino.pivot_table(index=['quality'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcohol</th>
      <th>chlorides</th>
      <th>citric acid</th>
      <th>density</th>
      <th>fixed acidity</th>
      <th>free sulfur dioxide</th>
      <th>pH</th>
      <th>qual/alc ratio</th>
      <th>residual sugar</th>
      <th>sulphates</th>
      <th>total sulfur dioxide</th>
      <th>volatile acidity</th>
    </tr>
    <tr>
      <th>quality</th>
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
      <th>3</th>
      <td>9.955000</td>
      <td>0.122500</td>
      <td>0.171000</td>
      <td>0.997464</td>
      <td>8.360000</td>
      <td>11.000000</td>
      <td>3.398000</td>
      <td>0.303286</td>
      <td>2.635000</td>
      <td>0.570000</td>
      <td>24.900000</td>
      <td>0.884500</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10.265094</td>
      <td>0.090679</td>
      <td>0.174151</td>
      <td>0.996542</td>
      <td>7.779245</td>
      <td>12.264151</td>
      <td>3.381509</td>
      <td>0.392724</td>
      <td>2.694340</td>
      <td>0.596415</td>
      <td>36.245283</td>
      <td>0.693962</td>
    </tr>
    <tr>
      <th>5</th>
      <td>9.899706</td>
      <td>0.092736</td>
      <td>0.243686</td>
      <td>0.997104</td>
      <td>8.167254</td>
      <td>16.983847</td>
      <td>3.304949</td>
      <td>0.507573</td>
      <td>2.528855</td>
      <td>0.620969</td>
      <td>56.513950</td>
      <td>0.577041</td>
    </tr>
    <tr>
      <th>6</th>
      <td>10.629519</td>
      <td>0.084956</td>
      <td>0.273824</td>
      <td>0.996615</td>
      <td>8.347179</td>
      <td>15.711599</td>
      <td>3.318072</td>
      <td>0.569801</td>
      <td>2.477194</td>
      <td>0.675329</td>
      <td>40.869906</td>
      <td>0.497484</td>
    </tr>
    <tr>
      <th>7</th>
      <td>11.465913</td>
      <td>0.076588</td>
      <td>0.375176</td>
      <td>0.996104</td>
      <td>8.872362</td>
      <td>14.045226</td>
      <td>3.290754</td>
      <td>0.614855</td>
      <td>2.720603</td>
      <td>0.741256</td>
      <td>35.020101</td>
      <td>0.403920</td>
    </tr>
    <tr>
      <th>8</th>
      <td>12.094444</td>
      <td>0.068444</td>
      <td>0.391111</td>
      <td>0.995212</td>
      <td>8.566667</td>
      <td>13.277778</td>
      <td>3.267222</td>
      <td>0.668146</td>
      <td>2.577778</td>
      <td>0.767778</td>
      <td>33.444444</td>
      <td>0.423333</td>
    </tr>
  </tbody>
</table>
</div>



## División, aplicación y combinación


```python
# ¿Qué pasaría si quisiéramos saber el contenido de alcohol mas alto para cada rango de calidad?
# Podemos usar la mecánica de groupby para dividir-aplicar-combinar
# Se crea una función que asigne un rango a cada vino, según el contenido de alcohol, siendo 1 el mayor contenido de alcohol.
def rango(df):
    df['alc_content_rank'] = np.arange(len(df)) + 1
    return df
```


```python
# Se ordena el dataframe por su valor de alcohol, en orden ascendente
dframe_vino.sort_values('alcohol',ascending=False,inplace=True)

# Se agrupa por su calidad y se aplica la función de rango
dframe_vino = dframe_vio.groupby('quality').apply(rango)
dframe_vino.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>fixed acidity</th>
      <th>volatile acidity</th>
      <th>citric acid</th>
      <th>residual sugar</th>
      <th>chlorides</th>
      <th>free sulfur dioxide</th>
      <th>total sulfur dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
      <th>quality</th>
      <th>qual/alc ratio</th>
      <th>alc_content_rank</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>652</th>
      <td>15.9</td>
      <td>0.36</td>
      <td>0.65</td>
      <td>7.5</td>
      <td>0.096</td>
      <td>22.0</td>
      <td>71.0</td>
      <td>0.99760</td>
      <td>2.98</td>
      <td>0.84</td>
      <td>14.9</td>
      <td>5</td>
      <td>0.335570</td>
      <td>1</td>
    </tr>
    <tr>
      <th>588</th>
      <td>5.0</td>
      <td>0.42</td>
      <td>0.24</td>
      <td>2.0</td>
      <td>0.060</td>
      <td>19.0</td>
      <td>50.0</td>
      <td>0.99170</td>
      <td>3.72</td>
      <td>0.74</td>
      <td>14.0</td>
      <td>8</td>
      <td>0.571429</td>
      <td>1</td>
    </tr>
    <tr>
      <th>142</th>
      <td>5.2</td>
      <td>0.34</td>
      <td>0.00</td>
      <td>1.8</td>
      <td>0.050</td>
      <td>27.0</td>
      <td>63.0</td>
      <td>0.99160</td>
      <td>3.68</td>
      <td>0.79</td>
      <td>14.0</td>
      <td>6</td>
      <td>0.428571</td>
      <td>1</td>
    </tr>
    <tr>
      <th>144</th>
      <td>5.2</td>
      <td>0.34</td>
      <td>0.00</td>
      <td>1.8</td>
      <td>0.050</td>
      <td>27.0</td>
      <td>63.0</td>
      <td>0.99160</td>
      <td>3.68</td>
      <td>0.79</td>
      <td>14.0</td>
      <td>6</td>
      <td>0.428571</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1270</th>
      <td>5.0</td>
      <td>0.38</td>
      <td>0.01</td>
      <td>1.6</td>
      <td>0.048</td>
      <td>26.0</td>
      <td>60.0</td>
      <td>0.99084</td>
      <td>3.70</td>
      <td>0.75</td>
      <td>14.0</td>
      <td>6</td>
      <td>0.428571</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Ahora finalmente podemos llamar al dataframe donde elrango del contenido de alcohol (alc_content_rank) es 1
# Se obtiene el número de conteos de calidad
num_de_calidad = dframe_vino['quality'].value_counts()
num_of_calidad
```




    5    681
    6    638
    7    199
    4     53
    8     18
    3     10
    Name: quality, dtype: int64




```python
# ¡Ahora mostraremos la información combinada, de los vinos que tienen el mayor contenido de alcohol para su rango!
dframe_vino[dframe_vino.alc_content_rank == 1].head(len(num_de_calidad))
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>fixed acidity</th>
      <th>volatile acidity</th>
      <th>citric acid</th>
      <th>residual sugar</th>
      <th>chlorides</th>
      <th>free sulfur dioxide</th>
      <th>total sulfur dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
      <th>quality</th>
      <th>qual/alc ratio</th>
      <th>alc_content_rank</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>652</th>
      <td>15.9</td>
      <td>0.36</td>
      <td>0.65</td>
      <td>7.5</td>
      <td>0.096</td>
      <td>22.0</td>
      <td>71.0</td>
      <td>0.99760</td>
      <td>2.98</td>
      <td>0.84</td>
      <td>14.9</td>
      <td>5</td>
      <td>0.335570</td>
      <td>1</td>
    </tr>
    <tr>
      <th>588</th>
      <td>5.0</td>
      <td>0.42</td>
      <td>0.24</td>
      <td>2.0</td>
      <td>0.060</td>
      <td>19.0</td>
      <td>50.0</td>
      <td>0.99170</td>
      <td>3.72</td>
      <td>0.74</td>
      <td>14.0</td>
      <td>8</td>
      <td>0.571429</td>
      <td>1</td>
    </tr>
    <tr>
      <th>142</th>
      <td>5.2</td>
      <td>0.34</td>
      <td>0.00</td>
      <td>1.8</td>
      <td>0.050</td>
      <td>27.0</td>
      <td>63.0</td>
      <td>0.99160</td>
      <td>3.68</td>
      <td>0.79</td>
      <td>14.0</td>
      <td>6</td>
      <td>0.428571</td>
      <td>1</td>
    </tr>
    <tr>
      <th>821</th>
      <td>4.9</td>
      <td>0.42</td>
      <td>0.00</td>
      <td>2.1</td>
      <td>0.048</td>
      <td>16.0</td>
      <td>42.0</td>
      <td>0.99154</td>
      <td>3.71</td>
      <td>0.74</td>
      <td>14.0</td>
      <td>7</td>
      <td>0.500000</td>
      <td>1</td>
    </tr>
    <tr>
      <th>45</th>
      <td>4.6</td>
      <td>0.52</td>
      <td>0.15</td>
      <td>2.1</td>
      <td>0.054</td>
      <td>8.0</td>
      <td>65.0</td>
      <td>0.99340</td>
      <td>3.90</td>
      <td>0.56</td>
      <td>13.1</td>
      <td>4</td>
      <td>0.305344</td>
      <td>1</td>
    </tr>
    <tr>
      <th>899</th>
      <td>8.3</td>
      <td>1.02</td>
      <td>0.02</td>
      <td>3.4</td>
      <td>0.084</td>
      <td>6.0</td>
      <td>11.0</td>
      <td>0.99892</td>
      <td>3.48</td>
      <td>0.49</td>
      <td>11.0</td>
      <td>3</td>
      <td>0.272727</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



## Tabulación cruzada


```python
# Las tabulaciones cruzadas son, básicamente, un caso especial de tablas dinámicas
# Vamos a crear un conjunto de datos pequeño

datos ="""\
Muestra   Animal   Inteligencia
1        Perro     Listo
2 Perro Listo
3 Gato Tonto
4 Gato Tonto
5 Perro Tonto
6 Gato Listo"""

# Se almacena como un dataframe
dframe = pd.read_table(StringIO(datos),sep='\s+')
dframe
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Muestra</th>
      <th>Animal</th>
      <th>Inteligencia</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Perro</td>
      <td>Listo</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Perro</td>
      <td>Listo</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Gato</td>
      <td>Tonto</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Gato</td>
      <td>Tonto</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Perro</td>
      <td>Tonto</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>Gato</td>
      <td>Listo</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Ahora podemos crear una tabla de tabulación cruzada, que básicamente es solo una tabla de frecuencias
pd.crosstab(dframe.Animal,dframe.Inteligencia,margins=True)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Inteligencia</th>
      <th>Tonto</th>
      <th>Listo</th>
      <th>All</th>
    </tr>
    <tr>
      <th>Animal</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Gato</th>
      <td>2</td>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Perro</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>All</th>
      <td>3</td>
      <td>3</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>



## ¡¡¡Felicidades, hemos terminado con el procesamiento de datos!!!


 [**Siguiente Lección**](Lecci%C3%B3n%2009%20-%20Visualizaci%C3%B3n_Datos.md)    
