---
tags:
  - note
status: finish
created: 2026-02-25
tech:
  - NativeWind
domain: App Development
---

# Fuentes Personalizadas - NativeWind

## Core Idea
> Como poder importar de manera correcta las fuentes personalizadas que usaremos en nuestra aplicación, aprendiendo la carga de estas mismas

## Explanation
Como NativeWind es muy parecido a **Tailwind CSS** la manera de agregar fuentes personalizadas será en el archivo de `tailwind.config.js`, es importante tener ya configurado de manera correcta nuestro [Native Wind](../99%20System/Archive/Native%20Wind.md).

### Pasos Generales
1. **Descargar fuentes:** Obtén los archivos `.ttf` o `.otf` (ej. Google Fonts).
2. **Colocar en assets:** Guárdalos en `assets/fonts/` (o la carpeta de recursos de tu proyecto).
3. **Configurar Tailwind:** Registra las familias tipográficas en `tailwind.config.js`.
4. **Cargar fuentes en App:** Usa `expo-font` para cargarlas asíncronamente antes de renderizar.

Después de agregarlas existirán 2 formas de poder usarlas:
1. Haciendo la llamada a la clase `style` y pasándole la *fontFamily* que queremos usar.
2. Usando las mismas clases customs de **NativeWind** usando `font-(nombre que le asignamos a la fuente)`.

Es recomendado usar un `useEffect` en el **Root Layout** para asegurar la carga de las fuentes. De esta manera, prevenimos que la app se muestre antes de tener los recursos listos (evitando el "flash" de fuente predeterminada).


## Connections
- **Related to:** [Native Wind](../99%20System/Archive/Native%20Wind.md)

## Application / Example

Archivo de configuración de Tailwind con las fuentes Agregadas:
```tsx
const { platformSelect } = require("nativewind/theme");

/** @type {import('tailwindcss').Config} */

module.exports = {
  // NOTE: Update this to include the paths to all files that contain Nativewind classes.
  content: [

    "./app/**/*.{js,jsx,ts,tsx}",
    "./App.tsx",
    "./components/**/*.{js,jsx,ts,tsx}",
    "./presentation/**/*.{js,jsx,ts,tsx}",
  ],

  presets: [require("nativewind/preset")],
  theme: {
    extend: {
    //AQUI ES DONDE SE AGREGAN LAS FUENTES
      fontFamily: {
        "work-black": ["WorkSans-Black", "sans-serif"],
        "work-light": ["WorkSans-Light", "sans-serif"],
        "work-medium": ["WorkSans-Medium", "sans-serif"],
         // Detecta el sistema operativo y selecciona la fuente en caso de no tener la fuente instalada
        system: platformSelect({
          ios: "Arial",
          android: "Roboto",
          default: "sans-serif",
        }),
      },
    },
  },
  plugins: [],
};
```

Las distintas formas de poder usarlos:

```tsx
<Text className="text-red-500 text-3xl"
        style = {{fontFamily: "WorkSans-Black"}}>
        Hola Mundo
</Text>
<Text className="text-red-500 text-3xl font-work-medium">Hola Mundo</Text>
<Text className="text-red-500 text-3xl font-work-light">Hola Mundo</Text>
```

Aplicar useEfectt para la carga 

```tsx
import "./global.css";
import { useEffect } from "react";
import { Slot, SplashScreen } from "expo-router"
import { useFonts } from "expo-font";

SplashScreen.preventAutoHideAsync();

const RootLayout = () => {
  const [fontsLoaded, error] = useFonts({
    "WorkSans-Black": require("../assets/fonts/WorkSans-Black.ttf"),
    "WorkSans-Light": require("../assets/fonts/WorkSans-Light.ttf"),
    "WorkSans-Medium": require("../assets/fonts/WorkSans-Medium.ttf"),
  });

  useEffect(() => {
    if (error) throw error;
    if (fontsLoaded) SplashScreen.hideAsync();
    
  }, [fontsLoaded, error]);
  
  if (!fontsLoaded && !error) return null;

  return <Slot />;

};

export default RootLayout;
```

## References
- Source: [Font Family NativeWind](https://www.nativewind.dev/docs/tailwind/typography/font-family)
- Image: 
![](../Attachments/Pasted%20image%2020260225161540.png)