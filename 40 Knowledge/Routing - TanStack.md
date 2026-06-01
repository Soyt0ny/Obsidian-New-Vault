---
tags:
  - note
status: evergreen
created: 2026-06-01
tech:
  - TanStack
domain: Frontend
---

# Routing - TanStack

## Core Idea
> Aprender cómo funciona el routing en TanStack y las diferentes formas que tiene para resolverlo

## Explanation

En TanStack Router existe el **file-based routing**: los archivos que creemos dentro de la carpeta `routes/` se convierten automáticamente en rutas accesibles en la web.

Para esto, TanStack exporta `createFileRoute`, que se encarga de crear la ruta y registrarla automáticamente en el `routeTree`.

> [!info] routeTree.gen.ts
> TanStack Router genera automáticamente el archivo `routeTree.gen.ts` escaneando la carpeta `routes/`. Este archivo registra todas las rutas del proyecto. **Nunca lo edites manualmente** — se sobreescribe en cada cambio.

### El archivo `__root.tsx`

En TanStack existe un archivo especial que se renderiza **siempre** antes de cargar cualquier otra ruta: `__root.tsx`. Aquí es donde se guarda la información persistente — Navbar, Footer, CSS globales, meta tags — y es obligatorio que incluya `<Outlet />` para que las rutas hijas se rendericen dentro de él.

```tsx
// routes/__root.tsx
import { createRootRoute, Outlet } from '@tanstack/react-router'

export const Route = createRootRoute({
  component: () => (
    <>
      <Navbar />
      <Outlet />
      <Footer />
    </>
  ),
})
```

> [!tip] Outlet es el punto de montaje
> Sin `<Outlet />` en `__root.tsx`, ninguna ruta hija se mostraría. Es el equivalente al `{children}` de un layout en Next.js.

### Subrutas y carpetas

Al crear una carpeta dentro de `routes/`, TanStack genera subrutas automáticamente:

```
routes/
├── __root.tsx        →  siempre renderizado
├── index.tsx         →  /
├── skills/
│   ├── index.tsx     →  /skills
│   └── new.tsx       →  /skills/new
```

Si queremos que `/skills` tenga su propia página, es necesario crear específicamente el archivo `index.tsx` dentro de la carpeta — ese archivo se convierte en el "home" de esa subruta.

### Rutas dinámicas

Para crear rutas dinámicas se usa el prefijo `$` en el nombre del archivo o carpeta:

```
routes/
├── skills/
│   └── $skillId.tsx     →  /skills/:skillId
└── profile/
    └── $userId/
        └── index.tsx    →  /profile/:userId
```

```tsx
// routes/skills/$skillId.tsx
export const Route = createFileRoute('/skills/$skillId')({
  component: SkillDetailPage,
})

function SkillDetailPage() {
  const { skillId } = Route.useParams()
  return <h1>Skill: {skillId}</h1>
}
```

> [!warning] Convención de naming
> TanStack usa `$param` en el sistema de archivos, pero internamente el parámetro se accede como `params.skillId` (sin el `$`). No confundir con la sintaxis `:param` de React Router.

### El componente `Link`

En una SPA (single page application) nunca debemos usar `<a href="/skills">` para navegar. Un `<a>` dispara una solicitud HTTP completa al servidor, recargando toda la página y destruyendo el estado de React. `Link` de TanStack Router hace navegación **client-side**: actualiza la URL, ejecuta los loaders de la ruta destino y renderiza el componente correspondiente — sin recargar.

```tsx
import { Link } from '@tanstack/react-router'

// Navegación simple
<Link to="/skills">Ver skills</Link>

// Ruta dinámica — params es obligatorio y tipado
<Link to="/skills/$skillId" params={{ skillId: skill.id }}>
  {skill.name}
</Link>
```

#### Por qué es type-safe

Aquí entra el `routeTree.gen.ts`. Cada vez que guardas un archivo en `routes/`, TanStack regenera ese archivo con los tipos de **todas las rutas registradas**. El componente `Link` usa esos tipos para validar el prop `to` en tiempo de compilación.

```tsx
// Error de TypeScript: la ruta /skills/delete no existe en el routeTree
<Link to="/skills/delete">Eliminar</Link>

// Error de TypeScript: falta el param obligatorio skillId
<Link to="/skills/$skillId">Ver</Link>

// Correcto
<Link to="/skills/$skillId" params={{ skillId: '42' }}>Ver</Link>
```

> [!info] La conexión con routeTree.gen.ts
> `routeTree.gen.ts` exporta el tipo `RegisteredRouter`, que contiene el mapa completo de rutas → params → search params. `Link` se tipa contra ese mapa. Si agregas una ruta nueva, `Link` la conoce de inmediato. Si renombras una ruta, TypeScript te marca todos los `Link` rotos antes de que lo descubras en el navegador.

> [!tip] Prefetching
> `Link` soporta `preload="intent"`: cuando el usuario hace hover sobre el link, TanStack ejecuta el loader de la ruta destino anticipadamente. La navegación resulta instantánea porque los datos ya están listos.

```tsx
<Link to="/skills" preload="intent">Ver skills</Link>
```

## Connections
- **Related to:** [[Fetch de Data y Loaders - TanStack]] — los loaders están atados a las rutas; cada ruta puede tener el suyo
- **Contrast with:** Next.js App Router — también es file-based pero usa convenciones distintas (`page.tsx`, `layout.tsx`) y no genera un `routeTree` explícito

## References
- Source: TanStack Router Docs — File-Based Routing
