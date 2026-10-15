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
