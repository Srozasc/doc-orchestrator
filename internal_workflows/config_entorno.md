---
name: config_entorno
keywords:
    - config entorno
    - env
    - environment
    - variables
    - configuracion
    - secrets
    - environment
    - env vars
    - config
outputs:
    - docs/AUTODOC_ENVIRONMENT_CONFIG.md
dependencies:
    - dependencias
---

# Configuración de Entorno y Variables

Este proceso mapea el "Contrato de Configuración" necesario para que la aplicación funcione.

### 1. Extracción de Variables
- Lee `.env.example`, `.env` y busca llamadas a variables de entorno en el código.
- Identifica archivos de configuración global del proyecto.

### 2. Clasificación de Configuración
- Categoriza por APIs, Secretos, Base de Datos y Flags de Característica.
- Identifica variables obligatorias vs opcionales.

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_ENVIRONMENT_CONFIG.md`.
- El documento debe incluir una tabla detallada de variables y una guía para configurar nuevos entornos.
