# Ejercicio SF Salaries

¡Bienvenido a un ejercicio rápido para que practiques tus habilidades de pandas! Utilizaremos el [Conjunto de datos de salarios SF] (https://www.kaggle.com/kaggle/sf-salaries) de Kaggle! Simplemente siga y complete las tareas descritas en negrita a continuación. Las tareas serán cada vez más difíciles a medida que avanza.

** Import pandas as pd.**


```python

```

** Cargue el archivo Salaries.csv en un dataframe llamado "sal".**


```python

```

** Verifique el encabezado del DataFrame. **


```python

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
      <th>Id</th>
      <th>EmployeeName</th>
      <th>JobTitle</th>
      <th>BasePay</th>
      <th>OvertimePay</th>
      <th>OtherPay</th>
      <th>Benefits</th>
      <th>TotalPay</th>
      <th>TotalPayBenefits</th>
      <th>Year</th>
      <th>Notes</th>
      <th>Agency</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>NATHANIEL FORD</td>
      <td>GENERAL MANAGER-METROPOLITAN TRANSIT AUTHORITY</td>
      <td>167411.18</td>
      <td>0.00</td>
      <td>400184.25</td>
      <td>NaN</td>
      <td>567595.43</td>
      <td>567595.43</td>
      <td>2011</td>
      <td>NaN</td>
      <td>San Francisco</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>GARY JIMENEZ</td>
      <td>CAPTAIN III (POLICE DEPARTMENT)</td>
      <td>155966.02</td>
      <td>245131.88</td>
      <td>137811.38</td>
      <td>NaN</td>
      <td>538909.28</td>
      <td>538909.28</td>
      <td>2011</td>
      <td>NaN</td>
      <td>San Francisco</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>ALBERT PARDINI</td>
      <td>CAPTAIN III (POLICE DEPARTMENT)</td>
      <td>212739.13</td>
      <td>106088.18</td>
      <td>16452.60</td>
      <td>NaN</td>
      <td>335279.91</td>
      <td>335279.91</td>
      <td>2011</td>
      <td>NaN</td>
      <td>San Francisco</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>CHRISTOPHER CHONG</td>
      <td>WIRE ROPE CABLE MAINTENANCE MECHANIC</td>
      <td>77916.00</td>
      <td>56120.71</td>
      <td>198306.90</td>
      <td>NaN</td>
      <td>332343.61</td>
      <td>332343.61</td>
      <td>2011</td>
      <td>NaN</td>
      <td>San Francisco</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>PATRICK GARDNER</td>
      <td>DEPUTY CHIEF OF DEPARTMENT,(FIRE DEPARTMENT)</td>
      <td>134401.60</td>
      <td>9737.00</td>
      <td>182234.59</td>
      <td>NaN</td>
      <td>326373.19</td>
      <td>326373.19</td>
      <td>2011</td>
      <td>NaN</td>
      <td>San Francisco</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



** Use el método .info () para averiguar cuántas entradas hay. **


```python

```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 148654 entries, 0 to 148653
    Data columns (total 13 columns):
     #   Column            Non-Null Count   Dtype  
    ---  ------            --------------   -----  
     0   Id                148654 non-null  int64  
     1   EmployeeName      148654 non-null  object 
     2   JobTitle          148654 non-null  object 
     3   BasePay           148045 non-null  float64
     4   OvertimePay       148650 non-null  float64
     5   OtherPay          148650 non-null  float64
     6   Benefits          112491 non-null  float64
     7   TotalPay          148654 non-null  float64
     8   TotalPayBenefits  148654 non-null  float64
     9   Year              148654 non-null  int64  
     10  Notes             0 non-null       float64
     11  Agency            148654 non-null  object 
     12  Status            0 non-null       float64
    dtypes: float64(8), int64(2), object(3)
    memory usage: 14.7+ MB
    

** ¿Cuál es el promedio de BasePay? **


```python

```




    66325.4488404877



** ¿Cuál es la mayor cantidad de OvertimePay en el conjunto de datos? **


```python

```




    245131.88



** ¿Cuál es el título del trabajo de JOSEPH DRISCOLL? Nota: use mayúsculas, de lo contrario, puede obtener una respuesta que no coincide (también hay una minúscula Joseph Driscoll). **


```python

```




    24    CAPTAIN, FIRE SUPPRESSION
    Name: JobTitle, dtype: object



** ¿Cuánto gana JOSEPH DRISCOLL (incluidos los beneficios)? **


```python

```




    24    270324.91
    Name: TotalPayBenefits, dtype: float64



** ¿Cuál es el nombre de la persona mejor pagada (incluidos los beneficios)? **


```python

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
      <th>Id</th>
      <th>EmployeeName</th>
      <th>JobTitle</th>
      <th>BasePay</th>
      <th>OvertimePay</th>
      <th>OtherPay</th>
      <th>Benefits</th>
      <th>TotalPay</th>
      <th>TotalPayBenefits</th>
      <th>Year</th>
      <th>Notes</th>
      <th>Agency</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>NATHANIEL FORD</td>
      <td>GENERAL MANAGER-METROPOLITAN TRANSIT AUTHORITY</td>
      <td>167411.18</td>
      <td>0.0</td>
      <td>400184.25</td>
      <td>NaN</td>
      <td>567595.43</td>
      <td>567595.43</td>
      <td>2011</td>
      <td>NaN</td>
      <td>San Francisco</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



** ¿Cuál es el nombre de la persona peor pagada (incluidos los beneficios)? ¿Notas algo extraño sobre cuánto le pagan a él o ella? **


```python


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
      <th>Id</th>
      <th>EmployeeName</th>
      <th>JobTitle</th>
      <th>BasePay</th>
      <th>OvertimePay</th>
      <th>OtherPay</th>
      <th>Benefits</th>
      <th>TotalPay</th>
      <th>TotalPayBenefits</th>
      <th>Year</th>
      <th>Notes</th>
      <th>Agency</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>148653</th>
      <td>148654</td>
      <td>Joe Lopez</td>
      <td>Counselor, Log Cabin Ranch</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>-618.13</td>
      <td>0.0</td>
      <td>-618.13</td>
      <td>-618.13</td>
      <td>2014</td>
      <td>NaN</td>
      <td>San Francisco</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



** ¿Cuál fue el promedio (promedio) de BasePay de todos los empleados por año? (2011-2014)? **


```python

```




    Year
    2011    63595.956517
    2012    65436.406857
    2013    69630.030216
    2014    66564.421924
    Name: BasePay, dtype: float64



** ¿Cuántos títulos de trabajo únicos hay? **


```python

```




    2159



** ¿Cuáles son los 5 trabajos más comunes? **


```python

```




    Transit Operator                7036
    Special Nurse                   4389
    Registered Nurse                3736
    Public Svc Aide-Public Works    2518
    Police Officer 3                2421
    Name: JobTitle, dtype: int64



** ¿Cuántos títulos laborales representaron una sola persona en 2013? (por ejemplo, Títulos de trabajo con una sola aparición en 2013?) **


```python

```




    202



** ¿Cuántas personas tienen la palabra Jefe en el título de su trabajo? (Esto es bastante complicado) **


```python

```


```python

```




    627



** Bonificación: ¿Existe una correlación entre la longitud de la cadena del Título del trabajo y el Salario? **


```python

```


```python

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
      <th>title_len</th>
      <th>TotalPayBenefits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>title_len</th>
      <td>1.000000</td>
      <td>-0.036878</td>
    </tr>
    <tr>
      <th>TotalPayBenefits</th>
      <td>-0.036878</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



# Buen trabajo!

 
 [**Ejercicios Resueltos**](Pandas%20Ejercicio%20-%20Soluci%C3%B3n.md)    



