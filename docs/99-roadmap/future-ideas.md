# Future Ideas

Este documento registra ideas, capacidades y extensiones que fueron identificadas durante el diseño del sistema pero que quedan fuera del alcance del MVP.

No representan compromisos de desarrollo. Son intenciones o posibilidades que podrían considerarse en versiones futuras según el aprendizaje obtenido con el producto inicial.

---

## Asistencia con IA

**Origen:** ADR-0007

El modelo jerárquico de Project → Objective → Task, combinado con el historial de cambios por tarea, genera una base de datos estructurada del comportamiento real del usuario.

Posibles usos futuros:

- Sugerencias automáticas de estimación de tiempo basadas en historial
- Detección de patrones de bloqueo o postergación
- Recomendaciones de replanificación
- Generación asistida de objetivos y tareas a partir de una idea o descripción
- Análisis de rendimiento personal (desvío estimado vs. real)

---

## Análisis de Rendimiento Personal

**Origen:** ADR-0007

El historial inmutable de cambios por tarea permite en el futuro construir vistas analíticas sobre el comportamiento del usuario:

- Comparación entre tiempo estimado y tiempo real por tarea, objetivo y proyecto
- Frecuencia de replanificación
- Proyectos con mayor o menor desvío
- Tendencias de productividad por período

---

## Autenticación Biométrica

**Origen:** ADR-0008, ADR-0009

El diseño de la aplicación como PWA con sesiones persistentes prepara el terreno para un modelo de desbloqueo rápido mediante biometría (huella digital, reconocimiento facial).

Esto requiere acceso a APIs del dispositivo disponibles a través de Progressive Web App o, en el futuro, una implementación como aplicación nativa.

---

## PIN de Acceso

**Origen:** ADR-0008

Como alternativa intermedia entre password completo y biometría, el sistema podría incorporar un PIN numérico para el flujo de unlock, reduciendo la fricción de acceso.

---

## Soporte Offline

**Origen:** ADR-0008

La arquitectura PWA habilita la posibilidad de soporte offline parcial:

- Lectura de proyectos, objetivos y tareas sin conexión
- Posible creación de tareas e ideas en modo offline con sincronización posterior

Requiere diseñar una estrategia de sincronización y resolución de conflictos.

---

## OAuth y Login Social

**Origen:** ADR-0009

El MVP utiliza autenticación propia con email y password para evitar dependencias externas. En versiones futuras se podría incorporar login con proveedores como Google o GitHub para simplificar el registro.

---

## Drag & Drop para Organización de Ideas

**Origen:** ADR-0005

La Home y los contenedores visuales (libros) están diseñados para permitir organización mediante gestos. El soporte completo de drag & drop para mover ideas entre libros fue identificado como una capacidad deseable no incluida en el MVP inicial.

---

## Formatos Adicionales de Ideas

**Origen:** ADR-0006

El MVP contempla texto, imagen y audio como formatos de idea. Futuras iteraciones podrían incorporar:

- Video
- Links con preview
- Documentos adjuntos
- Dibujos / sketches

---

## Aplicación Nativa (iOS / Android)

Si el uso de la PWA demuestra demanda en dispositivos móviles, podría evaluarse una implementación nativa para acceso a capacidades del dispositivo no disponibles desde el navegador (notificaciones push avanzadas, biometría nativa, widgets de pantalla de inicio).

---

## Compartir Proyectos

El diseño actual asume un único propietario por proyecto. En versiones futuras podría contemplarse la posibilidad de compartir proyectos de forma de solo lectura, o incluso colaboración limitada, sin convertir la aplicación en una herramienta de trabajo en equipo.
