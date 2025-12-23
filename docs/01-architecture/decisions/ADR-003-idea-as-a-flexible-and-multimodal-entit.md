# ADR-003 – Idea as a Flexible and Multimodal Entity

## Context

El módulo Brainstorm tiene como objetivo capturar ideas en el momento en que
surgen, independientemente del formato o contexto.

Durante el diseño se identificaron múltiples escenarios de uso:
ideas nacidas de imágenes, audios o texto breve, muchas veces sin estructura.

Se evaluó limitar el formato en el MVP, pero esto entraba en conflicto con el
propósito central del módulo.

## Decision

Definir Idea como una entidad flexible y multimodal desde el MVP.

## Rationale

- Las ideas pueden surgir en cualquier contexto.
- Forzar texto limita la captura espontánea.
- Imagen y audio son formas válidas de pensamiento.
- La captura es más importante que la estructura inicial.
- Postergar esto rompería el núcleo conceptual del producto.

## Implications

- Una Idea puede contener texto, imagen, audio o combinación.
- No se exige un formato específico al crear una Idea.
- La validación se basa en la existencia de contenido, no en su forma.
- El almacenamiento de medios se considera parte del MVP.
- La UI debe permitir capturas rápidas en distintos formatos.
