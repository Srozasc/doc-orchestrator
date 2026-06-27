---
name: dependencias
keywords:
    - dependencias
    - dependencias
    - librerias
    - paquetes
    - stack
    - versiones
    - dependecies
    - stack
outputs:
    - docs/AUTODOC_DEPENDENCIES.md
dependencies:
    - arqueologo
---

# Gestión de Dependencias y Ecosistema Técnico

Este proceso desglosa el stack tecnológico y las librerías que sostienen la aplicación.

### 1. Extracción de Manifiestos
- Lee `package.json`, `npm-shrinkwrap.json` o equivalentes.
- Separa dependencias de producción de las de desarrollo (devDependencies).

### 2. Categorización Técnica
- Agrupa por Core, UI/UX, Manejo de Datos y Herramientas de Calidad.
- Evalúa la criticidad de cada dependencia.

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_DEPENDENCIES.md`.
- El documento debe incluir un inventario categorizado y un análisis de la modernidad del stack.
