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
> Dominar el uso de **templates** y **enums** para crear código genérico y evitar el uso de *números mágicos*, comprendiendo la base estructural de C++ mediante **structs**.

## Explanation

### Enums (Enumeraciones)

Es la herramienta fundamental en C++ para evitar el uso de *valores arbitrarios* (números mágicos) durante el desarrollo. Su propósito principal es definir **estados claros** y mejorar drásticamente la *legibilidad* del código.

La manera moderna y recomendada de declararlos es mediante `enum class` (**Scoped Enums**). Esto eleva la enumeración al nivel de una clase, proporcionando un **tipado fuerte**.

> [!tip] Tipado Fuerte (Strong Typing)
> Al ser una clase, el compilador prohíbe comparar un `int` con un `enum` de forma directa. Esto te obliga a comparar *"peras con peras"*.
> - **Uso Correcto:** `Colors estado = Colors::muerto` 
`if(estado == Colors::muerto)` comparemos estado Colors con un estado Colors
>
> - **Error Común:** `if(estado == 0)` (Esto lanzará un error de compilación, protegiendo tu lógica) debido a que estamos comparando un tipo Colors con un int.

### Templates y Traits

Los **templates** permiten escribir funciones o clases *genéricas* que se adaptan automáticamente al tipo de dato que reciban. Se puede ver como un bloque de código que se "especializa" justo en el momento de ser llamado.

- **Traits (Fichas de Información):** Es una técnica avanzada donde utilizamos un `struct Traits<Tipo>` para crear una versión *especializada*. 
- **Analogía:** Funciona como un *diccionario* o *controlador* que proporciona información extra sobre un tipo específico (por ejemplo, traducir un valor de un Enum a su representación en `string`).

---

### La Estructura Base: ¿Struct vs Class?

Una duda recurrente es si un `struct` puede contener funciones al igual que un objeto. En el ecosistema de C++, la respuesta es **sí**.

> [!info] Realidad Técnica
> Técnicamente, un `struct` y una `class` son **idénticos** en capacidades; ambos pueden contener variables y funciones. La diferencia es puramente de *visibilidad por defecto* y *filosofía de diseño*.

1. **Visibilidad (Privacidad):**
    - **`struct`:** Todo es `public` por defecto (puertas abiertas).
    - **`class`:** Todo es `private` por defecto (caja fuerte).
2. **Filosofía de Uso:**
    - Utilizamos **`struct`** para *"Bolsas de Datos"* simples o **Nodos** en estructuras de datos, donde la protección de la memoria no es la prioridad.
    - Utilizamos **`class`** para *"Objetos Inteligentes"* donde el **Encapsulamiento** es vital para proteger la lógica interna.

---

## Application / Example

Ejemplo integrado de **Enum Class**, **Especialización de Templates** y **Struct**:

```cpp
#include <iostream>
#include <string>

using namespace std;

// Definición del Enum con tipado fuerte
enum class Color { red, green, orange };

// Base del Template para Traits
template <typename T>
struct Traits;

// Especialización del Trait para el tipo Color
template <>
struct Traits<Color> {
    // Función estática dentro de un struct público
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
    
    // Obtenemos el nombre usando la especialización del Template
    cout << "El color seleccionado es: " << Traits<Color>::name(mi_color) << endl;
    
    return 0;
}
```

## Connections
- **Related to:** [[Vectores en C++]], [[Aprendizaje de Algoritmos]]
- **Contrast with:** Arreglos estáticos y Clases con encapsulamiento privado.

## References
- [C++ Reference - Enum class](https://en.cppreference.com/w/cpp/language/enum)
- [C++ Reference - Struct vs Class](https://en.cppreference.com/w/cpp/language/classes)
