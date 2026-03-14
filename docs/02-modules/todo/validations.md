# Validations

## Purpose

Este documento define las reglas de validación del dominio para las entidades del módulo ToDo.

Las validaciones aseguran la integridad de los datos y previenen la creación de información inconsistente dentro del sistema.

Estas reglas representan validaciones de negocio y de consistencia del modelo, independientemente de la tecnología utilizada para implementarlas.

---

## Entity:

Las validaciones aplican a las siguientes entidades del módulo:

- Project
- Objective
- Task

Cada entidad comparte ciertas reglas comunes, pero también puede tener validaciones específicas según su rol dentro del sistema.

---

## Content Validation

El contenido creado dentro del módulo ToDo debe cumplir las siguientes reglas generales:

- Cada entidad debe tener un identificador único.
- Las entidades deben pertenecer a un único usuario.
- Una tarea siempre debe pertenecer a un objetivo.
- Un objetivo siempre debe pertenecer a un proyecto.
- No pueden existir entidades huérfanas dentro del sistema.

La estructura jerárquica del módulo es obligatoria:

Project → Objective → Task

---

## Field Validations

### id

- Obligatorio
- Único
- No editable
- Generado por el sistema

---

### title

- Obligatorio
- Debe contener texto
- Longitud mínima: 3 caracteres
- Longitud máxima: 120 caracteres

Aplica a:

- Project
- Objective
- Task

---

### description

- Opcional
- Longitud máxima recomendada: 1000 caracteres

Aplica a:

- Project
- Objective
- Task

---

### status

Valores permitidos:

- `pending`
- `in_progress`
- `completed`

Transiciones permitidas para Task:

| Desde | Hacia | Permitido |
|---|---|---|
| `pending` | `in_progress` | ✓ |
| `in_progress` | `completed` | ✓ |
| `in_progress` | `pending` | ✓ |
| `completed` | `pending` | ✗ |
| `completed` | `in_progress` | ✗ |

Reglas adicionales:

- Una tarea completada no puede cambiar de estado.
- El estado de Objective y Project se deriva del progreso de sus hijos; no se edita directamente.
- Un objetivo se considera completado cuando todas sus tareas están en estado `completed`.
- Un proyecto se considera completado cuando todos sus objetivos están en estado `completed`.

---

### time_estimate

Estado actual: **No-Scope (parking)**

- Opcional
- Debe ser un número positivo
- Representa tiempo estimado de ejecución

Aplica principalmente a:

- Task
- Objective (estimación agregada)

---

### estimated_date

Estado actual: **No-Scope (parking)**

- Opcional
- Debe ser una fecha válida
- Representa la fecha planificada para completar la entidad

Aplica a:

- Task
- Objective

---

### completed_at

- Opcional
- Solo puede existir si `status = completed`
- Registrado automáticamente por el sistema al completar la entidad
- No editable por el usuario

Aplica a:

- Task
- Objective
- Project

---

### is_active

- Booleano
- Valor por defecto: `false`
- Hasta dos Project pueden tener `is_active = true` en cualquier momento dado
- Si existen dos activos, deben representar un contexto principal y uno secundario de continuidad
- Solo un Objective por Project puede tener `is_active = true` en cualquier momento dado
- Un Project o Objective con `status = completed` no puede tener `is_active = true`

Aplica a:

- Project
- Objective

---

### change_history

- Colección inmutable de registros de cambio
- Generada automáticamente por el sistema
- No editable ni eliminable por el usuario
- Cada entrada registra:
  - campo modificado
  - valor anterior
  - valor nuevo
  - timestamp del cambio
- Campos que generan entradas en el historial: `status`, `time_estimate`, `estimated_date`

Nota: en la etapa actual, solo `status` está activo en alcance. `time_estimate` y `estimated_date` quedan reservados para una reactivación futura.

Aplica a:

- Task

---

## Temporal Validations

Las fechas deben mantener coherencia temporal dentro del sistema.

Reglas:

- `completed_at` no puede ser anterior a la fecha de creación.
- Si se reactiva planificación temporal, `estimated_date` debe representar una fecha futura o presente al momento de la planificación.
- Si se reactiva replanificación, las tareas no completadas podrán ser reprogramadas.

El sistema debe permitir ajustes de planificación sin bloquear la modificación de fechas.

---

## Out of Scope Validations

Las siguientes validaciones quedan fuera del alcance del sistema en la versión inicial:

- Coherencia aritmética entre la estimación de las tareas y la estimación del objetivo padre
- Detección de solapamiento de fechas entre tareas del mismo objetivo
- Dependencias explícitas entre tareas (una tarea bloqueada por otra)
- Validación de tiempo total disponible vs tiempo estimado del proyecto
- Análisis de productividad o métricas de rendimiento (previsto para integración futura con IA)

Las siguientes validaciones **no forman parte del MVP**:

- Detección automática de conflictos de planificación
- Dependencias entre tareas
- Restricciones de orden de ejecución
- Validaciones de carga de trabajo diaria
- Reglas avanzadas de estimación automática