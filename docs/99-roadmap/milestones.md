# Milestones

Este documento describe los hitos planificados para el desarrollo de la aplicación, organizados en fases que van desde el MVP hasta versiones posteriores.

Cada hito representa un estado del producto que puede ser probado y validado de forma independiente.

---

## Foundation — Prerequisites

### Milestone 0.1 — Account and Session

**Estado:** Planificado

**Objetivo:** Establecer autenticación y sesión persistente como base del producto.

**Alcance:**

- Registro de usuario con email y password
- Login con sesión persistente (cookie segura)
- Flujo de unlock para retomar sesión activa

**Referencias:**
- ADR-0009: User Authentication and Multi-User Data Isolation
- ADR-0010: Finalize Multi-User Authentication and Session Model

---

### Milestone 0.2 — Data Isolation

**Estado:** Planificado

**Objetivo:** Garantizar aislamiento de datos por usuario en toda operación de la API.

**Alcance:**

- Todas las entidades de dominio incluyen `user_id`
- Lectura y escritura filtradas por usuario autenticado
- Validación de ownership en operaciones de update/delete

**Referencias:**
- ADR-0009: User Authentication and Multi-User Data Isolation
- `docs/01-architecture/system-context.md`

---

## Phase 1 — Brainstorm Foundation

### Milestone 1.1 — Idea Entity

**Estado:** Planificado

**Objetivo:** Permitir capturar y organizar ideas de forma rápida y flexible.

**Alcance:**

- Modelo de datos de `Idea`
- Persistencia en base de datos y endpoints CRUD básicos
- Validaciones iniciales de contenido y timestamps
- Campos iniciales actualizados:
	- `id`
	- `bookId` (nullable)
	- `text` (opcional)
	- `imageUrl` (opcional)
	- `audioUrl` (opcional)
	- `gridX` y `gridY` (nullable, para posición en Book)
	- `status` (`active` | `archived`)
	- `convertedToTodo` (boolean)
	- `createdAt`
	- `updatedAt`

**Referencias:**
- ADR-0004: Brainstorm como módulo independiente
- ADR-0006: Idea as a Flexible and Multimodal Entity
- `docs/02-modules/brainstorm/validations.md`

---

### Milestone 1.2 — Book Organization

**Estado:** Planificado

**Objetivo:** Permitir separar y agrupar Ideas por contexto sin imponer estructura rígida.

**Alcance:**

- Entidad `Book` como contenedor visual de Ideas
- Relación `Book -> Ideas`
- Movimiento de Ideas entre Books y estado no agrupado (`bookId = null`)
- Books especiales del sistema (por ejemplo, configuración e ideas eliminadas)

**Referencias:**
- ADR-0011: Brainstorm Book–Idea Organization Model
- `docs/02-modules/brainstorm/business-rules.md`

---

### Milestone 1.3 — Idea Board

**Estado:** Planificado

**Objetivo:** Habilitar exploración visual simple de Ideas dentro de Brainstorm.

**Alcance:**

- Vista tipo grid para Ideas agrupadas
- Coordenadas `gridX` y `gridY` por Idea dentro de Book
- Restricción de unicidad de posición (`bookId`, `gridX`, `gridY`)
- Navegación simple entre Books

**Referencias:**
- ADR-0011: Brainstorm Book–Idea Organization Model
- `docs/02-modules/brainstorm/validations.md`

---

## Phase 2 — Todo System

### Milestone 2.1 — Project Entity

**Estado:** Planificado

**Objetivo:** Definir la entidad raíz del módulo Todo para organizar trabajo ejecutable.

**Alcance:**

- Modelo de datos de `Project`
- Endpoints CRUD básicos
- Persistencia y validaciones iniciales

**Referencias:**
- ADR-0007: Project Management Model in Todo List
- ADR-0013: Allow Dual Active Projects for Execution Continuity
- `docs/02-modules/todo/overview.md`

---

### Milestone 2.2 — Objective Entity

**Estado:** Planificado

**Objetivo:** Permitir descomponer proyectos en objetivos.

**Alcance:**

- Relación `Project -> Objective`
- Endpoints CRUD de objetivos
- Validaciones de pertenencia jerárquica

**Referencias:**
- ADR-0007: Project Management Model in Todo List
- ADR-0013: Allow Dual Active Projects for Execution Continuity

---

### Milestone 2.3 — Task Entity

**Estado:** Planificado

