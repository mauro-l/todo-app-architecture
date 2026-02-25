# ADR-0006: Establish Documentation Governance

## Status
Accepted

## Context

A medida que el proyecto evolucionó, se detectó la necesidad de formalizar reglas claras sobre cómo se gestiona la documentación.

Sin una gobernanza explícita, las decisiones pueden:

- Perderse en conversaciones.
- Volverse inconsistentes.
- Contradecir convenciones previas.
- Generar deuda técnica documental.

Además, el proyecto interactúa con sistemas de IA que no pueden acceder automáticamente a decisiones tomadas en otros contextos.

Era necesario definir un marco formal que establezca:

- Qué decisiones requieren ADR.
- Cómo se mantienen.
- Cómo deben interactuar las IA con la documentación.
- Qué carpeta es la fuente oficial de verdad.

## Decision

Se establece oficialmente el archivo:

/docs/01-architecture/documentation-governance.md

como documento rector de las reglas de documentación del proyecto.

A partir de esta ADR:

1. Toda decisión estructural o arquitectónica debe registrarse mediante ADR.
2. Las ADR son inmutables una vez aceptadas.
3. Los cambios se registran mediante nuevas ADR.
4. La carpeta `/docs` es la única fuente oficial de verdad.
5. Las interacciones con IA deben respetar la convención formal definida.

## Consequences

### Positive

- Se garantiza coherencia a largo plazo.
- Se reduce ambigüedad.
- Se evita pérdida de decisiones.
- Se establece trazabilidad formal.
- El proyecto adquiere estándar profesional.

### Negative

- Requiere disciplina adicional.
- Aumenta la carga inicial de documentación.

## Alternatives Considered

- No formalizar gobernanza  
  Rechazada por riesgo de inconsistencia y pérdida de decisiones.

- Mantener reglas implícitas  
  Rechazada porque las reglas no escritas tienden a romperse con el tiempo.