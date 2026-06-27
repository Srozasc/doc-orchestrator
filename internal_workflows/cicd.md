---
name: cicd
keywords:
    - cicd
    - cicd
    - pipeline
    - github actions
    - deploy
    - build
    - ci/cd
    - pipeline
    - github actions
outputs:
    - docs/AUTODOC_CI_CD_PIPELINE.md
dependencies:
    - dependencias
    - infraestructura
---

# Análisis de Pipeline de CI/CD

Este proceso reconstruye el flujo de automatización que lleva el código desde el repositorio hasta el entregable final.

### 1. Análisis de Pipelines
- Escanea carpetas de CI/CD (ej. `.github/workflows`, `vercel.json`, `package.json`).
- Identifica los pasos: Verificación, Pruebas, Construcción y Despliegue.

### 2. Modelado del Pipeline
- Reconstruye la secuencia de ejecución de los jobs y sus dependencias.
- Identifica los artefactos generados (ej. binarios, paquetes, contenedores).

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_CI_CD_PIPELINE.md`.
- El documento debe incluir:
    - **Diagrama del Pipeline (D2)**: Visualización del flujo de trabajo.
    - **Detalle de Etapas**: Qué ocurre en cada fase y los comandos involucrados.


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
- Usar un tono técnico y preciso. 
