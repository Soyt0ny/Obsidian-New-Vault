---
tags:
  - note
status: evergreen
created: 2026-03-12
tech:
domain: Algorithms
---

# Notación Asintótica

## Core Idea
> Es la herramienta matemática utilizada para describir el comportamiento del tiempo de ejecución o el uso de memoria de un algoritmo a medida que el tamaño de la entrada crece hacia el infinito.

## Explanation
La Notación Asintótica permite enfocarse en la eficiencia del algoritmo abstrayéndose de detalles de hardware o implementación específicos, centrándose en cómo escala la complejidad según la cantidad de elementos ($n$).

Existen tres tipos principales:
- **Big O ($O$) - Cota Superior:** Representa el peor de los casos. Es la más común ya que garantiza que el algoritmo no tardará más de lo indicado.
- **Omega ($\Omega$) - Cota Inferior:** Representa el mejor caso posible. Indica que el algoritmo tardará al menos ese tiempo.
- **Theta ($\Theta$) - Límite Ajustado:** Representa una cota exacta (superior e inferior). Es la forma más precisa de describir el tiempo de ejecución.

### Conceptos Clave

#### Logaritmos en Algoritmos
Los logaritmos son la operación inversa a los exponentes. Por ejemplo, $\log_2 8 = 3$ porque $2^3 = 8$.
En algoritmos como la **Búsqueda Binaria**, se utiliza $\log_2$ porque el espacio de búsqueda se divide a la mitad en cada paso.

#### Búsqueda Binaria
- **Requisito:** La lista debe estar **ordenada**. Si no lo está, el algoritmo no funciona correctamente.
- **Eficiencia:** El número máximo de pasos es $\lfloor \log_2 n \rfloor + 1$.
- **Ejemplo:** Para una lista de 128 elementos, $\log_2 128 = 7$, por lo que se requieren máximo $7 + 1 = 8$ comparaciones.

#### Notación Big O
Define la tasa de crecimiento del tiempo de ejecución. Es crucial para comparar algoritmos.

**Escalabilidad:**
Si cada elemento tarda 1ms:
- **Búsqueda Lineal ($n=100$):** 100ms.
- **Búsqueda Binaria ($n=100$):** ~7ms.

**Casos Comunes (de mejor a peor):**
1. $O(1)$ - Constante.
2. $O(\log n)$ - Logarítmico.
3. $O(n)$ - Lineal.
4. $O(n \log n)$ - Log-lineal.
5. $O(n^2)$ - Cuadrático.
6. $O(n!)$ - Factorial.

## Connections
- **Related to:** [[Aprendizaje de Algoritmos]]
- **Contrast with:** [[Operaciones Elementales - Algoritmos]]

## Application / Example

### Búsqueda Binaria (Python)
```python
def binary_search(array: list[int], target: int) -> int:
    start = 0
    end = len(array) - 1 
    while start <= end:
        mid = (start + end) // 2
        if array[mid] == target:
            return mid
        elif array[mid] < target:
            start = mid + 1
        else:
            end = mid - 1
    return -1
```

### Ejemplos de Complejidad
```python
# O(1) - Tiempo Constante
# El acceso por índice siempre toma el mismo tiempo.
def complejidad_constante(lista):
    return lista[0]

# O(n) - Tiempo Lineal
# El tiempo crece proporcionalmente al tamaño de la lista.
def complejidad_lineal(lista, objetivo):
    for elemento in lista:
        if elemento == objetivo:
            return True
    return False

# O(n^2) - Tiempo Cuadrático
# Común en bucles anidados.
def complejidad_cuadratica(lista):
    for i in lista:
        for j in lista:
            print(i, j)
```

## References
- Source: Grokking Algorithms, Chapter 1. [[Algorithms Ilustrado Grokking.pdf]]
