---
tags:
  - note
status: finish
created: 2026-02-25
tech:
  - NativeWind
  - Expo
  - ReactNative
domain: App Development
---

# Native Wind

## Core Idea
> NativeWind permite utilizar clases de utilidad estilo Tailwind CSS directamente en componentes de React Native, facilitando un estilizado rápido y declarativo mediante el prop `className`.

## Explanation
NativeWind funciona como un puente entre la sintaxis de Tailwind CSS y el sistema de estilos de React Native. Transforma las clases de utilidad en objetos de estilo nativos, permitiendo escribir interfaces de usuario de manera más veloz sin perder las optimizaciones de la plataforma.

A diferencia de las hojas de estilo tradicionales (`StyleSheet.create`), los estilos se aplican directamente en el JSX, reduciendo el cambio de contexto entre lógica y diseño.
## Application / Example
Uso básico con componentes de React Native:

```tsx
import { View, Text } from 'react-native';

export default function App() {
  return (
    <View className="flex-1 items-center justify-center bg-white">
      <View className="mt-10 p-4 bg-gray-100 rounded-lg">
        <Text className="text-red-500 text-3xl font-bold">
          Hola Mundo
        </Text>
      </View>
    </View>
  );
}
```

## Trade-offs
- **Pros:** Desarrollo rápido, consistencia con web si ya usas Tailwind.
- **Cons:** Puede desordenar el JSX con muchas clases (clutter); requiere configuración de Babel/Metro.

## References
- Source: [Documentación Oficial - Instalación](https://www.nativewind.dev/docs/getting-started/installation)
- Image:
 ![Imagen De Tailwind Como Funciona.png](../Attachments/Imagen%20De%20Tailwind%20Como%20Funciona.png.png)

