# Criterios de aceptación — HU1: Autenticación y gestión de usuarios

## 1. Objetivo

Establecer las condiciones que debe cumplir el sistema CheckU para permitir el inicio de sesión de los usuarios y el acceso a las funcionalidades correspondientes según su rol.

## 2. Roles de usuario

El sistema contempla los siguientes roles:

- **Administrador:** acceso a las funcionalidades autorizadas para la administración del sistema.
- **Profesor:** acceso a las funcionalidades correspondientes a sus actividades académicas.
- **Estudiante:** acceso a las funcionalidades correspondientes a su perfil y actividades académicas.

## 3. Criterios de aceptación

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

## 4. Resultado esperado

La aplicación web debe permitir un inicio de sesión seguro, mantener el estado de autenticación de forma adecuada y restringir el acceso a las funcionalidades de acuerdo con los permisos del usuario.

## 5. Consideraciones

- La interfaz debe mostrar mensajes claros ante errores de autenticación.
- Las credenciales y los tokens no deben exponerse innecesariamente.
- La validación de permisos debe ser respaldada por el backend.
- El comportamiento debe ser consistente con los endpoints y mecanismos de autenticación definidos para CheckU.