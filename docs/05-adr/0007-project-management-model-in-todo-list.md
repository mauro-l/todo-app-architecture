# ADR-0007: Project Management Model in Todo List

## Status
Superseded by ADR-0013

## Context

Todo App no está diseñada para funcionar como una lista de tareas simple, sino como un sistema de gestión personal de proyectos orientado a reducir la carga cognitiva y facilitar la ejecución sostenida.

Durante la definición conceptual del sistema se identificó un problema clave:

Cuando se visualizan demasiadas tareas simultáneamente, se produce sobrecarga cognitiva, lo que genera bloqueo y evitación.

Además, los objetivos grandes sin estructura intermedia generan ambigüedad y disminuyen la motivación. Se requiere un modelo que permita:

- Descomponer ideas grandes en unidades ejecutables
- Separar planificación de ejecución
- Registrar estimaciones vs tiempos reales
- Permitir replanificación flexible
- Servir como base futura para asistencia con IA

## Decision

Se adopta un modelo jerárquico compuesto por tres niveles:

### Project

- Representa un objetivo general
- Agrupa objetivos
- Tiene estimación global
- Tiene estado
- Puede estar activo o inactivo

### Objective

- Representa una parte concreta del proyecto
- Puede completarse de forma independiente
- Agrupa tareas
- Tiene su propia estimación

### Task

- Es la unidad mínima ejecutable
- Debe ser lo suficientemente pequeña como para no generar rechazo visual
- Contiene:
  - status (pending / in progress / completed)
  - time estimation
  - estimated date
  - actual completion date
  - change history

El sistema separa explícitamente:

- Planning View (visión global completa)
- Execution View (visión limitada y enfocada)

La Execution View debe mostrar:

- 1 proyecto activo
- 1 objetivo activo
- Máximo 1–3 tareas visibles simultáneamente

La replanificación es flexible y no punitiva:

- Las tareas pueden reprogramarse
- Las fechas posteriores se ajustan automáticamente
- Los desvíos quedan registrados
- No existe mecanismo de penalización

## Consequences

### Positive
- Reduce la sobrecarga cognitiva
- Mejora el foco en la ejecución
- Permite planificación sostenible
- Habilita análisis histórico de rendimiento
- Prepara la arquitectura para integración futura con IA

### Negative
- Incrementa la complejidad del modelo de datos
- Requiere lógica adicional de activación (project / objective)
- Aumenta la complejidad en el manejo de estados en UI

## Alternatives Considered

- Flat Task List – Rechazado porque incrementa la sobrecarga cognitiva y no escala para proyectos personales complejos  
- Project + Task (sin capa Objective) – Rechazado porque no ofrece estructura intermedia suficiente para objetivos grandes  