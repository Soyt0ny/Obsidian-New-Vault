---
tags:
  - problem
  - string
status: review
difficulty: Easy
platform: LeetCode
pattern:
  - string
tech:
domain: Algorithms
---

# Problem Name

## Description
Expandir el array que nos dan por si mismo, es decir si el array es {1,2,3} tendría que quedar {1,2,3,1,2,3}.

## Constraints
- `n == nums.length`
- `1 <= n <= 1000`
- `1 <= nums[i] <= 1000`

## Approach: [Strings]

### Intuition
Usar alguna función de insert para agregar el string a si mismo al final  o iterar en el arreglo de nos dieron agregando los valores al nuevo arreglo 2 veces

### Complexity Analysis
- **Time Complexity:** $O(n)$ - En caso de tener el array con el espacio correcto al usar un método de insert solamente sera $O(1)$ en caso de iterar con un for para agregar los cada valor 2 veces el tiempo sera $O(n)$
- **Space Complexity:** $O(n)$ - Detalle sobre el uso de memoria (Stack vs Heap) y estructuras auxiliares.

## Code Implementation

Implementacion con for
```cpp
using namespace std;

vector<int> getConcatenation(vector<int> &arr){
	int n = arr.size()
	vector<int> resp(2 * n);
	
	for(int i =0; i < n ; i++){
		resp[i] = arr[i]
		resp[i+n] = arr[i]
	}
	return resp
}
```

Implementacion con o(1)
```c++
vector<int> getConcatenation(vector<int> &arr){
	int n = arr.size()
	vector<int> resp;
	res.reserve(2*n)
	res =nums
	sum.insert()
	
	return resp
}
```
## Key Insights
> [!tip] Aprendizaje Clave
> Qué aprendiste de este problema o qué técnica específica optimizó la solución.

## Related Notes
- [[ALGORITHMS]]
---