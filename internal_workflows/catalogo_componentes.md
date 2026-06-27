---
name: catalogo_componentes
keywords:
    - catalogo componentes
    - componentes
    - ui
    - design
    - props
    - component catalog
    - storybook
outputs:
    - docs/AUTODOC_COMPONENT_CATALOG.md
dependencies:
    - feature_map
---

# Catálogo de Componentes de UI

Este proceso mapea el sistema de diseño y los componentes reutilizables del proyecto.

### 1. Escaneo de Componentes
- Lista los archivos en `src/components`, `src/ui` o equivalentes.
- Clasifica entre componentes de visualización y componentes lógicos.

### 2. Análisis de Interfaz
- Extrae las Propiedades (Props) y Parámetros principales.
- Identifica la interactividad y las librerías de UI utilizadas.

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_COMPONENT_CATALOG.md`.
- El documento debe incluir fichas técnicas de cada componente y una guía de reuso.
