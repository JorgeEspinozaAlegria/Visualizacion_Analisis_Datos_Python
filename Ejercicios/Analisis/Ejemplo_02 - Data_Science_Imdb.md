# Ejemplo 2 - Data Science en Internet Movie Database (IMDb)

IMDb es una base de datos en línea que contiene información de películas, programas de televisión, videos caseros, videojuegos y contenido de streaming en línea. Incluye elencos, equipos de producción, biografías personales, resumen de argumentos, trivia, calificaciones y comentarios de fans y críticos

```python
# Importemos las librerías que vamos a utilizar
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

%matplotlib inline
```

## Cargando datos


```python
# Carguemos los datos y visualicemos sus características
df = pd.read_csv('../../data/IMDB.csv', encoding='utf-8')
df.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>color</th>
      <th>director_name</th>
      <th>duration</th>
      <th>gross</th>
      <th>genres</th>
      <th>movie_title</th>
      <th>title_year</th>
      <th>language</th>
      <th>country</th>
      <th>budget</th>
      <th>imdb_score</th>
      <th>actors</th>
      <th>movie_facebook_likes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Color</td>
      <td>Martin Scorsese</td>
      <td>240</td>
      <td>116866727.0</td>
      <td>Biography|Comedy|Crime|Drama</td>
      <td>The Wolf of Wall Street</td>
      <td>2013</td>
      <td>English</td>
      <td>USA</td>
      <td>100000000.0</td>
      <td>8.2</td>
      <td>Leonardo DiCaprio,Matthew McConaughey,Jon Favreau</td>
      <td>138000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Color</td>
      <td>Shane Black</td>
      <td>195</td>
      <td>408992272.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>Iron Man 3</td>
      <td>2013</td>
      <td>English</td>
      <td>USA</td>
      <td>200000000.0</td>
      <td>7.2</td>
      <td>Robert Downey Jr.,Jon Favreau,Don Cheadle</td>
      <td>95000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>color</td>
      <td>Quentin Tarantino</td>
      <td>187</td>
      <td>54116191.0</td>
      <td>Crime|Drama|Mystery|Thriller|Western</td>
      <td>The Hateful Eight</td>
      <td>2015</td>
      <td>English</td>
      <td>USA</td>
      <td>44000000.0</td>
      <td>7.9</td>
      <td>Craig Stark,Jennifer Jason Leigh,Zoë Bell</td>
      <td>114000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Color</td>
      <td>Kenneth Lonergan</td>
      <td>186</td>
      <td>46495.0</td>
      <td>Drama</td>
      <td>Margaret</td>
      <td>2011</td>
      <td>English</td>
      <td>usa</td>
      <td>14000000.0</td>
      <td>6.5</td>
      <td>Matt Damon,Kieran Culkin,John Gallagher Jr.</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Color</td>
      <td>Peter Jackson</td>
      <td>186</td>
      <td>258355354.0</td>
      <td>Adventure|Fantasy</td>
      <td>The Hobbit: The Desolation of Smaug</td>
      <td>2013</td>
      <td>English</td>
      <td>USA</td>
      <td>225000000.0</td>
      <td>7.9</td>
      <td>Aidan Turner,Adam Brown,James Nesbitt</td>
      <td>83000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>duration</th>
      <th>gross</th>
      <th>title_year</th>
      <th>budget</th>
      <th>imdb_score</th>
      <th>movie_facebook_likes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>99.000000</td>
      <td>9.100000e+01</td>
      <td>99.000000</td>
      <td>9.500000e+01</td>
      <td>99.000000</td>
      <td>99.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>155.494949</td>
      <td>1.541914e+08</td>
      <td>1976.444444</td>
      <td>1.048570e+08</td>
      <td>6.892929</td>
      <td>66045.707071</td>
    </tr>
    <tr>
      <th>std</th>
      <td>72.797927</td>
      <td>1.399503e+08</td>
      <td>255.880601</td>
      <td>7.703169e+07</td>
      <td>1.925514</td>
      <td>58108.860365</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-50.000000</td>
      <td>4.122900e+04</td>
      <td>202.000000</td>
      <td>1.735000e+04</td>
      <td>-7.500000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>138.500000</td>
      <td>4.720632e+07</td>
      <td>2012.000000</td>
      <td>4.000000e+07</td>
      <td>6.550000</td>
      <td>25000.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>143.000000</td>
      <td>1.156040e+08</td>
      <td>2013.000000</td>
      <td>8.000000e+07</td>
      <td>7.200000</td>
      <td>54000.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>155.000000</td>
      <td>2.374894e+08</td>
      <td>2014.000000</td>
      <td>1.740000e+08</td>
      <td>7.850000</td>
      <td>85500.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>650.000000</td>
      <td>6.232795e+08</td>
      <td>2016.000000</td>
      <td>2.500000e+08</td>
      <td>8.800000</td>
      <td>349000.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.describe(include=['O'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>color</th>
      <th>director_name</th>
      <th>genres</th>
      <th>movie_title</th>
      <th>language</th>
      <th>country</th>
      <th>actors</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>88</td>
      <td>88</td>
      <td>98</td>
      <td>99</td>
      <td>99</td>
      <td>99</td>
      <td>99</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>3</td>
      <td>63</td>
      <td>56</td>
      <td>91</td>
      <td>1</td>
      <td>12</td>
      <td>88</td>
    </tr>
    <tr>
      <th>top</th>
      <td>Color</td>
      <td>Ridley Scott</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>Ben-Hur</td>
      <td>English</td>
      <td>USA</td>
      <td>Aidan Turner,Adam Brown,James Nesbitt</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>86</td>
      <td>4</td>
      <td>10</td>
      <td>3</td>
      <td>99</td>
      <td>77</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>

El conjunto de datos contiene información de varias películas, cuyas características son:


<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Definición</th>
      <th>Valores</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>color</th>
      <td>Si la película es a color</td>
      <td>Null = No, Color = Si</td>
    </tr>
    <tr>
      <th>director_name</th>
      <td>Nombre del director</td>
      <td></td>
    </tr>
    <tr>
      <th>duration</th>
      <td>Duración en minutos</td>
      <td></td>
    </tr>
    <tr>
      <th>gross</th>
      <td>Ingreso bruto</td>
      <td></td>
    </tr>
    <tr>
      <th>genres</th>
      <td>Géneros de la película</td>
      <td></td>
    </tr>
    <tr>
      <th>movie_title</th>
      <td>Título de la película</td>
      <td></td>
    </tr>
    <tr>
      <th>title_tear</th>
      <td>Año de la película</td>
      <td></td>
    </tr>
    <tr>
      <th>language</th>
      <td>Lenguaje de la película</td>
      <td></td>
    </tr>
    <tr>
      <th>country</th>
      <td>País de la película</td>
      <td></td>
    </tr>
    <tr>
      <th>budget</th>
      <td>Presupuesto de la película</td>
      <td></td>
    </tr>
    <tr>
      <th>imdb_score</th>
      <td>Calificación de la película en IMDb</td>
      <td></td>
    </tr>
    <tr>
      <th>actores</th>
      <td>Lista de los 3 principales actores</td>
      <td></td>
    </tr>
    <tr>
      <th>movie_facebook_likes</th>
      <td>Número de likes en Facebook</td>
      <td></td>
    </tr>
  </tbody>
</table>
</div>


## Limpieza de datos

### Exploración de los datos


```python
# Revisemos si hay datos nulos
df.isnull().values.any()
```




    True




```python
# Revisemos en que columnas hay datos nulos
df.isnull().any()
```




    color                    True
    director_name            True
    duration                False
    gross                    True
    genres                   True
    movie_title             False
    title_year              False
    language                False
    country                 False
    budget                   True
    imdb_score              False
    actors                  False
    movie_facebook_likes    False
    dtype: bool




```python
# Obtengamos el número de datos nulos por columna
df.isnull().sum()
```




    color                   11
    director_name           11
    duration                 0
    gross                    8
    genres                   1
    movie_title              0
    title_year               0
    language                 0
    country                  0
    budget                   4
    imdb_score               0
    actors                   0
    movie_facebook_likes     0
    dtype: int64



### Eliminar columnas irrelevantes


```python
# Eliminemos las columnas cuya información no es relevante para el análisis
df.drop(['color','language'], axis=1, inplace=True)
df.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>director_name</th>
      <th>duration</th>
      <th>gross</th>
      <th>genres</th>
      <th>movie_title</th>
      <th>title_year</th>
      <th>country</th>
      <th>budget</th>
      <th>imdb_score</th>
      <th>actors</th>
      <th>movie_facebook_likes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Martin Scorsese</td>
      <td>240</td>
      <td>116866727.0</td>
      <td>Biography|Comedy|Crime|Drama</td>
      <td>The Wolf of Wall Street</td>
      <td>2013</td>
      <td>USA</td>
      <td>100000000.0</td>
      <td>8.2</td>
      <td>Leonardo DiCaprio,Matthew McConaughey,Jon Favreau</td>
      <td>138000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Shane Black</td>
      <td>195</td>
      <td>408992272.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>Iron Man 3</td>
      <td>2013</td>
      <td>USA</td>
      <td>200000000.0</td>
      <td>7.2</td>
      <td>Robert Downey Jr.,Jon Favreau,Don Cheadle</td>
      <td>95000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Quentin Tarantino</td>
      <td>187</td>
      <td>54116191.0</td>
      <td>Crime|Drama|Mystery|Thriller|Western</td>
      <td>The Hateful Eight</td>
      <td>2015</td>
      <td>USA</td>
      <td>44000000.0</td>
      <td>7.9</td>
      <td>Craig Stark,Jennifer Jason Leigh,Zoë Bell</td>
      <td>114000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Kenneth Lonergan</td>
      <td>186</td>
      <td>46495.0</td>
      <td>Drama</td>
      <td>Margaret</td>
      <td>2011</td>
      <td>usa</td>
      <td>14000000.0</td>
      <td>6.5</td>
      <td>Matt Damon,Kieran Culkin,John Gallagher Jr.</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Peter Jackson</td>
      <td>186</td>
      <td>258355354.0</td>
      <td>Adventure|Fantasy</td>
      <td>The Hobbit: The Desolation of Smaug</td>
      <td>2013</td>
      <td>USA</td>
      <td>225000000.0</td>
      <td>7.9</td>
      <td>Aidan Turner,Adam Brown,James Nesbitt</td>
      <td>83000</td>
    </tr>
  </tbody>
