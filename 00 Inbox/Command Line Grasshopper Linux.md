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
- `~` Te mueve al directorio *home* personal
- `-` Te mueve al ultimo directorio donde estuviste
#### `ls (List Diretories)`

Ahora que sabemos como movernos al rededor del sistema es importante saber a que podemos acceder

El comando *ls* nos ayudara a poder listar los arhivos que existan en el directorio actual

##### Flags de ls

Cuando usamos *ls* podremos usar `flags` las cuales son como comandos extras que especifican como funciona el comando

`-a` nos permite poder listar todos los archivos hasta los archivos escondidos básicamente los que empiecen con `.` 

`-l` nos permite listar a los archivos dandonos informacion extra los cuales pueden ser, peso, fecha de `permisos/creador/grupo/peso/modificacion/nombre`

`-r` nos listara los archivos al revés de manera alfabética

##### Combinar flags

Podemos combiar las flags en un mismo comando esto hara que podamos modificar la manera en la que funciona el comando de manera especifca

`ls -lar` lista todos los elementos, con informacion extra y de manera alfabetica al revez

`ls -arl` hara exactamente lo mismo no importa el orden de las flags 

#### `touch`

*touch* es un comando que nos ayudara crear cualquier tipo de archivo vacio.
el comando se compone simplemente de `touch {nombre_del_archivo}.{extension}`
Podemos crear varios archivos al mismo tiempo agregando mas nombres y extensiones

##### Flags `touch`

`-r` nos permite cambiar el timeStamp  deun archivo por el de otro para esto tendremos que pasarle el archivo a modificar y el archivo del que tomaremos el time stamp

`-d` podremos pasarle manualmente el timeStamp que queremos agregar al archivo seleccionado


#### `file`

El comando *file* simplemente mostrara que tipo de archivo es el archivo que seleccionemos 

#### `cat`

Después de aprender a navegar atravez de los archivos a hora necesitamos saber como poder ver el contenido que estos tienen por lo cual sera necesario a prender el comando *cat* `concatenate` lo cual nos da una pequena pista de que podemos hacer con el

en primer lugar al usar el comando `cat` por si solo pasandole solo un archivo este nos dara su contenido en terminal

`cat holaMundo.txt` 

para poder concatener o juntar archivos sera necesario pasarle como parametros los 2 o mas archivos.
Imprimiendo en terminal en el orden en que los enviamos

Podemos usar `cat > {nombreDelArchivo}` para poder escribir/agregar contenido a un archivo desde la terminal al momento de termina de escribirlo tendremos que presionar `CTRL + D` para guardar los cambios

##### Flags comunes en Cat

`-n` Numera la cantidad de lineas que hay en el archivo empezando desde 1

`-b` solo nos dara las lineas que no esten vaciasq

#### `less`

El comando *less* nos ayudara a poder leer archivos grandes de manera sencilla debido a que nos dara la opcion de ir 'cambiando de pagina' para poder leerlo de poco en poco ademas de que esto, este comando no imprimira nada en la consoloa que estemos usando

##### Comandos/ Flags  a aprender

Cuando estemos dentro de less podremos usar  Page up Page down Up y Down para podernos mover

si precionamos `g` nos movera directamente al incio del archivo
si precionamos `G` nos movera al final del archivo 
si precionamos `h` nos mostrara informacion de ayuda

para hacer busquedas en el archivo podremos usar `/{palabra a buscar}` y presionar `enter` 

Para poder navegar entre las palabras seleccionadas 
podemos usar `n` para poder navegar al siguiente termino  
`N` para poder navegar al termino anteririos

#### `cp (Copy)`

Uno de los comandos mas importantes o basicos que podemos usar en linux es *cp* es el encargado de poder copiar archivos hacia algun directorio que nosotros escojamos la sintaxis es basicamente `cp [archivo] [direccion de destino]`

por ejemplo digamos que estamos en la ruta `/home/soyt0ny/desktop` y tenemos los siguientes archivos `/fotos holaMundo.html home.htmnl crack.txt /programas` 

Queremos mover `crack.txt` a la carpeta de `/programas` para hacer esto usaremos las rutas relativas en este caso y el comando *cp* 

`cp crack.txt /programas` lo que hara este comando es copiar el archivo adentro del directorio `/programas`

##### Comando de Bulk / Directorios

Si queremos mover varios archivos que nosotros sepamos que tendran cierto patron palabra o caracteres. podremos usar los siguientes 'wildCards'

- `*` Cualquier archivo que tenga este secuencia
- `?` cualqueir archivo que tenga por lo menos 1 de estos caracteres
- `[]` cualquier archivo que tenga los caracteres que estan entre los corchetes

por ejemplo mover todos los archios `.jpg` de nuestra carpeta `/fotos` en el `/desktop` a la carpetea de fotos que esta un nivel mas arriba de `/desktop`

en este caso tendremos que usar lar rutas absolutas debido a que tenemos que indicar exactamente en donde enviaremos las fotos siendo en este caso esta la ruta `/home/soyt0ny/fotos` 

`cp *.jpg /home/soyt0ny/fotos` esto enviara todos los archivos que justamente tengan .jpg a la carpeta de las fotos

##### Copiar directorios

Para poder copiar directorios

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

cd .  # no te mueve
cd .. # te mueve a un directorio mas arriba
cd ~  # te mueve al home personal
cd -  # te mueve al ultimo directorio en el que estabas
```

## References
- Source: [Command Line](https://labex.io/lesson/the-shell)
