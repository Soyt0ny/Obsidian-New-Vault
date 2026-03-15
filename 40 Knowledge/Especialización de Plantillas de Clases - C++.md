---
tags:
  - note
status: evergreen
created: 2026-03-14
tech:
  - C++
domain: Programming Languages
---

# Especialización de Plantillas de Clases en C++

## Core Idea
> La **Especialización** permite definir una lógica distinta para un tipo de dato específico cuando el "molde general" de la plantilla no es adecuado o eficiente para ese caso.

## Explanation

### El Caso de Excepción
Imagina que tu clase genérica funciona perfectamente para casi todos los datos, pero cuando recibe un `string` o un `float`, la lógica matemática se rompe o requiere un tratamiento especial.

La especialización le dice al compilador: *"Usa el molde general para todo, EXCEPTO cuando el usuario introduzca este tipo específico"*.

### Sintaxis
Se utiliza `template <>` (vacío) y se especifica el tipo al momento de declarar el nombre de la clase: `class NombreClase<tipo_especifico>`.

> [!warning] Diferencia Clave
> En la especialización, ya no usas el comodín `T` dentro de la clase, sino el tipo real (ej. `string`) porque ya sabemos exactamente con qué dato estamos tratando.

---

## Application / Example

```cpp
#include <iostream>
#include <string>

using namespace std;

// Plantilla general (Base)
template <typename T>
class Procesador {
public:
    void mensaje() { cout << "Usando procesador genérico." << endl; }
};

// Especialización total para el tipo string
template <>
class Procesador<string> {
private:
    string valor;

public:
    Procesador(string v) { valor = v; }
    
    void mensaje() { cout << "Usando procesador especializado para TEXTO." << endl; }
    
    string concatenar(string otro) {
        return valor + " y " + otro;
    }
};

int main() {
    Procesador<int> p1;
    p1.mensaje(); // Salida: genérico
    
    Procesador<string> p2("C++");
    p2.mensaje(); // Salida: especializado
    
    return 0;
}
```

## Connections
- **Related to:** [[Plantillas de Clases - C++]], [[Enumeración y Templates - C++]]
- **Part of:** [[Aprendizaje de C++]]
