---
tags:
  - note
status: evergreen
created: 2026-03-14
tech:
  - C++
domain: Programming Languages
---

# Plantillas de Clases (Class Templates)

## Core Idea
> Los **Class Templates** permiten definir una clase que puede trabajar con **cualquier tipo de dato** sin necesidad de reescribir el código para cada uno. Es la base de la **Programación Genérica**.

## Explanation

### ¿Por qué usarlos?
Imagina que quieres programar una estructura compleja como un `Árbol` o un `Grafo`. Sin plantillas, tendrías que crear una versión para `int`, otra para `string`, etc. Con plantillas, creas un solo "molde" que se adapta al tipo de dato que el usuario elija.

### Sintaxis y el "Comodín"
Para convertir una clase normal en una plantilla, usamos la instrucción `template <class T>` (o `typename T`).
- **T:** Es el comodín. Cada vez que C++ lea `T` dentro de la clase, lo sustituirá por el tipo de dato que el usuario ingrese al instanciarla.

> [!tip] Ventaja Técnica
> El uso de plantillas facilita el mantenimiento y reduce drásticamente la duplicación de código en estructuras de datos.

---

## Application / Example

```cpp
#include <iostream>
#include <string>

using namespace std;

template <class T>
class Caja {
private:
    T contenido; // T es nuestro comodín de tipo

public:
    Caja(T valor_inicial) {
        contenido = valor_inicial;
    }
    
    T obtenerContenido() {
        return contenido;
    }
};

int main() {
    // La misma clase funcionando con diferentes tipos
    Caja<int> cajaDeNumeros(100);
    Caja<string> cajaDeTextos("Hola Mundo");
    Caja<double> cajaDeDecimales(3.1416);

    cout << "Número: " << cajaDeNumeros.obtenerContenido() << endl;
    cout << "Texto: " << cajaDeTextos.obtenerContenido() << endl;
    
    return 0;
}
```

## Connections
- **Related to:** [[Clases en C++]], [[Especialización de Plantillas de Clases]]
- **Part of:** [[Aprendizaje de C++]]
