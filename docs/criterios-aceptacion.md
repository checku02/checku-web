# Criterios de aceptación — HU1, HU2 y HU3



## 1. Objetivo



Establecer las condiciones de aceptación de las historias de usuario HU1 (Autenticación y gestión de usuarios), HU2 (Gestión de grupos y alumnos) y HU3 (Gestión de docentes y asignaciones) del sistema CheckU.



## 2. Roles de usuario



El sistema contempla los siguientes roles:



- **Administrador:** acceso a las funcionalidades autorizadas para la administración del sistema.

- **Profesor:** acceso a las funcionalidades correspondientes a sus actividades académicas.

- **Estudiante:** acceso a las funcionalidades correspondientes a su perfil y actividades académicas.



## 3. HU1 — Autenticación y gestión de usuarios



### CA-01. Inicio de sesión exitoso



**Dado** que el usuario tiene una cuenta registrada y activa,

**cuando** ingresa sus credenciales correctas,

**entonces** el sistema debe autenticarlo y permitirle acceder a la plataforma.



### CA-02. Credenciales incorrectas



**Dado** que el usuario se encuentra en la pantalla de inicio de sesión,

**cuando** ingresa un correo o contraseña incorrectos,

**entonces** el sistema debe rechazar el acceso y mostrar un mensaje de error comprensible.



### CA-03. Campos obligatorios



**Dado** que el usuario intenta iniciar sesión,

**cuando** deja vacío uno o más campos obligatorios,

**entonces** el sistema debe solicitar que complete los campos requeridos.



### CA-04. Acceso según el rol



**Dado** que el usuario inició sesión correctamente,

**cuando** accede a la plataforma,

**entonces** el sistema debe mostrar las opciones y funcionalidades permitidas para su rol.



### CA-05. Protección de rutas



**Dado** que una ruta requiere autenticación,

**cuando** un usuario no autenticado intenta acceder a ella,

**entonces** el sistema debe impedir el acceso y dirigirlo al inicio de sesión.



### CA-06. Persistencia de sesión



**Dado** que el usuario inició sesión correctamente,

**cuando** navega entre las secciones de la plataforma,

**entonces** su sesión debe mantenerse mientras el mecanismo de autenticación la considere válida.



### CA-07. Token inválido o expirado



**Dado** que la sesión utiliza un token de autenticación,

**cuando** el token sea inválido o haya expirado,

**entonces** el sistema debe impedir el acceso a recursos protegidos y solicitar una nueva autenticación cuando corresponda.



### CA-08. Cierre de sesión



**Dado** que el usuario tiene una sesión activa,

**cuando** selecciona la opción de cerrar sesión,

**entonces** la aplicación debe finalizar la sesión local y evitar que el usuario continúe accediendo a las secciones protegidas sin autenticarse nuevamente.



## 4. HU2 — Gestión de grupos y alumnos



### CA-09. Gestión de grupos



**Dado** que un usuario tiene permisos para gestionar grupos,

**cuando** consulta o realiza una operación de gestión de grupos disponible en el sistema,

**entonces** el sistema debe mostrar la información correspondiente y procesar la operación conforme a las reglas definidas para la historia de usuario.



### CA-10. Gestión de alumnos



**Dado** que un usuario tiene permisos para gestionar alumnos,

**cuando** consulta o realiza una operación de gestión de alumnos disponible en el sistema,

**entonces** el sistema debe mostrar la información correspondiente y procesar la operación conforme a las reglas definidas para la historia de usuario.



### CA-11. Relación entre grupos y alumnos



**Dado** que existen grupos y alumnos registrados,

**cuando** se realiza una operación para relacionar un alumno con un grupo,

**entonces** el sistema debe validar la información recibida y aplicar la relación conforme a las reglas establecidas para la historia de usuario.



### CA-12. Validación de datos



**Dado** que se solicita una operación de gestión de grupos o alumnos,

**cuando** los datos proporcionados no cumplen las validaciones definidas,

**entonces** el sistema debe rechazar la operación e informar el error sin guardar información inválida.



## 5. HU3 — Gestión de docentes y asignaciones



### CA-13. Gestión de docentes



**Dado** que un usuario tiene permisos para gestionar docentes,

**cuando** consulta o realiza una operación de gestión de docentes disponible en el sistema,

**entonces** el sistema debe mostrar la información correspondiente y procesar la operación conforme a las reglas definidas para la historia de usuario.



### CA-14. Gestión de asignaciones



**Dado** que existen docentes y los registros necesarios para realizar asignaciones,

**cuando** un usuario autorizado registra o consulta una asignación,

**entonces** el sistema debe procesar la operación y mostrar la información correspondiente conforme a las reglas definidas para la historia de usuario.



### CA-15. Validación de asignaciones



**Dado** que se solicita registrar o modificar una asignación,

**cuando** la información no cumple las validaciones definidas o faltan datos obligatorios,

**entonces** el sistema debe rechazar la operación e informar el error.



### CA-16. Control de permisos



**Dado** que una operación de gestión de docentes o asignaciones requiere permisos específicos,

**cuando** un usuario sin los permisos necesarios intenta ejecutarla,

**entonces** el sistema debe impedir la operación.



## 6. HU4 — Proyección del código QR

### CA-17. Generación de sesión QR

**Dado** que un profesor ha iniciado sesión y cuenta con los permisos necesarios,

**cuando** solicita generar una sesión QR,

**entonces** el sistema debe responder exitosamente y proporcionar el token QR, el PIN y la imagen del código QR.

### CA-18. Proyección del código QR y PIN

**Dado** que se ha generado una sesión QR correctamente,

**cuando** el profesor accede a la vista de proyección,

**entonces** la interfaz debe mostrar el código QR en un tamaño adecuado para su visualización y el PIN de tres dígitos.

### CA-19. Regeneración del código QR

**Dado** que existe una sesión QR proyectada,

**cuando** el profesor solicita regenerar el código,

**entonces** el sistema debe generar un nuevo token QR y un nuevo PIN, e informar que la operación se realizó correctamente.

### CA-20. Manejo de errores y cierre de sesión QR

**Dado** que el profesor utiliza la funcionalidad de proyección del código QR,

**cuando** ocurre un error de validación, autenticación, permisos o conexión, o solicita cerrar la sesión QR,

**entonces** la interfaz debe manejar los errores de forma comprensible, permitir reintentar cuando corresponda y, al cerrar la sesión QR, confirmar que la sesión queda inactiva.

## 7. Resultado esperado

La aplicación web debe permitir la autenticación de usuarios y ofrecer las funcionalidades de gestión de grupos, alumnos, docentes, asignaciones y proyección del código QR que correspondan a las historias de usuario y los permisos definidos para CheckU.

## 8. Consideraciones

- La interfaz debe mostrar mensajes claros ante errores de autenticación y validación.
- Las credenciales y los tokens no deben exponerse innecesariamente.
- La validación de permisos debe estar respaldada por el backend.
- Las operaciones deben respetar las validaciones y reglas de negocio definidas para cada historia de usuario.
- Los criterios de HU2, HU3 y HU4 deben verificarse contra las historias de usuario, los endpoints y los casos de prueba acordados por el equipo antes de considerarse definitivos.
