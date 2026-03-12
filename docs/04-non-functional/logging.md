# Logging

## Goal

Definir una estrategia minima de logging para el MVP multi-user.
El objetivo es facilitar debugging cuando ocurra un error, sin agregar complejidad innecesaria.

## Scope

Aplica a frontend y backend del MVP.

## Log Levels

- `INFO`: eventos normales relevantes.
- `ERROR`: fallos que impiden completar una accion.

En esta fase no se requiere uso sistematico de `DEBUG`, `WARN` ni sistemas avanzados de observabilidad.

## What to Log

- Inicio de aplicacion y API.
- Errores al crear, editar o eliminar entidades principales.
- Errores de acceso a base de datos.
- Fallos de unlock/autenticacion (sin exponer credenciales).

## What Not to Log

- Passwords.
- PIN.
- Tokens completos.
- Datos sensibles en texto plano.

## Storage

- Backend: salida por consola.
- Frontend: consola del navegador solo para errores relevantes.

Opcional en una siguiente iteracion: archivo local rotativo para historial corto de errores.

## Minimum Format

Cada log debe incluir al menos:

- `timestamp`
- `level`
- `module`
- `message`

## Evolution Rule

Si el proyecto evoluciona a despliegue productivo con mayor escala, esta estrategia debe revisarse y ampliarse.
