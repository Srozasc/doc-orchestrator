---
name: arqueologo
keywords:
    - arqueologo
    - arquitectura
    - stack
    - tecnologia
    - estructura
    - modulos
    - ingenieria inversa
    - analisis
outputs:
    - docs/AUTODOC_ARCHITECTURE.md
dependencies: []
---

# Proceso de Arqueología de Arquitectura

Este proceso está diseñado para realizar una ingeniería inversa rápida de un proyecto y generar documentación técnica de alto nivel.

### 1. Exploración Inicial
- Escanea la raíz del proyecto para identificar la estructura general.
- Busca archivos de manifiesto: `package.json`, `go.mod`, `pom.xml`, `requirements.txt`, etc.
- Busca archivos de configuración: `tsconfig.json`, `next.config.ts`, `tailwind.config.ts`, `.env.example`.

### 2. Análisis del Stack Tecnológico
- Lee el archivo de manifiesto principal identificado.
- Extrae y resume:
    - **Lenguaje y Versión**: (ej. TypeScript 5, Python 3.12).
    - **Framework Core**: (ej. Next.js, Express, Electron, React).
    - **Librerías Críticas**: (ej. Prisma, D2, Tailwind).
    - **Scripts de Ejecución**: Identifica cómo se levanta y se testea la app.

### 3. Mapeo de la Anatomía del Proyecto
- Inspecciona las carpetas de `src` o raíz (hasta nivel 2 de profundidad).
- Deduce el patrón arquitectónico (ej. Limpia, Hexagonal, MVC o Cliente-Servidor).
- Identifica los "Entry Points" (ej. `main.ts`, `App.tsx`, `index.js`).

### 4. Generación de Documentación
- Crea o actualiza el archivo `docs/AUTODOC_ARCHITECTURE.md`.
- El documento debe incluir:
    - **Tech Stack Overview**: Tabla con tecnologías clave.
    - **Architecture Diagram (D2)**: Un diagrama de bloques o grafo que visualice la relación entre componentes.
    - **Project Structure**: Árbol de directorios anotado (bloque de código `text`).
    - **Quick Start**: Basado en los scripts encontrados.


### Ejemplo D2
```d2
direction: right
Frontend -> Backend: HTTP/JSON
Backend -> Database: queries

Frontend.shape: rectangle
Backend.shape: rectangle
Database.shape: cylinder
```

### Instrucciones de Estilo (No incluir en el documento)
- **Profesionalismo**: Sin emojis innecesarios en el documento final.
- **Contraste en D2**: Define siempre el color de la fuente (`color:#...`) en los estilos (`style`).
