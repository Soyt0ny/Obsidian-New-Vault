---
tags:
  - note
  - algorithms
  - pattern
  - sliding-window
status: evergreen
created: 2026-09-17
tech: Python
domain: Algorithms
---

# Sliding Window - Algoritmos

> [!tip] Primo hermano de Two Pointers
> Ver [[Two Pointers - Algoritmos]] para el patrón relacionado. La diferencia clave: Two Pointers busca **pares/tercias** en todo el arreglo; Sliding Window busca la mejor **subsecuencia contigua** (subarray/substring) que cumple una condición.

## Post-it (resumen rapido)

```
sliding window -> una "ventana" [L, R] que se desliza sobre el arreglo / string

usos:        subarray/substring contiguo que cumple una condicion
             (suma maxima, mas largo sin repetir, tamaño fijo, etc.)

tipos:       ventana de tamaño FIJO   -> R avanza, L avanza junto (R - L + 1 == k)
             ventana de tamaño VARIABLE -> R avanza siempre; L avanza solo
                                           cuando la ventana deja de cumplir la condicion

complejidad: O(n) -- cada puntero (L y R) recorre el arreglo a lo sumo una vez
```

## Las dos variantes

### 1. Ventana de tamaño fijo

El tamaño `k` de la ventana es un dato del problema. `R` avanza uno a uno; en cuanto la ventana llega a tamaño `k`, `L` avanza junto con `R` para mantenerlo fijo.

- **Util cuando:** el problema dice explícitamente "subarreglo de tamaño k" (ej: "máxima suma de cualquier subarreglo de tamaño k").
- **Ejemplo canonico:** Máxima suma de subarreglo de tamaño k.

```python
def max_sum_fixed_window(nums, k):
    window_sum = sum(nums[:k])
    best = window_sum
    for r in range(k, len(nums)):
        window_sum += nums[r] - nums[r - k]  # entra nums[r], sale el que quedo fuera
        best = max(best, window_sum)
    return best
```

### 2. Ventana de tamaño variable

`R` siempre avanza. `L` solo avanza cuando la ventana **deja de cumplir** la condición (se "encoge" hasta volver a cumplirla).

- **Util cuando:** buscas la ventana más larga (o más corta) que cumple una condición, y el tamaño no es un dato fijo.
- **Patron clasico:** mientras la condición se rompe, mover `L++`; en cada paso de `R`, actualizar la respuesta.
- **Ejemplos canonicos:**
  - Substring más largo sin caracteres repetidos
  - Subarreglo más corto con suma ≥ target
  - Longest Substring with At Most K Distinct Characters

```python
# Substring mas largo sin caracteres repetidos
def longest_unique_substring(s):
    seen = set()
    l = 0
    best = 0
    for r in range(len(s)):
        while s[r] in seen:
            seen.remove(s[l])
            l += 1
        seen.add(s[r])
        best = max(best, r - l + 1)
    return best
```

## Cuando usar Sliding Window

> [!info] Senales de que el problema pide sliding window
> - "Subarreglo / substring contiguo" (no cualquier subconjunto — tiene que ser contiguo)
> - Se pide un máximo/mínimo/conteo sobre **ventanas** de datos
> - Aparece un tamaño fijo `k`, o una condición que se puede "romper" y "reparar" (suma, conteo de caracteres, etc.)
> - Fuerza bruta sería revisar todas las sub-secuencias — O(n²) o peor — y sliding window lo baja a O(n)

> [!warning] Cuándo NO sirve
> Si la condición no es "monótona" (es decir, agrandar la ventana no garantiza que siga cumpliendo o dejando de cumplir de forma consistente), sliding window simple no aplica — ahí se necesita otra técnica (por ejemplo, prefix sums + hash map, visto en [[Hash Maps - Algoritmos]]).

## El truco mental clave

> [!tip] Por que es O(n) y no O(n²)?
> Aunque hay dos punteros (`L`, `R`), cada uno se mueve **hacia adelante únicamente** y a lo sumo `n` veces en total. El trabajo combinado es `O(2n) = O(n)`, igual que en [[Two Pointers - Algoritmos]].

## Connections
- **Contrast with:** [[Two Pointers - Algoritmos]] — Two Pointers busca pares/tercias en todo el arreglo; Sliding Window busca la mejor ventana contigua
- **Related to:** [[Hash Maps - Algoritmos]] — dentro de la ventana muchas veces se necesita un set/dict para saber qué contiene "ahora mismo"
- **Used in:** [[Análisis de Algoritmos - CUCEI]] — Unidad 2 (fuerza bruta) y Unidad 3 (divide y vencerás) tocan la idea de recorrer subarreglos de forma eficiente

## References
- Source: Nota creada al detectar que el vault referenciaba este patrón desde 2026-06 sin que existiera todavía (gap detectado en auditoría del 2026-09-17).
