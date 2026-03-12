# Technology Rationale

Este documento resume por que se selecciono cada tecnologia del MVP.

Fuente principal: `docs/05-adr/0008-technology-stack-selection-for-mvp.md`

## Frontend: React 18 + PWA

Motivo:

- Iteracion rapida de UI y ecosistema maduro.
- Experiencia instalable en desktop y mobile.
- Camino futuro para capacidades offline y APIs de dispositivo seleccionadas.

Tradeoffs:

- La UX de PWA puede ser menos fluida que una app nativa en algunos escenarios.
- Las capacidades offline y la integracion con plataforma requieren implementacion cuidadosa.

## Backend: Node.js + Express + TypeScript

Motivo:

- Setup simple de API REST.
- Velocidad alta de implementacion para CRUD del MVP.
- Lenguaje de modelos TypeScript compartido entre frontend y backend.

Tradeoffs:

- Si la complejidad crece de forma significativa, puede requerirse estructura adicional.
- Las convenciones de seguridad y arquitectura dependen de disciplina de implementacion.

## Database: PostgreSQL

Motivo:

- Modelo relacional robusto y ecosistema maduro.
- Buen encaje para tareas, brainstorms y relaciones futuras de proyectos.

Tradeoffs:

- Requiere disciplina de migraciones y de esquema desde el inicio.

## ORM: Drizzle ORM

Motivo:

- Experiencia orientada a TypeScript.
- Control claro de SQL con baja sobrecarga de abstraccion.
- Migraciones directas y entendibles.

Tradeoffs:

- Exige decisiones SQL mas explicitas que ORMs con mayor abstraccion.

## Authentication: Custom Single-User Session

Motivo:

- Encaja con el alcance del MVP: app personal para un unico usuario.
- Complejidad minima de auth para la entrega inicial.

Tradeoffs:

- La responsabilidad de seguridad queda dentro de la aplicacion.
- Una evolucion a multi-user o identidad externa puede requerir rediseno.
