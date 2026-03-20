---
tags:
  - problem
status: review
difficulty: Easy
platform: LeetCode
pattern:
  - set
  - HashMap
tech:
---

# Problem Name

## Description
Encontrar si el arreglo de numero, palabras que nos dan tiene duplicados 

## Constraints
- n == `nums.lenght`
- 1 <= `n` <= 1000
- 1 < `nums[i]` <=1000

## Approach: [HashMap] [Set] [Brute Force]

### Intuition
Existen 3 maneras en las cuales podemos resolver este problema, básicamente nos piden poder comprobar si los elementos de un arreglo estan duplciados

**Hashmap**
Consiste en guardar el valor que vemos como *key* y como *value* hacer un contador,
cada vez que se tome un nuevo numero se busca por su key, en caso de ya existir la key significa que ya existe y que en este caso estaría duplicado
**Set**
La estructura de set solo nos permite agregar valores que no estén duplicados, y la manera que tenemos para poder agregar estos elementos por lo cual si convertimos la lista a un set y la comparamos su longitud podemos ver si contien duplicados o no.

En este aproach es importante recalcar que depende del lenguaje de programacion en este caso, C++ y Python la manera de programarlo son difernetes

**Brute Force**
Fuerza bruta es la mas ineficiente de todas, debido a que tendriamos que comprar cada elemento con los demas elementos basicamente haci

### Complexity Analysis
- **Time Complexity:** $O(n)$ - Explicación detallada de la complejidad temporal.
- **Space Complexity:** $O(n)$ - Detalle sobre el uso de memoria (Stack vs Heap) y estructuras auxiliares.

## Code Implementation
```cpp
using namespace std;

// Tu solución aquí
```

## Key Insights
> [!tip] Aprendizaje Clave
> Qué aprendiste de este problema o qué técnica específica optimizó la solución.

## Related Notes
- [[ALGORITHMS]]
---