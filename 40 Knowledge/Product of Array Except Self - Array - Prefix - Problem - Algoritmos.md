---
tags:
  - problem
  - array
  - prefix-sum
status: evergreen
difficulty: Medium
platform: LeetCode
pattern:
  - Prefix
  - Suffix
tech:
  - Python
domain: Algorithms
---

# Product of Array Except Self

## Description
Dado un arreglo de enteros `nums`, devolver un arreglo `output` donde `output[i]` es el producto de todos los elementos de `nums` excepto `nums[i]`. Sin usar division y en $O(n)$.

## Constraints
- $n == \text{nums.length}$
- $2 \le n \le 10^5$
- $-30 \le \text{nums}[i] \le 30$

## Approach: Two Pass (Prefix + Suffix)

### Intuicion

Si se pudiera usar division, la solucion seria trivial: producto total / nums[i]. Sin division, el truco es separar el producto en dos partes:

```
output[i] = (nums[0] * ... * nums[i-1]) * (nums[i+1] * ... * nums[n-1])
                 producto a la izquierda           producto a la derecha
```

Se resuelve con **dos barridos lineales** (ida y vuelta), cada uno acumulando el producto de lo ya recorrido:

1. **Primer barrido (izquierda a derecha)**: por cada posicion `i`, guarda el producto acumulado de lo que esta a la izquierda de `i`. El acumulador arranca en 1 (identidad multiplicativa) porque "no hay nada" a la izquierda del primer elemento.

2. **Segundo barrido (derecha a izquierda)**: misma logica pero al reves. Toma el valor ya guardado en `output[i]` (que es el producto izquierda) y lo multiplica por el producto acumulado de lo que esta a la derecha.

```
nums =      [1,  2,  3,  4]

output despues del 1er barrido:
            [1,  1,  2,  6]    (producto de todo lo que esta a la izquierda)

output despues del 2do barrido:
            [24, 12, 8,  6]    (producto izquierda * producto derecha)
```

### Complexity Analysis
- **Time Complexity:** $O(n)$ — dos barridos lineales
- **Space Complexity:** $O(1)$ sin contar el output — solo dos variables acumuladoras

## Code Implementation

```python
def product_except_self(nums):
    n = len(nums)
    output = [0] * n

    producto = 1
    for i in range(n):
        output[i] = producto
        producto *= nums[i]

    producto = 1
    for i in range(n - 1, -1, -1):
        output[i] *= producto
        producto *= nums[i]

    return output


print(product_except_self([1, 2, 3, 4]))
print(product_except_self([-1, 1, 0, -3, 3]))
```

## Key Insights

> [!tip] Asignar antes de multiplicar
> En cada iteracion, PRIMERO se asigna el acumulador a `output[i]`, DESPUES se multiplica el acumulador por `nums[i]`. Asi el producto acumulado siempre representa "todo lo ya recorrido" sin incluir la posicion actual.

> [!info] Identidad multiplicativa
> El acumulador arranca en 1 porque `1 * x = x`. Si arrancara en 0, todo daria 0. Es el equivalente al `0` en sumas.

> [!warning] Sin usar enumerate
> A diferencia de los problemas de hash maps, aca no necesitamos el valor y el indice al mismo tiempo. Solo el indice para escribir en `output[i]`. Un `range(n)` alcanza.

## Related Notes
- **Related to:** [[Concatenation of Array - Array - Problem - Algoritmos]] — arrays y acceso por indice
- **Contrast with:** [[Two Sum - Hash Map - Array - Problem - Algoritmos]] — ahi se usaba dict para buscar complemento; aca no se busca nada, se acumula
- **Related to:** [[Valid Sudoku - Hash Set - Matrix - Problem - Algoritmos]] — ultimo problema del Dia 1, mismo patron de "todo excepto la posicion actual" pero en 2D
