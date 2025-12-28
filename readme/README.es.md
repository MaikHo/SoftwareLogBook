# SoftwareLogBook

## Idiomas
- Inglés (predeterminado)
- [Deutsch](README.de.md)
- [Español](README.es.md)
- [Français](README.fr.md)
- [日本語](README.ja.md)

SoftwareLogBook es un registro para sistemas de software que usa archivos Markdown con frontmatter YAML.

## Motivación y alcance
SoftwareLogBook documenta herramientas de software, sus despliegues y eventos del ciclo de vida en un formato que se puede leer y revisar sin herramientas especiales.

Por qué archivos + Markdown + Git:
- El texto plano es fácil de leer, comparar y revisar.
- Git aporta historial, trazabilidad y disciplina de append-only.
- La estructura sigue siendo utilizable en entornos con pocas herramientas.

Escenarios previstos:
- Inventarios pequeños o medianos de herramientas internas o de terceros.
- Equipos que quieren un único lugar auditable para lanzamientos, incidentes y notas de mantenimiento.
- Entornos donde basta un registro ligero basado en repositorio.

Lo que no es:
- No es una CMDB.
- No es un sistema de tickets.
- No es un sistema de monitorización.

## Conceptos centrales (alto nivel)
- Software: un registro que describe una herramienta y su contexto de responsabilidad.
- Deployment: una instancia instalada de una herramienta de software en un entorno.
- Entry: un registro de eventos append-only (p. ej., lanzamiento, incidente, mantenimiento).
- Global entry: un evento o política que aplica a todas las herramientas.
- Corrections: un registro dedicado que hace referencia al registro corregido.

## Estructura del repositorio
- `software/<softwareKey>/`: carpeta por herramienta.
- `software/<softwareKey>/software.md`: registro de software.
- `software/<softwareKey>/deployments/`: registros de despliegue.
- `software/<softwareKey>/entries/<YYYY>/`: registros del log por herramienta y año.
- `_global/entries/<YYYY>/`: registros globales del log por año.
- `taxonomy/`: enumeraciones compartidas y tipos de referencia.
- `templates/`: plantillas iniciales para nuevos registros.

## Flujo de trabajo mínimo
1. Crea un nuevo registro de software usando `../templates/software.template.md`.
2. Añade registros de despliegue usando `../templates/deployment.template.md`.
3. Añade entries usando `../templates/entry.template.md` (lanzamiento, incidente, mantenimiento).
4. Si algo necesita corrección, añade un nuevo entry con `type: correction` que haga referencia al entry original.

## Lecturas adicionales
- `../SPEC.md`: fuente de verdad para estructura y reglas.
- `../CONTRIBUTING.md`: guía sobre nombres, unicidad y append-only.
- `../GUARDRAILS.md`: comprobaciones recomendadas y guía de higiene.

## Viewer y tooling (opcional)
El repositorio es totalmente utilizable sin herramientas. Se pueden construir viewers o CLI, pero no forman parte del estándar.

## Licencia
MIT (ver `../LICENSE`)

## Translation note
This text was translated by ChatGPT.
