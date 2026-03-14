# ADR-0013: Allow Dual Active Projects for Execution Continuity

> Note: Los títulos deben escribirse en inglés y el contenido explicativo en español, siguiendo la convención definida en ADR-0000. Los nombres de los archivos seran asi 000x-nombre-del-archivo-en-ingles.md

## Status
Accepted

## Context
La ADR-0007 definió una Execution View enfocada en un único proyecto activo para reducir carga cognitiva.

Durante el refinamiento de roadmap y milestones se identificó un caso frecuente: un proyecto activo puede quedar bloqueado por una dependencia externa (espera de terceros, insumos, aprobaciones o tiempos muertos inevitables).

En esos escenarios, exigir exactamente un único proyecto activo puede frenar el avance diario del usuario y generar inactividad innecesaria.

Se requiere mantener el principio de foco, pero permitiendo continuidad operativa cuando existe bloqueo real del frente principal.

## Decision
Se ajusta la regla de activación del módulo Todo:

- Se permiten hasta **dos proyectos activos** en simultáneo.
- El primer proyecto activo se considera **principal**.
- El segundo proyecto activo se considera **secundario de continuidad**, habilitado para casos de bloqueo externo del principal.
- No se permiten más de dos proyectos activos al mismo tiempo.
- Se mantiene la regla de **un objetivo activo por cada proyecto activo**.
- La Execution View continúa limitada a **máximo 1–3 tareas visibles simultáneamente**.

Este cambio supersede únicamente la parte de activación de proyecto definida en ADR-0007. El resto del modelo jerárquico y de la filosofía de Execution View permanece vigente.

## Consequences

### Positive
- Evita frenar la ejecución cuando el proyecto principal se bloquea por factores externos.
- Mantiene foco operativo con un límite estricto (máximo dos proyectos activos).
- Conserva la simplicidad del modelo de ejecución sin abrir multitarea ilimitada.
- Mejora continuidad y percepción de progreso diario.

### Negative
- Incrementa complejidad en reglas de activación y en UI de Execution View.
- Requiere distinguir claramente proyecto principal vs secundario para evitar ambigüedad.
- Puede aumentar riesgo de dispersión si se usa el segundo activo sin un bloqueo real.

## Alternatives Considered

- **Mantener estrictamente 1 proyecto activo** – descartado porque bloquea continuidad operativa en escenarios externos no controlables por el usuario.

- **Permitir N proyectos activos sin límite** – descartado porque rompe el objetivo de foco y eleva la carga cognitiva.

- **No usar segundo proyecto activo y solo pausar el principal** – descartado porque no resuelve el problema de continuidad de ejecución en el mismo período de trabajo.
