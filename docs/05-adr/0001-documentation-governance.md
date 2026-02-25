# Documentation Governance

Este documento define las reglas oficiales para la creación, modificación y mantenimiento de la documentación del proyecto Todo App.

Su objetivo es garantizar consistencia, trazabilidad y coherencia arquitectónica a largo plazo.

---

## 1. Source of Truth

La documentación dentro de la carpeta `/docs` es la única fuente oficial de verdad del proyecto.

Ninguna decisión arquitectónica se considera oficial si no está documentada mediante una ADR.

---

## 2. Architectural Decisions Rule

Toda decisión que afecte:

- Arquitectura
- Estructura de carpetas
- Convenciones globales
- Librerías principales
- Patrones estructurales
- Estrategias de validación
- Estrategias de logging
- Persistencia de datos

Debe registrarse obligatoriamente mediante una ADR.

Si no existe ADR, la decisión no es oficial.

---

## 3. ADR Governance

Las ADR:

- Son inmutables.
- No se modifican después de estar en estado `Accepted`.
- Si una decisión cambia, se crea una nueva ADR.
- La anterior se marca como `Superseded`.

Ubicación oficial:
/docs/02-adr/

---

## 4. Language Convention

Regla oficial del proyecto:

- Carpetas → Inglés
- Archivos → Inglés
- Títulos (H1, H2, H3) → Inglés
- Status values → Inglés
- Contenido explicativo → Español

Definido en:
ADR-0000

---

## 5. Interaction with AI Systems

Las IA no pueden acceder automáticamente a otros chats ni recordar decisiones pasadas fuera del contexto actual.

Por lo tanto:

Cuando se cree una nueva ADR desde otro chat, se debe proporcionar explícitamente:

- Path oficial de ADR
- Último número usado
- Convención de nombre
- Estados permitidos
- Convención de idioma

Esto garantiza alineación con la gobernanza del proyecto.

---

## 6. Documentation Hierarchy

La estructura de `/docs` sigue el siguiente orden lógico:

- 00-introduction → Contexto general del proyecto
- 01-architecture → Diseño y estructura actual
- 02-adr → Historial de decisiones arquitectónicas

Architecture describe el estado actual.
ADR describe por qué se llegó a ese estado.

---

## 7. Principle of Consistency

La consistencia estructural tiene prioridad sobre la preferencia personal momentánea.

Cualquier cambio estructural debe formalizarse mediante ADR antes de aplicarse.

---

## 8. Long-Term Vision

Este proyecto está diseñado con mentalidad profesional y escalable.

La documentación no es decorativa.
Es parte del sistema.

Sin documentación gobernada, el sistema pierde coherencia con el tiempo.