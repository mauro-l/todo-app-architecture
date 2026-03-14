# System Context

Este documento define los límites del sistema y la distribución de responsabilidades entre sus capas para el MVP.

---

## High-Level Boundaries

- **Client:** React 18 PWA ejecutando en navegador o modo instalado.
- **API:** servicio Node.js + Express exponiendo endpoints REST.
- **Data:** PostgreSQL accedido mediante Drizzle ORM.

---

## Responsibility Split

**Client responsibilities:**

- Renderizar UI y flujos de usuario.
- Gestionar estado local de interacción.
- Invocar API backend para operaciones persistidas.
- Distinguir y renderizar Planning View vs Execution View según el módulo Todo.

**API responsibilities:**

- Validar requests y aplicar reglas de negocio.
- Gestionar ciclo de vida de sesiones de autenticación.
- Coordinar lecturas/escrituras con la capa de datos.
- Garantizar aislamiento de datos por usuario en cada operación (`user_id`).

**Data responsibilities:**

- Persistir entidades y relaciones del dominio.
- Asegurar integridad referencial (Project → Objective → Task).
- Asegurar performance de consultas mediante índices sobre `user_id` e `is_active`.

---

## Module Boundaries

### Brainstorm Module

- Captura de ideas en formato texto, imagen y audio.
- Organización mediante contenedores visuales (libros).
- No gestiona tareas ni proyectos.
- Puede iniciar el flujo de conversión hacia el módulo Todo.

**Entidades principales:** `Idea`, `Book`

### Todo Module

- Gestión jerárquica de trabajo ejecutable: Project → Objective → Task.
- Permite hasta dos proyectos activos simultáneamente (principal + secundario por continuidad).
- Mantiene un único objetivo activo por cada proyecto activo.
- Expone dos vistas: Planning View (global) y Execution View (enfocada, máx 1–3 tareas).
- Registra historial inmutable de cambios por tarea.

**Entidades principales:** `Project`, `Objective`, `Task`, `TaskChangeHistory`

### Relación entre módulos

- Brainstorm y Todo son módulos independientes.
- Una `Idea` puede convertirse en un `Project` mediante acción explícita del usuario.
- La conversión no elimina la idea original del Brainstorm.
- No existe dependencia de datos en sentido inverso (Todo no conoce la estructura interna de Brainstorm).

---

## Authentication Boundary

- El sistema utiliza autenticación propia basada en email y password con sesión persistente (cookie segura).
- Cada entidad del dominio está asociada a un `user_id`.
- El aislamiento de datos entre usuarios es responsabilidad de la capa API: todo acceso a datos debe validar que el recurso pertenece al usuario autenticado.

---

## MVP Constraints

- Sin arquitectura distribuida de microservicios.
- Sin soporte multi-tenant en esta fase (multi-user sí, multi-tenant no).
- Sin caché externo (Redis) ni CDN.
- Sin notificaciones push ni capacidades offline en el MVP inicial.

---

## Decision Traceability

- Stack tecnológico: `docs/05-adr/0008-technology-stack-selection-for-mvp.md`
- Modelo de autenticación: `docs/05-adr/0009-user-authentication-and-multi-user-data-isolation.md`
- Refinamiento final de autenticación: `docs/05-adr/0010-finalize-multi-user-authentication-and-session-model.md`
- Módulo Brainstorm: `docs/05-adr/0004-brainstorm-module.md`
- Módulo Todo: `docs/05-adr/0007-project-management-model-in-todo-list.md`
- Refinamiento de activación en ejecución: `docs/05-adr/0013-allow-dual-active-projects-for-execution-continuity.md`

