# Glossary

Este glosario define el lenguaje comun del proyecto para reducir ambiguedades entre arquitectura, dominio y documentacion.

## Product and Domain Terms

| Term | Definition |
| --- | --- |
| Brainstorm | Modulo orientado a captura rapida de ideas sin estructura obligatoria. |
| ToDo | Modulo orientado a ejecucion: organiza trabajo en Project -> Objective -> Task. |
| Idea | Unidad minima de captura en Brainstorm; puede contener texto, imagen, audio o combinaciones, y puede estar agrupada en un Book o no agrupada. |
| Book | Entidad de Brainstorm que agrupa Ideas; un Book contiene multiples Ideas y solo admite Ideas. |
| bookId | Referencia opcional desde Idea hacia Book; cuando es null la Idea queda no agrupada. |
| gridX / gridY | Coordenadas de posicion visual de una Idea dentro de un Book; cuando `bookId = null`, ambas coordenadas son null. |
| Project | Unidad principal de planificacion en ToDo que agrupa objetivos y tareas relacionadas. |
| Objective | Subunidad de un Project que organiza un conjunto coherente de tareas hacia un resultado intermedio. |
| Task | Unidad ejecutable minima dentro de un Objective. |
| Task Change History | Registro inmutable de cambios relevantes sobre una Task (estado, fechas, estimaciones, replanificacion). |
| Idea to Project Conversion | Flujo explicito mediante el cual una Idea de Brainstorm se transforma en un Project en ToDo sin eliminar la Idea original. |

## Planning and Execution Terms

| Term | Definition |
| --- | --- |
| Planning View | Vista global del modulo ToDo para planificar estructura completa (Projects, Objectives, Tasks). |
| Execution View | Vista enfocada para ejecutar trabajo en curso con baja carga cognitiva (maximo 1-3 tareas visibles). |
| Active Project | Project marcado como activo para concentrar ejecucion en un solo frente principal. |
| Active Objective | Objective activo dentro del Project activo; acota el foco operativo del momento. |
| Replanning | Ajuste de fechas/estimaciones sin penalizacion, manteniendo trazabilidad historica. |

## Authentication and Access Terms

| Term | Definition |
| --- | --- |
| Authentication | Proceso de verificar identidad del usuario mediante email/password y sesion persistente. |
| Session | Estado autenticado persistido mediante cookie segura administrada por backend. |
| Authenticated | Estado en el que el usuario tiene sesion valida y puede acceder a vistas protegidas. |
| Unauthenticated | Estado sin sesion valida; requiere login/registro para acceder a contenido protegido. |
| Session Expired | Estado transitorio cuando la sesion deja de ser valida y el cliente debe volver a login. |
| Authorization | Validacion de permisos sobre recursos; el API debe garantizar que cada recurso pertenezca al usuario autenticado. |
| user_id | Identificador del propietario de datos; base del aislamiento entre usuarios. |
| Data Isolation | Regla de seguridad por la cual un usuario no puede leer ni modificar recursos de otro usuario. |

## Architecture and Documentation Terms

| Term | Definition |
| --- | --- |
| MVP | Version minima util para validar valor del producto con el menor alcance posible. |
| ADR (Architecture Decision Record) | Documento de decision arquitectonica con contexto, alternativas y razonamiento. |
| Architecture Docs | Documentos que describen el estado actual del sistema y sus limites de responsabilidad. |
| System Context | Definicion de fronteras del sistema (Client, API, Data) y distribucion de responsabilidades. |
| Non-Functional Requirements | Requisitos de calidad no funcionales (seguridad, performance, logging, etc.). |

## State and Status Terms

| Term | Definition |
| --- | --- |
| pending | Estado de Task aun no iniciada. |
| in_progress | Estado de Task en ejecucion activa. |
| completed | Estado de Task finalizada. |
| is_active | Marca booleana de entidad activa usada para enfocar ejecucion y consultas eficientes. |
