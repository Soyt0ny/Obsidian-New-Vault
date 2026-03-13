---
tags:
  - note
status: in-progress
created:
tech:
domain:
---

# Notación Asintótica

## Core Idea
> One sentence summary of the concept.

## Explanation
Notacion Asintotica es la forma de solo enfocarte en como cambia algo dependiendo de la canitidad de elmeentos

Existen 3 :
- Big O - Cota Superior: Es el peor de los casos y es en la que la mayoria de veces nos enfocaremos 
- Omega - Cota inferior: Es el mejor caso posible
- Theta - Limite Ajustado: Es la manera de representar el tiempo de ejecucion cuando tiene un limete superior o inferiror. Es la notacion mas precisa


Books

 Capitulo 1 [[Algorithms Ilustrado Grokking.pdf]]
> *Que son los logaritmos* 
> Los logaritmos es la forma de representar lo inverso a los exponentes, $log_2 \space 8$ es básicamente decir cuantas veces tengo que multiplicar 2 para llegar a 8.  

En búsqueda binara es $log_2$ básicamente porque estamos partiendo la mitad la búsqueda

Busqueda binaria solo sirve cuando una lista esta ordenada, en caso de no estarlo el algoritmos es inutil porque estaría descarcanto elementos casi que al azar.

La búsqueda binaria siempre sera $\text{pasos} = \lfloor \log_2 n \rfloor + 1$ es decir imagina que tienes una lista con 128 elementos el numero de divisiones que hace son 7 pero necesita una comparación extra por lo cual sera 7 + 1 = 8

## Connections
- **Related to:** [[Related Note]]
- **Contrast with:** [[Opposing Concept]]

## Application / Example

Busqueda Binaria
```Python
def BS(array: list[int], target : int) -> int :
	start = 0
	end = len(array) - 1 
	while start <= end :
		mid = (start + end) // 2
		if array[mid] == target :
			return mid
		elif array[mid] < target:
			start = mid + 1
		else:
			end = mid - 1
```

```python
# Ejemplo de O(1) - Tiempo Constante
# No importa si la lista tiene 10 o 10 millones de elementos,
# acceder por índice siempre toma el mismo tiempo.
def complejidad_constante(lista):
    return lista # Una sola operación [28]

# Ejemplo de O(n) - Tiempo Linear
# El tiempo crece proporcionalmente al tamaño de la lista.
# Común en el patrón "Simple Search".
def complejidad_lineal(lista, objetivo):
    for elemento in lista: # Se ejecuta n veces [3, 29]
        if elemento == objetivo:
            return True
    return False

# Ejemplo de O(n^2) - Tiempo Cuadrático
# Común cuando tenemos bucles anidados.
# Si la lista dobla su tamaño, el tiempo se cuadriplica.
def complejidad_cuadratica(lista):
    for i in lista:         # n veces
        for j in lista:     # n veces por cada i
            print(i, j)     # Total: n * n operaciones [30, 31]

# Este concepto se aplica al patrón "Sliding Window" o "Two Pointers" 
# donde intentamos reducir un O(n^2) a un O(n) más eficiente [2].
```

## References
- Source: 
