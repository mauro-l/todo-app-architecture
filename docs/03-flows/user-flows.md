# User Flows

Este documento describe los flujos de autenticacion y acceso del MVP.

## Registration Flow

1. Usuario abre pantalla de registro.
2. Ingresa email y password.
3. Frontend envia request de registro al API.
4. API valida formato y unicidad de email.
5. API crea usuario y retorna sesion autenticada.
6. Cliente redirige al Home autenticado.

## Login Flow

1. Usuario abre pantalla de login.
2. Ingresa email y password.
3. Frontend envia credenciales al API.
4. API valida credenciales.
5. API crea/renueva sesion y responde con cookie segura.
6. Cliente redirige al Home autenticado.

## Persistent Session Flow

1. Usuario vuelve a abrir la app.
2. Cliente consulta endpoint de sesion actual usando cookie existente.
3. Si la sesion es valida, accede directamente al contenido.
4. Si la sesion no es valida o expiro, se redirige a login.

## Logout Flow

1. Usuario ejecuta logout desde la app.
2. Cliente invoca endpoint de cierre de sesion.
3. API invalida sesion activa y limpia cookie.
4. Cliente vuelve a pantalla de login.

## Authorization Constraint (All Business Flows)

- Toda operacion de Brainstorm y Todo requiere usuario autenticado.
- El API filtra y valida recursos por `user_id`.
- Si el recurso no pertenece al usuario autenticado, responde acceso denegado.
