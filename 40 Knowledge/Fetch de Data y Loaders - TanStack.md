---
tags:
  - note
status: evergreen
created: 2026-05-14
tech:
  - TanStack
domain: Frontend
---

# Fetch de Data y Loaders - TanStack

## Core Idea
> Entender cómo TanStack Router realiza el fetch de data y la carga para hacer su SSR

## Explanation

Cuando el usuario navega a una ruta, el navegador emite una solicitud *GET*. **TanStack Router** resuelve esa solicitud atravesando el árbol de rutas (*routeTree*), y es en ese momento cuando los **loaders** se ejecutan.

Por ejemplo, si navegamos a `skills/tanstack-query`, el router activa dos rutas simultáneamente:
1. La ruta `skills/` ejecuta su propio *loader*
2. La ruta `skills/tanstack-query` ejecuta el suyo

> [!info] Ejecución en paralelo
> Los loaders de todas las rutas activas se ejecutan **en paralelo**. TanStack Router no espera que uno termine para iniciar el siguiente — esto elimina el problema del "waterfall" de requests y mejora notablemente el rendimiento de carga inicial.

Una vez que los loaders resuelven, TanStack solo re-hidrata los **componentes afectados** por los cambios de datos, no la página completa. Esto es posible porque cada ruta administra su propio scope de datos de forma independiente.

> [!tip] Diferencia clave con SSR tradicional
> En SSR clásico se re-fetcha todo en cada navegación. Con TanStack Router, si navegas entre subrutas de `skills/`, el loader de `skills/` solo se re-ejecuta si sus dependencias cambiaron — el resto se sirve desde caché.

> [!warning] El loader no "modifica" el DOM
> El loader únicamente **retorna datos**. Es React quien decide qué partes del árbol de componentes se re-renderizan a partir de esos datos. No confundir responsabilidades.

## Application / Example

```tsx
// routes/skills/$skillId.tsx
export const Route = createFileRoute('/skills/$skillId')({
  loader: async ({ params }) => {
    const skill = await fetchSkill(params.skillId)
    return { skill }
  },
  component: SkillPage,
})

function SkillPage() {
  const { skill } = Route.useLoaderData()
  return <h1>{skill.name}</h1>
}
```

El hook `useLoaderData()` está **tipado automáticamente** a partir del valor de retorno del loader — TypeScript infiere el tipo sin configuración adicional.

## Connections
- **Related to:** [[Routing - TanStack]]
- **Contrast with:** React Query — mientras los loaders de TanStack se ejecutan a nivel de ruta (integrado con navegación), React Query opera de forma puramente client-side con cache reactivo. Pueden usarse juntos.

## References
- Source: TanStack Router Docs — Data Loading
