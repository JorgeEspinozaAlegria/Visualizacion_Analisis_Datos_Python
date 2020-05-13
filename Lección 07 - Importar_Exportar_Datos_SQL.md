# Importar y exportar datos desde una DB


```python
# Cargamos las librerias
import numpy as np
import pandas as pd
from pandas import Series,DataFrame
import pymysql
```

## Abrir la conección a la base de datos


```python
def connection():
    try:
        conn = pymysql.connect(host='JESPINOZAG3',
                               port=3306,
                               user='Axity',
                               password='Axity2019',
                               db='sakila')
    finally:
        print("Conexion Exitosa")
    return conn   
```

## Selección de datos 


```python
conn = connection()
    
sql = "select first_name,last_name,email,address_id from customer"
        
titles='Nombre Apellido EMAIL ADDRESS_ID'.split()
        
df=pd.read_sql(sql,con=conn)
        
df.columns = titles
           
conn.close()
df.head()
```

    Conexion Exitosa
    




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
      <th>Nombre</th>
      <th>Apellido</th>
      <th>EMAIL</th>
      <th>ADDRESS_ID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>MARY</td>
      <td>SMITH</td>
      <td>MARY.SMITH@sakilacustomer.org</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>PATRICIA</td>
      <td>JOHNSON</td>
      <td>PATRICIA.JOHNSON@sakilacustomer.org</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>LINDA</td>
      <td>WILLIAMS</td>
      <td>LINDA.WILLIAMS@sakilacustomer.org</td>
      <td>7</td>
    </tr>
    <tr>
      <th>3</th>
      <td>BARBARA</td>
      <td>JONES</td>
      <td>BARBARA.JONES@sakilacustomer.org</td>
      <td>8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ELIZABETH</td>
      <td>BROWN</td>
      <td>ELIZABETH.BROWN@sakilacustomer.org</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
conn = connection()
sql = "select concat(a.first_name ,' ', a.last_name) as name,a.email,b.address from customer a join address b on a.address_id = b.address_id"
titles='Nombre EMAIL ADDRESS_ID'.split()
df=pd.read_sql(sql,con=conn)
df.columns = titles
            
conn.close()
df.head()
```

    Conexion Exitosa
    




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
      <th>Nombre</th>
      <th>EMAIL</th>
      <th>ADDRESS_ID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>MARY SMITH</td>
      <td>MARY.SMITH@sakilacustomer.org</td>
      <td>1913 Hanoi Way</td>
    </tr>
    <tr>
      <th>1</th>
      <td>PATRICIA JOHNSON</td>
      <td>PATRICIA.JOHNSON@sakilacustomer.org</td>
      <td>1121 Loja Avenue</td>
    </tr>
    <tr>
      <th>2</th>
      <td>LINDA WILLIAMS</td>
      <td>LINDA.WILLIAMS@sakilacustomer.org</td>
      <td>692 Joliet Street</td>
    </tr>
    <tr>
      <th>3</th>
      <td>BARBARA JONES</td>
      <td>BARBARA.JONES@sakilacustomer.org</td>
      <td>1566 Inegl Manor</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ELIZABETH BROWN</td>
      <td>ELIZABETH.BROWN@sakilacustomer.org</td>
      <td>53 Idfu Parkway</td>
    </tr>
  </tbody>
</table>
</div>



## Join entre tablas


```python
conn = connection()
nom = 'JA'

sql = "select concat(a.first_name ,' ', a.last_name) as name,a.email,b.address from customer a join address b on a.address_id = b.address_id where first_name like '"+ nom +"%'"
titles='Nombre EMAIL ADDRESS_ID'.split()
df=pd.read_sql(sql,con=conn)
df.columns = titles
            
conn.close()
df.head()
```

    Conexion Exitosa
    




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
      <th>Nombre</th>
      <th>EMAIL</th>
      <th>ADDRESS_ID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>JANET PHILLIPS</td>
      <td>JANET.PHILLIPS@sakilacustomer.org</td>
      <td>1718 Valencia Street</td>
    </tr>
    <tr>
      <th>1</th>
      <td>JANICE WARD</td>
      <td>JANICE.WARD@sakilacustomer.org</td>
      <td>1150 Kimchon Manor</td>
    </tr>
    <tr>
      <th>2</th>
      <td>JANE BENNETT</td>
      <td>JANE.BENNETT@sakilacustomer.org</td>
      <td>1692 Ede Loop</td>
    </tr>
    <tr>
      <th>3</th>
      <td>JACQUELINE LONG</td>
      <td>JACQUELINE.LONG@sakilacustomer.org</td>
      <td>870 Ashqelon Loop</td>
    </tr>
    <tr>
      <th>4</th>
      <td>JAMIE RICE</td>
      <td>JAMIE.RICE@sakilacustomer.org</td>
      <td>879 Newcastle Way</td>
    </tr>
  </tbody>
</table>
</div>



  
 [**Siguiente Lección**](Lecci%C3%B3n%2008%20-%20Procesamiento_Datos.md)    

 

### Reference:

- https://pypi.org/project/PyMySQL/
- http://pymysql.readthedocs.io/en/latest/user/examples.html
