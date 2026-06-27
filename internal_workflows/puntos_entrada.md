---
name: puntos_entrada
keywords:
    - puntos entrada
    - entry
    - entrypoints
    - arranque
    - bootstrap
    - main
    - entry points
outputs:
    - docs/AUTODOC_ENTRY_POINTS.md
dependencies:
    - arqueologo
---

# Análisis de Puntos de Entrada (Entry Points)

Este proceso identifica dónde comienza la ejecución y cómo se orquesta la aplicación.

### 1. Identificación de Puntos de Entrada
- Busca archivos raíz de ejecución según el stack detectado:
    - Frontend/App: `App.tsx`, `index.tsx`, `main.ts`, `layout.tsx`.
    - Server/Backend: `server.js`, `main.py`, `app.ts`.
- Identifica archivos de configuración global (ej. `globals.css`, `.env`).

### 2. Análisis de Responsabilidades
- Determina:
    - Qué componentes globales se montan.
    - El flujo secuencial de carga (Bootstrapping).
    - Los puentes de comunicación (ej. IPC en Electron, Middlewares en APIs).

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_ENTRY_POINTS.md`.
- El documento debe incluir:
    - **Lista de Entry Points**: Con su ubicación y rol técnico.
    - **Secuencia de Inicialización**: Diagrama D2 o lista de pasos.
    - **Configuraciones Globales**: Detalle de variables críticas.


### Ejemplo D2
```d2
direction: right
Frontend -> Backend: HTTP/JSON
Backend -> Database: queries

Frontend.shape: rectangle
Backend.shape: rectangle
Database.shape: cylinder
```

### Instrucciones de Estilo
- Mantener una estética técnica y limpia. Sin emojis en el documento final.
