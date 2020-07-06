# Python Ejercicios - Solución

Este es un ejercicio opcional, para evaluar tu comprensión de los conceptos básicos de Python. Si encuentras esto extremadamente desafiante, entonces probablemente todavía no estés listo para el resto de este curso y no tengas suficiente experiencia en programación para continuar.

## Ejercicios

Responde las preguntas o completa las tareas descritas en negrita que se encuentran a continuación; utiliza el método específico que se describe, si corresponde.

Eleva 7 a la cuarta potencia


```python
7**4
```




    2401



** Divide esta cadena: **

    s = '¡Hola Sam!'

** en una lista. ** **


```python
s = '¡Hola Sam!'
```


```python
s.split()
```




    ['¡Hola', 'Sam!']



** Dadas las variables: **

    planeta = "Tierra"
    diametro = 12742

** Usa .format () para imprimir la siguiente cadena: **

    El diámetro de la Tierra es de 12742 kilómetros.


```python
planeta = "Tierra"
diametro = 12742
```


```python
print("El diámetro de la {} es {} kilómetros.".format(planeta,diametro))
```

    El diametro de la Tierra es 12742 kilómetros.


** Dada esta lista anidada, usa la indexación para obtener la palabra "hola" **


```python
lista = [1,2,[3,4],[5,[100,200,['hola']],23,11],1,7]
```


```python
lista[3][1][2][0]
```




    'hola'



** Dado este diccionario anidado, obten la palabra "hola". Esto puede ser complicado**


```python
d = {'k1':[1,2,3,{'truco':['ay','hombre','inception',{'objetivo':[1,2,3,'hola']}]}]}
```


```python
d['k1'][3]['truco'][3]['objetivo'][3]
```




    'hola'



** ¿Cuál es la principal diferencia entre una tupla y una lista? **


```python
# La tupla es inmutable
```

** Crea una función que tome el dominio del sitio web, del correo electrónico de una cadena con este formato: **

    usuario@dominio.com

** Entonces, por ejemplo, si usas "user@domain.com" devolvería: domain.com **


```python
def dominioObtener(email):
    return email.split('@')[-1]
```


```python
dominioObtener('user@domain.com')
```




    'domain.com'



** Crea una función básica que devuelva True si la palabra 'perro' está contenida en la cadena de entrada. No te preocupes por los casos extremos, como signos de puntuación que estén junto a la palabra 'perro', pero ten en cuenta las mayúsculas. **


```python
def buscaPerro(cadena):
    return 'perro' in cadena.lower().split()
```


```python
buscaPerro('¿Hay un perro aqui?')
```




    True



** Crea una función que cuente la cantidad de veces que la palabra 'perro' aparece en una cadena. Nuevamente, ignora los casos extremos. **


```python
def cuentaPerro(cadena):
    contador = 0
    for palabra in cadena.lower().split():
        if palabra == 'perro':
            contador += 1
    return contador
```


```python
cuentaPerro('Este perro corre más rápido que el otro perro')
```




    2



** Usa expresiones lambda y la función filter () para eliminar palabras de una lista, que no comiencen con la letra 's'. Por ejemplo:**

    secuencia = ['sopa','perro','sol','gato','genial']

** debe filtrarse a: **

    ['sopa','sol']


```python
secuencia = ['sopa','perro','sol','gato','genial']
```


```python
list(filter(lambda palabra: palabra[0]=='s',secuencia))
```




    ['sopa','sol']



### Problema Final

** Conduces demasiado rápido y un oficial de policía te detiene. Escribe una función
  para devolver uno de los 3 resultados posibles: "Sin Multa", "Multa Pequeña", o "Multa Grande".
  Si tu velocidad es de 60 o menos, el resultado es "Sin Multa". Si la velocidad está entre 61
  y 80 inclusive, el resultado es "Multa Pequeña". Si la velocidad es 81 o más, el resultado es "Multa Grande". A menos que sea tu cumpleaños (codificado como un valor booleano en los parámetros de la función); en tu cumpleaños, tu velocidad puede ser 5 más alta en total. **


```python
def velocimetro(velocidad, cumpleanios):

    if cumpleanios:
        limite = velocidad - 5
    else:
        limite = velocidad

    if limite > 80:
        return 'Multa Grande'
    elif limite > 60:
        return 'Multa Pequeña'
    else:
        return 'Sin Multa'
```


```python
velocimetro(81,True)
```




    'Multa Pequeña'




```python
velocimetro(81,False)
```




    'Multa Grande'



# Buen trabajo¡¡
