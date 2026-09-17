---
tags:
  - problem
  - hash-map
  - string
status: evergreen
difficulty: Medium
platform: LeetCode
pattern:
  - HashMap
  - sorting
tech:
  - Python
domain: Algorithms
---

# Group Anagrams

## Description
Dada una lista de strings, agrupar los anagramas juntos. Un anagrama es una palabra que con la misma cantidad de letras y mismas letras se puede reordenar para formar otra palabra (ej. `"eat"`, `"tea"`, `"ate"`).

## Constraints
- $n == \text{strings.length}$
- $1 \le n \le 10^4$
- $0 \le \text{strings}[i].length \le 100$
- Solo letras minusculas del alfabeto ingles

## Approach: Canonical Key with Hash Map

### Intuition
1. Ordenar alfabeticamente la palabra para crear una **llave canonica** (unica para cada grupo de anagramas).
2. Usar esa llave como clave en un diccionario. El valor es una lista con las palabras originales que comparten esa llave.
3. Devolver todas las listas del diccionario.

Para el sort: `sorted(string)` devuelve una **lista de letras** ordenadas, no un string. Por eso se necesita `"".join()` para reconstruir la palabra completa:

```python
"".join(sorted("eat"))   # -> "aet"
```

> [!tip] Llave canonica
> Dos anagramas siempre producen la misma llave cuando se ordenan. Alternativa para strings largos: una tupla de 26 contadores `("a": 1, "b": 0, ..., "t": 1)` — mas rapida, pero mas compleja de escribir.

### Complexity Analysis
- **Time Complexity:** $O(n \cdot k \log k)$ — donde $k$ es la longitud maxima de los strings. El sort domina.
- **Space Complexity:** $O(n \cdot k)$ — almacenamos todos los strings.

## Code Implementation

```python
def group_anagrams(strings):
    grupos = {}

    for string in strings:
        key = "".join(sorted(string))
        grupos.setdefault(key, []).append(string)

    return list(grupos.values())


print(group_anagrams(["eat", "tea", "tan", "ate", "nat", "bat"]))
print(group_anagrams([""]))
print(group_anagrams(["a"]))
```

## Key Insights

> [!info] setdefault: la clave tecnica
> `dict.setdefault(key, []).append(value)` hace dos cosas en una linea: si `key` no existe, la crea con una lista vacia, y luego hace `.append()` al valor de esa clave (sea recien creada o existente). Es el equivalente manual de `defaultdict`.

> [!tip] Por que sorted() sobre Counter()
> `sorted()` es $O(k \log k)$ y mas simple de escribir. Para strings largos (+100 chars), usar un array de 26 contadores es $O(k)$ pero mas propenso a errores en codigo en vivo. En entrevistas, empeza con sort.

## Related Notes
- **Concept:** [[Hash Maps - Algoritmos]] — hash table fundamentals y setdefault
- **Related to:** [[Two Sum - Hash Map - Array - Problem - Algoritmos]] — mismo patron de mapeo
- **Related to:** [[Concatenation of Array - Array - Problem - Algoritmos]] — estructura de arrays
