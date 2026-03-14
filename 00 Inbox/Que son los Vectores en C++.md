---
tags:
  - note
status: in-progress
created: 2026-03-14
tech:
  - C++
domain:
---

# Que son los Vectores en C++

## Core Idea
> Entender como se usan los Vectores como funcionan y sus diferencias

## Explanation
Un vector es un array dinámico, es decir que se gestiona la cantidad de memoria automáticamente.
Se usa cuando no sabes la cantidad de elementos exactos que estarán en un array, de esta manera podremos agregar mas elementos sin problemas.


| **Caracterisica**    | Arreglo: Normal (Estático) `int arr[5]`                                                                            | Vector (Dinámico) `vector<int> v`                                             |
| -------------------- | ------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- |
| **Tamano**           | **Fijo** Lo defines al compilar y no puede cambiar                                                                 | **Dinamico**. Puede creccer o encogerse en tiempo de ejecucion                |
| **Memoria**          | Usualmente en *stack* (rapida pero limitada)                                                                       | Los datos vieven en el *Heap* (dinamica, gestinonada, automaticamente)        |
| **Conoce su tamano** | **No** tienes que calcularclo con `sizeof` o llevar la cuenta tu mismo                                             | **Si**, llamando la funcion `v.size()`                                        |
| **Seguridad**        | Si accedes a `arr[10]` y solo tienes 5 elementos el programa puede colapsar (*Segmentation Fault*) silenciosamente | Puedes usar `v.at(10)` y te lanzara una excepción clara para atrapar el error |
### Operaciones mas comunes ($\bigO(1)$) 

- Agregar al final: `{vector}.push_back({elemento})` agrega el elemento al final de la lista
- Saber el tamano: `{vector}.size()` te devuelve cuantos elementos existen
- Acceder a un dato `{vector}[{posicion}]` te devuelve el dato que esta en la posicion seleccionada
- Eliminar el ultimo `{vector}.pop_back()` elimina el ultimo valor del vector

### Vector de Vectores

Un vector de vectores es basicamente una lista que se compone de otras listas

Lo importante aqui es que la gran diferencia es que este tipo de matriz es que cada fila puede tener tamanos distitnos  conocido como *jagged array* / *arreglo dentado*

## Connections
- **Related to:** [[Related Note]]
- **Contrast with:** [[Opposing Concept]]

## Application / Example
```C++
#include <vector>

vector<int> numeros; // vector vacio de entero
vector<string> palabras; //vector de textos

vector<vector<int>> matriz // esto es una matriz de numero enteros
```

## References
- Source: 
