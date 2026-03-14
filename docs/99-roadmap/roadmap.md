# Product Roadmap

## Purpose

El roadmap define la evolución planificada del producto a lo largo del tiempo.

Organiza el desarrollo en fases incrementales donde cada etapa agrega capacidades funcionales al sistema sin comprometer la simplicidad del producto.

El objetivo es construir primero los fundamentos del sistema y luego incorporar progresivamente herramientas que mejoren la organización y ejecución personal.

---

# Phase 1 — Brainstorm Foundation

Construcción del módulo Brainstorm como espacio de captura de ideas.

Incluye:

- creación de Ideas
- edición de Ideas
- archivado de Ideas
- soporte de contenido (texto, imagen, audio)
- creación de Books
- agrupación de Ideas dentro de Books
- organización visual de Ideas dentro de Books mediante grid

Objetivo:

Permitir capturar y organizar ideas de forma rápida y flexible.

---

# Phase 2 — Todo System

Implementación del sistema estructurado de gestión de proyectos personales.

Modelo jerárquico:

Project → Objective → Task

Incluye:

- creación de proyectos
- creación de objetivos
- creación de tareas
- estados de tarea
- conversión de Idea → Task

Objetivo:

Transformar ideas en acciones concretas.

---

# Phase 3 — Execution System

Construcción del sistema enfocado en ejecución.

Incluye:

- activación de proyectos
- activación de objetivos
- vista de ejecución
- limitación de tareas visibles
- priorización de tareas activas

Objetivo:

Reducir la carga cognitiva y facilitar avanzar en el trabajo diario.

---

# Phase 4 — AI Chat Utility

Incorporación de un chatbot conversacional integrado dentro de la aplicación.

Este chatbot funciona como herramienta auxiliar, similar a tener acceso directo a un asistente conversacional dentro del sistema.

El chatbot no forma parte del sistema de productividad ni interactúa con las entidades del producto.

Incluye:

- chat conversacional de propósito general dentro de la aplicación
- consultas rápidas de apoyo personal (información, dudas cotidianas, opiniones y mini-investigaciones)
- uso de `Gemini 1.5 Flash` por baja latencia y costo operativo bajo

Limitaciones:

- no tiene acceso a datos del usuario
- no accede a ideas, proyectos ni tareas
- no genera tareas automáticamente
- no interactúa con el sistema de productividad
- no realiza planificación del usuario

Es un chat independiente dentro de la aplicación.

Objetivo:

- familiarizarse con integración de modelos de IA en productos
- experimentar con APIs de modelos de lenguaje
- explorar posibilidades futuras sin afectar el núcleo del sistema

Esta fase funciona como primer punto de contacto entre el producto y las tecnologías de IA.

---

# Guiding Principle

El desarrollo del producto prioriza:

- simplicidad
- claridad
- bajo nivel de fricción
- foco en ejecución real

Las herramientas adicionales, como el chatbot, se incorporan sin interferir con el núcleo del producto, manteniendo la simplicidad y claridad del sistema.

Cada fase debe entregar valor funcional sin introducir complejidad innecesaria.