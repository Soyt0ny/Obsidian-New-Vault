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

```c++
int main(){

	string nombre;
	
	cin >> "Introduce el nombre de tu personaje " >> nombre
	
	Personaje (nombre)
	
	

	return 0;
}
```

## References
- Source: 
