# Casos de prueba funcionales — Login y sesión (HU1)

## Objetivo
Verificar el inicio de sesión y el comportamiento de la sesión de usuario en la plataforma web de CheckU.

## Alcance
Pruebas funcionales de autenticación, validación de credenciales, mensajes de error y acceso a la sesión. La ejecución debe realizarse en un entorno de pruebas.

## Casos de prueba

| ID | Escenario | Precondiciones | Pasos | Resultado esperado | Prioridad |
|---|---|---|---|---|---|
| WEB-HU1-001 | Inicio de sesión correcto | Existe un usuario de prueba activo. | 1. Abrir el formulario de login. 2. Ingresar credenciales válidas. 3. Enviar el formulario. | El sistema permite el acceso y muestra la pantalla correspondiente al usuario. | Alta |
| WEB-HU1-002 | Contraseña incorrecta | Existe un usuario de prueba. | 1. Abrir el login. 2. Ingresar el identificador correcto y una contraseña incorrecta. 3. Enviar. | Se rechaza el acceso y se muestra un mensaje de error comprensible. | Alta |
| WEB-HU1-003 | Usuario inexistente | El identificador no pertenece a una cuenta registrada. | 1. Abrir el login. 2. Ingresar un identificador inexistente y una contraseña cualquiera. 3. Enviar. | Se rechaza el acceso sin mostrar información sensible. | Alta |
| WEB-HU1-004 | Campos obligatorios vacíos | El formulario de login está disponible. | 1. Dejar vacíos los campos obligatorios. 2. Enviar el formulario. | Se solicita completar los campos y no se inicia sesión. | Alta |
| WEB-HU1-005 | Cierre de sesión | Hay una sesión autenticada. | 1. Seleccionar cerrar sesión. 2. Intentar acceder a una sección protegida. | La sesión se cierra y la sección protegida requiere autenticación. | Alta |
| WEB-HU1-006 | Persistencia de sesión al navegar | Hay una sesión autenticada. | 1. Iniciar sesión. 2. Navegar a otra sección autorizada. | La sesión se conserva mientras corresponda y el usuario mantiene el acceso autorizado. | Media |
| WEB-HU1-007 | Acceso a una ruta protegida sin sesión | No hay una sesión autenticada. | 1. Abrir directamente una ruta protegida. | El sistema impide el acceso y redirige al login o muestra una respuesta de acceso no autorizado. | Alta |
| WEB-HU1-008 | Validación del rol | Existen cuentas de prueba de los roles implementados. | 1. Iniciar sesión con cada cuenta. 2. Intentar abrir una sección de otro rol. | Se permite únicamente el acceso autorizado para el rol correspondiente. | Alta |

## Registro de ejecución
Estado inicial: Pendiente de ejecución.

Registrar para cada caso: fecha, entorno, datos de prueba, resultado real, estado (Aprobado/Reprobado/Bloqueado) y evidencia.

## Criterio de aceptación
Los casos deben ejecutarse en el entorno de pruebas. Se considera aprobada la validación cuando el resultado real coincide con el esperado y se conserva evidencia de ejecución. No registrar como aprobadas pruebas que no se hayan ejecutado.

# HU2 — Gestión de grupos

## Objetivo
Verificar el funcionamiento de las operaciones de alta y edición de grupos en la plataforma web de CheckU.

## Casos de prueba

