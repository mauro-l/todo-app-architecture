# ADR-0000: Define Documentation Language Convention

## Status
Accepted

## Context

Durante la evolución del proyecto se detectó la necesidad de mantener coherencia en el idioma utilizado dentro de la documentación.

El proyecto sigue convenciones técnicas internacionales (nombres de carpetas, archivos y estructuras), pero el desarrollador principal prefiere leer y redactar explicaciones en español para mayor claridad y comprensión.

Se evaluaron las siguientes opciones:

1. Documentación completamente en inglés.
2. Documentación completamente en español.
3. Estructura técnica en inglés y contenido explicativo en español.

Era necesario definir una regla clara para evitar inconsistencias futuras.

## Decision

Se define la siguiente convención oficial de idioma para todo el proyecto:

- Nombres de carpetas → Inglés
- Nombres de archivos → Inglés
- Títulos principales (H1) → Inglés
- Títulos de secciones (H2, H3) → Inglés
- Valores técnicos (Status, keywords, etc.) → Inglés
- Contenido explicativo → Español

Esta convención aplica a:
- ADR
- Documentación de arquitectura
- Documentación técnica futura

## Consequences

### Positive

- Se mantiene alineación con estándares internacionales.
- La estructura del proyecto resulta profesional y consistente.
- El contenido sigue siendo fácil de leer y comprender para el desarrollador.
- Se evita ambigüedad futura en nuevas documentaciones.

### Negative

- Puede generar mezcla visual de idiomas.
- Requiere disciplina para mantener la convención.

## Alternatives Considered

- Documentación completamente en inglés  
  Rechazada porque reduce claridad personal en etapas de diseño y análisis.

- Documentación completamente en español  
  Rechazada porque se aleja de convenciones técnicas internacionales.