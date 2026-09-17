---
tags:
  - note
  - algorithms
  - pattern
  - two-pointers
  - postit
  - amazon-prep
status: evergreen
created: 2026-06-22
tech: Python
domain: Algorithms
---

# Two Pointers — Post-it

> [!quote] Definicion
> **Two Pointers** → 2 indices que se mueven sobre el mismo arreglo / string para resolver en **O(n)** lo que con fuerza bruta seria O(n²).

## Cuando usarlo

- **Buscar par / tercia con target** → 2Sum, 3Sum, 4Sum
- **Palindromo** → Valid Palindrome
- **Invertir in-place** → Reverse String
- **Particionar** → Move Zeroes, quicksort pivot
- **Eliminar duplicados in-place** → Remove Duplicates
- **Container / trampa de agua** → Container With Most Water

## Las 2 variantes

| Variante | Setup | Pre-requisito | Caso de uso tipico |
|---|---|---|---|
| **Opuestos** | `L = 0, R = n-1` | array **ordenado** | buscar par, palindromo, area |
| **Misma dir (slow/fast)** | `slow = 0, fast = 1` | sin orden | in-place, detectar ciclo |

## Reglas de movimiento

> [!tip] Opuestos — mover el lado **menos prometedor**
> - `suma < target` → **L++**
> - `suma > target` → **R--**
> - `suma == target` → match, ambos avanzan + **dedup**

> [!tip] Misma dir — `slow` lleva la posicion **limpia**
> - `fast` valido y distinto a `slow` → copiar a `slow`, `slow++`
> - `fast` siempre avanza (es el explorador)

## Complejidad

> [!warning] Ojo — no es O(n²)
> Aunque tiene `while` dentro de `for`, **cada puntero se mueve a lo sumo n veces** → total **O(n)**.
> La clave: cada puntero solo avanza (nunca retrocede) en un sentido, o solo se cierra en el otro.

## Pre-requisito clave

> [!warning] Sin orden, no funciona la variante opuesta
> - **Opuestos**: array **ORDENADO** (o se puede ordenar)
> - **Misma dir**: NO requiere orden
> - Si no podes ordenar y necesitas opuestos → usar [[Hash Maps - Algoritmos]] en su lugar

## Patron canonico (slow/fast → remove duplicates)

```python
def remove_duplicates(nums):
    slow = 0
    for fast in range(1, len(nums)):
        if nums[fast] != nums[slow]:
            slow += 1
            nums[slow] = nums[fast]
    return slow + 1
```

## Truco mental rapido

> [!tip] La pregunta para detectar el patron
> "¿Puedo decidir cual de los dos indices mover segun una condicion simple (suma, comparacion)?"
> Si la respuesta es si → **two pointers**.

## Conexion

- Version larga con detalle: [[Two Pointers - Algoritmos]]
- Ejemplo aplicado: [[3Sum - Array - Two Pointers - Problem - Algoritmos]]
- Plan: [[Prep Amazon Internship]]
