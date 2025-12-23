# ADR-002 – Application Designed as Single-User

## Context

El proyecto Todo App Architecture se concibe como una aplicación personal,
orientada al uso individual, similar a una app bancaria o de notas privadas.

Desde el inicio del diseño se definió un flujo de autenticación simple, sin
gestión de usuarios múltiples ni credenciales tradicionales.

Durante el diseño del módulo Brainstorm surgió la necesidad de aclarar el
modelo de acceso y propiedad del contenido.

## Decision

Diseñar la aplicación como una experiencia estrictamente single-user.

## Rationale

- El objetivo principal es uso personal, no colaboración.
- Simplifica el modelo mental del usuario.
- Reduce complejidad innecesaria en el MVP.
- Permite sesiones persistentes y desbloqueo rápido (PIN/biometría).
- Evita modelar permisos, roles o ownership múltiple.

## Implications

- No existe concepto de usuarios múltiples.
- Todo el contenido pertenece al dueño de la app.
- No se implementan permisos ni compartición.
- La arquitectura puede asumir un único contexto de usuario.
- Una futura versión multi-user requeriría cambios explícitos.
