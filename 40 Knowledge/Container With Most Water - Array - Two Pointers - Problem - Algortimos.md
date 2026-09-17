---
tags:
  - problem
  - array
  - two-pointers
status: evergreen
difficulty: Medium
platform: LeetCode
pattern:
  - Two Pointers
tech:
  - Python
  - C++
domain: Algorithms
---

# Container With Most Water

## Description
Tenés que encontrar la cantidad máxima de agua que se puede contener a partir de un arreglo de enteros, donde cada entero representa la **altura** de una pared vertical. El "ancho" del contenedor es la distancia entre los índices de las dos paredes elegidas. El "alto" efectivo está limitado por la pared **más baja** (el agua se derrama por el lado más bajo).

> [!info] Formula del area
> `area = min(height[L], height[R]) * (R - L)`
> La altura es el minimo (pared limitante), el ancho es la distancia entre indices.

## Constraints
- $n == \text{height.length}$
- $2 \le n \le 10^5$
- $0 \le \text{height}[i] \le 10^4$

## Approach: Two Pointers (opuestos)

### Intuition
Necesito obtener 2 números de la lista para tener las 2 paredes del contenedor y a partir de esto comparar cuál de las 2 es la más pequeña, ya que es la altura máxima de agua que se puede obtener. Para poder recorrer, la manera en la que lo puedo hacer es usando Two Pointers, que me dará las 2 paredes.

Ahora, si estoy buscando el contenedor que más agua tenga es base × altura, así que tiene sentido empezar desde lados opuestos para tener la base más grande y de ahí ir reduciendo y obteniendo las medidas de las diferentes paredes.

La manera lógica de moverlos fue comparando la pared más chica y sumar o restar su índice para obtener otra pared, y calcular la cantidad de agua que necesitan. Al final solo se guarda la cantidad máxima de agua.

> [!info] Por que empezar en los extremos
> La base inicial es maxima (`n - 1`). Cualquier otro par de paredes tiene base menor, asi que para que tenga sentido competir necesitamos paredes **mucho** mas altas. Empezar en los extremos te da la mejor base "gratis".

### Complexity Analysis
- **Time Complexity:** $O(n)$
    El while corre como maximo `n - 1` veces. En cada vuelta hacemos trabajo $O(1)$ (un min, una multiplicacion, una comparacion). Como cada puntero se mueve a lo sumo `n` veces, el total es $O(n)$ — **no** $O(n^2)$ aunque haya un `while` que itera varias veces.
- **Space Complexity:** $O(1)$ auxiliar
    Solo usamos variables enteras (`L`, `R`, `max_water`, `minimo`, `container`). **El input no cuenta** como espacio auxiliar (es lo que recibimos, no lo que creamos).

> [!warning] Tu nota decia $O(n)$ para espacio
> Esta vez la complejidad temporal la clavaste. Pero la espacial quedo mal: dijiste $O(n)$ y es $O(1)$ auxiliar. Recorda: input no cuenta como espacio auxiliar. Si tuvieras que devolver el listado de areas, ahi si contaria como output.

## Code Implementation

### Python Implementation
```python
def container_water(heights: list[int]) -> int:
    max_water = 0
    L, R = 0, len(heights) - 1

    while L < R:
        # Altura limitante = la pared mas baja
        minimo = min(heights[L], heights[R])
        # Ancho = distancia entre paredes
        container = minimo * (R - L)

        if container > max_water:
            max_water = container

        # Mover la pared mas baja: es la unica que puede mejorar el area
        if heights[L] < heights[R]:
            L += 1
        else:
            R -= 1

    return max_water
```

### C++ Implementation
```cpp
using namespace std;

int containerWater(vector<int>& heights) {
    int max_water = 0;
    int L = 0, R = (int)heights.size() - 1;

    while (L < R) {
        int minimo = min(heights[L], heights[R]);
        int container = minimo * (R - L);

        if (container > max_water) {
            max_water = container;
        }

        // Mover la pared mas baja
        if (heights[L] < heights[R]) {
            L++;
        } else {
            R--;
        }
    }

    return max_water;
}
```

## Key Insights

> [!tip] Por que funciona la regla "mover la pared baja"
> El area es `min(h[L], h[R]) * (R - L)`. Si moves la pared **alta**, la base baja 1 y el `min` no puede subir (la nueva linea reemplazo a la alta, no a la baja). Dos factores que no suben -> el producto no sube. Mover la pared **baja** es la **unica** forma de tener chance de que el `min` mejore.
> 
> Esta es la diferencia entre $O(n)$ y $O(n^2)$: estas descartando un monton de pares sin perder el optimo.

> [!tip] La elegancia de los extremos opuestos
> Empezar con `L = 0, R = n - 1` te da la base maxima gratis. Cualquier otra eleccion inicial sacrifica base sin ganancia garantizada en altura.

> [!warning] Cuidado con el orden de la resta
> `R - L` es positivo, `L - R` es negativo. Un area negativa romperia la comparacion con `max_water` (que arranca en 0) y tu funcion devolveria siempre 0. Es un bug silencioso — el codigo corre, pero devuelve mal.

> [!tip] El empate se resuelve del lado R
> Cuando `heights[L] == heights[R]`, moves R por la rama `else`. Cualquiera de las dos sirve (es optimo en ambos casos), pero la convencion de la industria suele ser mover R para mantener el invariante "siempre avanzo el lado que limita".

## Related Notes
- [[ALGORITHMS]]
- [[Two Pointers - Algoritmos]] — patron completo con las 2 variantes
- [[Two Pointers - Postit - Algoritmos]] — referencia rapida de pantalla
- [[3Sum - Array - Two Pointers - Problem - Algortimos]] — mismo patron, anchor + 2 punteros
- [[Notacion Asintotica - Algoritmos]] — para entender por que es $O(n)$ y no $O(n^2)$
