---
name: reglas_negocio
keywords:
    - reglas negocio
    - reglas
    - logica
    - validaciones
    - negocio
    - policies
    - business rules
outputs:
    - docs/AUTODOC_BUSINESS_RULES.md
dependencies:
    - feature_map
---

# Extracción de Reglas de Negocio

Este proceso traduce el código técnico (`if/else`, validaciones, filtros) a reglas comprensibles para humanos.

### 1. Extracción de Lógica
- Escanea componentes y servicios buscando estructuras de control de flujo.
- Identifica validaciones de entrada, estados permitidos y políticas de operación.

### 2. Traducción Funcional
- Convierte la lógica de programación a declaraciones de lenguaje natural.
- Agrupa las reglas por funcionalidad (ej. Exportación, Renderizado, Seguridad).

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_BUSINESS_RULES.md`.
- El documento debe incluir:
    - **Tabla de Reglas**: Comparafiva entre Acción Técnica y Regla Operativa.
    - **Políticas Críticas**: Aquellas que afectan directamente el éxito del proceso.

### Instrucciones de Estilo
- Lenguaje claro y directo.
