---
tags:
  - note
status: in-progress
created:
tech:
domain:
---

# Enumeración Templates en C++

## Core Idea
> Entender los conceptos sobre **templates**, y **enum** en c++

## Explanation
### Enums

Enums es la forma que tenemos en *c++* de evitar usar numeros magicos al momento de estar programando, esto nos puede servir para usarlos al momento de hacer estados, ademas de que hace nuestro codigo un poco mas legible.

La manera moderna de declarar **enums** es convirtiendolos en una clase haciendo que el tipado sea mas fuerte.

`enum class Colors { elemento1, elemento2, elemento3}` 

Básicamente lo que estamos haciendo es agregar un valor numérico empezando desde 0 a los elementos que agregamos.

Un ejemplo de uso es poder escribir una condicional de una mejor manera 
`if(jugadorMuerto == 0)` convertirlo a `if(jugadorMuerto)` 

## Connections
- **Related to:** [[Related Note]]
- **Contrast with:** [[Opposing Concept]]

## Application / Example
```python
# Code example if applicable
```

## References
- Source: 
