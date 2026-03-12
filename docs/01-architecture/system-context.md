# System Context

Este documento define los limites de ejecucion para la arquitectura del MVP.

## High-Level Boundaries

- Client: React 18 PWA ejecutando en navegador o modo instalado.
- API: servicio Node.js + Express exponiendo endpoints REST.
- Data: PostgreSQL accedido mediante Drizzle ORM.

## Responsibility Split

Client responsibilities:

- Renderizar UI y flujos de usuario.
- Gestionar estado local de interaccion.
- Invocar API backend para operaciones persistidas.

API responsibilities:

- Validar requests y aplicar reglas de negocio.
- Gestionar ciclo de vida de sesiones de autenticacion.
- Coordinar lecturas/escrituras con la capa de datos.

Data responsibilities:

- Persistir entidades y relaciones del dominio.
- Asegurar integridad de datos y performance de consultas.

## MVP Constraints

- Modelo de producto single-user.
- Flujo de autenticacion custom simple.
- Sin arquitectura distribuida de microservicios.
- Sin soporte multi-tenant en esta fase.

## Decision Traceability

- Decision de stack: `docs/05-adr/0008-technology-stack-selection-for-mvp.md`
