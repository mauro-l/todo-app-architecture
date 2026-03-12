# Performance

## Goal

Definir los criterios mínimos de performance para el MVP, enfocados en garantizar una experiencia de uso fluida sin introducir optimizaciones prematuras.

El producto inicial está orientado a un volumen de datos personal y reducido. Las decisiones de performance deben ser proporcionadas a ese contexto.

---

## Scope

Aplica a:

- Frontend (React 18 PWA)
- Backend (Node.js + Express API REST)
- Base de datos (PostgreSQL + Drizzle ORM)

---

## Frontend

### Carga inicial

- La aplicación debe ser usable en menos de 3 segundos en una conexión estándar.
- El bundle inicial debe minimizarse mediante code splitting por módulo (Brainstorm / Todo).
- Los recursos estáticos deben servirse con caché apropiado (PWA service worker).

### Execution View

La Execution View es la vista de mayor frecuencia de uso y debe ser la más responsiva del sistema.

- Debe mostrar únicamente el proyecto activo, el objetivo activo y máximo 1–3 tareas.
- No debe cargar la totalidad de proyectos, objetivos ni tareas del usuario al renderizar.
- Las consultas deben ser específicas y acotadas al contexto activo.

### Planning View

- La carga de la Planning View puede ser diferida (lazy load) ya que su uso es menos frecuente.
- No es necesario que esté disponible instantáneamente al iniciar la sesión.

---

## Backend

### Tiempo de respuesta

- Las operaciones CRUD estándar (crear, leer, actualizar entidades) deben responder en menos de 300ms en condiciones normales de carga.
- Las consultas de la Execution View (proyecto activo + objetivo activo + tareas visibles) deben ser consultas directas y índice-friendly.

### Consultas

- Las entidades principales (`Project`, `Objective`, `Task`) deben contar con índices sobre `user_id` y `is_active` para evitar full table scans.
- El historial de cambios (`change_history`) de una tarea no debe incluirse en las consultas de listado general; debe cargarse solo cuando se acceda explícitamente al detalle de una tarea.

---

## Base de Datos

- El volumen esperado **por usuario** es bajo (orden de decenas de proyectos, cientos de tareas).
- El volumen agregado depende del número de usuarios registrados; los índices sobre `user_id` son la principal estrategia para mantener performance de consultas a medida que crece la base de usuarios.
- No se requieren estrategias de particionado, réplicas ni caché externo (Redis) en el MVP.
- Las migraciones deben mantenerse explícitas y versionadas mediante Drizzle ORM.

---

## Out of Scope

Las siguientes optimizaciones quedan fuera del alcance del MVP:

- Caché de consultas (Redis, memcached)
- CDN para assets
- Paginación server-side en listas (el volumen personal no lo requiere en esta fase)
- Monitoreo de performance en producción (APM)
- Tests de carga o benchmarks formales

---

## Evolution Rule

Si el sistema comienza a servir múltiples usuarios activos simultáneos o el volumen de datos por usuario crece significativamente, esta estrategia debe revisarse e incorporar indexado avanzado, paginación server-side y eventualmente caché de consultas.
