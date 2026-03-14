# State Transitions

Este documento define las transiciones de estado de autenticacion para el MVP.

## Authentication State Machine

Estados:

- `Unauthenticated`
- `Authenticating`
- `Authenticated`
- `SessionExpired`

Transiciones:

1. `Unauthenticated -> Authenticating`
	- Trigger: usuario envia login o registro.

2. `Authenticating -> Authenticated`
	- Trigger: API valida credenciales y establece sesion.

3. `Authenticating -> Unauthenticated`
	- Trigger: credenciales invalidas o request rechazada.

4. `Authenticated -> SessionExpired`
	- Trigger: expiracion/invalidez de sesion detectada por API.

5. `SessionExpired -> Unauthenticated`
	- Trigger: cliente limpia estado local y redirige a login.

6. `Authenticated -> Unauthenticated`
	- Trigger: logout explicito por usuario.

## Route Guard Rule

- Vistas protegidas solo son accesibles en estado `Authenticated`.
- Cualquier estado distinto redirige a `login`.