</table>
</div>



### Manejar atributos de texto


```python
# Sustituyamos los datos categóricos nulos
df['director_name'].fillna('', inplace=True)
```

### Manejar atributos numéricos


```python
# Sustituyamos los datos numéricos nulos
df['gross'].fillna(0, inplace=True)
df['budget'].fillna(0, inplace=True)
```

### Unificar nombres de países


```python
# Unifiquemos los nombres de los países, convirtiéndolos a mayusculas y la codificación de USA
df['country']=df['country'].str.upper()
df['country'] = np.where(df['country']=='UNITED STATES','USA', df['country'])
df.head(20)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>director_name</th>
      <th>duration</th>
      <th>gross</th>
      <th>genres</th>
      <th>movie_title</th>
      <th>title_year</th>
      <th>country</th>
      <th>budget</th>
      <th>imdb_score</th>
      <th>actors</th>
      <th>movie_facebook_likes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Martin Scorsese</td>
      <td>240</td>
      <td>116866727.0</td>
      <td>Biography|Comedy|Crime|Drama</td>
      <td>The Wolf of Wall Street</td>
      <td>2013</td>
      <td>USA</td>
      <td>100000000.0</td>
      <td>8.2</td>
      <td>Leonardo DiCaprio,Matthew McConaughey,Jon Favreau</td>
      <td>138000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Shane Black</td>
      <td>195</td>
      <td>408992272.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>Iron Man 3</td>
      <td>2013</td>
      <td>USA</td>
      <td>200000000.0</td>
      <td>7.2</td>
      <td>Robert Downey Jr.,Jon Favreau,Don Cheadle</td>
      <td>95000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Quentin Tarantino</td>
      <td>187</td>
      <td>54116191.0</td>
      <td>Crime|Drama|Mystery|Thriller|Western</td>
      <td>The Hateful Eight</td>
      <td>2015</td>
      <td>USA</td>
      <td>44000000.0</td>
      <td>7.9</td>
      <td>Craig Stark,Jennifer Jason Leigh,Zoë Bell</td>
      <td>114000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Kenneth Lonergan</td>
      <td>186</td>
      <td>46495.0</td>
      <td>Drama</td>
      <td>Margaret</td>
      <td>2011</td>
      <td>USA</td>
      <td>14000000.0</td>
      <td>6.5</td>
      <td>Matt Damon,Kieran Culkin,John Gallagher Jr.</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Peter Jackson</td>
      <td>186</td>
      <td>258355354.0</td>
      <td>Adventure|Fantasy</td>
      <td>The Hobbit: The Desolation of Smaug</td>
      <td>2013</td>
      <td>USA</td>
      <td>225000000.0</td>
      <td>7.9</td>
      <td>Aidan Turner,Adam Brown,James Nesbitt</td>
      <td>83000</td>
    </tr>
    <tr>
      <th>5</th>
      <td></td>
      <td>183</td>
      <td>330249062.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>Batman v Superman: Dawn of Justice</td>
      <td>202</td>
      <td>USA</td>
      <td>250000000.0</td>
      <td>6.9</td>
      <td>Henry Cavill,Lauren Cohan,Alan D. Purwin</td>
      <td>197000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Peter Jackson</td>
      <td>-50</td>
      <td>303001229.0</td>
      <td>Adventure|Fantasy</td>
      <td>The Hobbit: An Unexpected Journey</td>
      <td>2012</td>
      <td>USA</td>
      <td>180000000.0</td>
      <td>7.9</td>
      <td>Aidan Turner,Adam Brown,James Nesbitt</td>
      <td>166000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Edward Hall</td>
      <td>180</td>
      <td>0.0</td>
      <td>Drama|Romance</td>
      <td>Restless</td>
      <td>2012</td>
      <td>UK</td>
      <td>0.0</td>
      <td>7.2</td>
      <td>Rufus Sewell,Hayley Atwell,Charlotte Rampling</td>
      <td>434</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Joss Whedon</td>
      <td>173</td>
      <td>623279547.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>The Avengers</td>
      <td>2012</td>
      <td>USA</td>
      <td>220000000.0</td>
      <td>8.1</td>
      <td>Chris Hemsworth,Robert Downey Jr.,Scarlett Joh...</td>
      <td>123000</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Joss Whedon</td>
      <td>173</td>
      <td>623279547.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>The Avengers</td>
      <td>2012</td>
      <td>USA</td>
      <td>220000000.0</td>
      <td>8.1</td>
      <td>Chris Hemsworth,Robert Downey Jr.,Scarlett Joh...</td>
      <td>123000</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Tom Tykwer</td>
      <td>172</td>
      <td>27098580.0</td>
      <td>Drama|Sci-Fi</td>
      <td>Cloud Atlas</td>
      <td>2012</td>
      <td>GERMANY</td>
      <td>102000000.0</td>
      <td>-7.5</td>
      <td>Tom Hanks,Jim Sturgess,Jim Broadbent</td>
      <td>124000</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Null</td>
      <td>158</td>
      <td>102515793.0</td>
      <td>Crime|Drama|Mystery|Thriller</td>
      <td>The Girl with the Dragon Tattoo</td>
      <td>2011</td>
      <td>USA</td>
      <td>90000000.0</td>
      <td>7.8</td>
      <td>Robin Wright,Goran Visnjic,Joely Richardson</td>
      <td>54000</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Christopher Spencer</td>
      <td>170</td>
      <td>59696176.0</td>
      <td>NaN</td>
      <td>Son of God</td>
      <td>2014</td>
      <td>USA</td>
      <td>22000000.0</td>
      <td>5.6</td>
      <td>Roma Downey,Amber Rose Revah,Darwin Shaw</td>
      <td>15000</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Christopher Nolan</td>
      <td>169</td>
      <td>187991439.0</td>
      <td>Adventure|Drama|Sci-Fi</td>
      <td>Interstellar</td>
      <td>2014</td>
      <td>USA</td>
      <td>165000000.0</td>
      <td>8.6</td>
      <td>Matthew McConaughey,Anne Hathaway,Mackenzie Foy</td>
      <td>349000</td>
    </tr>
    <tr>
      <th>14</th>
      <td>F. Gary Gray</td>
      <td>167</td>
      <td>161029270.0</td>
      <td>Biography|Crime|Drama|History|Music</td>
      <td>Straight Outta Compton</td>
      <td>2015</td>
      <td>USA</td>
      <td>28000000.0</td>
      <td>7.9</td>
      <td>Aldis Hodge,Neil Brown Jr.,R. Marcos Taylor</td>
      <td>76000</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Richard Linklater</td>
      <td>165</td>
      <td>25359200.0</td>
      <td>Drama</td>
      <td>Boyhood</td>
      <td>2014</td>
      <td>USA</td>
      <td>4000000.0</td>
      <td>8.0</td>
      <td>Ellar Coltrane,Lorelei Linklater,Libby Villari</td>
      <td>92000</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Quentin Tarantino</td>
      <td>580</td>
      <td>162804648.0</td>
      <td>Drama|Western</td>
      <td>Django Unchained</td>
      <td>2012</td>
      <td>USA</td>
      <td>100000000.0</td>
      <td>8.5</td>
      <td>Leonardo DiCaprio,Christoph Waltz,Ato Essandoh</td>
      <td>199000</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Michael Bay</td>
      <td>165</td>
      <td>245428137.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>Transformers: Age of Extinction</td>
      <td>2014</td>
      <td>USA</td>
      <td>210000000.0</td>
      <td>5.7</td>
      <td>Bingbing Li,Sophia Myles,Kelsey Grammer</td>
      <td>56000</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Christopher Nolan</td>
      <td>164</td>
      <td>448130642.0</td>
      <td>Action|Thriller</td>
      <td>The Dark Knight Rises</td>
      <td>2012</td>
      <td>USA</td>
      <td>250000000.0</td>
      <td>8.5</td>
      <td>Tom Hardy,Christian Bale,Joseph Gordon-Levitt</td>
      <td>164000</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Peter Jackson</td>
      <td>164</td>
      <td>255108370.0</td>
      <td>Adventure|Fantasy</td>
      <td>The Hobbit: The Battle of the Five Armies</td>
      <td>2014</td>
      <td>NEW ZEALAND</td>
      <td>250000000.0</td>
      <td>7.5</td>
      <td>Aidan Turner,Adam Brown,James Nesbitt</td>
      <td>65000</td>
    </tr>
  </tbody>
</table>
</div>



### Arreglando la entrada de datos incorrecta


```python
# Corrijamos la codificación de datos nulos
df['director_name'] = np.where(df['director_name']=='N/A','', df['director_name'])
df['director_name'] = np.where(df['director_name']=='Nan','', df['director_name'])
df['director_name'] = np.where(df['director_name']=='Null','', df['director_name'])
```

### Manejo de valores atípicos


```python
# Cambiemos los datos numéricos a float
df["gross"]=df["gross"].astype(float)
df["duration"]=df["duration"].astype(float)
df["budget"]=df["budget"].astype(float)

