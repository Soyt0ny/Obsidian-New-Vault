---
tags:
  - note
  - math
  - algebra
status: evergreen
created: 2026-09-17
tech:
domain: Math
---

# Factorización - Álgebra

## Core Idea
> Factorizar es escribir una expresión como un **producto** de factores en vez de una suma/resta. Es el paso obligatorio antes de resolver ecuaciones cuadráticas y antes de simplificar fracciones algebraicas.

## Explanation

> [!tip] Regla de oro
> Antes de intentar cualquier método de abajo, siempre revisa primero si hay un **factor común**. Es el error más frecuente: aplicar un método complicado cuando un factor común simple ya resolvía todo.

### 1. Factor común
Saca el término que se repite en todos los sumandos.
$$ax + ay = a(x + y)$$
Ejemplo: $6x^2 + 9x = 3x(2x + 3)$

### 2. Diferencia de cuadrados
$$a^2 - b^2 = (a+b)(a-b)$$
Ejemplo: $x^2 - 25 = (x+5)(x-5)$

> [!warning] No existe la "suma de cuadrados"
> $a^2 + b^2$ **no se factoriza** con números reales. Solo la diferencia ($a^2 - b^2$) tiene esta forma.

### 3. Trinomio cuadrado perfecto
$$a^2 \pm 2ab + b^2 = (a \pm b)^2$$
Ejemplo: $x^2 + 6x + 9 = (x+3)^2$ (porque $2 \cdot x \cdot 3 = 6x$ coincide)

### 4. Trinomio de la forma $x^2 + bx + c$ (coeficiente 1)
Busca dos números $p, q$ tal que $p \cdot q = c$ y $p + q = b$.
$$x^2 + bx + c = (x+p)(x+q)$$
Ejemplo: $x^2 + 5x + 6$ → busco dos números que multiplicados den 6 y sumados den 5 → 2 y 3 → $(x+2)(x+3)$

### 5. Trinomio de la forma $ax^2 + bx + c$ (coeficiente $a \neq 1$)
Método del "aspa simple" / tanteo: busca $p, q$ tal que $p \cdot q = a \cdot c$ y $p + q = b$, y reescribe el término medio.
Ejemplo: $2x^2 + 7x + 3$
```
a·c = 2·3 = 6, necesito p+q=7 y p·q=6  ->  p=6, q=1
2x^2 + 6x + 1x + 3
2x(x+3) + 1(x+3)
(2x+1)(x+3)
```

### 6. Factorización por agrupación (4 términos)
Agrupa de 2 en 2, saca factor común de cada grupo, y luego el factor común de los grupos.
Ejemplo: $x^3 + 3x^2 + 2x + 6 = x^2(x+3) + 2(x+3) = (x+3)(x^2+2)$

### 7. Suma y diferencia de cubos
$$a^3 + b^3 = (a+b)(a^2 - ab + b^2)$$
$$a^3 - b^3 = (a-b)(a^2 + ab + b^2)$$
Ejemplo: $x^3 - 8 = (x-2)(x^2+2x+4)$

## Connections
- **Prerequisite for:** [[Ecuaciones Cuadráticas - Álgebra]] — el primer método para resolver $ax^2+bx+c=0$ es factorizar
- **Related to:** [[Leyes de los Exponentes - Álgebra]] — reconocer cuadrados/cubos depende de las leyes de exponentes
- **Used in:** [[Ecuaciones Diferenciales - CUCEI]] — al simplificar antes de separar variables o integrar

## Application / Example
```
Factorizar completamente: 2x^3 - 8x

Paso 1 (factor común):        2x(x^2 - 4)
Paso 2 (diferencia de cuadrados dentro): 2x(x-2)(x+2)

Resultado: 2x(x-2)(x+2)
```

## References
- Source: Repaso de álgebra, creado a partir de una necesidad detectada en clase de Ecuaciones Diferenciales (2026-09-17).
- Plan original: [[Repaso de Algebra]]
