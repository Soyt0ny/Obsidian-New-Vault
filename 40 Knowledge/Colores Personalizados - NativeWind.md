---
tags:
  - note
status: finish
created: 2026-02-25
Tech:
  - NativeWind
Domain: APP DEVELOPMENT
---

# Colores Personalizados - NativeWind

## Core Idea
> Saber como se crean los colores personalizados en NativeWind

## Explanation

Para poder crear nuevos colores en [Native Wind](Native%20Wind.md) es tan fácil como modificar el archivo de `tailwind.config.js` en este agregaremos nuestro modulo *colors* donde definiremos los distintos valores que tendrán nuestras clases personalizadas.

Después los podremos usar en nuestro código como cualquier otro tipo de variable **NativeWind**

## Connections
- **Related to:** [NativeWind](../99%20System/Archive/Native%20Wind.md)

## Application / Example


Tailwind Config personalizando colores
```tsx
// tailwind.config.js

module.exports = {
  theme: {
    extend: {
      colors: {
		// Se pueden usar valores HEX, RGB o HSL
		primary: "#123456",
		// Definición de paleta completa para un color
        secondary: {
          100: "#BD9AFD",
          200: "#AC84F8",
          300: "#9B6BF2",
          400: "#8A52EC",
          500: "#7939E6", // Color base recomendado
          600: "#6820E0",
          700: "#5706DA",
          800: "#4600D4",
          900: "#3500CE",
        },
        accent: "#123456",
      },
    },
  },
};
```

Uso de Colores
```tsx
// Ejemplo usando componentes de React Native con clases de NativeWind
<View className="bg-primary p-4 rounded-lg">
  <Text className="text-white text-xl font-bold">Título Primario</Text>
</View>

<Text className="text-secondary-100 text-3xl font-system">Hola Mundo (Tono Claro)</Text>

<Text className="text-secondary-500 text-3xl font-system">Hola Mundo (Tono Base)</Text>

<Text className="text-secondary-900 text-3xl font-system">Hola Mundo (Tono Oscuro)</Text>

<Text className="text-accent text-3xl font-system">Hola Mundo (Acento)</Text>
```

### Tip: Autocompletado en VS Code
Para obtener autocompletado de estos colores personalizados, asegúrate de tener instalada la extensión **Tailwind CSS IntelliSense** y que tu archivo `tailwind.config.js` esté en la raíz del proyecto.
## References
- Source: [Colores Personalizados NativeWind](https://www.nativewind.dev/docs/customization/colors)
Image:
![](../Attachments/Pasted%20image%2020260225170512.png)

