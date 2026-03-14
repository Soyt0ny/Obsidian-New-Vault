---
tags:
  - note
status: evergreen
created: 2026-03-14
tech:
  - C++
domain: Software Engineering
---

# Vectores en C++ (std::vector)

## Core Idea
> El `std::vector` es un array dinámico que gestiona la memoria automáticamente. Se utiliza cuando no se conoce la cantidad exacta de elementos al inicio, permitiendo agregar más elementos sin problemas.

## Explanation

### Diferencias entre Arreglo Estático y Vector

| Característica | Arreglo: Normal (Estático) `int arr[5]` | Vector (Dinámico) `vector<int> v` |
| :--- | :--- | :--- |
| **Tamaño** | Fijo. Se define al compilar y no puede cambiar. | Dinámico. Puede crecer o encogerse en tiempo de ejecución. |
| **Memoria** | Usualmente en Stack (rápida pero limitada). | Los datos viven en el Heap (dinámica, gestionada automáticamente). |
| **Conoce su tamaño** | No. Tienes que calcularlo con `sizeof` o llevar la cuenta. | Sí, llamando la función `v.size()`. |
| **Seguridad** | Si accedes fuera de rango, el programa puede colapsar silenciosamente. | Puedes usar `v.at(10)` y lanzará una excepción clara. |

### Operaciones más comunes ($O(1)$)

- **Agregar al final:** `v.push_back({elemento})` agrega el elemento al final de la lista.
- **Saber el tamaño:** `v.size()` devuelve cuántos elementos existen.
- **Acceder a un dato:** `v[posicion]` devuelve el dato en la posición seleccionada.
- **Eliminar el último:** `v.pop_back()` elimina el último valor del vector.

---

### Optimización de Memoria: reserve() vs Inicialización con tamaño

Para declarar un vector se inicializa con el tipo de dato y nombre. Si queremos asignar una cantidad X de espacios desde el inicio, hay dos formas principales:

#### Opción 1: Usar `.reserve()` (Afecta la Capacidad)
Aparta espacio para `X` elementos en la memoria de una vez, pero mantiene el tamaño en 0. Los `push_back()` se vuelven instantáneos porque el espacio ya está reservado.
```cpp
vector<int> fila;
fila.reserve(10); // Aparta memoria pero size() sigue siendo 0
```

#### Opción 2: Inicializar con tamaño (Afecta el Tamaño)
Crea las "habitaciones" de una vez y las llena con ceros (para tipos `int`). Aquí se usan corchetes `[]` en lugar de `push_back()`.
```cpp
vector<int> fila(10); // size() es 10, todos son 0
```

#### Nota sobre el rendimiento
**¿Es mejor (elementos) porque reserva espacio pero no el valor?**
En realidad, `vector<int> v(n)` **sí** inicializa los valores (los llena de ceros). 
- Usar `reserve()` + `push_back()` evita escribir esos ceros iniciales (memoria cruda).
- Sin embargo, usar `v(n)` y acceder con `v[i]` es la opción preferida cuando sabes el tamaño exacto, ya que llenar memoria con ceros es extremadamente rápido en procesadores modernos y permite una sintaxis más limpia.

---

### Vector de Vectores (Matrices Dinámicas)

Un vector de vectores es una lista que se compone de otras listas. La gran diferencia con una matriz tradicional es que cada fila puede tener tamaños distintos, conocido como **jagged array** (arreglo dentado).

**Construcción Manual:**
No se puede asignar simplemente `v[fila][columna]` si la fila no existe. El proceso es:
1. Crear un vector temporal para la fila: `vector<int> fila_temp`.
2. Llenar esa fila con datos.
3. Usar `push_back(fila_temp)` para meter la fila entera dentro del vector de vectores.

Se utiliza comúnmente para estructuras como **Grafos** (listas de adyacencia).

### Recorrido idiomático (Iteración)
Para imprimir un vector de forma eficiente en C++ moderno:
```cpp
for (const auto& elemento : v) {
    std::cout << elemento << "\n";
}
```

## Application / Example
```cpp
#include <iostream>
#include <vector>

int main() {
    // Vector de vectores
    std::vector<std::vector<int>> matriz;
    
    // Crear una fila dinámicamente
    std::vector<int> fila1;
    fila1.push_back(10);
    fila1.push_back(20);
    
    // Agregar la fila a la matriz
    matriz.push_back(fila1);
    
    return 0;
}
```

## Connections
- **Related to:** [[Notación Asintótica]], [[Aprendizaje de Algoritmos]]
- **Contrast with:** Arreglos estáticos de C.

## References
- [C++ Reference - std::vector](https://en.cppreference.com/w/cpp/container/vector)
- Diálogo de aprendizaje sobre gestión de memoria.
