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

# Ecuaciones Cuadráticas - Álgebra

## Core Idea
> Una ecuación cuadrática tiene la forma $ax^2 + bx + c = 0$, con $a \neq 0$. Tiene hasta 2 soluciones. Hay 3 formas de resolverla — elige la más rápida según el caso.

## Explanation

### Método 1: Factorización (el más rápido, cuando aplica)
Si $ax^2+bx+c$ se puede factorizar (ver [[Factorización - Álgebra]]), cada factor igualado a cero da una solución.
```
x^2 - 5x + 6 = 0
(x-2)(x-3) = 0
x-2=0 -> x=2       x-3=0 -> x=3
```

### Método 2: Completar el cuadrado
Sirve cuando no factoriza fácil, y además es la base para entender de dónde sale la fórmula general.
```
x^2 + 6x - 7 = 0
x^2 + 6x = 7
x^2 + 6x + 9 = 7 + 9      (sumo (b/2)^2 = 9 en ambos lados)
(x+3)^2 = 16
x+3 = ±4
x = 1  o  x = -7
```

### Método 3: Fórmula general (siempre funciona)
$$x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$$
Ejemplo: $2x^2 + 3x - 2 = 0$ → $a=2, b=3, c=-2$
```
x = (-3 ± √(9 - 4·2·(-2))) / (2·2)
x = (-3 ± √25) / 4
x = (-3 ± 5) / 4
x = 1/2   o   x = -2
```

### El discriminante ($\Delta = b^2 - 4ac$) te dice qué esperar ANTES de resolver
> [!info] Lee el discriminante primero
> - $\Delta > 0$ → 2 soluciones reales distintas
> - $\Delta = 0$ → 1 solución real (doble)
> - $\Delta < 0$ → 2 soluciones complejas (no reales)

## Connections
- **Prerequisite for:** [[Factorización - Álgebra]] (relación en ambos sentidos: factorizar resuelve, y resolver revela la factorización)
- **Related to:** [[Leyes de los Exponentes - Álgebra]] — simplificar antes de aplicar la fórmula
- **Used in:** [[Ecuaciones Diferenciales - CUCEI]] — Unidad 2 (orden superior): para una ecuación homogénea con coeficientes constantes, la "ecuación característica" es literalmente una cuadrática (o de mayor grado), y el discriminante decide si la solución tiene raíces reales distintas, una raíz doble, o raíces complejas (oscilación). Es la misma tabla de arriba, aplicada a un problema de ecuaciones diferenciales.

## Application / Example
```
Ecuación diferencial (Unidad 2): y'' + 5y' + 6y = 0
Ecuación característica:          r^2 + 5r + 6 = 0
Se resuelve exactamente como una cuadrática normal:
(r+2)(r+3) = 0  ->  r = -2, r = -3
Solución de la ecuación diferencial: y = C1·e^(-2x) + C2·e^(-3x)
```
> Este es el motivo por el que dominar cuadráticas no es "solo álgebra" — es directamente la mitad del trabajo de la Unidad 2 de Ecuaciones Diferenciales.

## References
- Source: Repaso de álgebra, creado a partir de una necesidad detectada en clase de Ecuaciones Diferenciales (2026-09-17).
- Plan original: [[Repaso de Algebra]]
