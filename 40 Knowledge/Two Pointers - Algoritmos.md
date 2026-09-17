---
tags:
  - note
  - algorithms
  - pattern
  - two-pointers
  - amazon-prep
status: evergreen
created: 2026-06-22
tech: Python
domain: Algorithms
---

# Two Pointers - Algoritmos

> [!tip] Post-it rapido
> Para referencia rapida de pantalla / escritorio, ver: [[Two Pointers - Postit - Algoritmos]]

## Post-it (resumen rapido)

```
two pointers -> 2 indices que se mueven sobre el arreglo / string

usos:        buscar pares con target / palindromos / invertir /
             particionar / eliminar duplicados in-place /
             container con agua / subconjuntos

setup:       .L = 0, R = n-1      (opuestos)
             .slow = 0, fast = 1  (misma direccion, Floyd)

movimiento:  segun condicion — si suma < target L++,
             si suma > target R--
             regla de oro: mover el lado menos prometedor

complejidad: O(n) — cada puntero se mueve a lo sumo n veces

pre-requisito (variantes opuestos): array ORDENADO
```

## Las dos variantes

### 1. Punteros opuestos (`L = 0, R = n-1`)

Los punteros arrancan en extremos opuestos y se acercan al centro.

- **Util cuando:** el arreglo esta ordenado (o lo podes ordenar) y queres encontrar un par, una tercia, o un area.
- **Regla de movimiento:** el puntero que movés depende de la condicion. Si `nums[L] + nums[R] < target` -> L++. Si `> target` -> R--. Si `== target` -> match.
- **Ejemplos canonicos:**
  - 3Sum (visto en [[3Sum - Array - Two Pointers - Problem - Algoritmos]])
  - Container With Most Water
  - Valid Palindrome
  - Two Sum II (arreglo ordenado)

> [!tip] Por que ordenar primero?
> Sin orden no podes decidir que puntero mover. Si `nums[L] + nums[R] < target`, no sabes si el problema es que `L` es chico o `R` es grande. Con el arreglo ordenado, la direccion es **unica**.

### 2. Punteros misma direccion (`slow`, `fast`)

Ambos punteros arrancan al inicio y avanzan en la misma direccion, pero a velocidades diferentes (o con un desfase).

- **Util cuando:** queres modificar el arreglo **in-place** o detectar ciclos / duplicados en un solo pase.
- **Patron clasico:** `slow` lleva la posicion "limpia" y `fast` explora. Cuando `fast` encuentra algo valido, lo copia en `slow` y avanza.
- **Ejemplos canonicos:**
  - Remove Duplicates from Sorted Array
  - Move Zeroes
  - Linked List Cycle (Floyd)
  - Partition array por pivot (quicksort)

```python
# Patron slow/fast para quitar duplicados in-place
def remove_duplicates(nums):
    slow = 0
    for fast in range(1, len(nums)):
        if nums[fast] != nums[slow]:
            slow += 1
            nums[slow] = nums[fast]
    return slow + 1
```

## Cuando usar Two Pointers

> [!info] Senales de que el problema pide two pointers
> - "Encontrar dos elementos que..." y el input es arreglo/string
> - "Verificar palindromo"
> - "Contenedor / trampa de agua" (areas entre lineas)
> - "Eliminar / mover elementos in-place" (sin crear nuevo arreglo)
> - El input esta **ordenado** o **puede ordenarse**
> - Hay un target numerico claro (suma, diferencia, etc.)

> [!warning] Si el input NO esta ordenado y no podes ordenarlo
> Two pointers en variantes opuestos **no funciona** sin orden. En ese caso, el camino es hash map (visto en [[Hash Maps - Algoritmos]]) o fuerza bruta con optimizacion parcial.

## El truco mental clave

> [!tip] Por que es O(n) y no O(n²)?
> Aunque parece un doble bucle, en realidad **cada puntero se mueve a lo sumo n veces** en total, no n². El total de movimientos combinados es a lo sumo `2n`. Por eso es lineal, no cuadratico. Esto es valido siempre que cada puntero solo avance (nunca retroceda) o que cada iteracion elimine al menos un candidato.

## Connections
- **Used in:** [[3Sum - Array - Two Pointers - Problem - Algoritmos]] — variante opuestos con anchor
- **Related to:** [[Hash Maps - Algoritmos]] — alternativa cuando el input no se puede ordenar
- **Related to:** [[Notación Asintótica - Algoritmos]] — para entender por que O(n) y no O(n²)
- **Contrast with:** [[Sliding Window - Algoritmos]] — patron "primo hermano" para subarrays/substrings

## References
- Source: Sesion de preparacion Amazon — Dia 2 (Junio 22, 2026).
- Plan original: [[Prep Amazon Internship]]
