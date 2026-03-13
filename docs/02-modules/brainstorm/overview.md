# Brainstorm Module – Overview

## Purpose

El módulo Brainstorm tiene como objetivo permitir la captura rápida y flexible de ideas en el momento en que surgen.

Está diseñado para reducir al mínimo la fricción entre el pensamiento y el registro, priorizando la inmediatez por sobre la organización o el refinamiento.

---

## What is an Idea?

Una Idea es la unidad mínima de información dentro de Brainstorm.

Representa un pensamiento, inspiración o momento capturado por el usuario, sin necesidad de estar completo, estructurado o desarrollado.

Una Idea puede nacer desde:
- Texto
- Una imagen
- Un audio
- O cualquier combinación de los anteriores

---

## Core Principles

- Capture over structure  
- Flexibility over rigidity  
- Personal space  
- No forced progression  

Brainstorm no exige que las ideas evolucionen, se completen o se conviertan en tareas.

---

## Scope

Brainstorm incluye:
- Creación de Ideas
- Edición de Ideas
- Agrupación de Ideas en Books (contenedores visuales)
- Conversión manual de Ideas en Todos
- Visualización simple de Ideas

Brainstorm no incluye:
- Gestión de tareas
- Priorización
- Fechas límite
- Inteligencia artificial
- Clasificación automática

---

## Book as Visual Container

Book es la unidad de agrupación visual dentro de Brainstorm.

- Una Idea puede pertenecer a un Book o quedar no agrupada.
- El Book permite organizar Ideas por contexto o tema sin imponer una taxonomía rígida.
- El usuario puede mover Ideas entre Books en función de su necesidad del momento.

El módulo contempla también Books especiales del sistema (por ejemplo, configuración o ideas eliminadas), manteniendo la misma metáfora visual.

---

## Book Theme

El tema de un Book representa su intención de agrupación (por ejemplo: trabajo, hogar, aprendizaje, referencias).

- El tema del Book es una ayuda de organización, no una regla de negocio restrictiva.
- Una Idea no queda limitada por el tema del Book y puede moverse a otro contenedor.
- El sistema no interpreta semánticamente el contenido para forzar un tema.

Nota: la ADR-0011 formaliza Book, `bookId` opcional y la posicion en grilla (`gridX`, `gridY`) para Ideas agrupadas; no formaliza `theme` como campo obligatorio de dominio.

---

## Relationship with Other Modules

Brainstorm y TodoList son módulos independientes.

- Brainstorm se enfoca en la **captura**
- TodoList se enfoca en la **ejecución**

Una Idea puede convertirse en un Todo, pero no es obligatorio ni automático.

---

## User Context

La aplicación está diseñada como una herramienta personal.

- Un solo usuario
- Contenido privado
- Sesiones persistentes
- Acceso rápido, similar a una app bancaria

---

## Non-Goals

Brainstorm no pretende:
- Optimizar productividad
- Forzar metodologías
- Imponer estructuras mentales
- Reemplazar sistemas de gestión de tareas
