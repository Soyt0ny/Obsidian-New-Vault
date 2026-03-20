---
tags:
  - problem
  - array
  - concatenation
status: evergreen
difficulty: Easy
platform: LeetCode
pattern:
  - array
tech:
  - C++
  - Python
domain: Algorithms
---

# Concatenation of Array

## Description
Dado un arreglo de enteros `nums` de longitud $n$, se debe crear un arreglo `ans` de longitud $2n$ tal que `ans[i] == nums[i]` y `ans[i + n] == nums[i]` para $0 \le i < n$ (indexado desde 0). Básicamente, `ans` es la concatenación de dos arreglos `nums`.

## Constraints
- $n == \text{nums.length}$
- $1 \le n \le 1000$
- $1 \le \text{nums}[i] \le 1000$

## Approach: Array Doubling

### Intuition
La solución consiste en duplicar el contenido del arreglo original en un nuevo espacio de memoria. Podemos lograr esto de tres formas principales:
1.  **Asignación Directa:** Pre-alojar el doble de espacio y llenar ambas mitades simultáneamente en un solo recorrido.
2.  **Inserción por Rango:** Utilizar funciones nativas del lenguaje que optimicen la copia de bloques de memoria.
3.  **Operadores de Concatenación:** En lenguajes de alto nivel como Python, el operador `+` está altamente optimizado para esta tarea.

### Complexity Analysis
- **Time Complexity:** $\bigO(n)$
    Recorremos el arreglo original de tamaño $n$ una sola vez. Las operaciones de copia o inserción por rango también operan en tiempo lineal respecto a $n$.
- **Space Complexity:** $\bigO(n)$
    Se requiere un nuevo arreglo de tamaño $2n$ para almacenar el resultado. Este espacio se asigna dinámicamente en el **Heap**.

## Code Implementation

### C++ Implementations
```cpp
#include <vector>

using namespace std;

/**
 * @brief Solución mediante pre-asignación y doble puntero lógico.
 * @note Es la forma más eficiente ya que evita redimensionamientos.
 */
vector<int> getConcatenation_Manual(vector<int>& nums) {
    int n = nums.size();
    vector<int> ans(2 * n); // Asignación en el Heap
    
    for (int i = 0; i < n; i++) {
        ans[i] = nums[i];
        ans[i + n] = nums[i];
    }
    return ans;
}

/**
 * @brief Solución usando funciones de la STL.
 */
vector<int> getConcatenation_STL(vector<int>& nums) {
    vector<int> ans = nums; // Copia inicial
    ans.insert(ans.end(), nums.begin(), nums.end()); // Concatenación de rangos
    return ans;
}
```

### Python Implementations
```python
def get_concatenation_operator(nums: list[int]) -> list[int]:
    """
    Forma idiomática y más rápida en Python.
    """
    return nums + nums

def get_concatenation_extend(nums: list[int]) -> list[int]:
    """
    Modifica una copia de la lista original.
    """
    ans = nums.copy()
    ans.extend(nums)
    return ans

def get_concatenation_multiply(nums: list[int]) -> list[int]:
    """
    Equivalente a nums + nums.
    """
    return nums * 2
```

## Key Insights

> [!info] Gestión de Memoria: Reserve vs Constructor
> En C++, `vector<int> ans(2 * n)` reserva el espacio **y** lo inicializa con ceros (u otro valor por defecto), lo que toma tiempo $\bigO(n)$. Por otro lado, `reserve(2 * n)` solo separa el espacio en el **Heap** sin inicializarlo, lo cual es útil si vamos a usar `push_back()` repetidamente para evitar re-hashes y copias costosas de memoria.

> [!tip] Python Idioms: Operadores de Secuencia
> El operador `+` en Python para listas invoca internamente un método de concatenación en C que es extremadamente eficiente para copiar bloques de memoria contiguos.

> [!tip] Localidad de Referencia
> Al llenar `ans[i]` y `ans[i+n]` en el mismo bucle, aprovechamos la **caché del procesador**, aunque el acceso a `i+n` pueda causar un pequeño salto en la memoria, sigue siendo más eficiente que dos bucles separados.

## Related Notes
- [[ALGORITHMS]]
- [[Vectores - C++]]
- [[LeetCode Problems]]
