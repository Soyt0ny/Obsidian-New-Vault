---
tags:
  - note
  - algorithms
  - data-structures
  - set
  - postit
  - amazon-prep
status: evergreen
created: 2026-06-22
tech: Python
domain: Algorithms
---

# Set — Post-it

> [!quote] Definicion
> **Set** → coleccion **desordenada** de elementos **unicos** con busqueda, insercion y eliminacion en **O(1) promedio**. Es un hash map donde solo importan las claves: el valor es simplemente la **presencia**.

## Cuando usarlo

- **Detectar duplicados** → ¿ya lo vi?
- **Membership test** → ¿esta x en la coleccion?
- **Comparar 2 conjuntos de datos** (interseccion, union, diferencia)
- **Eliminar duplicados** de una lista

## Metodos clave

| Metodo | Que hace | Falla si no existe? |
|---|---|---|
| `s.add(x)` | agregar elemento | NO |
| `s.remove(x)` | eliminar elemento | **SI** (KeyError) |
| `s.discard(x)` | eliminar elemento | NO |
| `s.pop()` | eliminar y devolver un elemento arbitrario | SI si esta vacio |
| `x in s` | verificar pertenencia | NO |

> [!tip] `remove` vs `discard`
> - Si **estas seguro** que x existe → `remove` (te avisa si te equivocaste)
> - Si **no sabes** si existe → `discard` (silencioso, no rompe)

## Algebra de conjuntos (importante para problemas)

| Operador | Nombre | Ejemplo | Resultado |
|---|---|---|---|
| `a & b` | interseccion | `{1,2} & {2,3}` | `{2}` |
| `a \| b` | union | `{1,2} \| {2,3}` | `{1, 2, 3}` |
| `a - b` | diferencia | `{1,2} - {2,3}` | `{1}` |
| `a ^ b` | diferencia simetrica | `{1,2} ^ {2,3}` | `{1, 3}` |

## Restriccion critica

> [!warning] Solo elementos hasheables
> Para que un elemento pueda estar en un `set` (o ser clave de un dict) debe ser **inmutable**.
> - Tuplas, strings, numeros: OK
> - Listas, sets, dicts: **NO** (son mutables, no se pueden hashear)

## Patron canonico (detectar duplicado)

```python
def contiene_duplicado(nums):
    vistos = set()
    for num in nums:
        if num in vistos:
            return True
        vistos.add(num)
    return False
```

## Truco mental rapido

> [!tip] La pregunta para detectar el patron
> "¿Solo necesito saber si algo esta o no esta, sin asociar un valor?"
> Si la respuesta es si → **Set**.
> Si ademas necesito asociar un valor → [[Hash Maps - Postit - Algoritmos]].

## Conexion

- Version larga con detalle: [[Sets - Algoritmos]]
- Complemento: [[Hash Maps - Algoritmos]] — set con valores
- Plan: [[Prep Amazon Internship]]