# Eliminemos datos atípicos:
# Duraciones de películas menores a 10 minutos y mayores a 300 minutos
# Calificaciones IMDb negativas
# Años anteriores a 2010
df['duration'] = np.where(df['duration']<=10,0, df['duration'])
df['duration'] = np.where(df['duration']>300,0, df['duration'])
df['imdb_score'] = np.where(df['imdb_score']<=0,0, df['imdb_score'])
df['title_year'] = np.where(df['title_year']<2010,0, df['title_year'])
```

### División de datos


```python
# Separemos los datos de los actores en 3 columnas
actor_list = df["actors"].str.split(",", n = 2, expand = True) # n : max index
df["actor1"]= actor_list[0]
df["actor2"]= actor_list[1]
df["actor3"]= actor_list[2]
df.drop(columns=['actors'], inplace=True)
```

### Crear una nueva métrica: ingreso bruto sobre presupuesto


```python
# Generemos la nueva métrica
df['GOB'] = df.apply(lambda row: row['gross']/row['budget'] if row['budget']!=0 else 0, axis=1)
```


```python
# Veamos cuales son las películas con el valor más alto
top_GOB=df.sort_values('GOB',ascending=False).head(10)
print(top_GOB)
```

            director_name  duration        gross  \
    43        Tate Taylor     146.0  169705587.0   
    15  Richard Linklater     165.0   25359200.0   
    14       F. Gary Gray     167.0  161029270.0   
    59                        142.0  407999255.0   
    75                        138.0  150117807.0   
    44   Francis Lawrence     146.0  424645577.0   
    76    Robert Zemeckis     138.0   93749203.0   
    94      Steve McQueen     134.0   56667870.0   
    8         Joss Whedon     173.0  623279547.0   
    9         Joss Whedon     173.0  623279547.0   

                                     genres                      movie_title  \
    43                                Drama                         The Help   
    15                                Drama                          Boyhood   
    14  Biography|Crime|Drama|History|Music           Straight Outta Compton   
    59      Adventure|Drama|Sci-Fi|Thriller                 The Hunger Games   
    75                          Crime|Drama                  American Hustle   
    44            Adventure|Sci-Fi|Thriller  The Hunger Games: Catching Fire   
    76                       Drama|Thriller                           Flight   
    94              Biography|Drama|History                 12 Years a Slave   
    8               Action|Adventure|Sci-Fi                     The Avengers   
    9               Action|Adventure|Sci-Fi                     The Avengers   

        title_year country       budget  imdb_score  movie_facebook_likes  \
    43        2011     USA   25000000.0         8.1                 75000   
    15        2014     USA    4000000.0         8.0                 92000   
    14        2015     USA   28000000.0         7.9                 76000   
    59        2012     USA   78000000.0         7.3                140000   
    75        2013     USA   40000000.0         7.3                 63000   
    44        2013     USA  130000000.0         7.6                 82000   
    76        2012     USA   31000000.0         7.3                 64000   
    94        2013     USA   20000000.0         8.1                 83000   
    8         2012     USA  220000000.0         8.1                123000   
    9         2012     USA  220000000.0         8.1                123000   

                   actor1               actor2                 actor3       GOB  
    43         Emma Stone  Bryce Dallas Howard             Mike Vogel  6.788223  
    15     Ellar Coltrane    Lorelei Linklater          Libby Villari  6.339800  
    14        Aldis Hodge       Neil Brown Jr.       R. Marcos Taylor  5.751045  
    59  Jennifer Lawrence      Josh Hutcherson       Anthony Reynolds  5.230760  
    75  Jennifer Lawrence       Christian Bale         Bradley Cooper  3.752945  
    44  Jennifer Lawrence      Josh Hutcherson  Sandra Ellis Lafferty  3.266504  
    76  Denzel Washington      Bruce Greenwood       Nadine Velazquez  3.024168  
    94  Quvenzhané Wallis        Scoot McNairy           Taran Killam  2.833394  
    8     Chris Hemsworth    Robert Downey Jr.     Scarlett Johansson  2.833089  
    9     Chris Hemsworth    Robert Downey Jr.     Scarlett Johansson  2.833089  


### Guardar los datos


```python
df.to_csv(r'../../data/new_IMDB.csv', index=None)
```

### Análisis de datos


```python
# Leamos los datos guardados en un dataframe
df_imdb = pd.read_csv('../../data/new_IMDB.csv')
df_imdb.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>director_name</th>
      <th>duration</th>
      <th>gross</th>
      <th>genres</th>
      <th>movie_title</th>
      <th>title_year</th>
      <th>country</th>
      <th>budget</th>
      <th>imdb_score</th>
      <th>movie_facebook_likes</th>
      <th>actor1</th>
      <th>actor2</th>
      <th>actor3</th>
      <th>GOB</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Martin Scorsese</td>
      <td>240.0</td>
      <td>116866727.0</td>
      <td>Biography|Comedy|Crime|Drama</td>
      <td>The Wolf of Wall Street</td>
      <td>2013</td>
      <td>USA</td>
      <td>100000000.0</td>
      <td>8.2</td>
      <td>138000</td>
      <td>Leonardo DiCaprio</td>
      <td>Matthew McConaughey</td>
      <td>Jon Favreau</td>
      <td>1.168667</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Shane Black</td>
      <td>195.0</td>
      <td>408992272.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>Iron Man 3</td>
      <td>2013</td>
      <td>USA</td>
      <td>200000000.0</td>
      <td>7.2</td>
      <td>95000</td>
      <td>Robert Downey Jr.</td>
      <td>Jon Favreau</td>
      <td>Don Cheadle</td>
      <td>2.044961</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Quentin Tarantino</td>
      <td>187.0</td>
      <td>54116191.0</td>
      <td>Crime|Drama|Mystery|Thriller|Western</td>
      <td>The Hateful Eight</td>
      <td>2015</td>
      <td>USA</td>
      <td>44000000.0</td>
      <td>7.9</td>
      <td>114000</td>
      <td>Craig Stark</td>
      <td>Jennifer Jason Leigh</td>
      <td>Zoë Bell</td>
      <td>1.229913</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Kenneth Lonergan</td>
      <td>186.0</td>
      <td>46495.0</td>
      <td>Drama</td>
      <td>Margaret</td>
      <td>2011</td>
      <td>USA</td>
      <td>14000000.0</td>
      <td>6.5</td>
      <td>0</td>
      <td>Matt Damon</td>
      <td>Kieran Culkin</td>
      <td>John Gallagher Jr.</td>
      <td>0.003321</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Peter Jackson</td>
      <td>186.0</td>
      <td>258355354.0</td>
      <td>Adventure|Fantasy</td>
      <td>The Hobbit: The Desolation of Smaug</td>
      <td>2013</td>
      <td>USA</td>
      <td>225000000.0</td>
      <td>7.9</td>
      <td>83000</td>
      <td>Aidan Turner</td>
      <td>Adam Brown</td>
      <td>James Nesbitt</td>
      <td>1.148246</td>
    </tr>
  </tbody>
