# Architecture Overview

Este documento describe el estado actual de la arquitectura para el MVP.

## Current Stack (At a Glance)

| Area | Technology | Scope in MVP |
| --- | --- | --- |
| Frontend | React 18 + PWA | UI, navegacion y aplicacion web instalable |
| Backend | Node.js + Express + TypeScript | API REST y reglas de aplicacion |
| Database | PostgreSQL | Almacenamiento persistente de datos |
| ORM | Drizzle ORM | Esquema SQL, consultas y migraciones |
| Authentication | Multi-user email/password + secure session cookie | Registro, login persistente y aislamiento de datos por usuario |

## Decision Source

- Registro principal de decision: `docs/05-adr/0008-technology-stack-selection-for-mvp.md`

## Related Architecture Docs

- `docs/01-architecture/principles.md`
- `docs/01-architecture/technology-rationale.md`
- `docs/01-architecture/system-context.md`

## Last Reviewed

- 2026-03-12
