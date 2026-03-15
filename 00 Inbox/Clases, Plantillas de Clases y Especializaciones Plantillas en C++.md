---
tags:
  - note
status: in-progress
created:
tech:
domain:
---

# Clases, Plantillas de Clases y Especializaciones Plantillas en C++

## Core Idea
> Entender que son las clases, como funcionan las platinas de clases y la especializaciones plantillas en c++

## Explanation

### Clases
Una clase es la forma que tenemos en programación de poder hacer tener un *Objeto* (me refiero a algo que podremos usar varias veces) con ciertas reglas ya definidas.
Otra forma de verlo es como un plano de una casa, la clase es la encargada de definir que es lo que se podrá hacer en la casa, que lugares tendrán ventanas **Public**, en que lugar se guarda la comida **variables propias** y que lugares no tendran ventanas al exterior **Private**.

Una clase se compone de 3 cosas fundamentales

- Atributos/Variables : En cargados de almacenar informacion, o estados especificos 
- Metodos : Esto es la logica de nuestra clase lo que define como se guardan o se usa la informacion que tenemos 
- Modificadores de acceso: Define si la informacion que tenemos como la forma en que los procesamos se puede compartir o es unica de la clase en la que estamos trabajando.
#### Constructor

De que nos sirve tener todo un plano en general si nunca lo usaremos, básicamente esto es lo que hace el constructor, inicializa la clase dándole atributos predefinidos por la misma clase, tambien puede ejecutar ciertos metodos al momento de crearce en caso de que asi lo queramos

Un constructor tiene estos fundamentos: 

- Tiene exactamente el mismo nombre que la classe
- No devuelve nada es una funcion/metodo de tipo void con la diferencia de que no es neceario declararlo como void


### Plantilla de clases

A diferencia de las clases al usar plantillas de clases es una forma de decirle a la clase que no importa el tipo de dato que se le entregue actuara de las misma maneras que le digamos.

Mas conocido como *Programación Genérica*
#### Sintaxis

Para poder convertir una **Clase** a una *Plantilla de clases* no es nada complicado, solo necesitas agregar `template<class T>` 

- Template: avisa al compilador que lo que sigue es una plantilla
- `<class T>` o `<typename T>` Es lo mismo, básicamente le dice a C++, que la letra T sera el comodín, cada vez que en la clase se lea T sera el tipo de dato que el usuario ingreso

#### Ventajas

Imagina que quieres programar un arbol o un grafo, si no usaras plantillas tendrías que programar un arbol para cada tipo de dato, en este caso al estar usando platillas no seria necesario debido a que el comodín facilita las cosas

### Especialización de plantillas
Imagina que t

## Connections
- **Related to:** [[Related Note]]
- **Contrast with:** [[Opposing Concept]]

## Application / Example

Declarar clase una clase

```c++

class Personaje{
private:
	strign nombre;
	int salud;
	
public:
	Personaje(string nombre_personaje){
		nombre = nombre_personaje
		salud = 100
	}
	void recibirDano(int cantidadDano){
		salud -= cantidadDano 
	}
	
	void info(){
		cout << "Tienes " << salud << " Puntos de vida." << '\n'
	}
}
```

Uso de Metodos y Constructor de una clase :
```c++
int main(){

	string nombre; // se declara una variable para recibir el nombre que le pondremosa nuestra constructor
	
	// se guarda el nombre
	cin >> "Introduce el nombre de tu personaje " >> nombre;
	
	// se inicializa el constructor pasandole la informacion necesario
	Personaje heroe(nombre);
	
	// Se accede a los metodos, en caso de ser necesario se para informacion
	heroe.recibirDano(10);
	
	heore.info();

	return 0;
}
```



Declarar una plantilla de clase: 
```C++

template <class T>
class Caja{
private:
	// en lugar de usar int, bool, float etc usamos T que es nuestro comodin
	T contenido;
}

public:
	// el contructor recibe un valor con el tipo de dato T que es nuestro comodin
	Caja(T valor_inical){
		contenido = valor_inical;
	}
	
	// un metodo que devuelve un valor T que es nuestro comodin
	T obtenerContenido(){
		return contenido
	}

```

```C++
// Podemos hacer que la misma clase contenga difereten tipos de datos
Caja<int> cajaDeNumeros(100);

Caja<string> cajaDeTextos("Hola Mundo");

Caja<double> cajaDeDecimales(3.1416);
```

## References
- Source: 
