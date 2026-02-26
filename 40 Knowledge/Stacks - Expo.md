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

# Stacks Expo

## Core Idea
> El **Stack Navigator** (`<Stack />`) en Expo Router gestiona una pila de pantallas donde cada nueva vista se coloca encima de la anterior, proporcionando transiciones nativas y una barra de navegación.

## Explanation
Es el tipo de navegación más común, similar a una baraja de cartas. Cuando navegas a una nueva ruta, la pantalla se "empuja" (push) al stack. Cuando regresas, se "extrae" (pop).

En **Expo Router**, se define típicamente en un archivo `_layout.tsx`:
- El componente `<Stack />` envuelve las rutas hijas.
- Puedes configurar opciones por pantalla usando `<Stack.Screen />` (título, botones en el header, visibilidad).
- Soporta navegación profunda (deep linking) automáticamente basada en la estructura de archivos.

## Connections
- **Related to:** [[Navegación - Expo]] (Base de la navegación)
- **Contrast with:** **Tabs** (Navegación paralela/inferior), **Drawer** (Menú lateral).

## Application / Example
Ejemplo de `app/_layout.tsx`:

```tsx
import { Stack } from 'expo-router';

export default function Layout() {
  return (
    <Stack
      screenOptions={{
        headerStyle: { backgroundColor: '#f4511e' },
        headerTintColor: '#fff',
      }}
    >
      {/* Configuración específica para la ruta 'index' */}
      <Stack.Screen 
        name="index" 
        options={{ title: 'Inicio' }} 
      />
      {/* Configuración para 'details' */}
      <Stack.Screen 
        name="details/[id]" 
        options={{ title: 'Detalles' }} 
      />
    </Stack>
  );
}
```

## References
- Source: [Expo Stacks Docs](https://docs.expo.dev/router/advanced/stack/)
