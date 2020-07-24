# Importar y exportar datos desde una DB


```python
# Cargar las librerias
import numpy as np
import pandas as pd
from pandas import Series,DataFrame
import pymysql
```

## Abrir la conexión a la base de datos


```python
def conexion():
    try:
        conex = pymysql.connect(host='JESPINOZAG3',
                               port=3306,
                               user='Axity',
                               password='Axity2019',
                               db='sakila')
    finally:
        print("Conexion Exitosa")
    return conex   
```

## Selección de datos

La base de datos contiene datos de clientes, entre ellos: nombre, apellido, correo electrónico y el identificador de su dirección.


```python
conex = conexion()

sql = "select first_name,last_name,email,address_id from customer"

titulos = 'Nombre Apellido Email Direccion'.split()

df =pd.read_sql(sql, con=conex)

df.columns = titulos

conex.close()
df.head()
```

    Conexion Exitosa





<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Apellido</th>
      <th>Email</th>
      <th>Direccion</th>
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
# Se importan los datos con una sentencia sql que realiza un join entre dos tablas

conex = conexion()
sql = "select concat(a.first_name ,' ', a.last_name) as name,a.email,b.address from customer a join address b on a.address_id = b.address_id"
titulos = 'Nombre Email Direccion'.split()
df = pd.read_sql(sql, con=conex)
df.columns = titulos

conex.close()
df.head()
```

    Conexion Exitosa





<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Email</th>
      <th>Direccion</th>
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
conex = conexion()
nom = 'JA'

sql = "select concat(a.first_name ,' ', a.last_name) as name,a.email,b.address from customer a join address b on a.address_id = b.address_id where first_name like '"+ nom +"%'"
titulos='Nombre Email Direccion'.split()
df = pd.read_sql(sql, con=conex)
df.columns = titulos

conex.close()
df.head()
```

    Conexion Exitosa





<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Email</th>
      <th>Direccion</th>
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



### Referencias:

- https://pypi.org/project/PyMySQL/
- http://pymysql.readthedocs.io/en/latest/user/examples.html