</table>
</div>



### Explorar los Datos


```python
#import  qgrid
#qgrid = qgrid.show_grid(df_imdb, show_toolbar=True)
#qgrid

```

### Directores cuyas películas tienen el mayor de ingresos brutos con respecto a su presupuesto (GOB):


```python
# Ordenemos los datos por GOB
top_GOB = df_imdb.sort_values('GOB',ascending=False).head(15)
```


```python
# Obtengamos el apellido del director
top_GOB['director_familyName'] = df_imdb["director_name"].str.split(" ", n = 2, expand = True) [1]
```


```python
# Grafiquemos los datos
fig,ax = plt.subplots(figsize=(8, 5))
ax = sns.barplot(x="director_familyName", y="GOB", data=top_GOB)

ax.set_xticklabels(ax.get_xticklabels(), rotation=90)
fig.suptitle('Top movie directors with highest GOB', fontsize=18)
ax.set_xlabel('Director name',fontsize=18)
ax.set_ylabel('Gross over Budget',fontsize=18)
ax.tick_params(axis='x', labelsize=14)
ax.tick_params(axis='y', labelsize=14)
```


![png](/images/lmdb/output_37_0.png)


### Agrupación de películas

Revisaremos si la calificación IMDb tiene alguna relación con los ingresos brutos con respecto al presupuesto.
De esta manera, podemos predecir los ingresos brutos que tendrá una nueva película


