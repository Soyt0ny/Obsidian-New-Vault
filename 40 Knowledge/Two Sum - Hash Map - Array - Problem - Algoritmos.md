---
tags:
  - problem
  - hash-map
  - array
status: evergreen
difficulty: Easy
platform: LeetCode
pattern:
  - HashMap
tech:
  - Python
domain: Algorithms
---

# Two Sum

## Description
Dada una lista de numeros y un `target`, encontrar dos numeros en la lista que sumen el target y devolver la posicion de esos dos numeros. Cada entrada tiene exactamente una solucion, y no se puede usar el mismo elemento dos veces.

## Constraints
- $n == \text{nums.length}$
- $2 \le n \le 10^4$
- $-10^9 \le \text{nums}[i] \le 10^9$
- $-10^9 \le \text{target} \le 10^9$
- Exactamente una solucion valida

## Approach: Hash Map (One Pass)

### Intuition
1. Restar el valor del numero actual al target. Eso da el **complemento** que estamos buscando.
2. Buscar en el diccionario si el complemento ya fue visto.
3. Si esta, devolver su valor (la posicion donde se guardo) y el indice actual.
4. Si no esta, crear una nueva clave en el diccionario con el valor del indice actual.

> [!warning] Orden: check-then-store
> Primero se BUSCA el complemento, luego se GUARDA el numero actual. Si guardas antes de buscar y el complemento es igual al numero actual, un elemento se emparejaria consigo mismo — ej. `nums = [3, 3]` devolveria `[0, 0]` en vez de `[0, 1]`.

### Complexity Analysis
- **Time Complexity:** $O(n)$ — un solo paso por el array
- **Space Complexity:** $O(n)$ — en el peor caso guardamos los $n$ elementos en el diccionario

## Code Implementation

```python
def two_sum(nums, target):
    visto = {}

    for index, num in enumerate(nums):
        complemento = target - num
        if complemento in visto:
            return [visto[complemento], index]
        visto[num] = index


print(two_sum([2, 7, 11, 15], 9))
print(two_sum([3, 3], 6))
print(two_sum([3, 2, 4], 6))
```

## Key Insights

> [!info] Por que el diccionario, no la lista
> Buscar `complemento in lista` seria $O(n)$ por busqueda, $O(n^2)$ total. El diccionario reduce cada busqueda a $O(1)$ promedio, dejando el algoritmo en $O(n)$.

> [!tip] El complemento como clave
> La idea clave de Two Sum es **no buscar el par, sino guardar lo ya visto y preguntar "lo que necesito, ya lo vi?"**. Ese patron (complemento) se repite en varios problemas.

## Related Notes
- **Concept:** [[Hash Maps - Algoritmos]] — hash table fundamentals
- **Contrast with:** [[Contains Duplicate - Hash - Set - Problem - Algoritmos]] — mismo patron hash, distinto objetivo
- **Related to:** [[Group Anagrams - Hash Map - String - Problem - Algoritmos]] — misma tecnica de mapeo
