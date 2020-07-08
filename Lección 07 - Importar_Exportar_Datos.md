# Importar y exportar datos


```python
# Cargar las librerias
import numpy as np
import pandas as pd
from pandas import Series,DataFrame
```

## Importar datos desde archivos CSV y txt

El conjunto de datos Iris es, probablemente, el mejor conocido dentro de la literatura de reconocimiento de patrones
Contiene muestras de 3 especies de iris (Iris Setosa, Iris Virginica e Iris Versicolor)
Las características que se incluyen son la longitud y el ancho de los sépalos y los pétalos en centímetros
En base a la combinación de estas características, se buscan modelos que permitan diferenciar las especies entre si


```python
# Leer un archivo csv
dframe = pd.read_csv('data/iris_dataset.csv')
dframe
```




<div>
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
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>145</th>
      <td>6.7</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>146</th>
      <td>6.3</td>
      <td>2.5</td>
      <td>5.0</td>
      <td>1.9</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>147</th>
      <td>6.5</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.0</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>148</th>
      <td>6.2</td>
      <td>3.4</td>
      <td>5.4</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>149</th>
      <td>5.9</td>
      <td>3.0</td>
      <td>5.1</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
  </tbody>
</table>
<p>150 rows × 5 columns</p>
</div>




```python
# Leer un archivo csv/tabla especificando el separador
dframe = pd.read_table('data/iris_dataset.csv',sep=',')
dframe
```




<div>
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
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>145</th>
      <td>6.7</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>146</th>
      <td>6.3</td>
      <td>2.5</td>
      <td>5.0</td>
      <td>1.9</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>147</th>
      <td>6.5</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.0</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>148</th>
      <td>6.2</td>
      <td>3.4</td>
      <td>5.4</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>149</th>
      <td>5.9</td>
      <td>3.0</td>
      <td>5.1</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
  </tbody>
</table>
<p>150 rows × 5 columns</p>
</div>




```python
dframe
```




<div>
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
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>145</th>
      <td>6.7</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>146</th>
      <td>6.3</td>
      <td>2.5</td>
      <td>5.0</td>
      <td>1.9</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>147</th>
      <td>6.5</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.0</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>148</th>
      <td>6.2</td>
      <td>3.4</td>
      <td>5.4</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>149</th>
      <td>5.9</td>
      <td>3.0</td>
      <td>5.1</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
  </tbody>
</table>
<p>150 rows × 5 columns</p>
</div>




