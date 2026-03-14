# ADR-0012: Introduce AI Chat Utility as Isolated Assistant

> Note: Los títulos deben escribirse en inglés y el contenido explicativo en español, siguiendo la convención definida en ADR-0000. Los nombres de los archivos seran asi 000x-nombre-del-archivo-en-ingles.md

## Status
Accepted

## Context
Durante la definición del roadmap se decidió incorporar una fase específica para experimentar con integración de IA dentro del producto.

El sistema principal está enfocado en organización personal y ejecución (Brainstorm + Todo), por lo que agregar capacidades de IA acopladas al dominio podía introducir complejidad prematura y desviar el foco del MVP.

Se necesitaba una forma de:

- experimentar con APIs de modelos de lenguaje en un caso real
- obtener aprendizaje de integración y operación (latencia, costos, UX)
- evitar impacto sobre reglas de negocio, datos y flujos centrales

## Decision
Se incorpora un **AI Chat Utility** como chat conversacional **aislado** dentro de la aplicación.

Reglas del alcance inicial:

- El chat es auxiliar y no forma parte del sistema de productividad.
- No tiene acceso a datos internos del usuario (Ideas, Projects, Objectives, Tasks).
- No crea ni modifica entidades del dominio.
- No automatiza planificación ni ejecución.
- Se utiliza `Gemini 1.5 Flash` como modelo inicial por equilibrio entre latencia, costo y capacidad conversacional general.

## Consequences

### Positive
- Permite aprender integración de IA sin afectar el núcleo del producto.
- Mantiene separación clara de responsabilidades entre módulos de productividad y utilidad conversacional.
- Reduce riesgo de errores funcionales sobre datos del usuario.
- Habilita evolución futura basada en evidencia real de uso y costos.

### Negative
- El chat no aporta automatización directa al flujo de trabajo del usuario en esta fase.
- Introduce un nuevo frente de operación (monitoreo de costo y disponibilidad del proveedor de IA).
- Puede generar expectativas de integración profunda que aún no forman parte del alcance.

## Alternatives Considered

- **Integrar IA directamente con entidades del sistema desde la primera versión** – descartado por riesgo alto de complejidad, acoplamiento prematuro y posible degradación del foco del producto.

- **Postergar completamente IA para fases futuras** – descartado porque limita aprendizaje temprano sobre integración técnica y experiencia de uso.
