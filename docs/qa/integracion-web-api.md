# Pruebas de integración Web ↔ API – HU4 (Proyección del QR y errores)

Documento de pruebas de integración entre el frontend web (Next.js) y el backend (Flask) correspondiente a la Historia de Usuario 4.

Fecha: 16 de octubre de 2026  
Responsable: Brenda Veranea Gutierrez (QA Integración)

---

## HU4 – Proyección del QR

| ID      | Caso                                      | Resultado esperado                                      | Estado |
|---------|-------------------------------------------|---------------------------------------------------------|--------|
| INT-W40 | Generar sesión QR (profesor autenticado)  | 200/201 + token_qr + pin + imagen QR                    |        |
| INT-W41 | Proyectar QR en pantalla                  | Se muestra QR grande + PIN de 3 dígitos                 |        |
| INT-W42 | Regenerar código QR                       | Nuevo token y nuevo PIN, mensaje de éxito               |        |
| INT-W43 | Error al generar QR (sin permiso)         | 403                                                     |        |
| INT-W44 | Error de red / backend caído              | Mensaje genérico de error + opción de reintentar        |        |
| INT-W45 | Cerrar sesión QR                          | 200 + la sesión queda inactiva                          |        |

## Notas

- La vista del proyector debe mostrar mensaje de error genérico y permitir regenerar el código.
- Se verifica el manejo de códigos 400, 401, 403 y errores de red en el frontend.
- El frontend usa el header `Authorization: Bearer <token>`.