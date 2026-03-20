---
tags:
  - note
status: evergreen
tech: Linux
domain: Os
---

# Advanced Text-Fu: I/O Redirection and Stream Processing

## Core Concept
> El dominio de *Text-Fu* en entornos Unix-like no se trata solo de conocer comandos, sino de entender la abstracción de **File Descriptors (FD)** y cómo el Kernel gestiona el flujo de bytes entre procesos mediante **Pipes** y **Buffers**.

## Technical Architecture

### 1. File Descriptors and Kernel Abstraction
En Linux, cada proceso inicia con tres canales estándar vinculados por defecto a la terminal (*TTY*):

- **`0` (stdin):** Flujo de entrada. Por defecto, el teclado.
- **`1` (stdout):** Flujo de salida estándar para datos procesados.
- **`2` (stderr):** Flujo de diagnóstico/errores, desacoplado del flujo de datos principal.

> [!info] Kernel Buffering
> El Kernel utiliza un **Buffer circular** (típicamente de 64KB) para los *pipes*. Los datos se almacenan en memoria (Kernel Space) hasta que el proceso de lectura los consume. Esto evita accesos innecesarios a disco, operando a velocidades de memoria RAM.

#### Redirecciones y Entorno
- **`2> /dev/null`**: Descarte a nivel de Kernel. El dispositivo nulo es un sumidero de bits eficiente.
- **`&>`**: Unificación de `stdout` y `stderr`.
- **`env` (Environment)**: Gestión del bloque de entorno del proceso. Al usar `export`, la variable se copia del stack del shell al espacio de memoria del proceso hijo.

---

### 2. The Linux Text Toolbox (Complexity Analysis)

El procesamiento de texto en CLI es altamente eficiente porque opera sobre **Streams**, minimizando el uso de la *Heap* al procesar datos línea por línea.

#### A. Herramientas de Extracción ($O(n)$)
- **`cut`**: Extrae campos o caracteres mediante *offsets* fijos.
- **`head` / `tail`**: Extraen el inicio o el final de un flujo. `tail -f` utiliza *Inotify* para reaccionar a eventos del sistema de archivos sin *polling*.
- **`grep`**: Búsqueda de patrones lineales. Utiliza el algoritmo *Boyer-Moore* para saltar caracteres y optimizar la búsqueda.

#### B. Herramientas de Transformación ($O(n)$)
- **`tr` (Translate)**: Reemplazo o eliminación de caracteres. Utiliza una **Lookup Table** (256 bytes) en memoria para una traducción instantánea.
- **`expand` / `unexpand`**: Conversión entre tabulaciones y espacios.
- **`paste`**: Fusión horizontal de líneas de múltiples archivos.
- **`join`**: Une líneas de dos archivos basándose en un campo común. **Requiere entrada ordenada** ($O(n+m)$).
- **`split`**: Fragmenta archivos grandes en piezas pequeñas basándose en líneas o bytes.

#### C. Herramientas de Análisis y Ordenación
- **`sort` ($O(n \log n)$)**: Implementa *External Merge Sort*. Si el dataset excede la RAM, utiliza memoria secundaria (disco).
- **`uniq` ($O(n)$)**: Deduplicación lineal de líneas adyacentes.
- **`wc` (Word Count) y `nl` (Number Lines)**: Análisis estadístico básico de streams.

---

### 3. Advanced Pipelines: Pipe and Tee

- **Pipe (`|`)**: Conecta el `stdout` del proceso A con el `stdin` del proceso B. Es una forma de **Programación Funcional** en la shell: `f(g(x))`.
- **Tee**: Actúa como un divisor de flujo. Duplica el *stdout* hacia un archivo (persistente) y lo mantiene en el *pipeline* para procesamiento posterior.

```bash
# Ejemplo: Capturar logs, numerarlos y filtrar errores en un solo paso
cat server.log | tee full_backup.log | nl | grep "ERROR"
```

> [!tip] Optimization Insight
> La regla de oro es **filtrar temprano**. Ejecutar `grep` o `cut` antes de un `sort` reduce drásticamente el valor de $n$, disminuyendo el tiempo de ejecución de la fase $O(n \log n)$.

## Application Example: Data Cleaning
```bash
# Limpiar un CSV, ordenar por ID, quitar duplicados y expandir tabs a espacios
cat data.csv | tr ',' '\t' | expand | sort -k1,1 | uniq > clean_data.txt
```

## Connections
- **Parent Area:** [[Curso Linux Labex]]
- **Related Notes:** [[ALGORITHMS]], [[Command Line - Linux]]
- **Deep Dive:** *The Algorithm Design Manual* (Sección de Sorting/Searching).

## References
- POSIX IEEE Std 1003.1.
- GNU Coreutils documentation.
