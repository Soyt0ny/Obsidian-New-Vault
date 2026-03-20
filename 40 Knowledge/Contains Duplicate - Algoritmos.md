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
tech: C++
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

/**
 * @brief Fuerza bruta (No recomendada para N > 1000).
 */
bool hasDuplicate_Brute(const vector<int>& nums) {
    int n = nums.size();
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (nums[i] == nums[j]) return true;
        }
    }
    return false;
}
```

## Key Insights

> [!info] Gestión de Memoria: Stack vs Heap
> Las estructuras como `vector`, `unordered_set` y `unordered_map` almacenan sus elementos en el **Heap**. Esto permite manejar grandes volúmenes de datos que excederían el límite del **Stack**, pero requiere una gestión cuidadosa (automatizada por los contenedores de la STL).

> [!tip] Referencias y Rendimiento
> El uso de `&` (referencias) en los parámetros de la función (ej. `vector<int>& nums`) evita la **copia costosa** del objeto completo. Al usar `const`, aseguramos que la función no modificará los datos originales, manteniendo la integridad del arreglo.

> [!tip] Retorno de `insert()`
> En C++, `unordered_set::insert()` devuelve un `std::pair`. El miembro `.second` es un booleano que indica si el elemento es **nuevo** en el conjunto. Es la forma más eficiente de comprobar existencia e insertar en un solo paso.

## Related Notes
- [[ALGORITHMS]]
- [[Vectores - C++]]
- [[Enumeración y Templates - C++]]