```python
# Obtengamos ambas columnas
df_c=df_imdb.loc[(df_imdb['GOB']>0) & df_imdb['imdb_score']>0][['imdb_score','GOB']]
df_c.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>imdb_score</th>
      <th>GOB</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>8.2</td>
      <td>1.168667</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7.2</td>
      <td>2.044961</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7.9</td>
      <td>1.229913</td>
    </tr>
    <tr>
      <th>3</th>
      <td>6.5</td>
      <td>0.003321</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7.9</td>
      <td>1.148246</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Importemos las librerías que vamos a utilizar
from sklearn.cluster import KMeans
from scipy.spatial.distance import cdist
```


### Elbow Method


```python
# Apliquemos un algoritmo de Kmeans para determinar en cuantos grupos se puede dividor la información
K = range(1, 10)
meandist = []
for k in K:
    km = KMeans(n_clusters=k)
    km.fit(df_c)
    meandist.append(sum(np.min(cdist(df_c, km.cluster_centers_,'euclidean'), axis=1)) / df_c.shape[0])
plt.plot(K, meandist, '--', color='blue')
plt.xlabel('K')
plt.ylabel('Average SSE')
plt.title('Selecting the best K')
```

![png](/images/lmdb/output_38_0.png)

### Centroides


```python
# Como se observa en la gráfica, el número óptimo de grupos es 3
# Utilicemos este valor para definir los centroides y entrenar el modelo
km_ = KMeans(n_clusters=3)
km_.fit(df_c)
```


