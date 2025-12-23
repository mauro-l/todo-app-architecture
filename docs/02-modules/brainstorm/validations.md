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

Una Idea es válida si contiene al menos una de las siguientes formas de contenido:

- Texto
- Imagen
- Audio

Al menos uno de estos campos debe existir para que la Idea sea considerada válida.

---

## Field Validations

### id
- Obligatorio
- Único
- No editable

### text
- Opcional
- Tipo string
- Si existe, no puede ser un string vacío

### imageUrl
- Opcional
- Tipo string
- Debe representar una URL válida
- Solo una imagen permitida en el MVP

### audioUrl
- Opcional
- Tipo string
- Debe representar una URL válida
- Solo un audio permitido en el MVP

### status
- Obligatorio
- Valores permitidos:
  - active
  - archived

### convertedToTodo
- Obligatorio
- Tipo boolean
- Valor por defecto: false

### createdAt
- Obligatorio
- Fecha válida
- Generada por el sistema

### updatedAt
- Obligatorio
- Fecha válida
- Actualizada automáticamente por el sistema

---

## Out of Scope Validations

Las siguientes validaciones no forman parte del MVP:

- Tamaño máximo de imagen
- Duración máxima de audio
- Validaciones semánticas de contenido
- Límite de cantidad de Ideas
