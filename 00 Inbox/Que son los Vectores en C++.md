---
tags:
  - note
status: review
created: 2026-03-14
tech:
  - C++
domain:
---

# Que son los Vectores en C++

## Core Idea
> Ent entender como se usan los Vectores como funcionan y sus diferencias

## Explanation
Un vector es un array dinámico, es decir que se gestiona la cantidad de memoria automáticamente.
Se usa cuando no sabes la cantidad de elementos exactos que estarán en un array, de esta manera podremos agregar mas elementos sin problemas.


| **Caracterisica**    | Arreglo: Normal (Estático) `int arr[5]`                                                                            | Vector (Dinámico) `vector<int> v`                                             |
| -------------------- | ------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- |
| **Tamano**           | **Fijo** Lo defines al compilar y no puede cambiar                                                                 | **Dinamico**. Puede creccer o encogerse en tiempo de ejecucion                |
| **Memoria**          | Usualmente en *stack* (rapida pero limitada)                                                                       | Los datos vieven en el *Heap* (dinamica, gestinonada, automaticamente)        |
| **Conoce su tamano** | **No** tienes que calcularclo con `sizeof` o llevar la cuenta tu mismo                                             | **Si**, llamando la funcion `v.size()`                                        |
| **Seguridad**        | Si accedes a `arr[10]` y solo tienes 5 elementos el programa puede colapsar (*Segmentation Fault*) silenciosamente | Puedes usar `v.at(10)` y te lanzara una excepción clara para atrapar el error |
|                      |                                                                                                                    |                                                                               |
### Operaciones mas comunes ($\bigO(1)$) 

- Agregar al final: `{vector}.push_back({elemento})` agrega el elemento al final de la lista
- Saber el tamano: `{vector}.size()` te devuelve cuantos elementos existen
- Acceder a un dato `{vector}[{posicion}]` te devuelve el dato que esta en la posicion seleccionada
- Eliminar el ultimo `{vector}.pop_back()` elimina el ultimo valor del vector


### Vectores
GEMINI EXPLICA ESTO

Para poder declarar un vector sera necesario inicializar nuestro *vector* seguido de nuestro tipo de dato, ademas de declarar le nombre de la variable. en caso de que queramos agregar en ese momento una cantidad X de espacios lo haremos usando `()`

##### Opción 1: Usar `.reserve()` (Afecta la Capacidad)

Le dices al vector: _"Oye, aparta espacio para `X` elementos en la memoria de una vez, pero mantén mi tamaño en 0"_. Como ya tiene el espacio apartado, los `push_back` se vuelven instantáneos.


``` c++
        vector<int> fila_actual;
        fila_actual.reserve(elementos); // ¡Optimización! Aparta la memoria de golpe
        
        for(int elemento = 0; elemento < elementos ; elemento++){
            int num = 0;
            cin >> num;
            fila_actual.push_back(num); // Ahora es muchísimo más rápido
        }
```

##### Opción 2: Inicializar el vector con un tamaño (Afecta el Tamaño)

Le dices al vector: _"Créame de una vez las `X` habitaciones y llénalas con ceros"_. Como las habitaciones **ya existen**, ya no usas `push_back`, ¡ahora sí puedes usar los corchetes `[ ]`!

C++

```
        // Al poner (elementos) en el paréntesis, creas el vector ya con ese tamaño
        vector<int> fila_actual(elementos); 
        
        for(int elemento = 0; elemento < elementos ; elemento++){
            // Como las "habitaciones" ya están construidas, podemos guardar directo
            cin >> fila_actual[elemento]; 
        }
```

Ambas opciones son excelentes y demuestran un dominio profundo de cómo funciona la memoria en C++.

**Un detalle extra de estilo:** Usar `printf` está perfecto y funciona muy rápido, pero en el mundo puramente de C++ suele usarse `cout`. Para que imprima un salto de línea y sea igual de rápido, los programadores de C++ escriben: `cout << lista[fila][col] << "\n";` (Usar `"\n"` es más rápido que usar `endl`).

