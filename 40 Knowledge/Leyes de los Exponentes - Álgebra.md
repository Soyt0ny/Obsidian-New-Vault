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

# Leyes de los Exponentes - Álgebra

## Core Idea
> Las leyes de los exponentes son reglas fijas para operar potencias. Sirven para simplificar expresiones antes de factorizar, resolver ecuaciones, o derivar/integrar en Ecuaciones Diferenciales.

## Explanation

### 1. Producto de potencias con la misma base
$$a^m \cdot a^n = a^{m+n}$$
Ejemplo: $x^3 \cdot x^4 = x^{7}$

> [!warning] Error común
> $a^m \cdot a^n \neq a^{m \cdot n}$. Los exponentes se **suman**, no se multiplican. $x^3 \cdot x^4 = x^7$, no $x^{12}$.

### 2. Cociente de potencias con la misma base
$$\frac{a^m}{a^n} = a^{m-n}, \quad a \neq 0$$
Ejemplo: $\dfrac{x^5}{x^2} = x^{3}$

### 3. Potencia de una potencia
$$(a^m)^n = a^{m \cdot n}$$
Ejemplo: $(x^2)^3 = x^{6}$

### 4. Potencia de un producto
$$(ab)^n = a^n b^n$$
Ejemplo: $(2x)^3 = 2^3 x^3 = 8x^3$

### 5. Potencia de un cociente
$$\left(\frac{a}{b}\right)^n = \frac{a^n}{b^n}, \quad b \neq 0$$
Ejemplo: $\left(\dfrac{x}{3}\right)^2 = \dfrac{x^2}{9}$

### 6. Exponente cero
$$a^0 = 1, \quad a \neq 0$$
No importa qué tan complicada sea la base, si el exponente es 0, el resultado es 1.

### 7. Exponente negativo
$$a^{-n} = \frac{1}{a^n}$$
Ejemplo: $x^{-2} = \dfrac{1}{x^2}$. Un exponente negativo **no** hace el número negativo — lo manda al denominador.

### 8. Exponente fraccionario (raíces)
$$a^{m/n} = \sqrt[n]{a^m} = \left(\sqrt[n]{a}\right)^m$$
Ejemplo: $x^{1/2} = \sqrt{x}$, $\;x^{2/3} = \sqrt[3]{x^2}$

> [!tip] Cómo no perderse
> Todas estas reglas solo se cumplen **con la misma base**. $x^3 \cdot y^4$ no se simplifica con estas leyes — ahí no hay nada que hacer salvo dejarlo como está.

## Connections
- **Prerequisite for:** [[Factorización - Álgebra]] — reconocer patrones de exponentes (cuadrados, cubos) es el primer paso para factorizar
- **Prerequisite for:** [[Ecuaciones Cuadráticas - Álgebra]] — simplificar antes de resolver
- **Used in:** [[Ecuaciones Diferenciales - CUCEI]] — al derivar/integrar potencias de $x$

## Application / Example
```
Simplificar: (x^3 · x^-1)^2 / x^4

Paso 1 (producto, regla 1):     x^3 · x^-1 = x^(3-1) = x^2
Paso 2 (potencia de potencia):  (x^2)^2 = x^4
Paso 3 (cociente, regla 2):     x^4 / x^4 = x^0 = 1

Resultado: 1
```

## References
- Source: Repaso de álgebra, creado a partir de una necesidad detectada en clase de Ecuaciones Diferenciales (2026-09-17).
- Plan original: [[Repaso de Algebra]]
