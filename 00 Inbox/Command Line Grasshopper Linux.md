---
tags:
  - note
status: in-progress
created: 2026-03-09
tech:
  - Linux
domain: Os
---

# Command Line Grasshopper Linux

## Core Idea
> Entender como funciona los comandos básicos de la terminal en Linux

## Explanation
### La shell

Para poder empezar a conocer como usar linux es importante saber usar la shell.
La **Shell** es uno de los programas mas poderos en casi cualquier sistema operativo debido a que acepta comandos los cuales ejecutan acciones en nuestro sistema operativo

Cuando nostros abrimos una *Terminal* o *Consola* lo que hacemos es abrir una sesión de la **Shell** para poder interactuar con ella 

#### Bash
En este caso aprenderemos a usar **Bash** `(Bourne Again Shell)` aunque existe otras opciones como *zsh* *ksh* etc. bash es la mas usada en la mayoría de distribuciones.

#### Shell prompt
Cuando abrimos una terminal la Shell nos saludara con un mensaje usualmente con este formato `username@hostname:directorio_actual$`
```bash
soyt0ny@kuro:/home/pete $
```

el signo de dinero `$` significa que la terminal esta lista para recibir comandos.
#### `echo`

El primer comando que aprenderemos sera `echo`
Este comando es simplemente dice replica lo que la instrucción que nosotros te damos.
Si enviamos una cadena de texto nos devolverá la misma cadena de texto 

#### `pwd (Print Working Directory)`

En **Linux** el principal concepto es que todo son archivos y se tratan como archivos.
Estos archivos se organizan de manera gerearcia conocida como una estuctura de archivos.

##### Arbol de directorios en Linux
El arbol de directorio en linux empieza desde el nivel mas alto llamado *root* el cual esta representado por un slash `/` de ahi se pueden ver diferetens ramas de directorios siempre llendo hacia abajo

```txt
/ 
|-- bin 
| |-- file1 
| |-- file2 
|-- etc 
| |-- file3 
| `-- directory1 
| |-- file4 
| `-- file5 
|-- home 
|-- var
```

##### Como entender las rutas de archivos

La locacion/direccion de un archivo se describe de la secuencia de otros directorios/archivos desde un punto de inicio hasta el destino especifico si tienes una carpeta llamada `star` que esta adentro de `/home` y tienes una carpeta llamada `peliculas` adentro de `star` la ruta se veria algo asi `/home/star/peliculas`

##### Como saber donde estoy

Para poder navegar entre nuestros archivos es muy importante saber donde estas en todo momento es por eso que en linux existe *pwd*
`print working directory` al ejecutar este comando la shell nos regresara la direccion donde nos encontramos acutalmente empezando desde `/`

#### `cd (Change Directory)`

Para poder movernos dentro del sistema de directorios de linux necesitaremos la direccion exacta a donde nos gustaria movernos. La herramienta principal apr ahacer esto es
*cd* entender este comando es fundamental para poder trabajar desde la terminal

##### Entendiendo las rutas

Existen 2 maneras de poder especificar una direcion *absoluta* y *relativa*

- **Rutas absolutas** esta es básicamente una ruta que empieza desde el directorio *root* `/` hasta la direcion a donde nos moveremos
- **Rutas relativas** las rutas relaticas se usan caundo ya estamos en una direccion y queremos entrar a un subdirectior que esta en el nivel en que estamos no ahce falta escribir toda la ruta absoluta solo ahce falta escribir el lugar a donde nos moveremos, por ejemplo estamos en `home/star/` y dentro de este directorio existe `tareas` que es otro directorio no es necesario escribir el path absoluto solamente escribir `/tareas` 
##### Comandos esenciales 

Navegar usando rutas absolutas en un poco complicado por lo cual existen comandos que nos lo facilitaran al usar *cd* 

- `.` Representa el directorio actual
- `..` Te mueve un nivel arriba del directorio actual
- `d` Te mueve al directorio *home* persona
#### `ls (List Diretories)`

#### `touch`

#### `file`

#### `cat`

#### `less`

#### `history`

#### `cp (Copy)`

#### `mv (Move)`

#### `mkdir (Make Directory)`

#### `rm (Remove)`

#### `find`

#### `help`

#### `man`

#### `whatis`

#### `alias`

#### `exit`
## Connections
- **Related to:**  [[Curso Linux Labex]]
- **Contrast with:** [[Opposing Concept]]

## Application / Example
```shell
echo "Hello World" #input
"hello World" # output
pwd #input
/home/soyt0ny/Desktop # output
```

## References
- Source: [Command Line](https://labex.io/lesson/the-shell)
