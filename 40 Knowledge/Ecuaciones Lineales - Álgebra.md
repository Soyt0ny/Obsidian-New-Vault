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

# Ecuaciones Lineales - Álgebra

## Core Idea
> Una ecuación lineal es de la forma $ax + b = 0$: la incógnita solo aparece elevada a la potencia 1. Siempre tiene **una** solución (salvo casos degenerados).

## Explanation

### Ecuación lineal con una incógnita
$$ax + b = 0 \;\Rightarrow\; x = -\frac{b}{a}, \quad a \neq 0$$

**Pasos para resolver cualquier ecuación lineal:**
1. Elimina paréntesis (propiedad distributiva).
2. Junta todos los términos con $x$ de un lado, y los números del otro.
3. Divide entre el coeficiente de $x$.

Ejemplo:
```
3(x - 2) = 5x + 4
3x - 6 = 5x + 4        (distribuir)
3x - 5x = 4 + 6         (juntar términos)
-2x = 10
x = -5
```

> [!warning] Casos especiales
> - Si al simplificar queda algo como $0 = 0$ → infinitas soluciones (la ecuación es una identidad).
> - Si queda algo como $0 = 5$ → no hay solución.

### Sistemas de 2 ecuaciones lineales (2 incógnitas)
$$\begin{cases} a_1x + b_1y = c_1 \\ a_2x + b_2y = c_2 \end{cases}$$

**Método de sustitución:** despeja una variable en una ecuación, y sustitúyela en la otra.
```
x + y = 10
2x - y = 5

De la 1ra: y = 10 - x
Sustituyo en la 2da: 2x - (10-x) = 5 -> 3x - 10 = 5 -> x = 5
y = 10 - 5 = 5
```

**Método de eliminación:** multiplica una o ambas ecuaciones para que una variable se cancele al sumarlas.
```
x + y = 10
x - y = 2

Sumo ambas ecuaciones: 2x = 12 -> x = 6
Sustituyo: 6 + y = 10 -> y = 4
```

## Connections
- **Prerequisite for:** [[Ecuaciones Cuadráticas - Álgebra]]
- **Related to:** [[Factorización - Álgebra]] — factorizar a veces convierte una ecuación complicada en varias ecuaciones lineales simples
- **Used in:** [[Ecuaciones Diferenciales - CUCEI]] — Unidad 2, al resolver por coeficientes indeterminados aparecen sistemas lineales para encontrar constantes

## Application / Example
```
Resolver: 2(x+3) - 4 = 3x - (x-2)

2x + 6 - 4 = 3x - x + 2
2x + 2 = 2x + 2

Esto es una identidad (0=0) -> infinitas soluciones, se cumple para cualquier x.
```

## References
- Source: Repaso de álgebra, creado a partir de una necesidad detectada en clase de Ecuaciones Diferenciales (2026-09-17).
- Plan original: [[Repaso de Algebra]]
