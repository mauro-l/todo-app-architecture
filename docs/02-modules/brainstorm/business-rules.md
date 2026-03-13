# Business Rules – Brainstorm Module

## 1. Purpose of the Module

El módulo Brainstorm está diseñado para capturar ideas en el momento en que surgen, sin fricción ni estructura obligatoria.  
Su objetivo principal es permitir que el usuario externalice pensamientos, inspiraciones y momentos de forma rápida, dejando la refinación para más adelante (o nunca).

Brainstorm prioriza la captura por sobre la organización.

---

## 2. Ownership and Access

- Brainstorm es un espacio personal por cuenta de usuario.
- Todas las Ideas pertenecen exclusivamente al usuario autenticado propietario.
- La aplicación permite múltiples usuarios con aislamiento de datos por `user_id`.
- No existe el concepto de contenido compartido en el MVP.
- Todo el contenido es privado por definición para cada cuenta.

---

## 3. Content Flexibility

- Una Idea puede originarse de distintas formas según el momento y el contexto.
- Una Idea puede contener uno o más de los siguientes elementos:
  - Texto
  - Imágenes
  - Audios
- El formato de origen no define la importancia ni el valor de la Idea.
- Capturar el momento es más importante que estructurarlo.
- El sistema no debe forzar un formato específico al momento de crear una Idea.
- Las Ideas pueden permanecer incompletas, vagas o sin desarrollar de forma indefinida.

---

## 4. Idea Lifecycle

- Una Idea se crea como una captura cruda.
- Una Idea puede crearse asociada a un Book o sin Book (`bookId = null`).
- Una Idea puede permanecer sin cambios indefinidamente.
- Una Idea puede editarse o expandirse con el tiempo.
- Una Idea puede moverse entre Books o pasar a estado no agrupado sin perder historial de la propia Idea.
- Una Idea puede marcarse como convertida en un Todo.
- La conversión no elimina ni reemplaza la Idea original.
- Las Ideas no se archivan ni eliminan automáticamente.

---

## 5. Status Rules

- Toda Idea tiene un estado.
- El estado representa la situación de la Idea dentro de Brainstorm, no su calidad ni prioridad.
- Los cambios de estado son siempre acciones explícitas del usuario.
- No existen transiciones automáticas de estado.

---

## 6. Book Rules

- Book es el contenedor visual oficial para agrupar Ideas en Brainstorm.
- Todo Book pertenece a un unico usuario (`user_id`).
- Una Idea puede no tener Book asignado (`bookId = null`).
- El sistema permite Books especiales definidos por producto (por ejemplo, configuracion e ideas eliminadas).
- Los Books solo pueden contener Ideas.
- Los Books especiales no cambian la naturaleza de la Idea: solo representan contexto de organizacion.

### 6.1 Grid Position Rules

- Una Idea puede tener posicion en grilla (`gridX`, `gridY`) cuando pertenece a un Book.
- Si una Idea no pertenece a Book (`bookId = null`), entonces `gridX = null` y `gridY = null`.
- El sistema no interpreta semanticamente la posicion en grilla; es organizacion visual definida por el usuario.
- Debe evitarse que dos Ideas ocupen la misma posicion dentro del mismo Book.

### 6.2 Book Theme Rules

- Todo Book puede definir un `theme` descriptivo de agrupacion.
- El `theme` tiene objetivo de organizacion visual y cognitiva.
- El `theme` no aplica validaciones semanticas sobre el contenido de las Ideas.
- El usuario puede mover una Idea a un Book con distinto `theme` en cualquier momento.

Nota: `theme` queda como criterio de UX/documentacion y no como requerimiento obligatorio de dominio en ADR-0011.

---

## 7. Conversion Rules

- Una Idea puede convertirse en un Todo.
- La conversión es opcional.
- La conversión no implica que la Idea esté completa ni priorizada.
- Las Ideas convertidas siguen siendo accesibles dentro de Brainstorm.
- Brainstorm y TodoList conviven, pero son módulos conceptualmente independientes.

---

## 8. Non-goals

El módulo Brainstorm **no busca**:
- Imponer metodologías de productividad
- Rankear Ideas por importancia
- Analizar o interpretar automáticamente el contenido
- Obligar a categorizar al momento de la creación
- Forzar progresión o cierre de Ideas
