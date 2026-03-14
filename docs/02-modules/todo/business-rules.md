# ToDo Rules – ToDo Module

## 1. Purpose of the Module

El módulo ToDo es responsable de transformar ideas definidas en trabajo ejecutable.

Mientras que Brainstorm permite capturar ideas sin estructura ni presión, el módulo ToDo permite organizar esas ideas en proyectos concretos y avanzar en su ejecución de manera progresiva.

El objetivo principal del módulo es:

- Descomponer objetivos grandes en unidades ejecutables
- Facilitar la planificación personal
- Reducir la carga cognitiva durante la ejecución
- Registrar progreso de ejecución

Este módulo representa el espacio donde las ideas pasan de **concepto a acción**.

---

## 2. Ownership and Access

Las entidades del módulo ToDo pertenecen al usuario que las crea.

Cada usuario es propietario de:

- sus proyectos
- sus objetivos
- sus tareas

No existe colaboración multiusuario en la versión inicial del sistema.

El acceso a la información está restringido al propietario del contenido.

---

## 3. Content Flexibility

El sistema permite distintos niveles de estructura dependiendo del nivel de claridad del proyecto.

Un proyecto puede comenzar con pocos objetivos o tareas y evolucionar progresivamente.

Las tareas no necesitan definirse completamente desde el inicio; el sistema permite agregar, modificar o eliminar tareas durante la ejecución del proyecto.

La planificación es iterativa y adaptable.

---

## 4. Idea Lifecycle

Las ideas suelen originarse en el módulo Brainstorm.

El flujo esperado es:

Brainstorm Idea  
↓  
Conversión a Proyecto en ToDo  
↓  
Definición de Objetivos  
↓  
Descomposición en Tareas  
↓  
Ejecución y seguimiento  

No todas las ideas deben convertirse en proyectos.

El usuario decide cuándo una idea está lo suficientemente definida para transformarse en trabajo ejecutable.

---

## 5. Status Rules

Las tareas pueden tener los siguientes estados:

- **pending** – tarea definida pero no iniciada  
- **in_progress** – tarea actualmente en ejecución  
- **completed** – tarea finalizada  

Los objetivos y proyectos se consideran completados cuando todas sus tareas asociadas están completadas.

El sistema puede recalcular automáticamente el estado de objetivos y proyectos según el progreso de sus tareas.

---

## 6. Conversion Rules

Las ideas del módulo Brainstorm pueden convertirse en proyectos dentro del módulo ToDo.

Durante la conversión:

- se crea un nuevo proyecto
- se conserva la referencia a la idea original
- el contenido puede reutilizarse como descripción del proyecto

La conversión no elimina la idea original del Brainstorm.

Esto permite mantener el historial del proceso creativo.

---

## 7. Non-goals

El módulo ToDo **no está diseñado para funcionar como un gestor de tareas tradicional o una lista simple de pendientes**.

Tampoco busca imponer planificación rígida ni penalizar retrasos.

Los siguientes objetivos quedan explícitamente fuera del alcance del módulo:

- microgestión obligatoria de cada actividad
- planificación estricta sin posibilidad de cambio
- métricas de productividad punitivas
- presión para completar tareas en tiempos exactos

El sistema está diseñado para acompañar el proceso real de trabajo del usuario y facilitar la ejecución sostenida.

---

## 8. Activation Rules

El sistema puede mantener hasta dos proyectos activos de forma simultánea: un proyecto principal y un proyecto secundario de continuidad.

**Project activation:**

- Puede haber hasta dos proyectos con estado `active` en un momento dado.
- Cuando existe un solo proyecto activo, se considera foco principal.
- El segundo proyecto activo se habilita únicamente como continuidad frente a bloqueo externo del principal.
- Al intentar activar un tercer proyecto, el sistema debe exigir desactivar uno de los activos actuales.
- Un proyecto completado no puede ser activado.

**Objective activation:**

- Solo puede haber un objetivo activo por cada proyecto activo.
- Al activar un objetivo diferente dentro del mismo proyecto, el objetivo previamente activo pasa a estado `inactive`.
- Un objetivo completado no puede ser activado.

Esta restricción busca balancear foco y continuidad: mantener un frente principal y permitir un frente secundario cuando el principal esté bloqueado externamente.

---

## 9. Execution View Rules

El sistema distingue dos vistas con propósitos distintos:

**Planning View**

- Muestra la visión global completa del usuario.
- Sin restricción de visibilidad: todos los proyectos, objetivos y tareas son accesibles.
- Usada para planificar y reorganizar el trabajo.

**Execution View**

- Muestra únicamente:
  - 1 o 2 proyectos activos
  - 1 objetivo activo por cada proyecto activo
  - Máximo 1–3 tareas visibles simultáneamente
- Esta limitación es intencional para prevenir la sobrecarga cognitiva durante la ejecución.
- El usuario no ve la totalidad de sus tareas pendientes en esta vista.

---

## 10. Replanning Rules

Estado actual: **No-Scope (parking)**.

Las reglas de replanificación temporal quedan fuera de alcance en la etapa actual.

Si la fase se reactiva en el futuro, estas reglas deberán redefinirse y versionarse nuevamente.

---

## 11. Change History

Cada tarea mantiene un registro inmutable de sus cambios.

El historial registra:

- Cambios de estado (`status`)
- Cambios de estimación de tiempo (`time_estimate`) [No-Scope actual]
- Cambios de fecha estimada (`estimated_date`) [No-Scope actual]
- Fecha y hora en que se realizó cada cambio

Reglas:

- El historial es generado automáticamente por el sistema.
- El usuario no puede editar ni eliminar entradas del historial.
- El historial permite analizar desvíos entre planificación inicial y ejecución real.
- Sirve como base para evolución futura del sistema cuando se reactive planificación temporal.