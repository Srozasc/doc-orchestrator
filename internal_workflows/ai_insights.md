---
name: ai_insights
keywords:
    - ai insights
    - ia
    - ai
    - ml
    - insights
    - recomendaciones
    - modelo
    - inteligencia artificial
    - machine learning
outputs:
    - docs/AUTODOC_AI_INSIGHTS_MODEL.md
dependencies:
    - arqueologo
    - feature_map
---

# Modelo de Insights y Lógica de IA

Este proceso analiza los componentes de inteligencia artificial para explicar cómo se generan las recomendaciones y el valor que aportan.

### 1. Análisis del Flujo de Datos
- Identifica las fuentes de datos (Contextos, Propiedades, Estados).
- Analiza cómo se transforman estos datos en sugerencias para el usuario.

### 2. Explicación del Modelo
- Describe los criterios y umbrales de decisión.
- Detalla los tipos de recomendaciones (Estáticas vs Dinámicas).

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_AI_INSIGHTS_MODEL.md`.
- El documento debe incluir un diagrama D2 del proceso de decisión y un catálogo de los insights disponibles.

### Ejemplo D2
```d2
direction: right
Frontend -> Backend: HTTP/JSON
Backend -> Database: queries

Frontend.shape: rectangle
Backend.shape: rectangle
Database.shape: cylinder
```