```python
# Despleguemos los resultados del entrenamiento
centroids=km_.cluster_centers_
labels = km_.labels_
```


```python
print(centroids)
print(labels)
```

### Graficar los centroides


```python
# Grafiquemos los grupos generados
fig = plt.figure(figsize=(8,6))
colors = ["yellow","red","green"]
df_array = np.array(df_c)

for i in range(len(df_array)):
    plt.scatter(df_array[i][0],df_array[i][1],c=colors[labels[i]],s=50,marker='o',edgecolors='black')

plt.scatter(centroids[:,0], centroids[:,1], marker='x', color='black',s=300)
fig.suptitle('Clustering Movies', fontsize=18)
plt.ylabel('GOB')
plt.xlabel('IMDB Score')
```

Text(0.5, 0, 'IMDB Score')

![png](/images/lmdb/output_39_0.png)


## Relación entre la calificación IMDb Score y los likes en Facebook

Revisaremos si la calificación IMDb tiene alguna relación con los likes en Facebook.
De esta manera, podemos predecir los likes que tendrá una nueva película

```python
# Se rescalan los datos de los likes, para que esten en una escala similar a la de la calificación IMDb
df_imdb['movie_facebook_likes']=df_imdb['movie_facebook_likes'].apply(lambda row: row/10000)
```

