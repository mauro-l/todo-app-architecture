# ADR-0008: Initial Technology Stack for MVP

## Status

Accepted

## Context

El proyecto consiste en una aplicación personal orientada a la gestión de ideas y ejecución de tareas, separando claramente dos dominios principales: **Brainstorm** (captura de ideas) y **Todo** (ejecución de tareas).

El objetivo del MVP es permitir iterar rápidamente sobre el producto, validar el modelo de uso y mantener una arquitectura simple que permita crecer sin introducir complejidad innecesaria.

La aplicación debe funcionar tanto en **desktop como en dispositivos móviles**, con posibilidad de instalación como aplicación y potencial soporte futuro para capacidades del dispositivo como biometría.

Dado que el producto comenzará como una herramienta personal con un único usuario, no se requiere inicialmente una arquitectura distribuida ni sistemas complejos de autenticación o multi-tenant.

Por lo tanto, se necesitaba seleccionar un stack tecnológico que priorice:

* rapidez de desarrollo
* simplicidad de mantenimiento
* buen soporte de tipado
* capacidad de escalar gradualmente
* compatibilidad con web y mobile

## Decision

Se adopta el siguiente stack tecnológico para el desarrollo del MVP:

### Frontend

**React 18 + PWA**

React permite un desarrollo rápido con un ecosistema maduro y amplio soporte de librerías.
La aplicación será implementada como **Progressive Web App (PWA)** para permitir:

* ejecución en navegador
* instalación como aplicación en dispositivos
* potencial soporte offline
* acceso a APIs del dispositivo en el futuro (biometría, almacenamiento, etc.)

### Backend

**Node.js + Express + TypeScript**

Se utilizará Node.js con Express para construir una API REST simple.
TypeScript se utilizará para mejorar la mantenibilidad del código y reducir errores en tiempo de desarrollo.

Esta combinación permite implementar rápidamente una API CRUD sin introducir complejidad innecesaria.

### Database

**PostgreSQL**

PostgreSQL se utilizará como base de datos principal debido a su robustez, confiabilidad y excelente soporte para modelos relacionales, adecuados para entidades como:

* brainstorms
* tareas
* proyectos (futuro)
* relaciones entre entidades

### ORM

**Drizzle ORM**

Se utilizará Drizzle ORM para la interacción con la base de datos.
Drizzle fue seleccionado por:

* fuerte integración con TypeScript
* control explícito sobre SQL
* migraciones claras
* menor sobrecarga conceptual comparado con otros ORMs

### Authentication

El sistema de autenticación será **propio y simple**, basado en sesión persistente.

El flujo consiste en:

1. **Setup inicial**

   * creación de usuario con email y contraseña
2. **Sesión persistente**

   * el usuario permanece autenticado
3. **Unlock**

   * desbloqueo mediante contraseña

En futuras iteraciones se podrán agregar:

* PIN de acceso
* autenticación biométrica

El sistema está diseñado para **un único usuario**, similar a aplicaciones personales o financieras donde el login ocurre una sola vez y luego se utiliza desbloqueo rápido.

## Consequences

### Positive

* Desarrollo rápido del MVP.
* Stack ampliamente conocido y con gran ecosistema.
* Arquitectura simple y fácil de mantener.
* Buen soporte de tipado gracias a TypeScript.
* Posibilidad de evolucionar hacia funcionalidades mobile mediante PWA.
* PostgreSQL permite escalar el modelo de datos sin cambios estructurales importantes.

### Negative

* La arquitectura basada en Express puede requerir refactorización si el sistema crece significativamente.
* La implementación de autenticación propia implica responsabilidad adicional en seguridad.
* La experiencia mobile mediante PWA puede no ser tan fluida como una aplicación nativa en algunos escenarios.

## Alternatives Considered

* **Next.js Fullstack** – No se eligió para evitar acoplar frontend y backend en el MVP y mantener una API independiente.

* **Prisma ORM** – No se eligió debido a mayor abstracción sobre SQL y menor control directo comparado con Drizzle.

* **Firebase / Supabase Backend** – No se eligió para evitar dependencia fuerte en servicios gestionados y mantener control total de la arquitectura.

* **Aplicación Mobile Nativa (React Native / Flutter)** – No se eligió en el MVP para reducir el alcance inicial y priorizar iteración rápida mediante web.
