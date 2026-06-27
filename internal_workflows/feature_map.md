---
name: feature_map
keywords:
    - feature map
    - features
    - funcionalidad
    - componentes
    - valor
    - producto
    - mapa de funcionalidades
outputs:
    - docs/AUTODOC_FEATURE_MAP.md
dependencies:
    - arqueologo
    - catalogo_componentes
---

# Mapa de Funcionalidades (Feature Map)

Este proceso actúa como un puente entre el código técnico y las capacidades del producto.

### 1. Inventario de Componentes
- Lista los archivos clave en `src/components` y `src/app`.
- Analiza la intención de cada componente.

### 2. Mapeo a Valor de Negocio
- Asocia componentes técnicos con "Features" que el usuario puede usar.
- Describe el beneficio de cada característica.

### 3. Generación de Documentación
- Crea o actualiza `docs/AUTODOC_FEATURE_MAP.md`.
- El documento debe incluir una tabla que relacione: Característica, Componente Técnico y Beneficio.

### Instrucciones de Estilo
- Mantener un tono enfocado en el valor para el usuario.
