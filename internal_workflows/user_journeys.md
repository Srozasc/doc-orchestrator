---
name: user_journeys
keywords:
    - user journeys
    - journeys
    - flujos
    - usuario
    - paths
    - escenarios
    - flujos de usuario
    - user flows
outputs:
    - docs/AUTODOC_USER_JOURNEYS.md
dependencies:
    - feature_map
---

# Análisis de Flujos de Usuario (User Journeys)

Este proceso analiza la interactividad para reconstruir los flujos de usuario desde una perspectiva funcional.

### 1. Rastreo de Caminos
- Identifica las vistas/páginas disponibles y sus puntos de entrada.
- Busca botones, links y llamadas a la acción (CTAs) para entender las transiciones.

### 2. Modelado del Viaje
- Conecta las vistas en una secuencia lógica (Inicio -> Acción -> Resultado).
- Identifica los objetivos que el usuario busca cumplir.

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_USER_JOURNEYS.md`.
- El documento debe incluir:
    - **Mapa de Flujos (D2)**: Visualización de las transiciones.
    - **Descripción de Escenarios**: Explicación de los caminos críticos (Happy Path y Edge Cases).


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
- Usar diagramas claros. Asegurar contraste en los colores de D2.
