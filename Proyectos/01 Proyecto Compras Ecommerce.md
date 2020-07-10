# Ejercicio de compras ecommerce

¡En este ejercicio se te darán algunos datos falsos, sobre algunas compras realizadas a través de Amazon! Simplemente sigue las instrucciones y haz todo lo posible para responder las preguntas y completar las tareas. No dudes en consultar las soluciones. La mayoría de las tareas se pueden resolver de diferentes maneras. En su mayor parte, las preguntas se vuelven cada vez más difíciles.

Por favor, disculpa cualquier cosa que no tenga sentido en el "mundo real" en el conjunto de datos; todos los datos son falsos e inventados.

También ten en cuenta que todas estas preguntas se pueden responder con una sola línea de código.
____
** Importa pandas y lee el archivo csv de Compras de ecommerce. Configúralo en un dataframe llamado ecom. **


```python

```


```python

```

** Revisa los primeros 5 datos del dataframe**


```python

```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Address</th>
      <th>Lot</th>
      <th>AM or PM</th>
      <th>Browser Info</th>
      <th>Company</th>
      <th>Credit Card</th>
      <th>CC Exp Date</th>
      <th>CC Security Code</th>
      <th>CC Provider</th>
      <th>Email</th>
      <th>Job</th>
      <th>IP Address</th>
      <th>Language</th>
      <th>Purchase Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16629 Pace Camp Apt. 448\nAlexisborough, NE 77...</td>
      <td>46 in</td>
      <td>PM</td>
      <td>Opera/9.56.(X11; Linux x86_64; sl-SI) Presto/2...</td>
      <td>Martinez-Herman</td>
      <td>6011929061123406</td>
      <td>02/20</td>
      <td>900</td>
      <td>JCB 16 digit</td>
      <td>pdunlap@yahoo.com</td>
      <td>Scientist, product/process development</td>
      <td>149.146.147.205</td>
      <td>el</td>
      <td>98.14</td>
    </tr>
    <tr>
      <th>1</th>
      <td>9374 Jasmine Spurs Suite 508\nSouth John, TN 8...</td>
      <td>28 rn</td>
      <td>PM</td>
      <td>Opera/8.93.(Windows 98; Win 9x 4.90; en-US) Pr...</td>
      <td>Fletcher, Richards and Whitaker</td>
      <td>3337758169645356</td>
      <td>11/18</td>
      <td>561</td>
      <td>Mastercard</td>
      <td>anthony41@reed.com</td>
      <td>Drilling engineer</td>
      <td>15.160.41.51</td>
      <td>fr</td>
      <td>70.73</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Unit 0065 Box 5052\nDPO AP 27450</td>
      <td>94 vE</td>
      <td>PM</td>
      <td>Mozilla/5.0 (compatible; MSIE 9.0; Windows NT ...</td>
      <td>Simpson, Williams and Pham</td>
      <td>675957666125</td>
      <td>08/19</td>
      <td>699</td>
      <td>JCB 16 digit</td>
      <td>amymiller@morales-harrison.com</td>
      <td>Customer service manager</td>
      <td>132.207.160.22</td>
      <td>de</td>
      <td>0.95</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7780 Julia Fords\nNew Stacy, WA 45798</td>
      <td>36 vm</td>
      <td>PM</td>
      <td>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_8_0 ...</td>
      <td>Williams, Marshall and Buchanan</td>
      <td>6011578504430710</td>
      <td>02/24</td>
      <td>384</td>
      <td>Discover</td>
      <td>brent16@olson-robinson.info</td>
      <td>Drilling engineer</td>
      <td>30.250.74.19</td>
      <td>es</td>
      <td>78.04</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23012 Munoz Drive Suite 337\nNew Cynthia, TX 5...</td>
      <td>20 IE</td>
      <td>AM</td>
      <td>Opera/9.58.(X11; Linux x86_64; it-IT) Presto/2...</td>
      <td>Brown, Watson and Andrews</td>
      <td>6011456623207998</td>
      <td>10/25</td>
      <td>678</td>
      <td>Diners Club / Carte Blanche</td>
      <td>christopherwright@gmail.com</td>
      <td>Fine artist</td>
      <td>24.140.33.94</td>
      <td>es</td>
      <td>77.82</td>
    </tr>
  </tbody>
</table>
</div>



** ¿Cuántas filas y columnas hay? **


```python

```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 10000 entries, 0 to 9999
    Data columns (total 14 columns):
     #   Column            Non-Null Count  Dtype  
    ---  ------            --------------  -----  
     0   Address           10000 non-null  object
     1   Lot               10000 non-null  object
     2   AM or PM          10000 non-null  object
     3   Browser Info      10000 non-null  object
     4   Company           10000 non-null  object
     5   Credit Card       10000 non-null  int64  
     6   CC Exp Date       10000 non-null  object
     7   CC Security Code  10000 non-null  int64  
     8   CC Provider       10000 non-null  object
     9   Email             10000 non-null  object
     10  Job               10000 non-null  object
     11  IP Address        10000 non-null  object
     12  Language          10000 non-null  object
     13  Purchase Price    10000 non-null  float64
    dtypes: float64(1), int64(2), object(11)
    memory usage: 1.1+ MB


** ¿Cuál es el precio de compra (Purchase Price) promedio? **


```python

```




    50.347302



** ¿Cuáles fueron los precios de compra (Purchase Price) más altos y más bajos? **


```python

```




    99.99




```python

```




    0.0



** ¿Cuántas personas tienen el inglés 'en' como idioma de elección (Language) en el sitio web? **


```python

```




    Address             1098
    Lot                 1098
    AM or PM            1098
    Browser Info        1098
    Company             1098
    Credit Card         1098
    CC Exp Date         1098
    CC Security Code    1098
    CC Provider         1098
    Email               1098
    Job                 1098
    IP Address          1098
    Language            1098
    Purchase Price      1098
    dtype: int64



** ¿Cuántas personas tienen el título (Job) de "Abogado" (Lawyer)? **



```python

```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 30 entries, 470 to 9979
    Data columns (total 14 columns):
     #   Column            Non-Null Count  Dtype  
    ---  ------            --------------  -----  
     0   Address           30 non-null     object
     1   Lot               30 non-null     object
     2   AM or PM          30 non-null     object
     3   Browser Info      30 non-null     object
     4   Company           30 non-null     object
     5   Credit Card       30 non-null     int64  
     6   CC Exp Date       30 non-null     object
     7   CC Security Code  30 non-null     int64  
     8   CC Provider       30 non-null     object
     9   Email             30 non-null     object
     10  Job               30 non-null     object
     11  IP Address        30 non-null     object
     12  Language          30 non-null     object
     13  Purchase Price    30 non-null     float64
    dtypes: float64(1), int64(2), object(11)
    memory usage: 3.5+ KB


** ¿Cuántas personas hicieron la compra durante la mañana y cuántas personas hicieron la compra durante la tarde (AM or PM)? **

**(Pista: Revisa [value_counts()](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.value_counts.html) ) **


```python

```




    PM    5068
    AM    4932
    Name: AM or PM, dtype: int64



** ¿Cuáles son los 5 títulos de trabajo (Job) más comunes? **


```python

```




    Interior and spatial designer        31
    Lawyer                               30
    Social researcher                    28
    Research officer, political party    27
    Designer, jewellery                  27
    Name: Job, dtype: int64



** Alguien realizó una compra que provino del lote (Lot): "90 WT", ¿cuál fue el precio de compra (Purchase Price) de esta transacción? **


```python

```




    513    75.1
    Name: Purchase Price, dtype: float64



** ¿Cuál es el correo electrónico (Email) de la persona con el siguiente número de tarjeta de crédito (Credit Card): 4926535242672853 **


```python

```




    1234    bondellen@williams-garza.com
    Name: Email, dtype: object



** ¿Cuántas personas tienen American Express como su proveedor de tarjeta de crédito (CC Provider) * e * hicieron una compra (Purchase Price) mayor a $ 95? **


```python

```




    Address             39
    Lot                 39
    AM or PM            39
    Browser Info        39
    Company             39
    Credit Card         39
    CC Exp Date         39
    CC Security Code    39
    CC Provider         39
    Email               39
    Job                 39
    IP Address          39
    Language            39
    Purchase Price      39
    dtype: int64



** Difícil: ¿Cuántas personas tienen una tarjeta de crédito que caduca en 2025 (CC Exp Date)? **


```python

```




    1033




** Difícil: ¿Cuáles son los 5 principales proveedores / hosts de correo electrónico más populares (por ejemplo, gmail.com, yahoo.com, etc.) **


```python

```




    hotmail.com     1638
    yahoo.com       1616
    gmail.com       1605
    smith.com         42
    williams.com      37
    Name: Email, dtype: int64



# ¡Excelente trabajo!

[**Proyecto Solución**](01%20Proyecto%20Compras%20Ecommerce%20-%20Solucion.ipynb)  
