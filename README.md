# Práctica: Préstamo de equipo

Nombre: Andres Mejia Bustamante
Número de cuenta: 0801200421463

## Respuestas

Paso 1. Catálogo de equipos

1. ¿Qué pasa con un equipo cuando se desmarca el campo Activo? ¿Por qué es mejor que borrarlo?

El equipo queda archivado y deja de aparecer en las listas normales. Es mejor que borrarlo porque conserva su información y el historial de préstamos.

2. ¿Para qué sirve copy=False en el campo codigo?

Evita que el código de inventario se copie automáticamente al duplicar un equipo, permitiendo asignarle un código diferente.



Paso 2. Registro de préstamos

1. Este modelo usa \_name y \_inherit al mismo tiempo. ¿Qué hace cada uno aquí?

\_name define el nombre del nuevo modelo, mientras que \_inherit permite incorporar las funciones de mail.thread, como el historial de mensajes y cambios.

1. ¿Qué hace tracking=True en el campo state?

Permite registrar automáticamente los cambios de estado del préstamo en el chatter, mostrando el historial de modificaciones.

