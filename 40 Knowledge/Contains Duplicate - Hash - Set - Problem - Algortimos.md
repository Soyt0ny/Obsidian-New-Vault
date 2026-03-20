---
tags:
  - problem
  - hash-set
  - hash-map
status: evergreen
difficulty: Easy
platform: LeetCode
pattern:
  - set
  - HashMap
tech:
  - C++
  - Python
domain: Algorithms
---

# Contains Duplicate

## Description
Determinar si un arreglo de enteros (`nums`) contiene algún elemento duplicado. La función debe devolver `true` si cualquier valor aparece al menos dos veces en el arreglo, y `false` si todos los elementos son distintos.

## Constraints
- $n == \text{nums.length}$
- $1 \le n \le 10^5$
- $-10^9 \le \text{nums}[i] \le 10^9$

## Approach: Hash-based Solution (Set & Map)

### Intuition
Existen tres estrategias principales para resolver este problema, cada una con distintos compromisos entre tiempo y memoria:

1.  **HashSet (Estrategia Óptima):**
    Utilizamos un **conjunto desordenado** para almacenar los elementos ya vistos. Al ser una estructura basada en *hashing*, la búsqueda e inserción tienen un tiempo promedio constante. Si al intentar insertar un elemento este ya existe, confirmamos un duplicado.
2.  **HashMap (Contador):**
    Similar al Set, pero registramos la **frecuencia** de cada elemento. Si la frecuencia de cualquier elemento supera 1, existe un duplicado. Es útil si necesitáramos saber cuántas veces se repite cada número.
3.  **Brute Force (Inadecuado):**
    Comparar cada elemento con todos los demás mediante bucles anidados. Es altamente ineficiente para conjuntos de datos grandes.

### Complexity Analysis
- **Time Complexity:** $O(n)$
    Tanto en el *Set* como en el *Map*, recorremos el arreglo una sola vez. Las operaciones de inserción y búsqueda en un `unordered_set` o `unordered_map` son $O(1)$ en promedio.
- **Space Complexity:** $O(n)$
    En el peor de los casos (sin duplicados), almacenaremos los $n$ elementos en la estructura de datos. Estas estructuras se asignan en el **Heap** (montículo) de la memoria, a diferencia de las variables locales simples que residen en el **Stack** (pila).

## Code Implementation

### C++ Implementations
```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
#include <unordered_map>

using namespace std;

/**
 * @brief Solución optimizada usando unordered_set.
 * @note El uso de reserve() evita re-hashes innecesarios en el Heap.
 */
bool hasDuplicate_Set(vector<int>& nums) {
    unordered_set<int> seen;
    seen.reserve(nums.size()); // Optimización de memoria en el Heap
    
    for (int num : nums) {
        // insert() devuelve un pair: {iterador, bool}
        // second es true si la inserción fue exitosa (no existía)
        if (!seen.insert(num).second) {
            return true;
        }
    }
    return false;
}

/**
 * @brief Solución alternativa usando unordered_map.
 */
bool hasDuplicate_Map(const vector<int>& nums) {
    unordered_map<int, int> counts;
    counts.reserve(nums.size());
    
    for (int num : nums) {
        if (++counts[num] > 1) {
            return true;
        }
    }
    return false;
}
```

### Python Implementations
```python
from collections import Counter

def has_duplicate_set(nums: list[int]) -> bool:
    """
    Estrategia más eficiente en Python:
    Comparar la longitud del set con la de la lista original.
    """
    return len(set(nums)) != len(nums)

def has_duplicate_hashmap(nums: list[int]) -> bool:
    """
    Uso de un diccionario (HashMap) para contar frecuencias.
    """
    counts = {}
    for num in nums:
        # get(num, 0) devuelve 0 si la key no existe
        counts[num] = counts.get(num, 0) + 1
        if counts[num] > 1:
            return True
    return False

def has_duplicate_counter(nums: list[int]) -> bool:
    """
    Uso de collections.Counter para obtener frecuencias.
    """
    counts = Counter(nums)
    for freq in counts.values():
        if freq > 1:
            return True
    return False
```

## Key Insights

> [!tip] Python Idioms: `set()`
> En Python, la solución `len(set(nums)) != len(nums)` es extremadamente concisa y rápida, ya que la conversión a `set` ocurre en el nivel de implementación de C (CPython), lo que suele ser más veloz que un bucle `for` manual.

> [!info] Gestión de Memoria: Stack vs Heap
> Las estructuras como `vector`, `unordered_set` y `unordered_map` en C++, así como las `list` y `set` en Python, almacenan sus elementos en el **Heap**. Esto permite manejar grandes volúmenes de datos que excederían el límite del **Stack**. En Python, la gestión del Heap es automática a través del *Garbage Collector*.

> [!tip] Referencias y Rendimiento
> El uso de `&` (referencias) en los parámetros de la función (ej. `vector<int>& nums`) evita la **copia costosa** del objeto completo. Al usar `const`, aseguramos que la función no modificará los datos originales, manteniendo la integridad del arreglo.

> [!tip] Retorno de `insert()`
> En C++, `unordered_set::insert()` devuelve un `std::pair`. El miembro `.second` es un booleano que indica si el elemento es **nuevo** en el conjunto. Es la forma más eficiente de comprobar existencia e insertar en un solo paso.

## Related Notes
- [[ALGORITHMS]]
- [[Vectores - C++]]
- [[Enumeración y Templates - C++]]
