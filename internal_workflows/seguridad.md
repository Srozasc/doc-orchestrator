---
name: seguridad
keywords:
    - seguridad
    - seguridad
    - security
    - vulnerabilidades
    - auditoria
    - csp
    - cors
    - security
outputs:
    - docs/AUTODOC_SECURITY_AUDIT.md
dependencies:
    - dependencias
---

# Postura de Seguridad y Auditoría

Este proceso realiza un inventario de las defensas y estándares de seguridad del proyecto.

### 1. Auditoría de Protecciones
- Revisa políticas de seguridad (CORS, CSP), sanitización de datos y manejo de sesiones.
- Identifica el uso de encriptación o hashes.

### 2. Análisis de Dependencias
- Revisa el estatus de vulnerabilidades conocidas en las librerías instaladas.
- Analiza la exposición de secretos o configuraciones sensibles.

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_SECURITY_AUDIT.md`.
- El documento debe incluir un resumen de las medidas de seguridad activas y el estado de salud de las dependencias.
