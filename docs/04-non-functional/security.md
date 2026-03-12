# Security

Este documento define requerimientos de seguridad para el MVP con autenticacion multi-usuario.

## Authentication Controls

- Passwords almacenados con hash robusto y sal unica por usuario.
- Cookie de sesion con flags `HttpOnly`, `Secure` y `SameSite` apropiado.
- Validacion de sesion en cada request a endpoints protegidos.
- Revocacion de sesion en logout.

## Authorization Controls

- Toda consulta y mutacion de dominio debe incluir filtro por `user_id`.
- El backend nunca debe confiar en `user_id` enviado por cliente.
- Cualquier acceso a recurso ajeno retorna rechazo de autorizacion.

## Input and API Protection

- Validacion de payloads en API (tipos, formato, campos obligatorios).
- Mensajes de error de login no deben filtrar si el email existe.
- Aplicar rate limiting en endpoints de login/registro.

## Session Risk Mitigation

- Expiracion de sesion configurable y renovacion controlada.
- Invalidez de cookie debe forzar retorno a login.
- No exponer tokens de sesion en logs ni en respuestas de API.

## Logging and Monitoring Baseline

- Registrar intentos de login exitosos y fallidos.
- Registrar eventos de logout y expiracion de sesion.
- Evitar almacenar secretos o passwords en logs.

## Traceability

- Decision principal: `docs/05-adr/0010-finalize-multi-user-authentication-and-session-model.md`
- Decision relacionada: `docs/05-adr/0009-user-authentication-and-multi-user-data-isolation.md`