### Regresion Lineal con Seaborn


```python
# Utilicemos la función preconstruída de Seaborn, para realizar una regresión linear entre la calificación IMDb y los likes de Facebook
fig = plt.figure(figsize=(8,8))
sns.regplot('imdb_score', 'movie_facebook_likes', df_imdb, fit_reg=True,order=2,color='red')
```

     <matplotlib.axes._subplots.AxesSubplot at 0x1c7827517c8>

![png](/images/lmdb/output_40_0.png)


### Regresión Lineal para predecir la calificación IMDb


```python
# Asignemos la calificación IMDb como característica y los likes de Facebook como valor a predecir
X = df_imdb['imdb_score'].values[:,np.newaxis]
y = df_imdb['movie_facebook_likes'].values
```


```python
# Importemos las librerías a utilizar
from sklearn.linear_model import LinearRegression
```


```python
# Generemos un modelo de regresión lineal
lr = LinearRegression()
```


```python
# Entrenemos el modelo con los datos
lr.fit(X, y)
```
     LinearRegression(copy_X=True, fit_intercept=True, n_jobs=None, normalize=False)

#### Predicción:


```python
# Hagamos la predicción de un nuevo dato
IMDB_score=8.8
X_test=np.array([IMDB_score]).reshape(1,-1)
X_test
```
     array([[8.8]])

```python
y_pred = lr.predict(X_test)
print(f"Facebook likes estimation (10k) for a IMDB score:{IMDB_score}-->{y_pred}")
```

     Facebook likes estimation (10k) for a IMDB score:8.8-->[9.34539641]

#### Graficar el modelo y la predicción


```python
# Grafiquemos los resultados
fig,ax = plt.subplots(figsize=(10, 7))

plt.xlabel('IMDB score');
plt.ylabel('Facebook like (10K)');

plt.scatter(X, y,color='blue')
plt.plot(X, lr.predict(X), color='red', linestyle='--', lw=3)

plt.scatter(X_test, y_pred, color='yellow', s=300, edgecolors='black')
```

     <matplotlib.collections.PathCollection at 0x1c7827f5088>

![png](/images/lmdb/output_41_0.png)
