# Validations

## Purpose

Definir las validaciones necesarias para garantizar que una Idea sea válida desde el punto de vista funcional y técnico dentro del módulo Brainstorm.

Estas validaciones determinan si una Idea puede ser creada o actualizada, pero no definen comportamientos ni decisiones de negocio.

---

## Entity: Idea

Una Idea representa una unidad mínima de pensamiento capturada por el usuario.  
Puede expresarse en diferentes formatos y evolucionar en el tiempo.

---

## Content Validation

Una Idea es válida si contiene **al menos una** de las siguientes formas de contenido:

- Texto
- Imagen
- Audio

Una Idea **no puede existir sin contenido**.  
No se permite la creación de Ideas completamente vacías.

---

## Field Validations

### id
- Obligatorio
- Único
- No editable

---

### text
- Opcional
- Tipo string
- Si existe, no puede ser un string vacío
- Puede ser corto, incompleto o informal

---

### imageUrl
- Opcional
- Tipo string
- Debe representar una URL válida
- Solo una imagen permitida en el MVP

---

### audioUrl
- Opcional
- Tipo string
- Debe representar una URL válida
- Solo un audio permitido en el MVP

---

### status
- Obligatorio
- Tipo string
- Valores permitidos:
  - active
  - archived
- No se permiten valores fuera del conjunto definido

---

### convertedToTodo
- Obligatorio
- Tipo boolean
- Valor por defecto: false
- No afecta la validez del contenido de la Idea

---

### createdAt
- Obligatorio
- Fecha válida
- Generada por el sistema

---

### updatedAt
- Obligatorio
- Fecha válida
- Debe ser mayor o igual a `createdAt`
- Actualizada automáticamente por el sistema en cada modificación

---

## Temporal Validations

- `createdAt` no puede ser posterior a `updatedAt`
- Toda actualización de una Idea debe modificar `updatedAt`

---

## Out of Scope Validations

Las siguientes validaciones **no forman parte del MVP**:

- Tamaño máximo de imagen
- Duración máxima de audio
- Validaciones semánticas de contenido
- Límite de cantidad de Ideas
- Múltiples imágenes o audios por Idea
