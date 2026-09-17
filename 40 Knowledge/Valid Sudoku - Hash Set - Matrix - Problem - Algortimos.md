---
tags:
  - problem
  - hash-set
  - matrix
status: evergreen
difficulty: Medium
platform: LeetCode
pattern:
  - Set
tech:
  - Python
domain: Algorithms
---

# Valid Sudoku

## Description
Determinar si un tablero de Sudoku parcialmente lleno es valido. Un Sudoku es valido si en cada fila, cada columna y cada sub-cuadricula de 3x3 no se repiten numeros del 1 al 9. Las celdas vacias (`"."`) se ignoran.

## Constraints
- `tablero.length == 9`
- `tablero[i].length == 9`
- `tablero[i][j]` es un digito `"1"`-`"9"` o `"."`

## Approach: Hash Set per Dimension (Three Parallel Histories)

### Intuition

El problema se reduce a una pregunta por celda: "este numero ya aparecio en mi fila, en mi columna o en mi caja 3x3?"

Para responderla en $O(1)$ por pregunta, mantenemos **tres listas de sets**, una por dimension:

| Lista | Indexada por | Guarda |
|---|---|---|
| `filas[fila]` | indice de fila (0-8) | valores ya vistos en esa fila |
| `columnas[col]` | indice de columna (0-8) | valores ya vistos en esa columna |
| `cajas[caja]` | indice de caja 3x3 (0-8) | valores ya vistos en esa sub-cuadricula |

Cada visita a una celda tiene tres pasos:

1. Si el valor es `"."`, lo saltamos (`continue`).
2. Si el valor ya esta en `filas[fila]`, `columnas[col]` o `cajas[caja]` -> Sudoku invalido.
3. Si no esta en ninguna, lo agregamos a las tres.

### La formula de la caja

Para saber en que caja 3x3 estamos, se usa la formula:

```
caja = (fila // 3) * 3 + (columna // 3)
```

Esto "achica" la grilla 9x9 a una mini-grilla 3x3 de cajas:

```
       col//3 ->   0    1    2
                   -----------
fila//3 | 0   |  c0 | c1 | c2 |
        | 1   |  c3 | c4 | c5 |
        | 2   |  c6 | c7 | c8 |
```

- `fila // 3` dice en que "macro-fila" de cajas estamos (0, 1, o 2)
- `columna // 3` dice en que "macro-columna" de cajas estamos (0, 1, o 2)
- Se multiplica `fila // 3` por 3 porque cada macro-fila tiene 3 cajas

**Ejemplo:** celda `(fila=4, columna=7)`:
- `4 // 3 = 1` (segunda macro-fila de cajas: filas 3-5)
- `7 // 3 = 2` (tercera macro-columna: columnas 6-8)
- `caja = 1 * 3 + 2 = 5` -> la caja del medio-derecha

### Complexity Analysis
- **Time Complexity:** $O(1)$ — el tablero siempre es 9x9 (81 celdas), operacion constante
- **Space Complexity:** $O(1)$ — 27 sets en total (9 filas + 9 columnas + 9 cajas), cada uno con maximo 9 elementos

## Code Implementation

```python
def validar_sudoku(tablero):
    filas = [set() for _ in range(9)]
    columnas = [set() for _ in range(9)]
    cajas = [set() for _ in range(9)]

    for fila, valores in enumerate(tablero):
        for columna, valor in enumerate(valores):
            if valor == ".":
                continue

            caja = (fila // 3) * 3 + (columna // 3)

            if valor in filas[fila]:
                return False
            if valor in columnas[columna]:
                return False
            if valor in cajas[caja]:
                return False

            filas[fila].add(valor)
            columnas[columna].add(valor)
            cajas[caja].add(valor)

    return True
```

## Key Insights

> [!tip] Sets paralelos, no un set por caja
> La solucion usa **tres listas de sets** (filas, columnas, cajas), no un solo set por cada caja 3x3. Cada lista registra una dimension diferente del tablero.

> [!info] Por que $O(1)$ en vez de $O(n)$
> Aunque hay bucles anidados, el tablero de Sudoku tiene tamano fijo (9x9 = 81 celdas). La complejidad es constante — no crece con la entrada.

> [!warning] Check antes de store
> Primero se verifica si el valor YA existe en el set (`in`), y solo si no existe se agrega (`.add()`). Si guardaras antes de verificar, nunca detectarias duplicados.

## Related Notes
- **Concept:** [[Sets - Algoritmos]] — membership test con sets
- **Related to:** [[Hash Maps - Algoritmos]] — mismo hash table subyacente
- **Related to:** [[Contains Duplicate - Hash - Set - Problem - Algortimos]] — deteccion de duplicados
