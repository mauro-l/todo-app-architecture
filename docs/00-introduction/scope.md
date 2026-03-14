# Scope

## Purpose

El scope define los límites funcionales del producto: qué problemas busca resolver la aplicación y qué funcionalidades forman parte de su alcance.

También establece qué aspectos **no forman parte del producto**, evitando expansión innecesaria del sistema (scope creep).

---

## In Scope

Las siguientes capacidades forman parte del núcleo del producto.

### Idea Capture (Brainstorm)

Un espacio libre para registrar ideas sin estructura previa.

Incluye:

- captura rápida de ideas
- notas simples
- almacenamiento de referencias o conceptos
- posibilidad de evolucionar una idea hacia un proyecto
- agrupación opcional de ideas mediante Books
- organización visual de ideas dentro de Books

Objetivo:
Permitir capturar pensamiento sin fricción.

---

### Personal Project Management (Todo List)

Sistema estructurado para transformar ideas en acciones.

Basado en el modelo jerárquico:

Project → Objective → Task

Incluye:

- creación de proyectos
- división de proyectos en objetivos
- división de objetivos en tareas
- estados de tarea (pending / in progress / completed)

---

### Execution-Focused Task System

El sistema prioriza la ejecución reduciendo la carga cognitiva.

Incluye:

- activación de proyecto
- activación de objetivo
- vista de ejecución con foco limitado
- máximo de 1–3 tareas visibles simultáneamente

Objetivo:
Facilitar avanzar sin generar bloqueo.

---

### Time Estimation and Tracking

Permite mejorar la planificación personal.

Incluye:

- estimación de tiempo por tarea
- registro de tiempo real
- comparación entre estimado y real

---

### Flexible Replanning

La planificación es adaptativa y no punitiva.

Incluye:

- reprogramación de tareas
- ajuste automático de fechas posteriores
- registro de desvíos

Objetivo:
Acompañar el proceso real de trabajo del usuario.

---

### AI Chat Utility (auxiliary)

El producto incluye un chat conversacional auxiliar como herramienta independiente.

Incluye:

- consultas generales de apoyo cotidiano
- exploración rápida de información
- asistencia informal no vinculada al sistema de productividad

Restricciones:

- no accede a datos internos del usuario (ideas, proyectos o tareas)
- no genera tareas de forma automática
- no planifica ni modifica el trabajo del usuario

Objetivo:

Experimentar integración de modelos de lenguaje sin afectar el núcleo del producto.

---

### History and Progress Tracking

Permite analizar el progreso a lo largo del tiempo.

Incluye:

- historial de cambios de tareas
- registro de estimaciones y tiempos reales
- seguimiento del avance de proyectos

---

## Out of Scope

Las siguientes capacidades **no forman parte del producto en esta etapa**.

### Multi-user collaboration

- trabajo colaborativo
- gestión de equipos
- permisos entre usuarios

La aplicación está diseñada como herramienta **personal**.

---

### Real-time synchronization

- edición simultánea
- sincronización en tiempo real entre usuarios

---

### External integrations

- integraciones con servicios externos
- automatizaciones con otras aplicaciones

---

### AI-driven automation (initial phase)

Si bien existe un chat auxiliar independiente, funcionalidades como:

- generación automática de tareas
- planificación automática
- recomendaciones basadas en patrones

no forman parte del alcance inicial del producto.

---

## Guiding Principle

El producto se enfoca en **organización personal y ejecución clara**, evitando complejidad innecesaria.

La prioridad es construir un sistema simple, flexible y sostenible que acompañe el proceso real de pensamiento y trabajo del usuario.