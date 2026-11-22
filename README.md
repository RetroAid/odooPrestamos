# Práctica: Préstamo de equipo

Nombre: TU NOMBRE
Número de cuenta: TU NÚMERO

## Respuestas

Paso 1. Catálogo de equipos
1. ¿Qué pasa con un equipo cuando se desmarca el campo Activo? ¿Por qué es mejor que borrarlo?

El equipo queda archivado y deja de aparecer en las listas normales. Es mejor que borrarlo porque conserva su información y el historial de préstamos.

2. ¿Para qué sirve copy=False en el campo codigo?

Evita que el código de inventario se copie automáticamente al duplicar un equipo, permitiendo asignarle un código diferente.


Paso 2. Registro de préstamos
1. Este modelo usa _name y _inherit al mismo tiempo. ¿Qué hace cada uno aquí?

_name define el nombre del nuevo modelo, mientras que _inherit permite incorporar las funciones de mail.thread, como el historial de mensajes y cambios.

2. ¿Qué hace tracking=True en el campo state?

Permite registrar automáticamente los cambios de estado del préstamo en el chatter, mostrando el historial de modificaciones.


Paso 3. Equipos del préstamo
1. En fields.One2many("prestamo.linea", "prestamo_id"), ¿qué indica cada parámetro?

prestamo.linea indica el modelo relacionado y prestamo_id es el campo que conecta cada línea con su préstamo correspondiente.

2. ¿Qué pasa con las líneas cuando se borra un préstamo? ¿Qué parte del código lo define?

Las líneas relacionadas se eliminan automáticamente. Esto lo define ondelete="cascade" en el campo prestamo_id del modelo prestamo.linea.


Paso 4. Flujo de estados
1. Los botones ya se ocultan según el estado. ¿Por qué los métodos vuelven a validar el estado?

Porque ocultar los botones solo controla la interfaz. Las validaciones en los métodos impiden ejecutar acciones incorrectas desde otros medios y garantizan la seguridad del sistema.

2. ¿Qué hace prestamo.linea_ids.equipo_id.write(...)? ¿Por qué no hace falta un for para cada equipo?

Actualiza el estado de todos los equipos relacionados con el préstamo. No necesita un for porque Odoo permite modificar varios registros al mismo tiempo mediante write().


Paso 5. Reglas del préstamo
1. El campo equipo_id ya filtra los equipos disponibles. ¿Por qué hace falta el TODO 5?

Porque un equipo puede cambiar de estado después de seleccionarlo. Esta validación comprueba nuevamente su disponibilidad antes de confirmar el préstamo.

2. ¿En qué momento se ejecuta un método con @api.constrains? ¿Y la validación de action_prestar?

@api.constrains se ejecuta al crear o modificar los campos correspondientes de un registro. La validación de action_prestar se ejecuta cuando se intenta confirmar el préstamo mediante esa acción.


Paso 6. Contacto, kanban y búsqueda
1. ¿Qué pasa si arrastra una tarjeta del kanban a otra columna? ¿Por qué?

El equipo cambia automáticamente al estado de la columna de destino, porque la vista kanban está agrupada por el campo estado, que permite modificar su valor al mover la tarjeta.

2. El campo prestamo_ids se agregó a res.partner. ¿Se crea una columna nueva en la tabla de contactos? Explique.

No, porque prestamo_ids es un campo One2many que muestra los préstamos relacionados. La relación se almacena mediante el campo partner_id del modelo prestamo.prestamo, sin crear una columna adicional en la tabla de contactos.