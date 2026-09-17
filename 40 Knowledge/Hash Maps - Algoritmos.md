---
tags:
  - note
  - algorithms
  - data-structures
  - hash-map
  - leetcode
  - amazon-prep
status: evergreen
created: 2026-06-20
tech: Python
domain: Algorithms
---

# Hash Maps - Algoritmos

> [!tip] Post-it rapido
> Para referencia rapida de pantalla / escritorio, ver: [[Hash Maps - Postit - Algoritmos]]

## Core Idea
> Un Hash Map (en Python: `dict`) mapea **claves -> valores** con acceso, insercion y busqueda en tiempo $O(1)$ en promedio, gracias a una funcion hash que determina directamente la ubicacion interna del valor.

## Explanation

### Como se almacenan los arrays en memoria

Cuando se asigna una lista, la computadora la guarda en un bloque de **memoria contigua**. Es decir, el primer espacio es 1000, el segundo 1004, el tercero 1008 (en el caso de enteros, donde cada entero pesa 4 bytes).

La manera que tiene la CPU de encontrar el valor rapido es con una simple multiplicacion: encuentra el **inicio de la lista** (en este caso 1000) y multiplica el **peso de los elementos** (4 bytes) por la **posicion solicitada**. De esta manera accede al dato almacenado en ese espacio de memoria de manera instantanea -- $O(1)$.

```
direccion_real = direccion_base + (indice x tamano_elemento)
```

Una sola operacion aritmetica, sin importar si el indice es 0 o 1,000,000. Por eso el acceso por indice es $O(1)$ real, no solo "promedio".

> [!warning] Listas ligadas: $O(n)$ de verdad
> En las **listas ligadas** si es necesario recorrer cada elemento hasta encontrarlo, debido a que al no estar en espacios de memoria contiguos, la CPU tiene que acceder uno por uno siguiendo los punteros. No existe la aritmetica de punteros.

### La funcion hash

La funcion hash basicamente **convierte cualquier cosa en un numero**, y siempre que entres con el mismo input te dara el mismo resultado.

La manera en la que un hash se calcula para ubicar elementos en un Hash Map es:

```
numero_de_cajon = numero_a_buscar % cantidad_de_cajones
```

El operador `%` (modulo) devuelve el residuo de dividir `a` entre `b`. De esta manera, siempre que busques un numero se guardara en el mismo cajon.

### Colisiones: el peor caso

Lo peor que puede suceder en un Hash Map se llama **colision**. Esto pasa cuando un numero distinto al que ya esta almacenado **da el mismo residuo**, dando como consecuencia guardarlo en el mismo cajon.

Cuando eso pasa, ese cajon ya no contiene un solo elemento, sino varios — formando una mini-lista de los elementos que colisionaron. Al momento de buscar en ese cajon, el algoritmo tiene que recorrer cada elemento de esa lista, haciendo que el tiempo suba a $O(n)$.

> [!warning] Por que se dice $O(1)$ "en promedio"
> El caso promedio del Hash Map es $O(1)$ porque las colisiones se distribuyen uniformemente entre los cajones cuando la funcion hash es buena. Pero en el **peor caso patologico** (todo cae en el mismo cajon), se degrada a $O(n)$. En entrevistas, se acepta $O(1)$ en promedio y se menciona la degradacion como matiz.

### setdefault: la forma sin librerias de inicializar claves

En Python, `dict.setdefault(clave, valor_default)`:

1. Si la clave **ya existe** -> devuelve su valor actual.
2. Si la clave **no existe** -> la crea con `valor_default` y devuelve ese valor.

Es la forma manual (sin usar `defaultdict` de `collections`) de "obtener o crear" una entrada en el diccionario. Patron tipico:

```python
grupos.setdefault("aet", []).append("eat")
```

Una sola linea resuelve el caso "primera vez" y "siguientes veces".

## Cuando usar Hash Map

> [!info] Indicadores de que necesitas un Hash Map
> - Necesitas buscar un elemento en $O(1)$ en vez de $O(n)$?
> - Necesitas **contar frecuencias** de elementos?
> - Necesitas **detectar duplicados**?
> - Necesitas **agrupar elementos** por alguna propiedad (como en Group Anagrams)?

> [!warning] Trade-off espacio vs tiempo
> El Hash Map **gasta mas memoria** que un array simple para ganar velocidad. Es una decision de ingenieria que se repite todo el tiempo. En entrevistas, **mencionar este trade-off** demuestra que entiendes, no solo memorizaste.

## Application / Example

El patron general de "buscar o crear" con `setdefault` se usa en muchos problemas. Ejemplo tipico: contar frecuencias sin usar `Counter`:

```python
def contar_frecuencias(palabras):
    frecuencias = {}
    for palabra in palabras:
        frecuencias[palabra] = frecuencias.get(palabra, 0) + 1
    return frecuencias
```

## Connections
- **Related to:** [[Sets - Algoritmos]] — un set es un hash map sin valores
- **Related to:** [[Notacion Asintotica - Algoritmos]] — para entender $O(1)$, $O(n)$, $O(n \log n)$
- **Related to:** [[Two Sum - Hash Map - Array - Problem - Algortimos]] — complemento con dict
- **Related to:** [[Group Anagrams - Hash Map - String - Problem - Algortimos]] — llave canonica con setdefault
- **Related to:** [[Valid Sudoku - Hash Set - Matrix - Problem - Algortimos]] — sets paralelos
- **Related to:** [[Contains Duplicate - Hash - Set - Problem - Algortimos]] — mismo hash table, distinto uso
- **Related to:** [[Concatenation of Array - Array - Problem - Algortimos]] — arrays en memoria contigua
- **Contrast with:** [[Vectores - C++]] — implementacion distinta en C++ (`std::unordered_map`)

## References
- Source: Sesion de preparacion Amazon — Dia 1 (Junio 19-20, 2026).
- Problemas de hash map: [[Two Sum - Hash Map - Array - Problem - Algortimos]], [[Group Anagrams - Hash Map - String - Problem - Algortimos]], [[Valid Sudoku - Hash Set - Matrix - Problem - Algortimos]]
