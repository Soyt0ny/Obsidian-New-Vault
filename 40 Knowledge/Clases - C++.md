---
tags:
  - note
status: evergreen
created: 2026-03-14
tech:
  - C++
domain: Programming Languages
---

# Clases en C++

## Core Idea
> Una **clase** es un plano o molde que define las reglas, estados y comportamientos de un *Objeto* para que pueda ser reutilizado múltiples veces en el programa.

## Explanation

### El Concepto del "Plano"
Imagina que una clase es el **plano de una casa**. El plano define qué se puede hacer en ella y cómo está distribuida:
- **Public (Ventanas):** Lo que es visible y accesible desde el exterior.
- **Private (Almacén/Interior):** Donde se guarda la información propia que no debe ser vista ni tocada desde afuera.

### Componentes Fundamentales
Una clase se compone de tres pilares:
1.  **Atributos (Variables):** Encargados de almacenar información o estados específicos.
2.  **Métodos (Lógica):** Definen cómo se usa o procesa la información.
3.  **Modificadores de acceso:** Determinan si la información es compartida (`public`) o única de la clase (`private`).

> [!info] El Constructor
> Es el encargado de **inicializar** la clase. Le da atributos predefinidos al objeto en el momento de su creación. 
> - Tiene el **mismo nombre** que la clase.
> - No devuelve ningún valor (es similar a un `void` pero no se declara como tal).

---

## Application / Example

```cpp
#include <iostream>
#include <string>

using namespace std;

class Personaje {
private:
    string nombre;
    int salud;
    
public:
    // Constructor: Inicializa nombre y salud
    Personaje(string nombre_personaje) {
        nombre = nombre_personaje;
        salud = 100;
    }

    void recibirDano(int cantidadDano) {
        salud -= cantidadDano;
    }
    
    void info() {
        cout << nombre << " tiene " << salud << " puntos de vida." << endl;
    }
};

int main() {
    string nombre;
    cout << "Introduce el nombre de tu personaje: ";
    cin >> nombre;
    
    // Inicialización usando el constructor
    Personaje heroe(nombre);
    heroe.recibirDano(10);
    heroe.info();

    return 0;
}
```

## Connections
- **Related to:** [[Vectores en C++]], [[Enumeración y Templates en C++]]
- **Part of:** [[Aprendizaje de C++]]
- [[Plantillas de Clases en C++]]
