# Architectural Decision Records (ADR)

Este directorio contiene todos los registros de decisiones arquitectónicas del proyecto Todo App.

---

## What is an ADR?

Un Architectural Decision Record (ADR) es un documento que registra una decisión arquitectónica importante tomada durante el desarrollo del proyecto.

Cada ADR explica:

- El contexto del problema
- La decisión tomada
- Las consecuencias
- Las alternativas consideradas

Los ADR permiten entender por qué se tomó una decisión, no solamente cómo funciona el sistema.

---

## Naming Convention

Los archivos deben seguir el siguiente formato:

NNNN-short-title-in-kebab-case.md

Ejemplo:

0005-move-adr-to-docs-folder.md  
0006-use-zod-for-validation.md  

Reglas:

- 4 dígitos obligatorios
- Numeración incremental
- No reutilizar números
- No renumerar ADR existentes
- Usar kebab-case
- El nombre debe describir la decisión

---

## Status Values

Cada ADR debe incluir uno de los siguientes estados:

- Proposed
- Accepted
- Deprecated
- Superseded

---

## How to Create a New ADR

1. Copiar `TEMPLATE.md`
2. Renombrar usando el siguiente número incremental
3. Completar el contenido
4. Realizar commit con el mensaje:

docs(adr): add ADR-XXXX short description

---

## Important

Los ADR son registros históricos inmutables.

Si una decisión cambia:

- No modificar la ADR original
- Crear una nueva ADR
- Marcar la anterior como `Superseded`