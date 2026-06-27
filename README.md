# doc-orchestrator

Skill Mavis que genera documentación técnica profesional en PDF a partir de código fuente. Funciona enteramente offline — el binario `mdtopdf-rs` incluye Typst y D2 embeídos.

## Qué hace

Recibe un directorio, detecta plugins `internal_workflows/*.md` que definen qué extrae del código (arq, endpoints, dependencias, reglas de negocio, etc.), y produce un PDF por plugin + un PDF consolidado.

## Estructura

```
doc-orchestrator/
├── SKILL.md                  ← definición del skill para Mavis
├── bin/
│   └── MdToPdf/
│       └── mdtopdf-rs.exe    ← 46 MB, Typst 0.15 + D2 0.7.1 embebidos
└── internal_workflows/        ← 14 plugins de extracción
    ├── arqueologo.md
    ├── puntos_entrada.md
    ├── dependencias.md
    └── ...
```

## Instalación

```powershell
# Copiar todo a ~/.mavis/skills/
Copy-Item -Recurse doc-orchestrator C:\Users\<tu-user>\.mavis\skills\
```

Requiere Windows x64. No necesita permisos de admin.

## Uso en Mavis

```
/skill doc-orchestrator
> Analizá el proyecto D:\proyectos\mi-app y generá la documentación
```

## Dependencias del sistema

- Windows x64
- Sin runtime adicional — el exe es self-contained
- ~100 MB de espacio libre para PDFs generados

## Licencia

MIT — Sebastián Rozas, 2026