pero al usar (elementos), reserva el espacio de memoria pero no el valor, eso es mejor que llenaro de 0, no ?

## Gemini dijo

¡Qué excelente pregunta! Tienes una intuición muy aguda para el rendimiento y la gestión de memoria. Es exactamente el tipo de cosas que un buen programador de C++ se pregunta.

Sin embargo, aquí tengo que corregir un pequeño detalle técnico: **es al revés de lo que piensas**.

Cuando usas los paréntesis `(elementos)`, C++ **sí** construye los elementos y los inicializa por defecto (en el caso de los `int`, los llena de ceros).

Aquí te explico la diferencia exacta entre las dos optimizaciones que te mencioné para que veas qué pasa en la memoria:

### 1. Usar `(elementos)` = Construye y llena de ceros

- **Sintaxis:** `vector<int> fila(5);`
    
- **¿Qué hace en memoria?** Va al Heap, aparta espacio para 5 enteros y **escribe un `0` en cada uno de ellos**.
    
- **Efecto:** Tu `size` es 5 y tu `capacity` es 5.
    
- **Pro:** Puedes usar inmediatamente los corchetes `cin >> fila[i];`.
    
- **Contra (técnico):** Haces "trabajo doble". Primero C++ escribe ceros, y milisegundos después tú los sobrescribes con los números del usuario mediante el `cin`.
    

### 2. Usar `.reserve(elementos)` = Solo aparta el terreno crudo

- **Sintaxis:** `vector<int> fila; fila.reserve(5);`
    
- **¿Qué hace en memoria?** Va al Heap y "cerca" un terreno donde caben 5 enteros, pero **no toca lo que hay adentro** (deja la memoria cruda/basura).
    
- **Efecto:** Tu `capacity` es 5, pero tu `size` sigue siendo **0**.
    
- **Pro:** Te ahorras el trabajo de llenarlo de ceros.
    
- **Contra (técnico):** Como el `size` es 0, no puedes usar corchetes `[ ]`. Tienes que usar `push_back()`, y cada vez que llamas a `push_back()`, el vector tiene que actualizar internamente su contador de `size` sumándole 1.
    

---

### Entonces, ¿cuál es mejor?

En la teoría más estricta, `.reserve()` seguido de `push_back()` evita escribir ceros innecesarios.

Pero en la práctica y en la vida real de C++, **usar `vector<int> fila(elementos);` suele ser la preferida** cuando sabes el tamaño exacto. ¿Por qué?

1. Llenar un bloque de memoria contigua con ceros es una operación tan optimizada a nivel de procesador que toma casi cero tiempo.
    
2. Usar corchetes `fila[i]` dentro de tu ciclo `for` es una simple suma de memoria, mientras que llamar a la función `push_back()` tiene un ligerísimo costo extra por procesar la actualización del tamaño.
    

Al final, ambas son soluciones de nivel experto (O(n) en notación Big O) y son infinitamente mejores que no reservar memoria en absoluto. Cualquiera de las dos que pongas en tus apuntes te hará destacar.

### Vector de Vectores

Un vector de vectores es basicamente una lista que se compone de otras listas

Lo importante aqui es que la gran diferencia es que este tipo de matriz es que cada fila puede tener tamaños distintas  conocido como *jagged array* / *arreglo dentado*

Cuando creamos un vector de vectores no podemos simplemente asignar un valor `{vector}[fila][columna]` necesitamos crear esa fila por lo cual tendremos que crear un vector el cual almacenara la cantidad de datos que queremos `vector<int>` lo llenamos capturando el numero y luego con la función `push_back()` lo agregamos al final, cuando este llena esa fila usaremos una vez mas la función `push_back()` para agregarla al vector de vectores
`{vector de vectores}.push_back({vector})`

Se puede usar para cosas como grafos etc.

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
