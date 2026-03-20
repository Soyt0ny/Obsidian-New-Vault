---
tags:
  - note
status: evergreen
created: 2026-03-19
tech:
  - C++
  - Python
domain: Algorithms
---

# Sumatorias Matemáticas - Algoritmos

## Core Idea
> Las sumatorias son la herramienta matemática fundamental para contabilizar el número exacto de operaciones en un algoritmo, permitiendo derivar su complejidad asintótica ($\mathcal{O}(n)$).

## Explanation

Entender sumatorias es vital para analizar bucles y estructuras iterativas. Las **tres fórmulas esenciales** que debes memorizar son:

> [!tip] Fórmulas Primarias
> 1. **Constante:** $\sum_{i=1}^{n} k = k \cdot n$
> 2. **Lineal (Gauss):** $\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$
> 3. **Cuadrática:** $\sum_{i=1}^{n} i^{2} = \frac{n(n+1)(2n+1)}{6}$

### Regla de Cambio de Límites
Cuando una suma no empieza en 1, se calcula restando la parte inicial faltante a la suma total:

$$
\sum_{i=a}^{b} f(i) = \sum_{i=1}^{b} f(i) - \sum_{i=1}^{a-1} f(i)
$$

**Ejemplo:**
$$
\sum_{i=5}^{10} 7 = \sum_{i=1}^{10} 7 - \sum_{i=1}^{4} 7 = 7(10) - 7(4) = 7(6) = 42
$$

## Connections
- **Related to:** [[Notación Asintótica - Algoritmos]], [[Operaciones Elementales - Algoritmos]]

## Application / Example

Relación directa entre **Código** y **Sumatorias**:

### 1. Bucle Simple (Lineal)
```cpp
for (int i = 1; i <= n; i++) {
    // Operación constante O(1)
}
```
**Análisis:**
$$
\sum_{i=1}^{n} 1 = n = \Theta(n)
$$

### 2. Bucles Anidados Independientes (Cuadrático)
```cpp
for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= n; j++) {
        // Operación constante
    }
}
```
**Análisis:**
$$
\sum_{i=1}^{n}\sum_{j=1}^{n} 1 = \sum_{i=1}^{n} n = n^{2} = \Theta(n^{2})
$$

### 3. Bucles Anidados Dependientes (Triangular)
```cpp
for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= i; j++) {
        // El bucle interno depende de 'i'
    }
}
```
**Análisis:**
$$
\sum_{i=1}^{n}\sum_{j=1}^{i} 1 = \sum_{i=1}^{n} i = \frac{n(n+1)}{2} \approx \frac{1}{2}n^2 = \Theta(n^{2})
$$

> [!info] Detalle Técnico: La condición del bucle
> En un bucle `for` o `while`, la condición se evalúa $n+1$ veces (la última falla y termina el bucle). Aunque para exactitud matemática esto añade un $+1$, asintóticamente ($\Theta$) se ignora porque los términos de menor orden no afectan el crecimiento a gran escala.

## References
- **Cormen, Leiserson, Rivest, Stein**: *Introduction to Algorithms* (Appendix A: Summations).
