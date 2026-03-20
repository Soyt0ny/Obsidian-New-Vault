---
tags:
  - note
status: evergreen
created: 2026-03-18
tech:
  - C++
domain: Programming Languages
---

# Strings en C++ (std::string)

## Core Idea
> El `std::string` es un objeto de la STL que representa una secuencia dinámica de caracteres. A diferencia de los arreglos de C (`char[]`), gestiona su propia memoria y permite redimensionarse automáticamente.

## Explanation

### Estructura y Memoria
Un string en C++ se comporta como un contenedor secuencial. Los caracteres se almacenan en posiciones de memoria contiguas, lo que permite un acceso aleatorio extremadamente rápido.

- **Gestión de Memoria:** El objeto `string` vive en el **Stack**, pero los caracteres que componen la cadena se almacenan en el **Heap**. Esto permite que la cadena crezca sin que el programador tenga que gestionar punteros manualmente.
- **Acceso:** Al ser similar a un arreglo, acceder a un carácter por índice (`s[i]`) tiene una complejidad de **$O(1)$**.

### Lectura y Flujos (cin vs getline)
Es fundamental entender cómo capturar strings:
1. `cin >> variable;`: Lee hasta encontrar el primer espacio en blanco, tabulación o salto de línea.
2. `getline(cin, variable);`: Lee toda la línea, incluyendo espacios, hasta encontrar un salto de línea (`\n`).

> [!tip] Métodos Indispensables
> - `.size()` o `.length()`: Retornan la cantidad de caracteres ($O(1)$).
> - `.push_back(char)`: Añade un carácter al final ($O(1)$ amortizado).
> - `.append(string)`: Concatena otra cadena al final.
> - `.empty()`: Verifica si el string no tiene caracteres.

---

### Modificación y Concatenación
A diferencia de otros lenguajes (como Python o Java), los strings en C++ son **mutables**. Puedes cambiar un carácter directamente sin crear una copia de toda la cadena.

## Application / Example
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string nombre;

    cout << "Ingresa tu nombre completo: ";
    // Usamos getline para capturar espacios
    getline(cin, nombre);

    // Acceso individual
    cout << "Primera letra: " << nombre[0] << "\n";
    
    // Modificación directa (Mutabilidad)
    nombre[0] = toupper(nombre[0]);

    // Métodos comunes
    cout << "Tu nombre es: " << nombre << "\n";
    cout << "Longitud: " << nombre.size() << " caracteres." << "\n";

    // Concatenación simple
    string saludo = "Hola, " + nombre;
    cout << saludo << endl;

    return 0;
}
```

## Connections
- **Related to:** [[Vectores - C++]] (comparten mucha lógica de contenedores), [[Aprendizaje de C++]]
- **Contrast with:** `char[]` (C-Style Strings), donde la memoria es estática y más difícil de manejar.

## References
- [C++ Reference - string](https://en.cppreference.com/w/cpp/string/basic_string)
- Guía de manipulación de flujos de E/S.
