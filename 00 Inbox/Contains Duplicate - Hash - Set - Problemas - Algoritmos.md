---
tags:
  - problem
status: review
difficulty: Easy
platform: LeetCode
pattern:
  - set
  - HashMap
tech:
---

# Problem Name

## Description
Encontrar si el arreglo de numero, palabras que nos dan tiene duplicados 

## Constraints
- n == `nums.lenght`
- 1 <= `n` <= 1000
- 1 < `nums[i]` <=1000

## Approach: [HashMap] [Set] [Brute Force]

### Intuition
Existen 3 maneras en las cuales podemos resolver este problema, básicamente nos piden poder comprobar si los elementos de un arreglo estan duplciados

**Hashmap**
Consiste en guardar el valor que vemos como *key* y como *value* hacer un contador,
cada vez que se tome un nuevo numero se busca por su key, en caso de ya existir la key significa que ya existe y que en este caso estaría duplicado
**Set**
La estructura de set solo nos permite agregar valores que no estén duplicados, y la manera que tenemos para poder agregar estos elementos por lo cual si convertimos la lista a un set y la comparamos su longitud podemos ver si contien duplicados o no.

En este aproach es importante recalcar que depende del lenguaje de programacion en este caso, C++ y Python la manera de programarlo son difernetes

**Brute Force**
Fuerza bruta es la mas ineficiente de todas, debido a que tendriamos que comprar cada elemento con los demas elementos basicamente haciendo un bucle anidado que nos terminaria dando un tiempo de $n^2$ 

### Complexity Analysis
Hashmap
- **Time Complexity:** $O(n)$ - No aumenta el tiempo de ejecucion debido a que solamente tendra que pasar por el array una sola vez
- **Space Complexity:** $O(n)$ - no lo se
Set
- **Time Complexity:** $O(n)$ - No aumenta tampoco el tiempo de ejecucion, solamente se necesita pasar 1 vez por los elementos o por casi todos, dependiendo el lenguaje de programacion
- **Space Complexity:** $O(n)$ - Se aumenta el espacio debido a que creamos un nuevo set
Brute Force
**Time Complexity:** $O(n^2)$ - Al comparar cada elemento uno por 1 significa que estmaos comparando el elemento 1 con todos luego el 2 contodos y asi hasta terminar
**Space Complexity:** No se necesita mas memoria

## Code Implementation
Código en C++
**Set**
```cpp
using namespace std;
#include <unorder_set>
#include <vector>

bool hasDuplicate(vector<int> & numeros){
	unorder_set<int> visto;
	visto.reserve(numeros.size());
	for( int numero : numeros){
		auto res = visto.insert(numero);
		if(!res.second){
			return true;
		}
	}
	return false;
}
```
**Map**
```c++
using namespace std;
#include <unorder_map>
#include <vector>



```
**Brute Force**


## Key Insights
> [!tip] Aprendizaje Clave
> Qué aprendiste de este problema o qué técnica específica optimizó la solución.

## Related Notes
- [[ALGORITHMS]]
---