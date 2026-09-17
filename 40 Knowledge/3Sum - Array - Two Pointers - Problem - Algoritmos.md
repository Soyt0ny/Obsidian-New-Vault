---
tags:
  - problem
  - array
  - two-pointers
  - sorting
status: evergreen
difficulty: Medium
platform: LeetCode
pattern:
  - Two Pointers
  - Sorting
tech:
  - Python
  - C++
domain: Algorithms
---

# 3Sum

## Description
Dado un arreglo de enteros `nums`, devolver todas las **tercias únicas** `[nums[i], nums[j], nums[k]]` tales que `i != j != k` y la suma de los tres sea `0`. El resultado no debe contener tercias duplicadas.

> [!warning] Aclaracion comun
> "Unicas" significa que el **valor** de la tercia no se repite, no que los indices sean distintos. Las permutaciones como `[-1, 0, 1]`, `[0, -1, 1]` y `[1, 0, -1]` cuentan como **una sola** tercia.

## Constraints
- $3 \le \text{nums.length} \le 3000$
- $-10^5 \le \text{nums}[i] \le 10^5$

## Approach: Two Pointers + Sorting

### Intuition
La intuicion de **ordenar primero** es correcta, pero hay una razon tecnica fuerte detras:

1. **Permite usar two pointers:** en un arreglo desordenado, no hay forma eficiente de decidir hacia donde mover `L` o `R` porque no hay relacion de orden.
2. **Agrupa duplicados:** una vez ordenado, los valores iguales quedan contiguos, lo que habilita la deduplicacion lineal.
3. **Permite poda temprana:** si `nums[i] > 0` (con el arreglo ya ordenado), cualquier suma de tres valores sera $> 0$ y podemos cortar el bucle.

La idea central es: **fijar un elemento** (`i`) y resolver el subproblema **2Sum** sobre el resto del arreglo, que tiene solucion $O(n)$ con two pointers. Como esto se repite para cada `i`, el costo total es $O(n^2)$.

### Complexity Analysis
- **Time Complexity:** $O(n^2)$
    Sorting $O(n \log n)$ + bucle externo $O(n)$ que ejecuta un escaneo two-pointers $O(n)$ en cada iteracion. El termino dominante es $n \cdot n = n^2$.
- **Space Complexity:** $O(1)$ auxiliar
    El arreglo se ordena in-place y solo usamos punteros enteros. **El output no cuenta** como espacio auxiliar porque es el resultado pedido, no memoria de trabajo.

> [!warning] Tu nota decia $O(n)$
> Dijiste "la idea es buscar una solucion de O(n)" pero el algoritmo que escribiste es $O(n^2)$. Dos punteros dentro de un `for` no es "una sola iteracion": por **cada** `i` recorres una porcion del arreglo con `L` y `R`. Es lineal **dentro** de cada vuelta del `for`, no lineal en total. La unica forma de llegar a $O(n)$ en este problema seria con un hash set bien afinado, y aun asi seguiria siendo $O(n^2)$ en el peor caso por la deduplicacion.

## Code Implementation

### Python Implementation
```python
def three_sum(nums: list[int]) -> list[list[int]]:
    triplets = []
    order_nums = sorted(nums)
    n = len(order_nums)

    for i, anchor in enumerate(order_nums):
        # Poda: si el anchor es positivo, no hay forma de sumar 0
        if anchor > 0:
            break

        # Saltar anchors duplicados
        if i > 0 and order_nums[i] == order_nums[i - 1]:
            continue

        L, R = i + 1, n - 1
        while L < R:
            current = anchor + order_nums[L] + order_nums[R]

            if current == 0:
                triplets.append([anchor, order_nums[L], order_nums[R]])
                L += 1
                R -= 1
                # Deduplicar AMBOS lados despues de encontrar match
                while L < R and order_nums[L] == order_nums[L - 1]:
                    L += 1
                while L < R and order_nums[R] == order_nums[R + 1]:
                    R -= 1
            elif current < 0:
                L += 1
            else:
                R -= 1

    return triplets
```

> [!warning] Bug que tenia tu codigo
> Solo deduplicabas `L` despues de un match, pero **no deduplicabas `R`**. Con un input como `[-2, 0, 0, 2, 2, 2]` producias la tercia `[-2, 0, 2]` varias veces. El arreglo de output no es solo "lo que devolvemos", es parte del contrato del problema.

### C++ Implementation
```cpp
using namespace std;

vector<vector<int>> threeSum(vector<int>& nums) {
    vector<vector<int>> triplets;
    sort(nums.begin(), nums.end());
    int n = nums.size();

    for (int i = 0; i < n - 2; i++) {
        if (nums[i] > 0) break;

        if (i > 0 && nums[i] == nums[i - 1]) continue;

        int L = i + 1, R = n - 1;
        while (L < R) {
            int current = nums[i] + nums[L] + nums[R];

            if (current == 0) {
                triplets.push_back({nums[i], nums[L], nums[R]});
                L++;
                R--;
                while (L < R && nums[L] == nums[L - 1]) L++;
                while (L < R && nums[R] == nums[R + 1]) R--;
            } else if (current < 0) {
                L++;
            } else {
                R--;
            }
        }
    }

    return triplets;
}
```

## Key Insights

> [!tip] Sort + Two Pointers es el patron canonico
> Para problemas del tipo "encontrar K-tuplas que suman X", la combinacion **ordenar + anclar + two pointers** aparece una y otra vez (3Sum, 4Sum, 3Sum Closest). Vale la pena memorizar la estructura.

> [!tip] La deduplicacion es la parte sutil
> Hay tres niveles de deduplicacion: el anchor (`i`), el puntero izquierdo (`L`) y el puntero derecho (`R`). Cualquiera que se olvide produce tercias repetidas en casos con valores duplicados.

> [!tip] La poda `if anchor > 0: break` es gratis
> En el peor caso no mejora la complejidad asintotica, pero en la practica puede cortar el bucle externo mucho antes cuando el input tiene muchos positivos. Es una optimizacion defensiva, no un cambio de algoritmo.

## Related Notes
- [[ALGORITHMS]]
- [[Notación Asintótica - Algoritmos]]
- [[Concatenation of Array - Array - Problem - Algoritmos]]
