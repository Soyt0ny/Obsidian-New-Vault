---
tags:
  - note
  - algorithms
  - data-structures
  - hash-map
  - postit
  - amazon-prep
status: evergreen
created: 2026-06-22
tech: Python
domain: Algorithms
---

# Hash Map — Post-it

> [!quote] Definicion
> **Hash Map** → estructura que mapea **clave → valor** con acceso, insercion y busqueda en **O(1) promedio**.

## Cuando usarlo

- **Buscar** un elemento en O(1) en vez de O(n)
- **Contar frecuencias** (cuantas veces aparece cada cosa)
- **Detectar duplicados** (¿ya lo vi?)
- **Agrupar elementos** por alguna propiedad (anagramas, etc.)

## Metodos clave

| Metodo | Que hace | Crea entrada? |
|---|---|---|
| `dict[clave] = valor` | asignar / sobrescribir | si |
| `dict.get(clave, default)` | leer sin riesgo | NO |
| `dict.setdefault(clave, default)` | leer, crear si no existe | si |
| `clave in dict` | verificar existencia | NO |
| `dict.pop(clave)` | eliminar y devolver | NO |

> [!tip] El par clave
> `setdefault` (crea si no existe) ↔ `get` (lee sin crear)
> Son el yin y el yang de "obtener o crear" en un dict.

## Colisiones — el peor caso

> [!warning] No es "el mismo elemento"
> Una colision pasa cuando **dos claves DISTINTAS caen en el mismo cajon** (mismo residuo del `hash % n_cajones`). Eso degrada el cajon a una mini-lista y la busqueda pasa de O(1) a O(n).

| Caso | Complejidad | Cuando ocurre |
|---|---|---|
| Promedio | O(1) | funcion hash bien distribuida |
| Peor caso | O(n) | todas las claves en el mismo cajon |

## Trade-off

> [!warning] Espacio vs tiempo
> Hash Map **gasta mas memoria** que un array simple a cambio de velocidad. Es una decision de diseno que se repite siempre — **mencionarla en entrevistas** demuestra que entendes el trade-off, no solo memorizaste.

## Patron canonico (contar frecuencias sin Counter)

```python
def contar_frecuencias(palabras):
    frecuencias = {}
    for palabra in palabras:
        frecuencias[palabra] = frecuencias.get(palabra, 0) + 1
    return frecuencias
```

## Truco mental rapido

> [!tip] La pregunta para detectar el patron
> "¿Necesito buscar, contar, o agrupar por clave en O(1)?"
> Si la respuesta es si → **Hash Map**.
> Si solo necesito saber si algo esta → usar [[Sets - Postit - Algoritmos]] en su lugar.

## Conexion

- Version larga con detalle: [[Hash Maps - Algoritmos]]
- Complemento: [[Sets - Algoritmos]] — un set es un hash map sin valores
- Plan: [[Prep Amazon Internship]]
