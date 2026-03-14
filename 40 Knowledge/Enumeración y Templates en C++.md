---
tags:
  - note
status: evergreen
created: 2026-03-14
tech:
  - C++
domain: Software Engineering
---

# Enumeración y Templates en C++

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
- En lugar de: `int jugadorMuerto = 0; if (jugadorMuerto == Colors::muerto)` (Esto daría error por mezclar tipos).
    
- Lo ideal sería: `Colors estadoJugador = Colors::muerto; if (estadoJugador == Colors::muerto)` (Aquí comparas peras con peras).

### Template

Los template nos ayudaran a poder escribir funciones reutilizables dependiendo de tipo de dato **TRAITS** que resivamos es decir podremos crear un bloque de codigo que se activara en el momento en el que lo llamemos con el tipo definido.

`struct Tratis<{tipo}>` 

Estamos llamando a Traits y podra acceder a ciertas funcionalidades que nosotros delcaremos, es por decirlo asi un controllador y modelo al mismo tiempo.

---

### Registro de Aprendizaje (Log)

#### Tú dijiste:
> Enums es la forma que tenemos en c++ de evitar usar numeros magicos... La manera moderna de declarar enums es convirtiendolos en una clase haciendo que el tipado sea mas fuerte...
> 
> Template: Los template nos ayudaran a poder escribir funciones reutilizables dependiendo de tipo de dato TRAITS que resivamos... es por decirlo asi un controllador y modelo al mismo tiempo.

#### Gemini dijo:
¡Tus apuntes están fantásticos! Has logrado capturar la esencia pura de C++. 

**Sobre Enums:** Recuerda que con `enum class` comparas "peras con peras". No puedes comparar un `int` con un `Colors::muerto` directamente sin error. Lo ideal es: `Colors estadoJugador = Colors::muerto; if (estadoJugador == Colors::muerto)`.

**Sobre Templates y Traits:** 
- **Templates (La Herramienta):** Permiten escribir funciones genéricas para **cualquier** tipo de dato.
- **Traits (La Técnica):** Es cuando usamos la sintaxis `struct Traits<Tipo>` para crear una versión *especializada* del template. Es como un **"Diccionario"** o **"Ficha de Información"** sobre un tipo específico.

---

#### Tú preguntaste:
> ¿que diferneica tiene Struct con crear un objeto con diferentes funcciones ?

#### Gemini dijo:
Técnicamente, un `struct` y una `class` (clase/objeto) son exactamente lo mismo en C++. Un `struct` **sí** puede tener funciones adentro. La diferencia es la visibilidad por defecto y la filosofía de uso:

1. **La Única Diferencia Técnica: La Privacidad**
- **`struct` (Público por defecto):** Todo es accesible desde afuera a menos que digas lo contrario.
- **`class` (Privado por defecto):** Todo está protegido (cerrado) a menos que uses la palabra `public:`.

2. **La Diferencia Filosófica**
- Usamos **`struct`** para "Bolsas de Datos" simples (como los Nodos en estructuras de datos).
- Usamos **`class`** para "Objetos Inteligentes" que protegen su lógica interna.

---

## Application / Example

Ejemplo de uso de Enums, Templates y Struct:

```cpp
#include <iostream>
#include <string>

using namespace std;

enum class Color { red, green, orange };

// Definimos el Trait especializado para el Enum Color
template <typename T>
struct Traits;

template <>
struct Traits<Color> {
    static string name(Color c) {
        switch(c) {
            case Color::red:    return "red";
            case Color::green:  return "green";
            case Color::orange: return "orange";
            default:            return "unknown";
        }
    }
};

int main() {
    Color mi_color = Color::green;
    
    // Accedemos a la función del struct para obtener el nombre
    cout << "El color seleccionado es: " << Traits<Color>::name(mi_color) << endl;
    
    return 0;
}
```

## Connections
- **Related to:** [[Vectores en C++]], [[Aprendizaje de Algoritmos]]
- **Contrast with:** Arreglos estáticos y Clases (Encapsulamiento).

## References
- [C++ Reference - Enum class](https://en.cppreference.com/w/cpp/language/enum)
- [C++ Reference - Struct vs Class](https://en.cppreference.com/w/cpp/language/classes)
