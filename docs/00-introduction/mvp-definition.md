# MVP Definition

## Purpose

Este documento define de forma explícita qué alcance representa el MVP del producto.

Su objetivo es evitar ambigüedad entre roadmap, milestones y alcance funcional.

Nota: `scope.md` define alcance total de producto; este documento define el corte operativo del MVP.

---

## MVP

El MVP del producto abarca los milestones desde **0.1 hasta 4.3**.

Incluye:

- Foundation — Prerequisites
  - Milestone 0.1 — Account and Session
  - Milestone 0.2 — Data Isolation
- Phase 1 — Brainstorm Foundation
  - Milestone 1.1 — Idea Entity
  - Milestone 1.2 — Book Organization
  - Milestone 1.3 — Idea Board
- Phase 2 — Todo System
  - Milestone 2.1 — Project Entity
  - Milestone 2.2 — Objective Entity
  - Milestone 2.3 — Task Entity
- Phase 3 — Execution System
  - Milestone 3.1 — Project Activation
  - Milestone 3.2 — Objective Activation
  - Milestone 3.3 — Execution View
- Phase 4 — AI Chat Utility
  - Milestone 4.1 — Chat Interface
  - Milestone 4.2 — AI Integration
  - Milestone 4.3 — Conversation Handling

Resultado esperado del MVP:

- Captura de ideas en Brainstorm
- Conversión de ideas en estructura ejecutable en Todo
- Ejecución enfocada diaria con límite de tareas visibles
- Autenticación multi-user con aislamiento de datos por usuario
- Utilidad de chat conversacional integrada como asistente auxiliar

---

## Out of MVP

Las siguientes capacidades quedan fuera del MVP actual:

- Planning and Time Tracking [Deferred / Future Ideas]

Planning and Time Tracking queda fuera del plan activo y se documenta en `docs/99-roadmap/future-ideas.md`.

---

## Source of Truth

Para detalle operativo de cada hito, la fuente principal es:

- `docs/99-roadmap/milestones.md`

Para límites funcionales generales del producto:

- `docs/00-introduction/scope.md`

---

## MVP Done Checklist

Usar esta checklist como criterio de cierre del MVP.

### Foundation (0.1–0.2)

- [ ] Registro de usuario funcionando con email y password
- [ ] Login con sesión persistente en cookie segura
- [ ] Flujo de unlock/retoma de sesión activa implementado
- [ ] Todas las operaciones de Brainstorm y Todo validan `user_id`
- [ ] No es posible acceder ni modificar recursos de otro usuario

### Phase 1 — Brainstorm (1.1–1.3)

- [ ] CRUD básico de `Idea` implementado
- [ ] Validación de contenido: una Idea requiere al menos texto, imagen o audio
- [ ] Entidad `Book` implementada y asociable a Ideas
- [ ] Una Idea puede estar agrupada (`bookId`) o no agrupada (`bookId = null`)
- [ ] Vista de board/grid de Ideas disponible
- [ ] Restricción de posición en grid aplicada por (`bookId`, `gridX`, `gridY`)

### Phase 2 — Todo System (2.1–2.3)

- [ ] CRUD de `Project` implementado
- [ ] CRUD de `Objective` implementado con pertenencia a `Project`
- [ ] CRUD de `Task` implementado con pertenencia a `Objective`
- [ ] Estados de Task soportados: `pending`, `in_progress`, `completed`
- [ ] Conversión explícita de Idea a flujo ejecutable en Todo disponible

### Phase 3 — Execution System (3.1–3.3)

- [ ] Activación de proyectos implementada con máximo 2 activos simultáneos
- [ ] Distinción operativa entre proyecto principal y secundario disponible
- [ ] Activación de objetivo implementada (1 objetivo activo por proyecto activo)
- [ ] Execution View implementada con foco operativo
- [ ] Execution View muestra máximo 1–3 tareas visibles simultáneamente

### Phase 4 — AI Chat Utility (4.1–4.3)

- [ ] Interfaz de chat implementada (lista de mensajes, input y envío)
- [ ] Endpoint de chat backend implementado e integrado con el modelo
- [ ] Historial/contexto conversacional básico en sesión
- [ ] Restricciones de aislamiento respetadas (sin acceso a ideas/proyectos/tareas)

### Quality Gate (MVP)

- [ ] No hay contradicciones entre `mvp-definition.md`, `milestones.md` y `scope.md`
- [ ] Flujos principales de uso (captura → estructuración → ejecución) se pueden recorrer de punta a punta
- [ ] Documentación de decisiones (ADR) referenciada está actualizada y consistente
