# ADR-0010: Finalize Multi-User Authentication and Session Model

## Status
Accepted

## Context
La direccion del producto confirmo de forma definitiva el modelo de login para el MVP.

Aunque ADR-0009 ya establecia autenticacion con email y password para multiples usuarios, todavia quedaban inconsistencias en documentos de arquitectura y faltaba especificar con precision operacional el flujo de sesion persistente para implementacion.

Ademas, se definio explicitamente que autenticacion no se modelara como un modulo de dominio independiente dentro de `02-modules`, sino como una capacidad transversal de la plataforma.

## Decision
Se oficializa para el MVP el siguiente modelo de autenticacion:

- Registro e inicio de sesion con `email + password`.
- Sesion persistente basada en cookie segura HTTP-only.
- Contexto de usuario obligatorio en backend para toda operacion sobre datos.
- Aislamiento estricto por `user_id` en lectura y escritura.

Tambien se establece que:

- **Auth no se documenta como modulo de dominio** en `02-modules`.
- La documentacion de autenticacion se mantiene en:
  - arquitectura (`01-architecture`),
  - flujos (`03-flows`),
  - no funcionales de seguridad (`04-non-functional`),
  - y trazabilidad de decisiones (`05-adr`).

## Consequences

### Positive
- Elimina ambiguedades entre enfoque single-user y multi-user.
- Define un contrato claro para frontend, API y base de datos.
- Reduce riesgo de implementaciones inconsistentes de seguridad.
- Mantiene `02-modules` enfocado en dominio de negocio.

### Negative
- Requiere disciplina estricta en validaciones de ownership por request.
- Incrementa el alcance de pruebas de seguridad y sesiones desde etapas tempranas.

## Alternatives Considered
- Modelar Auth como modulo en `02-modules` – No elegido porque para el MVP se trata de una capacidad transversal, no de un bounded context de dominio.
- Mantener enfoque single-user con unlock local – No elegido porque limita pruebas con usuarios reales y contradice el objetivo actual de feedback multi-usuario.
