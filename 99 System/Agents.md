# Instrucciones para Agentes (Agents.md)

Este documento define las reglas y convenciones para agentes de IA que interactúan con esta bóveda de Obsidian.

## Estructura de la Bóveda (PARA)

La bóveda está organizada usando el método PARA:

| Carpeta        | Propósito                                      |
|----------------|------------------------------------------------|
| `00 Inbox/`    | Captura rápida; organizar después              |
| `10 Daily/`    | Una nota por día                               |
| `20 Projects/` | Trabajo activo (`Engineering/`, `University/`) |
| `30 Areas/`    | Responsabilidades continuas                    |
| `40 Knowledge/`| Notas atómicas perennes (Evergreen)            |
| `99 System/`   | Plantillas, config de agentes, adjuntos        |
| `Templates/`   | Plantillas de notas (no colocar notas aquí)    |

`Home.md` es el tablero principal.

## Convenciones de Notas

### Frontmatter
Todas las notas usan YAML frontmatter. Las etiquetas usan formato multi-línea.

```yaml
tags:
  - project
status: active
```

### Plantillas
Siempre basa las nuevas notas en la plantilla apropiada de `Templates/`:

| Plantilla            | Uso para                       | Frontmatter requerido                       |
|----------------------|--------------------------------|---------------------------------------------|
| `2-Daily Note.md`    | `10 Daily/`                    | `date: YYYY-MM-DD`, `tags: [daily]`         |
| `4-Project.md`       | `20 Projects/`                 | `tags: [project]`, `status: active`, `owner:`, `area:` |
| `1-Course.md`        | `30 Areas/University/Courses/` | `tags: [course]`, `semester:`, `professor:` |
| `3-Knowledge Note.md`| `40 Knowledge/`                | `tags: [note]`, `Tech:`, `Domain:`          |

**Nota:** Las notas diarias usan `{date}` como marcador de posición.
Los proyectos deben incluir `start_date: '{"date":null}'`.

### Nombres de Archivos
- Carpetas principales usan prefijos numéricos de dos dígitos (`00`, `10`, etc.).
- Notas diarias: `YYYY-MM-DD.md`.
- Otras notas: Títulos descriptivos claros.
- **Sin Emojis:** Evita estrictamente emojis en nombres de archivos, títulos o contenido.

## Estilo
- Tono profesional y conciso.
- **Sin Emojis** en el cuerpo del contenido.

## Flujo de Trabajo de Revisión
- Solo revisar archivos con `status: review` en el frontmatter.
- Si se pide revisar otro estado, **PREGUNTAR AL USUARIO**.
- Al completar revisión:
  1. Cambiar `status` a `finish`.
  2. Mover a `99 System/Archive/` (si aplica o se instruye).

## Configuración de Agentes
Las definiciones de habilidades por agente están en `99 System/Agents/`.
