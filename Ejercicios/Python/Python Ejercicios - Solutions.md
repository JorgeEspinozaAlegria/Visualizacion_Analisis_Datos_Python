# Python Ejercicios - Solución

Este es un ejercicio opcional para evaluar su comprensión de Python Basics. Si encuentra esto extremadamente desafiante, entonces probablemente todavía no esté listo para el resto de este curso y no tenga suficiente experiencia en programación para continuar.

## Ejercicios

Responda las preguntas o complete las tareas descritas en negrita a continuación, utilice el método específico descrito, si corresponde.

Eleva 7 a la cuarta potencia


```python
7**4
```




    2401



** Dividir esta cadena: **

    s = "Hola Sam!"
    
** en una lista. ** **


```python
s = 'Hi there Sam!'
```


```python
s.split()
```




    ['Hi', 'there', 'Sam!']



** Dadas las variables: **

    planeta = "Tierra"
    diámetro = 12742

** Use .format () para imprimir la siguiente cadena: **

    El diámetro de la Tierra es de 12742 kilómetros.


```python
planet = "Tierra"
diameter = 12742
```


```python
print("El diametro de la {} es {} kilómetros.".format(planet,diameter))
```

    El diametro de la Tierra es 12742 kilómetros.
    

** Dada esta lista anidada, use la indexación para tomar la palabra "hello" **


```python
lst = [1,2,[3,4],[5,[100,200,['hello']],23,11],1,7]
```


```python
lst[3][1][2][0]
```




    'hello'



** Dado este diccionario de nidos, toma la palabra "hello". Esté preparado, esto será molesto / complicado**


```python
d = {'k1':[1,2,3,{'tricky':['oh','man','inception',{'target':[1,2,3,'hello']}]}]}
```


```python
d['k1'][3]['tricky'][3]['target'][3]
```




    'hello'



** ¿Cuál es la principal diferencia entre una tupla y una lista? **


```python
# Tuple es inmutable
```

** Cree una función que tome el dominio del sitio web de correo electrónico de una cadena en el formulario: **

    usuario@dominio.com
    
** Entonces, por ejemplo, pasar "user@domain.com" devolvería: domain.com **


```python
def domainGet(email):
    return email.split('@')[-1]
```


```python
domainGet('user@domain.com')
```




    'domain.com'



** Cree una función básica que devuelva True si la palabra 'dog' está contenida en la cadena de entrada. No se preocupe por los casos extremos como una puntuación que se adjunta a la palabra dog, pero tenga en cuenta las mayúsculas. ** 


```python
def findDog(st):
    return 'dog' in st.lower().split()
```


```python
findDog('Is there a dog here?')
```




    True



** Cree una función que cuente la cantidad de veces que la palabra "dog" aparece en una cadena. Nuevamente ignore los casos extremos. **


```python
def countDog(st):
    count = 0
    for word in st.lower().split():
        if word == 'dog':
            count += 1
    return count
```


```python
countDog('This dog runs faster than the other dog dude!')
```




    2



** Use expresiones lambda y la función filter () para filtrar palabras de una lista que no comience con la letra 's'. Por ejemplo:**

    seq = ['soup','dog','salad','cat','great']

** debe filtrarse a: **

    ['soup','salad']


```python
seq = ['soup','dog','salad','cat','great']
```


```python
list(filter(lambda word: word[0]=='s',seq))
```




    ['soup', 'salad']



### Problema Final

** Conduces demasiado rápido y un oficial de policía te detiene. Escribir una función
  para devolver uno de los 3 resultados posibles: "No ticket", "Small ticket", or "Big Ticket".
  Si su velocidad es 60 o menos, el resultado es "No Ticket". Si la velocidad está entre 61
  y 80 inclusive, el resultado es "Small ticket". Si la velocidad es 81 o más, el resultado es "Big Ticket". A menos que sea su cumpleaños (codificado como un valor booleano en los parámetros de la función), en su cumpleaños, su velocidad puede ser 5 más alta en total
  casos. **


```python
def caught_speeding(speed, is_birthday):
    
    if is_birthday:
        speeding = speed - 5
    else:
        speeding = speed
    
    if speeding > 80:
        return 'Big Ticket'
    elif speeding > 60:
        return 'Small Ticket'
    else:
        return 'No Ticket'
```


```python
caught_speeding(81,True)
```




    'Small Ticket'




```python
caught_speeding(81,False)
```




    'Big Ticket'



# Buen trabajo¡¡

[**Siguiente Lección**](Visualizacion_Analisis_Datos_Python/blob/master/Lecci%C3%B3n%2005%20-%20Introducci%C3%B3n%20a%20NumPy.md)
