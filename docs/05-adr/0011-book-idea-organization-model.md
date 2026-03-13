# ADR-0011: Brainstorm Book–Idea Organization Model

> Note: Los títulos deben escribirse en inglés y el contenido explicativo en español, siguiendo la convención definida en ADR-0000. Los nombres de los archivos seran asi 000x-nombre-del-archivo-en-ingles.md

## Status
Accepted

## Context
El módulo Brainstorm permite capturar Ideas de forma rápida y sin fricción.

A medida que el usuario acumula múltiples Ideas, surge la necesidad de organizarlas dentro del espacio de Brainstorm sin introducir estructuras complejas ni obligatorias.

Para resolver este problema se introduce el concepto de **Book**, un contenedor que permite agrupar Ideas relacionadas dentro de Brainstorm.

Inicialmente el modelo contemplaba Ideas como entidades independientes sin una estructura de agrupación ni una organización visual dentro del contenedor.

Era necesario definir:

- Si Book debía existir como entidad del dominio.
- Si las Ideas debían pertenecer obligatoriamente a un Book.
- Qué tipo de contenido podía contener un Book.
- Cómo se organizan las Ideas dentro de un Book.

## Decision
Se define que **Book es una entidad del módulo Brainstorm cuyo propósito es agrupar Ideas**.

Las reglas del modelo son las siguientes:

- Un **Book puede contener múltiples Ideas**.
- Una **Idea puede pertenecer a un solo Book**.
- Una **Idea puede existir sin pertenecer a ningún Book**.
- Los **Books solo pueden contener Ideas**.

Para soportar este modelo, la entidad **Idea incluye una referencia opcional a Book**: bookId (nullable)

Cuando `bookId` es `null`, la Idea se considera **no agrupada** dentro del espacio Brainstorm.

Además, las Ideas pueden tener **una posición dentro del Book** que representa su ubicación en el tablero visual.

Esta posición se modela mediante coordenadas dentro de una grilla:
gridX
gridY

Estas coordenadas solo tienen significado cuando la Idea pertenece a un Book.

Cuando una Idea no pertenece a ningún Book:
gridX = null
gridY = null

El sistema no interpreta el significado de la posición dentro del tablero.  
La ubicación de las Ideas responde únicamente a la organización visual definida por el usuario.

El concepto de **Book es exclusivo del módulo Brainstorm**.

Otros módulos del sistema, como **Todo**, definirán sus propios mecanismos de organización y no utilizarán Books.

## Consequences

### Positive
- Permite organizar Ideas de forma visual sin imponer una estructura rígida.
- Mantiene el modelo del módulo Brainstorm simple y flexible.
- Permite que las Ideas existan independientemente de un Book.
- Facilita la organización espacial de Ideas dentro de un Book.
- Evita mezclar responsabilidades entre Brainstorm y otros módulos como Todo.

### Negative
- Introduce una nueva entidad en el modelo de datos.
- Requiere manejar casos donde una Idea no pertenece a ningún Book.
- Se deben gestionar restricciones para evitar múltiples Ideas en la misma posición del grid dentro de un Book.

## Alternatives Considered

- **Make Book mandatory for every Idea** – descartado porque introduce fricción al momento de capturar ideas rápidamente.

- **Allow Books to contain multiple entity types (Ideas, Todos, etc.)** – descartado para mantener el módulo Brainstorm enfocado exclusivamente en Ideas.