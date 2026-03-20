---
tags:
  - note
status: evergreen
created: 2026-03-19
tech:
  - Python
  - C++
domain: Algorithms
---

# Operaciones Elementales - Algoritmos

## Core Idea
> Una **Operación Elemental** es una unidad indivisible de trabajo computacional cuyo tiempo de ejecución se asume constante ($\Theta(1)$), independientemente de los datos de entrada o el hardware subyacente.

## Explanation

Para analizar algoritmos de forma matemática y universal, usamos una abstracción llamada **Modelo RAM** (Random Access Machine).

### Modelo RAM
En este modelo, ignoramos detalles como la caché, la temperatura del CPU o la velocidad de reloj específica. Asumimos que:
1.  Cada instrucción simple toma exactamente **1 unidad de tiempo**.
2.  El acceso a cualquier celda de memoria toma exactamente **1 unidad de tiempo**.
3.  Los bucles y subrutinas no son operaciones elementales; son composiciones de ellas.

### Lista de Operaciones Elementales
Cualquiera de las siguientes cuenta como **1 paso**:
- **Aritmética:** `+`, `-`, `*`, `/`, `%`, `floor`, `ceil`.
- **Movimiento de Datos:** Asignación (`a = b`), lectura (`x = A[i]`), escritura/copia.
- **Control:** Comparaciones (`<`, `==`), saltos (llamadas a función, `return`).

> [!warning] Cuidado con las "Operaciones Ocultas"
> En lenguajes de alto nivel (Python, JS), una línea de código puede ocultar muchas operaciones elementales.
> Ejemplo: `lista.sort()` **NO** es una operación elemental; es un algoritmo completo ($\mathcal{O}(n \log n)$).
> Ejemplo: `array1 = array2` (en C++ es copia elemento a elemento $\rightarrow \mathcal{O}(n)$, en Python es referencia $\rightarrow \mathcal{O}(1)$).

## Connections
- **Related to:** [[Notación Asintótica - Algoritmos]], [[Sumatorias Matemáticas - Algoritmos]]

## Application / Example

Contando operaciones en un fragmento de código:

```python
def example(arr):
    n = len(arr)       # 1 op (lectura/asignación)
    total = 0          # 1 op (asignación)
    
    # El encabezado del for incluye:
    # - Inicialización i=0 (1 op)
    # - Comparación i < n (n+1 veces)
    # - Incremento i++ (n veces)
    for i in range(n): 
        total += arr[i] # 2 ops (lectura + suma y asignación) * n veces
        
    return total       # 1 op (retorno)
```

**Costo Total ($T(n)$):**
$$
T(n) \approx 1 + 1 + (n+1) + n + 2n + 1 = 4n + 4
$$
$$
T(n) = \Theta(n)
$$

> [!info] Abstracción vs. Realidad
> El modelo RAM no predice el tiempo en milisegundos, predice el **crecimiento**. Un algoritmo con $100n$ operaciones es $\Theta(n)$, igual que uno con $n$. Para $n$ muy grande, la diferencia constante es irrelevante frente a cambios de orden (ej. $\Theta(n^2)$).

## References
- [[The Algorithm Design Manual by Steven S. Skiena.pdf]]
-  [[Introduction To Algorithms Pro.pdf]]
