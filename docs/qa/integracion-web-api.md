# Pruebas de integración Web ↔ API – HU1 (Sesión y rutas protegidas)

Documento de pruebas de integración entre el frontend web (Next.js) y el backend (Flask) correspondiente a la Historia de Usuario 1.

Fecha: 8 de octubre de 2026  
Responsable: Brenda Veranea Gutierrez (QA Integración)

---

## 1. Objetivo

Verificar que el flujo de autenticación, manejo de sesión JWT y protección de rutas del portal web funciona correctamente contra la API real.

---

## 2. Casos de prueba de integración

### 2.1 Login exitoso (Profesor / Admin)

| ID     | Caso                                      | Resultado esperado                                      | Estado |
|--------|-------------------------------------------|---------------------------------------------------------|--------|
| INT-W1 | Login con credenciales válidas de profesor| 200 + `access_token` + redirección a `/dashboard`       |        |
| INT-W2 | Login con credenciales válidas de admin   | 200 + `access_token` + redirección a `/admin`           |        |
| INT-W3 | Login con credenciales inválidas          | 401 + mensaje de error                                  |        |
| INT-W4 | Login de alumno desde web                 | 403 + código `ALUMNO_WEB_RESTRICTED`                    |        |

### 2.2 Manejo de sesión y token

| ID     | Caso                                      | Resultado esperado                                      | Estado |
|--------|-------------------------------------------|---------------------------------------------------------|--------|
| INT-W5 | Token válido en rutas protegidas          | Acceso permitido a `/dashboard`, `/grupos`, etc.        |        |
| INT-W6 | Token expirado                            | 401 + redirección a `/login`                            |        |
| INT-W7 | Token inválido / manipulado               | 401 + redirección a `/login`                            |        |
| INT-W8 | Cerrar sesión (logout)                    | Se elimina el token y redirige a `/login`               |        |

### 2.3 Rutas protegidas

| ID     | Caso                                      | Resultado esperado                                      | Estado |
|--------|-------------------------------------------|---------------------------------------------------------|--------|
| INT-W9 | Acceso a `/dashboard` sin token           | Redirección a `/login`                                  |        |
| INT-W10| Acceso a `/admin` con rol profesor        | 403 o redirección (según implementación)                |        |
| INT-W11| Endpoint `/api/auth/verify` con token válido | 200 + `valid: true` + rol correcto                  |        |

---

## 3. Notas de integración

- El frontend usa el header `Authorization: Bearer <token>`.
- La URL base de la API se toma de `NEXT_PUBLIC_API_URL` (por defecto `http://localhost:5000/api`).
- Los códigos de error del backend (`TOKEN_EXPIRED`, `INVALID_TOKEN`, `ALUMNO_WEB_RESTRICTED`) deben ser manejados en el cliente.
- Se verificó que el CORS está correctamente configurado para permitir las peticiones desde el origen del frontend.

---

## 4. Conclusión HU1

Las pruebas de integración de sesión y rutas protegidas se consideran **cubiertas** para el alcance de HU1.