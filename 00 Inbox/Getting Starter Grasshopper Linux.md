---
tags:
  - note
status: revision
created: 2026-03-09
tech:
  - Linux
domain: Os
---

# Getting Starter Grasshopper Linux

## Core Idea

> Entender un poco sobre la historia de como se creo Linux , que son las distribuciones y que tipos de distros existen

## Explanation

### Historia

El predecesor de Linux tal y como lo conocemos fue creado en 1969 por *Ken Thompson* y *Dennis Ritchie* fueron los creadores del Sistema Operativo **UNIX**.
Después de unos años reescribieron **UNIX** en C haciendo mas portable y a su vez mas amigable con otras personas.

En 1983 *Richard Stallman* crea un proyecto llamado **GNU** el objetivo era crear una sistema operativo open-source, además de póder proveer varias herramientas para el desarrollo de nuevas tecnologías

A principios de 1991 *Linus Torval* empezo a desarrollar un nuevo kernel como un proyecto personal. Este kernel que actualmente ente conocemos como Linux Kerner, era la piesa que necesitava **GNU**. 
La combinacion de las herramientas de **GNU** y del Kernel de Linux fue creado haciendo un sistema operativo que es altamante usado a dia de hoy

![[Pasted image 20260309113536.png]]

#### Cual es el rol de un Kernel

El kernel es el principal encargado de las operaciones de un systema, este actua como un puente entre el Software y el Hardkware dando instrucciones de como manejar los recursosd el sistema, tales como CPU,Memoria y la comuncacion con los perifericos.
En esencia un Kernel es el en cargado de poder hacer que todo funcione de cierta manera en tu computadora.
Antes de que se desarrollaran sistemas operativos como **BSD** o **MINIX** no existian kernels que fueran open-source

### Como escoger una distribución

Como vimos anterior mente cuando hablamos de linux nos referimos al kernel pero tipicamente le llamamos linux a las distrubuciones o `distros` estan son el sistema operativo completo.

Un sistema Linux se divide en 3 partes principales

- **Hardware** : esto es toda la parte fisicas de la computadora, cpu, memoria, espacios de almacenamiento etc.

- **Linux Kernel** : el encargado de manejar los recuersos del la computadora

- **Espacio de usuario** : aqui es donde nosotros interactuamos con la maquina, ya puede ser atravez de una Ui o desde CLI

#### Que es una Distro en Linux

Las distribuciones son paquetes que tienen el *kernel* de **Linux** , una colección de aplicaciones, utilidades, librerías etc.
Aparte de que algunas pueden variar entre tener GUI o no.
Básicamente son diferentes paquete pre armados con características diferentes dependiendo el uso que le daremos

#### Como escoger una distribucion

Al momento de inentar escoger una distro puede ser un pcoo tedioso debido a ala cantidad de opciones que existen. la clave para poder elegir una es tan sencillo como saber que tan envuelto en el sistema quieres estar y tu nivel de entrada en estos mismos

#### Puntos clave a considerar

- **Nivel de Experiencia** Si eres nuevo en linux, se recomeidna buscar distribuciones que sean beginner-friendly . Por ejemplo Ubuntu Linux Mint son bastante populares debido a que tanto su instalacion como su uso se parece mucho a otros sistemas operativos. Si ya tienes mas experiencia, puedes llegar a usar distros como Arch Linux o Gentoo
- **Ambiente de Escritorio** Es el encargado en definir como se sentirá y se vera tu sistema. las opciones mas populares son *GNOME*, *KDE Plasma* y *XFCE*.
  Tambien existen alternativas mas modernas como *Wayland* 
- **Administrado de paquetes** Las distribuciones usan los administradores de paquetes para poder installar,actualizar o desisntalar software. Los mas usados son `apt y archivos .deb` para distros basadas en *Debian* y `dnf o yum para archivos .rpm` para distros basadas en *Red-Hat*

La mejor manera de poder correr una distro sin necesidad de desaparecer tu sistema opertaivo actual es descargandola en una usb y tener algo que se le llama `Live USB`

## Connections
- **Related to:** [[Curso Linux Labex]]
- **Contrast with:** [[Command Line Grasshopper Linux]]

## References
- Source: [Labex Getting Starter](https://labex.io/lesson/linux-history)
