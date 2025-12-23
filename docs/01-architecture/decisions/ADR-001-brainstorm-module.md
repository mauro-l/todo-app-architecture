# ADR-001 – Brainstorm como módulo independiente

## Context
El proyecto Todo App Architecture busca ser una aplicación personal para organizar
ideas, notas y tareas. Durante la etapa inicial de diseño, se identificó que el
flujo de pensamiento (ideas, notas rápidas, borradores de proyectos) es distinto
al flujo de ejecución de tareas.

Actualmente, el foco del proyecto está puesto en el módulo Brainstorm, mientras
que el módulo Todo aún no está completamente definido.

## Decision
Definir Brainstorm como un módulo independiente, separado del módulo Todo.

## Rationale
- Brainstorm representa una etapa previa a la acción (pensar, capturar ideas).
- Separarlo reduce la complejidad inicial del sistema.
- Permite diseñar Brainstorm sin verse limitado por reglas típicas de un sistema de tareas.
- Facilita que el módulo Todo pueda definirse más adelante con mayor claridad.
- Refuerza la filosofía del proyecto: pensar antes de ejecutar.

## Implications
- Brainstorm tendrá vistas, flujos y lógica propios.
- El módulo Todo no es obligatorio para el funcionamiento inicial de la aplicación.
- A futuro, ambos módulos podrán integrarse, pero no dependerán entre sí.
- La arquitectura deberá contemplar modularidad desde el inicio.
