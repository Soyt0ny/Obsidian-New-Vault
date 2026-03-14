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
`if(jugadorMuerto == 0)` convertirlo a `if(jugadorMuerto == Colors::muerto)` 

en este caso estaria tomando el valor o el numero asignado a *muerto*.

### Template

Los template nos ayudaran a poder escribir funciones reutilizables dependiendo de tipo de dato **TRAITS** que resivamos es decir podremos crear un bloque de codigo que se activara en el momento en el que lo llamemos con el tipo definido

`struct Tratis<{tipo}>` 

Estamos llamando a Traits y podra acceder a ciertas funcionalidades que nosotros delcaremos, es por decirlo asi un controllador y modelo al mismo tiempo.

## Connections
- **Related to:** [[Related Note]]
- **Contrast with:** [[Opposing Concept]]

## Application / Example
```python

```

## References
- Source: 
