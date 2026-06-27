---
name: infraestructura
keywords:
    - infraestructura
    - infraestructura
    - servicios
    - cloud
    - proveedores
    - externos
    - infra
    - servicios externos
outputs:
    - docs/AUTODOC_INFRA_INVENTORY.md
dependencies:
    - dependencias
---

# Inventario de Infraestructura y Servicios

Este proceso identifica las dependencias de infraestructura y servicios externos que sostienen la aplicación.

### 1. Detección de Servicios
- Identifica APIs externas, proveedores de nube, bases de datos y herramientas de sistema (ej. Chromium, Node).
- Analiza archivos de configuración y variables de entorno.

### 2. Análisis de Dependencia
- Determina el rol de cada recurso (ej. "Motor de renderizado", "Autenticación", "Almacenamiento").
- Evalúa si la dependencia es bloqueante o si permite funcionamiento offline.

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_INFRA_INVENTORY.md`.
- El documento debe incluir:
    - **Tabla de Recursos**: Nombre, proveedor y propósito.
    - **Análisis de Resiliencia**: Dependencias críticas vs opcionales.

### Instrucciones de Estilo
- Mantener un formato estructurado y fácil de consultar.