**Objetivo:** Definir la unidad mínima de trabajo ejecutable.

**Alcance:**

- Relación `Objective -> Task`
- Estados de tarea: `pending`, `in_progress`, `completed`
- Base para conversión explícita de Idea a flujo ejecutable en Todo

**Referencias:**
- ADR-0007: Project Management Model in Todo List
- ADR-0013: Allow Dual Active Projects for Execution Continuity

---

## Phase 3 — Execution System

### Milestone 3.1 — Project Activation

**Estado:** Planificado

**Objetivo:** Permitir mantener foco operativo sin frenar avance cuando exista un bloqueo externo.

**Alcance:**

- Activación/desactivación explícita de proyectos
- Hasta 2 proyectos activos simultáneamente
- Distinción entre proyecto principal y proyecto secundario (fallback por bloqueo externo)
- Si no existe bloqueo, se recomienda operar con un único proyecto activo

**Referencias:**
- ADR-0007: Project Management Model in Todo List

---

### Milestone 3.2 — Objective Activation

**Estado:** Planificado

**Objetivo:** Definir foco por objetivo dentro de cada proyecto activo.

**Alcance:**

- Selección de objetivo activo por proyecto activo
- Filtrado de tareas relevantes según objetivo activo

**Referencias:**
- ADR-0007: Project Management Model in Todo List

---

### Milestone 3.3 — Execution View

**Estado:** Planificado

**Objetivo:** Reducir carga cognitiva durante la ejecución diaria.

**Alcance:**

- Vista enfocada de ejecución
- Máximo de 1 a 3 tareas visibles simultáneamente
- Priorización de tareas activas

**Referencias:**
- ADR-0007: Project Management Model in Todo List

---

## Phase 4 — Planning and Time Tracking

### Milestone 4.1 — Time Estimation

**Estado:** Planificado

**Objetivo:** Permitir estimar tiempo requerido por tarea.

**Alcance:**

- Campo de estimación por tarea
- Visualización de estimaciones en Planning View

**Referencias:**
- ADR-0007: Project Management Model in Todo List

---

### Milestone 4.2 — Time Tracking

**Estado:** Planificado

**Objetivo:** Registrar tiempo real invertido por tarea.

**Alcance:**

- Registro de tiempo trabajado
- Persistencia de tiempo real por tarea

**Referencias:**
- ADR-0007: Project Management Model in Todo List

---

### Milestone 4.3 — Estimation vs Reality

**Estado:** Planificado

**Objetivo:** Comparar esfuerzo planificado con esfuerzo real para mejorar planificación.

**Alcance:**

- Cálculo de diferencia entre estimado y real
- Visualización básica de desvío

**Referencias:**
- ADR-0007: Project Management Model in Todo List

---

### Milestone 4.4 — Flexible Replanning

**Estado:** Planificado

**Objetivo:** Permitir replanificar sin penalizar al usuario.

**Alcance:**

- Reprogramación explícita de tareas
- Ajuste automático de fechas posteriores
- Registro de desvíos en historial

**Referencias:**
- ADR-0007: Project Management Model in Todo List

---

## Phase 5 — AI Chat Utility

### Milestone 5.1 — Chat Interface

**Estado:** Planificado

**Objetivo:** Proveer una interfaz de chat conversacional integrada en la aplicación.

**Alcance:**

- Lista de mensajes
- Campo de entrada de texto
- Envío de mensajes y render de respuestas

**Referencias:**
- ADR-0012: Introduce AI Chat Utility as Isolated Assistant

---

### Milestone 5.2 — AI Integration

**Estado:** Planificado

**Objetivo:** Integrar el proveedor de modelo de lenguaje para responder consultas generales.

**Alcance:**

- Endpoint de chat en backend
- Integración con API de modelo (`Gemini 1.5 Flash`)
- Manejo básico de errores de proveedor

**Referencias:**
- ADR-0012: Introduce AI Chat Utility as Isolated Assistant

---

### Milestone 5.3 — Conversation Handling

**Estado:** Planificado

**Objetivo:** Mantener manejo conversacional básico sin acoplarse al dominio del producto.

**Alcance:**

- Historial de conversación en sesión
- Contexto conversacional básico
- Restricciones de alcance:
	- sin acceso a ideas, proyectos ni tareas
	- sin automatización de planificación
	- sin creación automática de tareas

**Referencias:**
- ADR-0012: Introduce AI Chat Utility as Isolated Assistant