| ID | Escenario | Precondiciones | Pasos | Resultado esperado | Prioridad |
|---|---|---|---|---|---|
| WEB-HU2-001 | Alta de grupo con datos válidos | El usuario tiene permisos para gestionar grupos. | 1. Abrir el módulo de grupos. 2. Seleccionar la opción para crear un grupo. 3. Completar los campos obligatorios con datos válidos. 4. Guardar. | El grupo se registra y aparece en el listado de grupos. | Alta |
| WEB-HU2-002 | Alta de grupo con campos obligatorios vacíos | El formulario de alta de grupo está disponible. | 1. Abrir el formulario. 2. Dejar vacíos los campos obligatorios. 3. Intentar guardar. | El sistema impide guardar el grupo y señala los campos que deben completarse. | Alta |
| WEB-HU2-003 | Alta de grupo con datos inválidos | El formulario de alta de grupo está disponible. | 1. Abrir el formulario. 2. Ingresar datos inválidos en uno o más campos. 3. Intentar guardar. | El sistema valida los datos, muestra un mensaje comprensible y no registra información inválida. | Alta |
| WEB-HU2-004 | Edición de un grupo existente | Existe un grupo registrado y el usuario tiene permisos para editarlo. | 1. Abrir el listado de grupos. 2. Seleccionar un grupo. 3. Modificar uno o más campos editables. 4. Guardar los cambios. | Los cambios se guardan y se muestran en la información del grupo. | Alta |
| WEB-HU2-005 | Edición sin modificar información | Existe un grupo registrado y el formulario de edición está disponible. | 1. Abrir un grupo para editarlo. 2. No modificar ningún campo. 3. Guardar, si la interfaz lo permite. | El sistema conserva la información existente y no genera cambios incorrectos. | Media |
| WEB-HU2-006 | Edición con campos obligatorios vacíos | Existe un grupo registrado y el formulario de edición está disponible. | 1. Abrir el formulario de edición. 2. Vaciar un campo obligatorio. 3. Intentar guardar. | El sistema impide guardar los cambios inválidos y muestra la validación correspondiente. | Alta |
| WEB-HU2-007 | Consulta del grupo después de editarlo | Se editó un grupo y el sistema informó que los cambios se guardaron. | 1. Volver al listado. 2. Abrir nuevamente el grupo editado. | Se muestra la información actualizada y persistente del grupo. | Media |

## Registro de ejecución
Estado inicial: Pendiente de ejecución.

Registrar para cada caso: fecha, entorno, datos de prueba, resultado real, estado (Aprobado/Reprobado/Bloqueado) y evidencia.

## Criterio de aceptación
Los casos deben ejecutarse en el entorno de pruebas. No registrar como aprobadas pruebas que no se hayan ejecutado.

# HU3 — Asignación de docentes a grupos

## Objetivo
Verificar el funcionamiento de la asignación de docentes a grupos en la plataforma web de CheckU.

## Casos de prueba

| ID | Escenario | Precondiciones | Pasos | Resultado esperado | Prioridad |
|---|---|---|---|---|---|
| WEB-HU3-001 | Asignación de docente a un grupo | Existe un docente y un grupo registrados. El usuario tiene permisos para realizar asignaciones. | 1. Abrir el módulo de asignaciones. 2. Seleccionar un grupo. 3. Seleccionar un docente. 4. Confirmar la asignación. | La asignación se registra y se muestra asociada al grupo correspondiente. | Alta |
| WEB-HU3-002 | Asignación sin seleccionar docente | Existe un grupo registrado y el formulario de asignación está disponible. | 1. Abrir el formulario. 2. Seleccionar un grupo. 3. No seleccionar un docente. 4. Intentar guardar. | El sistema impide completar la asignación y solicita seleccionar un docente. | Alta |
| WEB-HU3-003 | Asignación sin seleccionar grupo | Existe un docente registrado y el formulario de asignación está disponible. | 1. Abrir el formulario. 2. Seleccionar un docente. 3. No seleccionar un grupo. 4. Intentar guardar. | El sistema impide completar la asignación y solicita seleccionar un grupo. | Alta |
| WEB-HU3-004 | Consulta de una asignación existente | Existe una asignación registrada. | 1. Abrir el módulo de asignaciones. 2. Buscar el grupo o docente correspondiente. | El sistema muestra la relación correcta entre el docente y el grupo. | Alta |
| WEB-HU3-005 | Cambio de docente asignado | Existe un grupo con un docente asignado y la funcionalidad permite cambiar la asignación. | 1. Abrir la asignación existente. 2. Seleccionar otro docente válido. 3. Guardar los cambios. | Se actualiza la asignación y se muestra el docente correspondiente. | Alta |
| WEB-HU3-006 | Validación de docente inexistente o no disponible | El entorno permite preparar datos de prueba para validar docentes no disponibles o inválidos. | 1. Abrir el formulario de asignación. 2. Intentar seleccionar o enviar un docente inválido o no disponible. | El sistema rechaza la asignación inválida y muestra un mensaje comprensible. | Media |
| WEB-HU3-007 | Verificación de persistencia de la asignación | Se registró una asignación correctamente. | 1. Guardar la asignación. 2. Salir del módulo. 3. Volver a consultar el grupo. | La asignación permanece registrada y se muestra correctamente. | Alta |

## Registro de ejecución
Estado inicial: Pendiente de ejecución.

Registrar para cada caso: fecha, entorno, datos de prueba, resultado real, estado (Aprobado/Reprobado/Bloqueado) y evidencia.

## Criterio de aceptación
Los casos deben ejecutarse en el entorno de pruebas. No registrar como aprobadas pruebas que no se hayan ejecutado.
