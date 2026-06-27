---
name: doc-orchestrator
description: Módulo autónomo y dinámico para el análisis y generación de documentación técnica/funcional.
---

# Orquestador de Documentación (Doc Orchestrator)

Este skill es un motor de documentación extensible. No tiene procesos fijos; en su lugar, descubre y ejecuta "plugins" de documentación almacenados en su carpeta interna.

## 📁 Estructura del Módulo
- `SKILL.md`: Cerebro de coordinación y descubrimiento.
- `internal_workflows/`: Directorio de plugins (archivos `.md` con frontmatter YAML e instrucciones de análisis).
- `bin/MdToPdf/mdtopdf-rs.exe`: Motor CLI nativo de exportación a PDF (Tipst + D2 bundleados, ~46 MB, sin Chromium).

## 🧠 Lógica de Descubrimiento y Ejecución (Para el Agente)

Cuando recibas una petición de documentación, **DEBES** seguir este protocolo dinámico:

### 1. Fase de Descubrimiento (Plugin Discovery)
Antes de responder, ejecuta un `list_dir` en la ruta:
`{skill_path}/internal_workflows/`

Identifica todos los archivos `.md` disponibles. Lee el frontmatter YAML de cada uno (campos `keywords`, `outputs`, `dependencies`) para entender sus capacidades.

### 2. Fase de Matching
Analiza la petición del usuario y compárala con los `keywords` de cada plugin:
- Si el usuario pide algo general (ej. "documenta el código"), selecciona múltiples plugins relevantes (ej. `arqueologo.md`, `puntos_entrada.md`).
- Si el usuario pide algo específico (ej. "quiero ver la seguridad"), busca el plugin más cercano por `keywords` (ej. `seguridad.md`).
- Si un plugin tiene `dependencies`, ejecútalo después de sus dependencias.
- **Si no encuentras un plugin exacto**, informa al usuario cuáles tienes disponibles.

### 3. Fase de Ejecución
Para cada plugin seleccionado:
1. Lee el contenido del archivo `.md` en `internal_workflows/`.
2. Sigue estrictamente los pasos de análisis descritos en ese archivo.
3. Genera el artefacto Markdown resultante en la carpeta `docs/` del proyecto, usando el path declarado en `outputs` del frontmatter.

### 4. Sincronización PDF
Tras completar el Markdown, conviértelo a PDF ejecutando el motor CLI:
```
& "{skill_path}/bin/MdToPdf/mdtopdf-rs.exe" -i "{input_md}" -o "{output_pdf}"
```

Parámetros del motor:
- `-i, --input <path>`: archivo Markdown (requerido)
- `-o, --output <path>`: archivo PDF (default: `<input>.pdf`)
- `-p, --page-size <size>`: a4/letter/legal/a3/a5 (default: a4)
- `--no-diagrams`: deshabilitar diagramas D2 (renderiza como código)
- `-v, --verbose`: modo verbose

Diagramas: usa bloques de código ` ```d2 ` con sintaxis D2 (https://d2lang.com). El motor los renderiza automáticamente a SVG embebido en el PDF.

---

## 🚀 Cómo extender este Skill
Este skill es "Future-Proof". Para añadir una nueva capacidad de documentación:
1. Crea un nuevo archivo `.md` en `internal_workflows/` con frontmatter YAML:
   ```yaml
   ---
   name: mi_plugin
   keywords: [tema, sinonimo, otro]
   outputs: [docs/AUTODOC_MI_TEMA.md]
   dependencies: []
   ---
   ```
2. Define en él los pasos de análisis (qué archivos leer, qué buscar, qué escribir).
3. El orquestador lo detectará automáticamente en la siguiente ejecución.

## Convenciones
- Mantén la estética profesional (sin emojis en los documentos de `docs/`).
- Diagramas en sintaxis D2 dentro de bloques ` ```d2 `.
- Tipografía profesional gestionada automáticamente por Tipst.

## ⚠️ Trampas comunes al redactar los MD

Estas son fallas reales que aparecieron en la primera generación de la suite.
Aplícalas para que los próximos runs no repitan los mismos problemas.

### 1. Nunca escribir ` ```d2 ` literal fuera de un bloque de diagrama real

El parser busca la cadena ` ```d2 ` y la trata como apertura de bloque. Si
aparece dentro de un párrafo, tabla, bloque de código Rust o comentario, el
conversor intentará renderizar texto arbitrario como D2 y fallará.

**Mal**:
````
```rust
// ejemplo: ```d2    // ← aquí el parser se confunde
A -> B
```
````

**Bien**:
````
```rust
// ejemplo: bloque de diagrama D2 con sintaxis A -> B
```
````

Regla práctica: en prosa, referirse siempre como "bloque de diagrama D2" o
"bloque con sintaxis D2", nunca pegar la fence literal.

### 2. Nunca escribir ` ```lenguaje ` literal fuera de un bloque de código real

El conversor MD→Tipst emite los fences de bloque como raw blocks de Tipst.
Cualquier fence literal en medio de prosa (ej. "` ```rust ... ``` `" en una
descripción) abre un raw block sin cierre y Typst falla con
`unclosed raw text`.

**Mal**:
```
El bloque ` ```rust ... ``` ` se renderiza como raw Tipst.
```

**Bien**:
```
El bloque de código Rust se renderiza como raw Tipst.
```

### 3. Tablas con columnas largas se cortan en el render

Tipst ajusta automáticamente el ancho de columnas y puede romper tablas con
muchas columnas o texto largo en celdas. Limitar a 3-4 columnas y preferir
listas o párrafos cuando la tabla tenga más de 5 columnas.

### 4. El header `>` produce blockquotes

Un `>` al inicio de línea en markdown genera un blockquote en Tipst. Si
necesitas un `>` literal (ej. en una firma de comando), escaparlo o usar
código inline.

### 5. Bullets y numeración

Tipst convierte `-` en bullet y `1.` en numeración automáticamente. Si
necesitas un guion literal en una línea de prosa, usar `\-` en código inline.

### 6. Estilo de tablas (definido en el header del conversor)

Las tablas se renderizan con:

- **Header**: fondo azul oscuro (`#1e3a8a`) con texto blanco en negrita.
- **Filas pares**: fondo gris claro (`#f1f5f9`).
- **Filas impares**: fondo blanco.
- **Bordes**: 1pt gris medio (`#94a3b8`).

Estos estilos son fijos y no requieren configuración en el MD. Si querés
distinguirlas aún más, usar tablas con pocas columnas y celdas cortas.
Tablas con más de 4 columnas o celdas muy largas pueden deformarse al
ajustarse al ancho A4.