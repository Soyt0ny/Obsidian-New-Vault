---
tags:
  - note
status: finished
created: 2026-02-25
Tech:
  - Expo
  - ReactNative
Domain: APP DEVELOPMENT
---

# Navegación Expo

## Core Idea
> Aprender sobre como se *navega* dentro de una aplicación de expo, usando la estructura de carpetas

## Explanation
Cuando nosotros creamos una ampliación de expo nuestro directorio **APP** es donde se almacenaran nuestras *vistas/paginas* la manera correcta de poder separar nuestra aplicación es creando carpetas con el nombre que llevara nuestra *vista/pagina*, expo se encargara de hacer el Routing de manera correcta.

Es importante mencionar que existen distintas maneras de nombrar Estas Carpetas y  tales como :

`[nombre de la carpete]` = Crea los famosos Slugs los cuales son rutas dinámicas, esto nos puede servir en caso de que tengamos entradas que no serán constante esto puede ser como las entradas de un blog  etc.
`(nombre de la carpeta)` = creara un link simbólico, sirve para tener mejor organizado nuestros archivos, en nuestro link no se mostrara el nombre de la carpeta, solamente donde encuentre el index. un caso de uso puede ser para hacer las paginas de *Auth* donde la carpeta se llamara `(AUTH)` pero tendrá 2 rutas distintas una para el *Login* y otra para el *Sign*


Es importante saber que los archivos mas importantes son 
- `index`
	Basciamente es el archivo encargado de mostrar el contenido de la ruta en la que estamos
- `_layout`
	Es el archivo encargado de mostrar ciertos elementos siempre, muy usado para mostrar algún footer, hero, etc.

## Connections
- **Related to:** [[Expo Framework]], [[Stacks - Expo]]
- **Contrast with:** **React Navigation** (Librería base subyacente)

## Application / Example
Ejemplo de estructura de archivos para navegación con Tabs y Stack:

```txt
app/
├── _layout.tsx      # Layout raíz (Stack o Tabs)
├── index.tsx        # Ruta inicial (/)
├── (auth)/          # Grupo de rutas (no afecta URL)
│   ├── login.tsx    # /login
│   └── register.tsx # /register
└── user/
    └── [id].tsx     # Ruta dinámica (/user/123)
```

Para crear un link entre páginas:
```tsx
import { Link } from 'expo-router';

export default function Page() {
  return (
    <Link href="/user/1">Ver perfil</Link>
  );
}
```

## References
- Source: 
