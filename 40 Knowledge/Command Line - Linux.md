---
tags:
  - note
status: evergreen
created: 2026-03-09
tech:
  - Linux
domain: Os
---

# Command Line Grasshopper Linux

## Core Idea
> Entender cómo funcionan los comandos básicos de la terminal en Linux.

## Explanation
### La shell

La **Shell** es el programa que acepta comandos y los traduce en acciones del sistema operativo. Al abrir una **Terminal**, iniciamos una sesión de la Shell.

#### Bash
**Bash** `(Bourne Again Shell)` es la opción más común, aunque existen otras como *zsh* o *fish*.

#### Shell prompt
Formato típico: `username@hostname:directorio_actual$`. El símbolo `$` indica que está lista para recibir comandos.

---

### Comandos de Navegación y Archivos

#### `pwd` (Print Working Directory)
Muestra la ruta absoluta desde la raíz (`/`) hasta el directorio actual.

#### `cd` (Change Directory)
Permite moverse entre directorios.
- `.` : Directorio actual.
- `..` : Subir un nivel.
- `~` : Ir al Home.
- `-` : Ir al directorio anterior.

#### `ls` (List)
Lista el contenido de un directorio.
- `-a` : Muestra archivos ocultos (empiezan con `.`).
- `-l` : Lista detallada (permisos, dueño, tamaño, fecha).
- `-h` : Formato legible para humanos (KB, MB).

#### `touch`
Crea archivos vacíos o actualiza su timestamp.

#### `file`
Determina el tipo de archivo (texto, binario, imagen, etc.).

#### `cat` (Concatenate)
Muestra el contenido de un archivo en la terminal.
- `cat file1 file2 > combined.txt` : Junta archivos.

#### `less`
Visualizador de archivos grandes. Permite scroll.
- `/palabra` : Buscar hacia adelante.
- `n` / `N` : Siguiente / Anterior resultado.
- `q` : Salir.

---

### Manipulación de Archivos y Directorios

#### `cp` (Copy)
Copia archivos o directorios.
- `-r` : Recursivo (para directorios).
- `-i` : Interactivo (pide confirmación antes de sobrescribir).

#### `mv` (Move)
Mueve o renombra archivos y directorios.
- `mv viejo_nombre nuevo_nombre` : Renombrar.
- `mv archivo /ruta/destino/` : Mover.

#### `mkdir` (Make Directory)
Crea carpetas.
- `-p` : Crea directorios padres si no existen (ej. `mkdir -p a/b/c`).

#### `rm` (Remove)
Elimina archivos o directorios. **¡Cuidado! No hay papelera de reciclaje.**
- `-r` : Eliminar directorios y su contenido.
- `-f` : Forzar eliminación sin preguntar.

#### `find`
Busca archivos en una jerarquía de directorios.
- `find . -name "*.txt"` : Busca archivos .txt en el directorio actual.
- `-type d` : Buscar solo directorios.
- `-type f` : Buscar solo archivos.

---

### Ayuda y Documentación

#### `help`
Muestra ayuda breve sobre comandos integrados de la shell (built-ins).

#### `man` (Manual)
Muestra el manual completo de un comando. Es la fuente oficial.

#### `whatis`
Muestra una descripción de una sola línea sobre la función de un comando.

#### `alias`
Crea atajos para comandos largos.
- `alias ll='ls -lah'`

#### `exit`
Cierra la sesión actual de la terminal.

---

## Connections
- **Related to:** [[Curso Linux Labex]]
- **Contrast with:** [[Getting Started - Linux]]

## Application / Example
```bash
# Ejemplo de flujo de trabajo
mkdir -p proyecto/src
cd proyecto/src
touch main.py
ls -l
echo "print('Hola')" > main.py
cat main.py
```

## References
- Source: [Labex - The Shell](https://labex.io/lesson/the-shell)
