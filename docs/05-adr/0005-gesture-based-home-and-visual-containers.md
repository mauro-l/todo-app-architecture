# ADR-0005 – Navegación gestual y organización por contenedores visuales

## Context
El proyecto Todo App Architecture evoluciona hacia una aplicación personal centrada
en la organización de ideas, notas y tareas, con un fuerte énfasis en la experiencia
mental y cognitiva del usuario.

Durante el diseño de la Home, se identificó que una pantalla tradicional basada en
menús, listas o dashboards genera fricción y no representa el estado mental real
del usuario al ingresar a la aplicación.

Además, el proyecto ya cuenta con módulos conceptualmente distintos (Brainstorm,
Todo, futuras herramientas), lo que requiere una forma de navegación simple,
intuitiva y no invasiva.

## Decision
Diseñar la Home como un espacio central basado en gestos, donde:

- Las ideas se representan en una grilla visual.
- La navegación entre módulos se realiza mediante gestos direccionales.
- La organización de ideas se realiza mediante contenedores visuales (“libros”).
- La configuración y las ideas eliminadas se representan como libros especiales,
  manteniendo la misma metáfora visual.

## Rationale
- La Home funciona como un espacio de orientación y observación, no de ejecución.
- La navegación por gestos reduce la carga cognitiva y elimina la necesidad de menús
  tradicionales.
- La organización mediante “libros” permite clasificar ideas de forma visual y
  gestual, sin recurrir a formularios, etiquetas o estados complejos.
- Representar la configuración como un libro mantiene la coherencia conceptual del
  sistema.
- Tratar las ideas eliminadas como un contenedor visual evita borrados definitivos y
  favorece un enfoque más flexible y creativo.
- Refuerza la filosofía del proyecto: primero observar, luego decidir, y finalmente
  ejecutar.

## Implications
- La Home no mostrará listas de tareas ni acciones directas de ejecución.
- La navegación principal dependerá de gestos y animaciones claras.
- Será necesario diseñar interacciones de drag & drop para la organización de ideas.
- Los módulos (Brainstorm, Todo, etc.) deberán responder a una navegación direccional
  consistente.
- La arquitectura de datos deberá contemplar la relación entre ideas y contenedores
  visuales (libros).
- La configuración deja de ser un menú técnico y pasa a ser parte del sistema
  conceptual de la aplicación.