```python
# Si se necesita considerar los encabezados en la tabla
dframe = pd.read_csv('data/iris_dataset.csv',header=None)
dframe
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SepalLength</td>
      <td>SepalWidth</td>
      <td>PetalLength</td>
      <td>PetalWidth</td>
      <td>Class</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>146</th>
      <td>6.7</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>147</th>
      <td>6.3</td>
      <td>2.5</td>
      <td>5.0</td>
      <td>1.9</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>148</th>
      <td>6.5</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.0</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>149</th>
      <td>6.2</td>
      <td>3.4</td>
      <td>5.4</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>150</th>
      <td>5.9</td>
      <td>3.0</td>
      <td>5.1</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
  </tbody>
</table>
<p>151 rows × 5 columns</p>
</div>




```python
# Se puede especificar el número de filas a leer
pd.read_csv('data/iris_dataset.csv',header=None,nrows=2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SepalLength</td>
      <td>SepalWidth</td>
      <td>PetalLength</td>
      <td>PetalWidth</td>
      <td>Class</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
dframe
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SepalLength</td>
      <td>SepalWidth</td>
      <td>PetalLength</td>
      <td>PetalWidth</td>
      <td>Class</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>146</th>
      <td>6.7</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>147</th>
      <td>6.3</td>
      <td>2.5</td>
      <td>5.0</td>
      <td>1.9</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>148</th>
      <td>6.5</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.0</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>149</th>
      <td>6.2</td>
      <td>3.4</td>
      <td>5.4</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>150</th>
      <td>5.9</td>
      <td>3.0</td>
      <td>5.1</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
  </tbody>
</table>
<p>151 rows × 5 columns</p>
</div>



## Exportar datos en formato CSV


```python
# Para exportar datos a un archivo CSV
dframe.to_csv('data/mytextdata_out.csv')

```


```python
# Tambien se pueden usar otros delimitadores
# Se importa la libreria sys para poder visualizar el dataframe.
import sys

# Se usa sys.stdout para ver el archivo en panatalla y no guardarlo.
dframe.to_csv(sys.stdout,sep=',')
```

    ,0,1,2,3,4
    0,SepalLength,SepalWidth,PetalLength,PetalWidth,Class
    1,5.1,3.5,1.4,0.2,Iris-setosa
    2,4.9,3.0,1.4,0.2,Iris-setosa
    3,4.7,3.2,1.3,0.2,Iris-setosa
    4,4.6,3.1,1.5,0.2,Iris-setosa
    5,5.0,3.6,1.4,0.2,Iris-setosa
    6,5.4,3.9,1.7,0.4,Iris-setosa
    7,4.6,3.4,1.4,0.3,Iris-setosa
    8,5.0,3.4,1.5,0.2,Iris-setosa
    9,4.4,2.9,1.4,0.2,Iris-setosa
    10,4.9,3.1,1.5,0.1,Iris-setosa
    11,5.4,3.7,1.5,0.2,Iris-setosa
    12,4.8,3.4,1.6,0.2,Iris-setosa
    13,4.8,3.0,1.4,0.1,Iris-setosa
    14,4.3,3.0,1.1,0.1,Iris-setosa
    15,5.8,4.0,1.2,0.2,Iris-setosa
    16,5.7,4.4,1.5,0.4,Iris-setosa
    17,5.4,3.9,1.3,0.4,Iris-setosa
    18,5.1,3.5,1.4,0.3,Iris-setosa
    19,5.7,3.8,1.7,0.3,Iris-setosa
    20,5.1,3.8,1.5,0.3,Iris-setosa
    21,5.4,3.4,1.7,0.2,Iris-setosa
    22,5.1,3.7,1.5,0.4,Iris-setosa
    23,4.6,3.6,1.0,0.2,Iris-setosa
    24,5.1,3.3,1.7,0.5,Iris-setosa
    25,4.8,3.4,1.9,0.2,Iris-setosa
    26,5.0,3.0,1.6,0.2,Iris-setosa
    27,5.0,3.4,1.6,0.4,Iris-setosa
    28,5.2,3.5,1.5,0.2,Iris-setosa
    29,5.2,3.4,1.4,0.2,Iris-setosa
    30,4.7,3.2,1.6,0.2,Iris-setosa
    31,4.8,3.1,1.6,0.2,Iris-setosa
    32,5.4,3.4,1.5,0.4,Iris-setosa
    33,5.2,4.1,1.5,0.1,Iris-setosa
    34,5.5,4.2,1.4,0.2,Iris-setosa
    35,4.9,3.1,1.5,0.1,Iris-setosa
    36,5.0,3.2,1.2,0.2,Iris-setosa
    37,5.5,3.5,1.3,0.2,Iris-setosa
    38,4.9,3.1,1.5,0.1,Iris-setosa
    39,4.4,3.0,1.3,0.2,Iris-setosa
    40,5.1,3.4,1.5,0.2,Iris-setosa
    41,7.0,3.2,4.7,1.4,Iris-versicolor
    42,6.4,3.2,4.5,1.5,Iris-versicolor
    43,6.9,3.1,4.9,1.5,Iris-versicolor
    44,5.5,2.3,4.0,1.3,Iris-versicolor
    45,6.5,2.8,4.6,1.5,Iris-versicolor
    46,5.7,2.8,4.5,1.3,Iris-versicolor
    47,6.3,3.3,4.7,1.6,Iris-versicolor
    48,4.9,2.4,3.3,1.0,Iris-versicolor
    49,6.6,2.9,4.6,1.3,Iris-versicolor
    50,5.2,2.7,3.9,1.4,Iris-versicolor
    51,5.0,2.0,3.5,1.0,Iris-versicolor
    52,5.9,3.0,4.2,1.5,Iris-versicolor
    53,6.0,2.2,4.0,1.0,Iris-versicolor
    54,6.1,2.9,4.7,1.4,Iris-versicolor
    55,5.6,2.9,3.6,1.3,Iris-versicolor
    56,6.7,3.1,4.4,1.4,Iris-versicolor
    57,5.6,3.0,4.5,1.5,Iris-versicolor
    58,5.8,2.7,4.1,1.0,Iris-versicolor
    59,6.2,2.2,4.5,1.5,Iris-versicolor
    60,5.6,2.5,3.9,1.1,Iris-versicolor
    61,5.9,3.2,4.8,1.8,Iris-versicolor
    62,6.1,2.8,4.0,1.3,Iris-versicolor
    63,6.3,2.5,4.9,1.5,Iris-versicolor
    64,6.1,2.8,4.7,1.2,Iris-versicolor
    65,6.4,2.9,4.3,1.3,Iris-versicolor
    66,6.6,3.0,4.4,1.4,Iris-versicolor
    67,6.8,2.8,4.8,1.4,Iris-versicolor
    68,6.7,3.0,5.0,1.7,Iris-versicolor
    69,6.0,2.9,4.5,1.5,Iris-versicolor
    70,5.7,2.6,3.5,1.0,Iris-versicolor
    71,5.5,2.4,3.8,1.1,Iris-versicolor
    72,5.5,2.4,3.7,1.0,Iris-versicolor
    73,5.8,2.7,3.9,1.2,Iris-versicolor
    74,6.0,2.7,5.1,1.6,Iris-versicolor
    75,5.4,3.0,4.5,1.5,Iris-versicolor
    76,6.0,3.4,4.5,1.6,Iris-versicolor
    77,6.7,3.1,4.7,1.5,Iris-versicolor
    78,6.3,2.3,4.4,1.3,Iris-versicolor
    79,5.6,3.0,4.1,1.3,Iris-versicolor
    80,5.5,2.5,4.0,1.3,Iris-versicolor
    81,6.3,3.3,6.0,2.5,Iris-virginica
    82,5.8,2.7,5.1,1.9,Iris-virginica
    83,7.1,3.0,5.9,2.1,Iris-virginica
    84,6.3,2.9,5.6,1.8,Iris-virginica
    85,6.5,3.0,5.8,2.2,Iris-virginica
    86,7.6,3.0,6.6,2.1,Iris-virginica
    87,4.9,2.5,4.5,1.7,Iris-virginica
    88,7.3,2.9,6.3,1.8,Iris-virginica
    89,6.7,2.5,5.8,1.8,Iris-virginica
    90,7.2,3.6,6.1,2.5,Iris-virginica
    91,6.5,3.2,5.1,2.0,Iris-virginica
    92,6.4,2.7,5.3,1.9,Iris-virginica
    93,6.8,3.0,5.5,2.1,Iris-virginica
    94,5.7,2.5,5.0,2.0,Iris-virginica
    95,5.8,2.8,5.1,2.4,Iris-virginica
    96,6.4,3.2,5.3,2.3,Iris-virginica
    97,6.5,3.0,5.5,1.8,Iris-virginica
    98,7.7,3.8,6.7,2.2,Iris-virginica
    99,7.7,2.6,6.9,2.3,Iris-virginica
    100,6.0,2.2,5.0,1.5,Iris-virginica
    101,6.9,3.2,5.7,2.3,Iris-virginica
    102,5.6,2.8,4.9,2.0,Iris-virginica
    103,7.7,2.8,6.7,2.0,Iris-virginica
    104,6.3,2.7,4.9,1.8,Iris-virginica
    105,6.7,3.3,5.7,2.1,Iris-virginica
    106,7.2,3.2,6.0,1.8,Iris-virginica
    107,6.2,2.8,4.8,1.8,Iris-virginica
    108,6.1,3.0,4.9,1.8,Iris-virginica
    109,6.4,2.8,5.6,2.1,Iris-virginica
    110,7.2,3.0,5.8,1.6,Iris-virginica
    111,7.4,2.8,6.1,1.9,Iris-virginica
    112,7.9,3.8,6.4,2.0,Iris-virginica
    113,6.4,2.8,5.6,2.2,Iris-virginica
    114,6.3,2.8,5.1,1.5,Iris-virginica
    115,6.1,2.6,5.6,1.4,Iris-virginica
    116,7.7,3.0,6.1,2.3,Iris-virginica
    117,6.3,3.4,5.6,2.4,Iris-virginica
    118,6.4,3.1,5.5,1.8,Iris-virginica
    119,6.0,3.0,4.8,1.8,Iris-virginica
    120,6.9,3.1,5.4,2.1,Iris-virginica
    121,5.0,3.5,1.3,0.3,Iris-setosa
    122,4.5,2.3,1.3,0.3,Iris-setosa
    123,4.4,3.2,1.3,0.2,Iris-setosa
    124,5.0,3.5,1.6,0.6,Iris-setosa
    125,5.1,3.8,1.9,0.4,Iris-setosa
    126,4.8,3.0,1.4,0.3,Iris-setosa
    127,5.1,3.8,1.6,0.2,Iris-setosa
    128,4.6,3.2,1.4,0.2,Iris-setosa
    129,5.3,3.7,1.5,0.2,Iris-setosa
    130,5.0,3.3,1.4,0.2,Iris-setosa
    131,5.5,2.6,4.4,1.2,Iris-versicolor
    132,6.1,3.0,4.6,1.4,Iris-versicolor
    133,5.8,2.6,4.0,1.2,Iris-versicolor
    134,5.0,2.3,3.3,1.0,Iris-versicolor
    135,5.6,2.7,4.2,1.3,Iris-versicolor
    136,5.7,3.0,4.2,1.2,Iris-versicolor
    137,5.7,2.9,4.2,1.3,Iris-versicolor
    138,6.2,2.9,4.3,1.3,Iris-versicolor
    139,5.1,2.5,3.0,1.1,Iris-versicolor
    140,5.7,2.8,4.1,1.3,Iris-versicolor
    141,6.7,3.1,5.6,2.4,Iris-virginica
    142,6.9,3.1,5.1,2.3,Iris-virginica
    143,5.8,2.7,5.1,1.9,Iris-virginica
    144,6.8,3.2,5.9,2.3,Iris-virginica
    145,6.7,3.3,5.7,2.5,Iris-virginica
    146,6.7,3.0,5.2,2.3,Iris-virginica
    147,6.3,2.5,5.0,1.9,Iris-virginica
    148,6.5,3.0,5.2,2.0,Iris-virginica
    149,6.2,3.4,5.4,2.3,Iris-virginica
    150,5.9,3.0,5.1,1.8,Iris-virginica



```python
# Se puede elegir un subconjunto específico de columnas
dframe.to_csv(sys.stdout,columns=[0,1,2])
```

    ,0,1,2
    0,SepalLength,SepalWidth,PetalLength
    1,5.1,3.5,1.4
    2,4.9,3.0,1.4
    3,4.7,3.2,1.3
    4,4.6,3.1,1.5
    5,5.0,3.6,1.4
    6,5.4,3.9,1.7
    7,4.6,3.4,1.4
    8,5.0,3.4,1.5
    9,4.4,2.9,1.4
    10,4.9,3.1,1.5
    11,5.4,3.7,1.5
    12,4.8,3.4,1.6
    13,4.8,3.0,1.4
    14,4.3,3.0,1.1
    15,5.8,4.0,1.2
    16,5.7,4.4,1.5
    17,5.4,3.9,1.3
    18,5.1,3.5,1.4
    19,5.7,3.8,1.7
    20,5.1,3.8,1.5
    21,5.4,3.4,1.7
    22,5.1,3.7,1.5
    23,4.6,3.6,1.0
    24,5.1,3.3,1.7
    25,4.8,3.4,1.9
    26,5.0,3.0,1.6
    27,5.0,3.4,1.6
    28,5.2,3.5,1.5
    29,5.2,3.4,1.4
    30,4.7,3.2,1.6
    31,4.8,3.1,1.6
    32,5.4,3.4,1.5
    33,5.2,4.1,1.5
    34,5.5,4.2,1.4
    35,4.9,3.1,1.5
    36,5.0,3.2,1.2
    37,5.5,3.5,1.3
    38,4.9,3.1,1.5
    39,4.4,3.0,1.3
    40,5.1,3.4,1.5
    41,7.0,3.2,4.7
    42,6.4,3.2,4.5
    43,6.9,3.1,4.9
    44,5.5,2.3,4.0
    45,6.5,2.8,4.6
    46,5.7,2.8,4.5
    47,6.3,3.3,4.7
    48,4.9,2.4,3.3
    49,6.6,2.9,4.6
    50,5.2,2.7,3.9
    51,5.0,2.0,3.5
    52,5.9,3.0,4.2
    53,6.0,2.2,4.0
    54,6.1,2.9,4.7
    55,5.6,2.9,3.6
    56,6.7,3.1,4.4
    57,5.6,3.0,4.5
    58,5.8,2.7,4.1
    59,6.2,2.2,4.5
    60,5.6,2.5,3.9
    61,5.9,3.2,4.8
    62,6.1,2.8,4.0
    63,6.3,2.5,4.9
    64,6.1,2.8,4.7
    65,6.4,2.9,4.3
    66,6.6,3.0,4.4
    67,6.8,2.8,4.8
    68,6.7,3.0,5.0
    69,6.0,2.9,4.5
    70,5.7,2.6,3.5
    71,5.5,2.4,3.8
    72,5.5,2.4,3.7
    73,5.8,2.7,3.9
    74,6.0,2.7,5.1
    75,5.4,3.0,4.5
    76,6.0,3.4,4.5
    77,6.7,3.1,4.7
    78,6.3,2.3,4.4
    79,5.6,3.0,4.1
    80,5.5,2.5,4.0
    81,6.3,3.3,6.0
    82,5.8,2.7,5.1
    83,7.1,3.0,5.9
    84,6.3,2.9,5.6
    85,6.5,3.0,5.8
    86,7.6,3.0,6.6
    87,4.9,2.5,4.5
    88,7.3,2.9,6.3
    89,6.7,2.5,5.8
    90,7.2,3.6,6.1
    91,6.5,3.2,5.1
    92,6.4,2.7,5.3
    93,6.8,3.0,5.5
    94,5.7,2.5,5.0
    95,5.8,2.8,5.1
    96,6.4,3.2,5.3
    97,6.5,3.0,5.5
    98,7.7,3.8,6.7
    99,7.7,2.6,6.9
    100,6.0,2.2,5.0
    101,6.9,3.2,5.7
    102,5.6,2.8,4.9
    103,7.7,2.8,6.7
    104,6.3,2.7,4.9
    105,6.7,3.3,5.7
    106,7.2,3.2,6.0
    107,6.2,2.8,4.8
    108,6.1,3.0,4.9
    109,6.4,2.8,5.6
    110,7.2,3.0,5.8
    111,7.4,2.8,6.1
    112,7.9,3.8,6.4
    113,6.4,2.8,5.6
    114,6.3,2.8,5.1
    115,6.1,2.6,5.6
    116,7.7,3.0,6.1
    117,6.3,3.4,5.6
    118,6.4,3.1,5.5
    119,6.0,3.0,4.8
    120,6.9,3.1,5.4
    121,5.0,3.5,1.3
    122,4.5,2.3,1.3
    123,4.4,3.2,1.3
    124,5.0,3.5,1.6
    125,5.1,3.8,1.9
    126,4.8,3.0,1.4
    127,5.1,3.8,1.6
    128,4.6,3.2,1.4
    129,5.3,3.7,1.5
    130,5.0,3.3,1.4
    131,5.5,2.6,4.4
    132,6.1,3.0,4.6
    133,5.8,2.6,4.0
    134,5.0,2.3,3.3
    135,5.6,2.7,4.2
    136,5.7,3.0,4.2
    137,5.7,2.9,4.2
    138,6.2,2.9,4.3
    139,5.1,2.5,3.0
    140,5.7,2.8,4.1
    141,6.7,3.1,5.6
    142,6.9,3.1,5.1
    143,5.8,2.7,5.1
    144,6.8,3.2,5.9
    145,6.7,3.3,5.7
    146,6.7,3.0,5.2
    147,6.3,2.5,5.0
    148,6.5,3.0,5.2
    149,6.2,3.4,5.4
    150,5.9,3.0,5.1


##### Para mas información sobre los parametros para leer y escribir archivos CSV, consultar:
##### [Importar/Exportar datos CSV](https://docs.python.org/2/library/csv.html)

## Importar datos en formato JSON


```python
# Un ejemplo de cómo se ve una estructura JSON (JavaScript Object Notation):
json_obj = """
{   "animal": "Leon",
    "comida": ["Carne", "Verdura", "Miel"],
    "pelaje": "Dorado",
    "ropa": null,
    "dieta": [{"animal": "Gacela", "comida":"Pasto", "pelaje": "Cafe"}]
}
"""
```

Esta estructura json contiene los datos de un animal del zoológico, en el que se se especifican sus características.


```python
type(json_obj)
```




    str



### Diccionarios


```python
# Importar el modulo JSON
import json

# Cargar los datos en JSON
datos = json.loads(json_obj)

# Visualizar los datos
datos
```




    {'animal': 'Leon',
     'comida': ['Carne', 'Verdura', 'Miel'],
     'pelaje': 'Dorado',
     'ropa': None,
     'dieta': [{'animal': 'Gacela', 'comida': 'Pasto', 'fur': 'Cafe'}]}




```python
type(datos)
```




    dict




```python
# Convertir datos en JSON
json.dumps(datos)
```




    '{"animal": "Leon", "comida": ["Carne", "Verdura", "Miel"], "pelaje": "Dorado", "ropa": null, "dieta": [{"animal": "Gacela", "comida": "Pasto", "pelaje": "Cafe"}]}'




```python
# Despues de leer los datos JSON, se asignan a un dataframe
dframe = DataFrame(datos['dieta'])
dframe
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>animal</th>
      <th>comida</th>
      <th>pelaje</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Gacela</td>
      <td>Pasto</td>
      <td>Cafe</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Generemos un diccionario y un dataframe a partir de él
# Por defecto, las llaves del diccionario serán consideradas columnas del dataframe
datos1 = {'col_1': [3, 2, 1, 0], 'col_2': ['a', 'b', 'c', 'd']}
pd.DataFrame.from_dict(datos1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>col_1</th>
      <th>col_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3</td>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>d</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Generemos otro diccionario y un dataframe a partir de él
# En este caso, indicamos que las llaves se consideren como renglones del dataframe
datos = {'ren_1': [3, 2, 1, 0], 'ren_2': ['a', 'b', 'c', 'd']}
pd.DataFrame.from_dict(datos, orient='index')
```


<div>
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
      <th>ren_1</th>
      <td>3</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>ren_2</th>
      <td>a</td>
      <td>b</td>
      <td>c</td>
      <td>d</td>
    </tr>
  </tbody>
</table>
</div>



```python
# Generemos otro diccionario y un dataframe a partir de él
# En este caso, indicamos que las llaves se consideren como renglones del dataframe y las etiquetas para las columnas
pd.DataFrame.from_dict(datos, orient='index',
                       columns=['A', 'B', 'C', 'D'])
```


<div>
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
      <th>ren_1</th>
      <td>3</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>ren_2</th>
      <td>a</td>
      <td>b</td>
      <td>c</td>
      <td>d</td>
    </tr>
  </tbody>
</table>
</div>


### Archivos JSON

```python
import json

# Se importa un archivo json que contiene datos de un escuadrón de heroes, con sus características y sus integrantes
with open('data/ejemplo_JSON.json') as f:
  datos = json.load(f)

print(datos)
```

    {'squadName': 'Super hero squad', 'homeTown': 'Metro City', 'formed': 2016, 'secretBase': 'Super tower', 'active': True, 'members': [{'name': 'Molecule Man', 'age': 29, 'secretIdentity': 'Dan Jukes', 'powers': ['Radiation resistance', 'Turning tiny', 'Radiation blast']}, {'name': 'Madame Uppercut', 'age': 39, 'secretIdentity': 'Jane Wilson', 'powers': ['Million tonne punch', 'Damage resistance', 'Superhuman reflexes']}, {'name': 'Eternal Flame', 'age': 1000000, 'secretIdentity': 'Unknown', 'powers': ['Immortality', 'Heat Immunity', 'Inferno', 'Teleportation', 'Interdimensional travel']}]}



```python
# Se muestran los miembros en un dataframe
dframe = DataFrame(datos['members'])
dframe
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>age</th>
      <th>secretIdentity</th>
      <th>powers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Molecule Man</td>
      <td>29</td>
      <td>Dan Jukes</td>
      <td>[Radiation resistance, Turning tiny, Radiation...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Madame Uppercut</td>
      <td>39</td>
      <td>Jane Wilson</td>
      <td>[Million tonne punch, Damage resistance, Super...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Eternal Flame</td>
      <td>1000000</td>
      <td>Unknown</td>
      <td>[Immortality, Heat Immunity, Inferno, Teleport...</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Se importa un archivo json que contiene datos de clientes y sus características
with open('data/data.json') as f:
  datos = json.load(f)
print(datos)
```

    {'clients': [{'first_name': 'Sigrid', 'last_name': 'Mannock', 'age': 27, 'amount': 7.17}, {'first_name': 'Joe', 'last_name': 'Hinners', 'age': 31, 'amount': [1.9, 5.5]}, {'first_name': 'Theodoric', 'last_name': 'Rivers', 'age': 36, 'amount': 1.11}]}



```python
# Se muestran los clientes en un dataframe
dframe = DataFrame(datos['clients'])
dframe
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>first_name</th>
      <th>last_name</th>
      <th>age</th>
      <th>amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sigrid</td>
      <td>Mannock</td>
      <td>27</td>
      <td>7.17</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Joe</td>
      <td>Hinners</td>
      <td>31</td>
      <td>[1.9, 5.5]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Theodoric</td>
      <td>Rivers</td>
      <td>36</td>
      <td>1.11</td>
    </tr>
  </tbody>
</table>
</div>



### API en formato JSON


```python
# Instalar la libreria request con la instrucción conda install requests
import requests

# Se importan los datos a partir de la API de geolocalización de IPs
resp = requests.get('http://ip-api.com/json/208.80.152.201')
dict_train = json.loads(resp.content)
dict_train
```




    {'status': 'success',
     'country': 'United States',
     'countryCode': 'US',
     'region': 'TX',
     'regionName': 'Texas',
     'city': 'Dallas',
     'zip': '75270',
     'lat': 32.7767,
     'lon': -96.797,
     'timezone': 'America/Chicago',
     'isp': 'Wikimedia Foundation Inc.',
     'org': 'Wikimedia Foundation Inc',
     'as': 'AS14907 Wikimedia Foundation Inc.',
     'query': '208.80.152.201'}




```python
# Se convierte el diccionario en un dataframe
train = pd.DataFrame.from_dict(dict_train, orient='index')
train.reset_index(level=0, inplace=True)
train
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>status</td>
      <td>success</td>
    </tr>
    <tr>
      <th>1</th>
      <td>country</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>2</th>
      <td>countryCode</td>
      <td>US</td>
    </tr>
    <tr>
      <th>3</th>
      <td>region</td>
      <td>TX</td>
    </tr>
    <tr>
      <th>4</th>
      <td>regionName</td>
      <td>Texas</td>
    </tr>
    <tr>
      <th>5</th>
      <td>city</td>
      <td>Dallas</td>
    </tr>
    <tr>
      <th>6</th>
      <td>zip</td>
      <td>75270</td>
    </tr>
    <tr>
      <th>7</th>
      <td>lat</td>
      <td>32.7767</td>
    </tr>
    <tr>
      <th>8</th>
      <td>lon</td>
      <td>-96.797</td>
    </tr>
    <tr>
      <th>9</th>
      <td>timezone</td>
      <td>America/Chicago</td>
    </tr>
    <tr>
      <th>10</th>
      <td>isp</td>
      <td>Wikimedia Foundation Inc.</td>
    </tr>
    <tr>
      <th>11</th>
      <td>org</td>
      <td>Wikimedia Foundation Inc</td>
    </tr>
    <tr>
      <th>12</th>
      <td>as</td>
      <td>AS14907 Wikimedia Foundation Inc.</td>
    </tr>
    <tr>
      <th>13</th>
      <td>query</td>
      <td>208.80.152.201</td>
    </tr>
  </tbody>
</table>
</div>



## Exportar datos en formato JSON


```python
# Se genera un diccionario con datos de clientes
datos = {}
datos['clients'] = []
datos['clients'].append({
     'first_name': 'Sigrid',
     'last_name': 'Mannock',
     'age': 27,
     'amount': 7.17})
datos['clients'].append({
     'first_name': 'Joe',
     'last_name': 'Hinners',
     'age': 31,
     'amount': [1.90, 5.50]})
datos['clients'].append({
     'first_name': 'Theodoric',
     'last_name': 'Rivers',
     'age': 36,
     'amount': 1.11})

# Se creaa el archivo JSON con el diccionario anterior
with open('data/data.json', 'w') as archivo:
    json.dump(datos, archivo, indent=4)
```

## Importar datos en formato HTML


```python
# Se requiere instalar la librería html5lib con la instrucción "conda install html5lib", "conda install lxml"
from pandas import read_html
import lxml
import  html5lib

# Se toma una url para la lista de los bancos de EEUU que están en quiebra
url = 'http://www.fdic.gov/bank/individual/failed/banklist.html'
```


```python
lista = pd.io.html.read_html(url)
lista
```




    [                             Bank Name           City  ST   CERT  \
     0                 The First State Bank  Barboursville  WV  14361   
     1                   Ericson State Bank        Ericson  NE  18265   
     2     City National Bank of New Jersey         Newark  NJ  21111   
     3                        Resolute Bank         Maumee  OH  58317   
     4                Louisa Community Bank         Louisa  KY  58112   
     ..                                 ...            ...  ..    ...   
     556                 Superior Bank, FSB       Hinsdale  IL  32646   
     557                Malta National Bank          Malta  OH   6629   
     558    First Alliance Bank & Trust Co.     Manchester  NH  34264   
     559  National State Bank of Metropolis     Metropolis  IL   3815   
     560                   Bank of Honolulu       Honolulu  HI  21029   

                        Acquiring Institution       Closing Date  
     0                         MVB Bank, Inc.      April 3, 2020  
     1             Farmers and Merchants Bank  February 14, 2020  
     2                        Industrial Bank   November 1, 2019  
     3                     Buckeye State Bank   October 25, 2019  
     4      Kentucky Farmers Bank Corporation   October 25, 2019  
     ..                                   ...                ...  
     556                Superior Federal, FSB      July 27, 2001  
     557                    North Valley Bank        May 3, 2001  
     558  Southern New Hampshire Bank & Trust   February 2, 2001  
     559              Banterra Bank of Marion  December 14, 2000  
     560                   Bank of the Orient   October 13, 2000  

     [561 rows x 6 columns]]




```python
# Tomar el primer elemento de la lista de la base de datos y configurarlo como un Dataframe
dframe = lista[0]
dframe
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bank Name</th>
      <th>City</th>
      <th>ST</th>
      <th>CERT</th>
      <th>Acquiring Institution</th>
      <th>Closing Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>The First State Bank</td>
      <td>Barboursville</td>
      <td>WV</td>
      <td>14361</td>
      <td>MVB Bank, Inc.</td>
      <td>April 3, 2020</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Ericson State Bank</td>
      <td>Ericson</td>
      <td>NE</td>
      <td>18265</td>
      <td>Farmers and Merchants Bank</td>
      <td>February 14, 2020</td>
    </tr>
    <tr>
      <th>2</th>
      <td>City National Bank of New Jersey</td>
      <td>Newark</td>
      <td>NJ</td>
      <td>21111</td>
      <td>Industrial Bank</td>
      <td>November 1, 2019</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Resolute Bank</td>
      <td>Maumee</td>
      <td>OH</td>
      <td>58317</td>
      <td>Buckeye State Bank</td>
      <td>October 25, 2019</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Louisa Community Bank</td>
      <td>Louisa</td>
      <td>KY</td>
      <td>58112</td>
      <td>Kentucky Farmers Bank Corporation</td>
      <td>October 25, 2019</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>556</th>
      <td>Superior Bank, FSB</td>
      <td>Hinsdale</td>
      <td>IL</td>
      <td>32646</td>
      <td>Superior Federal, FSB</td>
      <td>July 27, 2001</td>
    </tr>
    <tr>
      <th>557</th>
      <td>Malta National Bank</td>
      <td>Malta</td>
      <td>OH</td>
      <td>6629</td>
      <td>North Valley Bank</td>
      <td>May 3, 2001</td>
    </tr>
    <tr>
      <th>558</th>
      <td>First Alliance Bank &amp; Trust Co.</td>
      <td>Manchester</td>
      <td>NH</td>
      <td>34264</td>
      <td>Southern New Hampshire Bank &amp; Trust</td>
      <td>February 2, 2001</td>
    </tr>
    <tr>
      <th>559</th>
      <td>National State Bank of Metropolis</td>
      <td>Metropolis</td>
      <td>IL</td>
      <td>3815</td>
      <td>Banterra Bank of Marion</td>
      <td>December 14, 2000</td>
    </tr>
    <tr>
      <th>560</th>
      <td>Bank of Honolulu</td>
      <td>Honolulu</td>
      <td>HI</td>
      <td>21029</td>
      <td>Bank of the Orient</td>
      <td>October 13, 2000</td>
    </tr>
  </tbody>
</table>
<p>561 rows × 6 columns</p>
</div>




```python
# Se despliegan los valores de las columnas
dframe.columns.values
```




    array(['Bank Name', 'City', 'ST', 'CERT', 'Acquiring Institution',
           'Closing Date'], dtype=object)



## Importar datos desde archivos de Excel xlsx

Se requiere importar las librerias:
- `xlrd` con la instrucción `conda install xlrd`
- `openpyxl` con la instrucción `conda install openpyxl`


```python
import xlrd
import openpyxl
```


```python
# Abrir el archivo de Excel como objeto
archivo = pd.ExcelFile('data/samplexls.xlsx')
```


```python
# Seleccionar la primer hoja del archivo de Excel y configurarla como DataFrame
dframe = archivo.parse('Data')
dframe
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Index</th>
      <th>Period</th>
      <th>Totals</th>
      <th>NumTicket</th>
      <th>Sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>2010/01</td>
      <td>35998.26</td>
      <td>0</td>
      <td>24602.7</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2010/02</td>
      <td>45663.64</td>
      <td>0</td>
      <td>29663.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>2010/03</td>
      <td>30316.40</td>
      <td>0</td>
      <td>30316.4</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>2010/04</td>
      <td>47283.78</td>
      <td>0</td>
      <td>29750.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2010/05</td>
      <td>36726.32</td>
      <td>0</td>
      <td>22128.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Otra forma de leer archivos de Excel
df=pd.read_excel('data/samplexls.xlsx', sheet_name='Data')
print(df.head())
```

       Index   Period    Totals  NumTicket    Sales
    0      0  2010/01  35998.26          0  24602.7
    1      1  2010/02  45663.64          0  29663.0
    2      2  2010/03  30316.40          0  30316.4
    3      3  2010/04  47283.78          0  29750.0
    4      4  2010/05  36726.32          0  22128.0


## Exportar datos a archivos de Excel


```python
df[0:2].to_excel('data/sampleexport.xlsx')
```


 [**Siguiente Lección**](Lecci%C3%B3n%2007%20-%20Importar_Exportar_Datos_SQL.md)    
