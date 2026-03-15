---
tags:
  - note
status: evergreen
created: 2026-03-09
tech:
  - Linux
domain: Os
---

# Getting Starter Grasshopper Linux

## Core Idea

> Entender la historia de la creación de Linux, qué son las distribuciones y qué tipos de distros existen.

## Explanation

### Historia

El predecesor de Linux fue creado en 1969 por *Ken Thompson* y *Dennis Ritchie*, quienes fueron los creadores del sistema operativo **UNIX**. Después de unos años, reescribieron **UNIX** en C, haciéndolo más portable y amigable para otros desarrolladores.

En 1983, *Richard Stallman* creó el proyecto **GNU** con el objetivo de desarrollar un sistema operativo de código abierto y proveer herramientas para el desarrollo tecnológico.

A principios de 1991, *Linus Torvalds* comenzó a desarrollar un nuevo kernel como proyecto personal. Este kernel, conocido actualmente como **Linux Kernel**, era la pieza que le faltaba a **GNU**. La combinación de las herramientas de **GNU** y el Kernel de Linux dio lugar a un sistema operativo ampliamente utilizado hoy en día.

![[Pasted image 20260309113536.png]]

#### ¿Cuál es el rol de un Kernel?

El kernel es el principal encargado de las operaciones de un sistema; actúa como un puente entre el Software y el Hardware, dando instrucciones sobre cómo manejar los recursos del sistema, tales como CPU, Memoria y la comunicación con los periféricos. En esencia, el Kernel hace que todo funcione correctamente en la computadora. Antes de sistemas como **BSD** o **MINIX**, no existían kernels que fueran completamente open-source y libres.

### Arquitectura de un Sistema Linux

Un sistema Linux se divide en tres partes principales:

- **Hardware**: La parte física (CPU, memoria, almacenamiento, etc.).
- **Linux Kernel**: El encargado de gestionar los recursos del hardware.
- **Espacio de Usuario**: Donde interactuamos con la máquina, ya sea a través de una interfaz gráfica (GUI) o la línea de comandos (CLI).

#### ¿Qué es una Distro en Linux?

Las distribuciones son paquetes que incluyen el **Linux Kernel**, una colección de aplicaciones, utilidades y librerías preconfiguradas. Pueden variar dependiendo de si incluyen una interfaz gráfica o están orientadas a servidores (solo CLI).

### Cómo escoger una distribución

Elegir una distro puede ser abrumador debido a la gran cantidad de opciones. La clave es identificar tu nivel de experiencia y el uso que le darás al sistema.

#### Puntos clave a considerar

- **Nivel de Experiencia**: 
  - *Principiantes*: Se recomiendan distros "beginner-friendly" como **Ubuntu** o **Linux Mint**, ya que su instalación y uso son intuitivos.
  - *Avanzados*: Distros como **Arch Linux** o **Gentoo** ofrecen un control total pero requieren mayor conocimiento técnico.
- **Entorno de Escritorio (Desktop Environment)**: Define la apariencia y el flujo de trabajo. Opciones populares incluyen **GNOME** (moderno), **KDE Plasma** (personalizable) y **XFCE** (ligero).
- **Administrador de Paquetes**: Es el sistema para instalar y actualizar software.
  - `apt` (.deb): Usado en distros basadas en **Debian** (como Ubuntu).
  - `dnf/yum` (.rpm): Usado en distros basadas en **Red Hat** (como Fedora).
  - `pacman`: Usado en **Arch Linux**.

**Tip:** La mejor manera de probar una distro sin alterar tu sistema actual es mediante una **Live USB**.

## Connections
- **Related to:** [[Curso Linux Labex]]
- **Contrast with:** [[Command Line Grasshopper Linux]]

## References
- Source: [Labex Getting Starter](https://labex.io/lesson/linux-history)
