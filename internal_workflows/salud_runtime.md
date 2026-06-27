---
name: salud_runtime
keywords:
    - salud runtime
    - observabilidad
    - logs
    - salud
    - health
    - monitoring
    - observability
    - monitoreo
outputs:
    - docs/AUTODOC_RUNTIME_HEALTH.md
dependencies:
    - infraestructura
---

# Salud del Sistema y Observabilidad

Este proceso identifica las herramientas y prácticas de monitoreo y logging del proyecto.

### 1. Identificación de Observabilidad
- Busca wrappers de logs, integraciones con Sentry, Datadog o similares.
- Identifica el manejo de excepciones globales.

### 2. Análisis de Salud
- Busca endpoints de salud o métricas de performance.
- Identifica indicadores clave (ej. tiempos de respuesta, errores críticos).

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_RUNTIME_HEALTH.md`.
- El documento debe detallar la estrategia de logs y cómo verificar la salud operativa del sistema.
