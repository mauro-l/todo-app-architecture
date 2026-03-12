# Milestones

Este documento describe los hitos planificados para el desarrollo de la aplicación, organizados en fases que van desde el MVP hasta versiones posteriores.

Cada hito representa un estado del producto que puede ser probado y validado de forma independiente.

---

## M1 – Autenticación y Setup Inicial

**Estado:** Planificado

**Objetivo:** Establecer la base del sistema con soporte multi-usuario y sesiones persistentes.

**Alcance:**

- Registro de usuario con email y password
- Login con sesión persistente (cookie segura)
- Aislamiento de datos por usuario (`user_id` en todas las entidades)
- Flujo de unlock para retomar sesión activa

**Referencias:**
- ADR-0009: User Authentication and Multi-User Data Isolation

---

## M2 – Módulo Brainstorm

**Estado:** Planificado

**Objetivo:** Permitir la captura rápida de ideas sin estructura ni presión.

**Alcance:**

- Creación de ideas en formato texto, imagen y audio
- Organización de ideas en contenedores visuales (libros)
- Navegación gestual entre módulos desde la Home
- Visualización de ideas en grilla
- Contenedor especial para ideas eliminadas (papelera visual)
- Contenedor especial para configuración

**Referencias:**
- ADR-0004: Brainstorm como módulo independiente
- ADR-0005: Navegación gestual y organización por contenedores visuales
- ADR-0006: Idea as a Flexible and Multimodal Entity

---

## M3 – Módulo Todo: Jerarquía y Planificación

**Estado:** Planificado

**Objetivo:** Permitir estructurar ideas en proyectos ejecutables con objetivos y tareas.

**Alcance:**

- Creación y gestión de Projects, Objectives y Tasks
- Estimaciones de tiempo y fechas por tarea
- Estados: `pending`, `in_progress`, `completed`
- Planning View: visión global completa de todos los proyectos
- Activación de proyecto y objetivo (uno activo por vez)
- Historial de cambios por tarea (change history inmutable)

**Referencias:**
- ADR-0007: Project Management Model in Todo List

---

## M4 – Execution View y Replanificación

**Estado:** Planificado

**Objetivo:** Implementar la vista de ejecución enfocada y el modelo de replanificación flexible.

**Alcance:**

- Execution View: 1 proyecto activo + 1 objetivo activo + máx 1–3 tareas visibles
- Reprogramación de tareas sin penalización
- Ajuste automático de fechas posteriores al reprogramar
- Registro de desvíos en el historial de cambios

**Referencias:**
- ADR-0007: Project Management Model in Todo List

---

## M5 – Integración Brainstorm → Todo

**Estado:** Planificado

**Objetivo:** Permitir que una idea del módulo Brainstorm se convierta en un proyecto del módulo Todo.

**Alcance:**

- Conversión de idea a proyecto (flujo explícito del usuario)
- Conservación de la referencia a la idea original
- La idea original no se elimina del Brainstorm
- El contenido de la idea puede reutilizarse como descripción del proyecto

**Referencias:**
- ADR-0004: Brainstorm como módulo independiente
- ADR-0007: Project Management Model in Todo List

---

## M6 – Estabilización y Feedback

**Estado:** Planificado

**Objetivo:** Validar el producto con usuarios reales y estabilizar la experiencia.

**Alcance:**

- Corrección de bugs y ajustes de UX
- Soporte básico PWA: instalación como aplicación en dispositivos
- Revisión de flujos completos (captura → planificación → ejecución)
- Recolección de feedback para definir iteraciones futuras

**Referencias:**
- ADR-0008: Technology Stack Selection for MVP
