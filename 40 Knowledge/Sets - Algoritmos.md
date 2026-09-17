---
tags:
  - note
  - algorithms
  - data-structures
  - set
  - amazon-prep
status: evergreen
created: 2026-06-20
tech: Python
domain: Algorithms
---

# Sets - Algoritmos

> [!tip] Post-it rapido
> Para referencia rapida de pantalla / escritorio, ver: [[Sets - Postit - Algoritmos]]

## Core Idea
> Un Set (en Python: `set`) es una coleccion **desordenada** de elementos **unicos** con busqueda, insercion y eliminacion en $O(1)$ promedio. Internamente es un hash table sin valores — solo las claves.

## Explanation

### Set vs Hash Map

Un `set` es un **hash map donde solo nos importan las claves**. La funcion hash funciona igual: convierte el elemento en un numero, aplica modulo, y lo guarda en un cajon. Pero no hay valor asociado — el elemento esta (presente) o no esta (ausente).

| Hash Map (`dict`) | Set (`set`) |
|---|---|
| Clave -> Valor | Solo clave (valor = presencia) |
| `dict["a"] = 1` | `set.add("a")` |
| Busqueda de valor por clave | Busqueda de pertenencia |
| Util para: frecuencias, agrupacion | Util para: deduplicacion, membresia |

### Operaciones principales

```python
s = set()           # set vacio
s = {1, 2, 3}       # set literal (no confundir con dict)

s.add(4)            # agregar elemento
s.remove(2)         # eliminar (error si no existe)
s.discard(9)        # eliminar (seguro, no error)

1 in s              # membership test -- O(1)
len(s)              # cantidad de elementos unicos

# Set algebra
a = {1, 2, 3}
b = {3, 4, 5}

a & b               # interseccion -> {3}
a | b               # union -> {1, 2, 3, 4, 5}
a - b               # diferencia -> {1, 2}
a ^ b               # diferencia simetrica -> {1, 2, 4, 5}
```

### Como funciona internamente

El mismo principio del Hash Map:

```
numero_de_cajon = hash(elemento) % cantidad_de_cajones
```

La diferencia es que cada cajon solo guarda la presencia del elemento (no un valor asociado). Al hacer `x in s`, la funcion hash determina que cajon revisar, y si el elemento esta ahi, la respuesta es `True` en $O(1)$.

> [!info] Las tuplas son hashables, las listas no
> Para que un elemento pueda estar en un `set` debe ser **hasheable** (inmutable). Las tuplas funcionan, las listas no. Esto sale seguido en entrevistas.

### Cuando usar Set

- **Detectar duplicados**: si un elemento ya aparecio
- **Membership test**: preguntar "esta X en la coleccion?" repetidamente
- **Interseccion/Union entre colecciones**: comparar dos conjuntos de datos
- **Eliminar duplicados**: convertir una lista a set y volver a lista

> [!warning] No confundir con Hash Map
> Si necesitas asociar un VALOR a cada clave (contar frecuencias, agrupar), usa `dict`. Si solo necesitas saber si algo existe o no, usa `set`.

## Connections
- **Same mechanism:** [[Hash Maps - Algoritmos]] — mismo hash table, distinta API
- **Related to:** [[Contains Duplicate - Hash - Set - Problem - Algoritmos]] — deteccion de duplicados con set
- **Related to:** [[Valid Sudoku - Hash Set - Matrix - Problem - Algoritmos]] — membership test con sets paralelos
- **Contrast with:** [[Vectores - C++]] — `std::unordered_set` como implementacion

## Application / Example

El patron clasico: detectar si un elemento ya fue visto.

```python
def contiene_duplicado(nums):
    vistos = set()
    for num in nums:
        if num in vistos:
            return True
        vistos.add(num)
    return False
```

## References
- Source: Sesion de preparacion Amazon — Dia 1 (Junio 19-20, 2026).
