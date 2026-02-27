---
tags:
  - note
status: finish
created: 2026-02-25
tech:
  - Expo
domain: App Development
---

# Expo Framework

## Core Idea
> Expo es un ecosistema de herramientas y servicios construido sobre **React Native** que simplifica el desarrollo de aplicaciones nativas universales (iOS, Android, Web).

## Explanation
Expo abstrae mucha de la complejidad de la configuración nativa (Xcode, Android Studio) permitiendo escribir aplicaciones completas usando solo JavaScript/TypeScript.

Sus componentes principales son:
- **Expo SDK**: Una librería estándar con acceso a APIs nativas (Cámara, GPS, Notificaciones, etc.) pre-instaladas y listas para usar.
- **Expo Go**: Una app cliente que permite previsualizar tu proyecto en un dispositivo físico escaneando un código QR, sin necesidad de compilar código nativo durante el desarrollo.
- **EAS (Expo Application Services)**: Servicios en la nube para construir binarios (.apk, .ipa), gestionar credenciales y enviar actualizaciones OTA (Over-the-Air).
- **Expo Router**: Sistema de navegación basado en archivos (similar a Next.js) que viene por defecto en los proyectos modernos.

## Connections
- **Related to:** [[React Native]], [[Next.js]] (Filosofía similar)
- **Contrast with:** **React Native CLI** (donde tienes control total del código nativo pero mayor complejidad de configuración).

## Application / Example
Para iniciar un proyecto nuevo:
```bash
npx create-expo-app@latest mi-app
```

## References
- Source: 
