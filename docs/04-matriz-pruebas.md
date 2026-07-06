# 04 - Matriz de Pruebas SAST, DAST y Ethical Hacking

## Objetivo

Registrar las pruebas de seguridad que se ejecutaran sobre el proyecto FirmaloPe-Platform, indicando tipo de prueba, componente, resultado esperado, estado y evidencia.

## Estados utilizados

- PENDIENTE: La prueba aun no fue ejecutada.
- OK: La prueba fue ejecutada y el resultado fue correcto.
- OBSERVADO: La prueba fue ejecutada y se encontro algo por mejorar.
- REVISAR: La prueba requiere mayor validacion.
- NO APLICA: La prueba no corresponde al alcance definido.

---

# 1. Pruebas SAST

| ID | Tipo | Componente | Prueba | Resultado esperado | Estado | Evidencia |
|---|---|---|---|---|---|---|
| SAST-001 | SAST | API | Revisar paquetes NuGet vulnerables | Identificar paquetes con advertencias NU1902, NU1903, NU1904 o similares | PENDIENTE | sast/ |
| SAST-002 | SAST | Web/API | Revisar secretos en configuracion | No deben existir passwords, tokens o connection strings expuestos sin proteccion | PENDIENTE | sast/ |
| SAST-003 | SAST | API | Revisar configuracion JWT | JWT debe tener secreto seguro, expiracion y validacion adecuada | PENDIENTE | sast/ |
| SAST-004 | SAST | Web | Revisar Web.config | No debe exponer informacion sensible innecesaria | PENDIENTE | sast/ |
| SAST-005 | SAST | API | Revisar appsettings.json | No debe exponer secretos sensibles ni configuraciones inseguras | PENDIENTE | sast/ |
| SAST-006 | SAST | Web/API | Revisar Swagger y DeveloperExceptionPage | No deben estar activos en ambientes no autorizados | PENDIENTE | sast/ |
| SAST-007 | SAST | Web/API | Revisar headers configurados por codigo | No deben exponerse headers de disclosure | PENDIENTE | sast/ |
| SAST-008 | SAST | Web | Revisar archivos JavaScript | No deben quedar console.log, debugger o datos sensibles visibles | PENDIENTE | sast/ |
| SAST-009 | SAST | API | Revisar framework netcoreapp3.1 | Documentar riesgo por version fuera de soporte | PENDIENTE | sast/ |
| SAST-010 | SAST | Web | Revisar .NET Framework 4.6.2 | Documentar compatibilidad y soporte requerido | PENDIENTE | sast/ |

---

# 2. Pruebas DAST Web

| ID | Tipo | Componente | Prueba | Resultado esperado | Estado | Evidencia |
|---|---|---|---|---|---|---|
| WEB-001 | DAST Web | Login | Cargar pantalla de login | La pantalla debe cargar sin error 500 ni stacktrace | PENDIENTE | evidencias/ |
| WEB-002 | DAST Web | Login | Login sin contrasena | Debe rechazar el intento y no iniciar sesion | PENDIENTE | evidencias/ |
| WEB-003 | DAST Web | Login | Login con usuario invalido | Debe mostrar mensaje controlado sin revelar informacion sensible | PENDIENTE | evidencias/ |
| WEB-004 | DAST Web | Login/MFA | Login valido debe exigir MFA | No debe permitir ingreso sin OTP correcto | PENDIENTE | evidencias/ |
| WEB-005 | DAST Web | reCAPTCHA | Reutilizar token reCAPTCHA | El segundo intento debe fallar o ser rechazado | PENDIENTE | evidencias/ |
| WEB-006 | DAST Web | Sesion | Acceder endpoint sensible sin sesion | Debe responder 401, 403 o 400 controlado | PENDIENTE | evidencias/ |
| WEB-007 | DAST Web | Errores | Forzar parametros invalidos | No debe mostrar stacktrace ni errores internos | PENDIENTE | evidencias/ |
| WEB-008 | DAST Web | Headers | Revisar headers HTTP | No debe exponer Server, X-Powered-By, X-AspNet-Version u otros innecesarios | PENDIENTE | evidencias/ |
| WEB-009 | DAST Web | Cache | Revisar cache en paginas sensibles | Debe usar controles de cache adecuados | PENDIENTE | evidencias/ |
| WEB-010 | DAST Web | Autorizacion | Cambiar parametros tipo idSolicitud/idDocumento | No debe permitir acceso a recursos no autorizados | PENDIENTE | evidencias/ |

---

# 3. Pruebas DAST API

| ID | Tipo | Componente | Prueba | Resultado esperado | Estado | Evidencia |
|---|---|---|---|---|---|---|
| API-001 | DAST API | JWT | Llamar endpoint protegido sin JWT | Debe responder 401 Unauthorized | PENDIENTE | evidencias/ |
| API-002 | DAST API | JWT | Llamar endpoint con JWT invalido | Debe responder 401 Unauthorized sin stacktrace | PENDIENTE | evidencias/ |
| API-003 | DAST API | JWT | Llamar endpoint con JWT expirado | Debe responder 401 Unauthorized | PENDIENTE | evidencias/ |
| API-004 | DAST API | Swagger | Revisar acceso a Swagger | Debe estar deshabilitado si la configuracion lo indica | PENDIENTE | evidencias/ |
| API-005 | DAST API | Errores | Enviar request malformado | Debe responder 400 controlado | PENDIENTE | evidencias/ |
| API-006 | DAST API | Paginacion | Enviar pageSize extremo y pageNumber negativo | Debe responder 400 o manejar validacion correctamente | PENDIENTE | evidencias/ |
| API-007 | DAST API | Headers | Revisar headers HTTP | No debe exponer informacion tecnologica innecesaria | PENDIENTE | evidencias/ |
| API-008 | DAST API | Rate Limit | Probar multiples requests repetidos | Debe existir control de rate limit si aplica | PENDIENTE | evidencias/ |
| API-009 | DAST API | Autorizacion | Intentar acceder a recurso de otro usuario | Debe rechazar acceso no autorizado | PENDIENTE | evidencias/ |
| API-010 | DAST API | Content-Type | Enviar content-type incorrecto | Debe responder controladamente | PENDIENTE | evidencias/ |

---

# 4. Controles Ethical Hacking

| ID | Tipo | Componente | Prueba | Resultado esperado | Estado | Evidencia |
|---|---|---|---|---|---|---|
| EH-001 | Ethical Hacking | Alcance | Confirmar alcance autorizado | Debe existir autorizacion clara de Web y API | PENDIENTE | docs/ |
| EH-002 | Ethical Hacking | Ambientes | Confirmar ambiente QA/UAT | Debe identificarse ambiente autorizado para pruebas | PENDIENTE | docs/ |
| EH-003 | Ethical Hacking | Integraciones | Confirmar integraciones externas dentro/fuera de alcance | No se deben probar integraciones sin autorizacion | PENDIENTE | docs/ |
| EH-004 | Ethical Hacking | Evidencias | Guardar request/response y capturas | Toda prueba debe tener evidencia trazable | PENDIENTE | evidencias/ |
| EH-005 | Ethical Hacking | Reporte | Preparar reporte tecnico y ejecutivo | Debe documentarse impacto, evidencia y recomendacion | PENDIENTE | reportes/ |

---

# 5. Resumen de avance

| Categoria | Total pruebas | OK | Observado | Pendiente |
|---|---:|---:|---:|---:|
| SAST | 10 | 0 | 0 | 10 |
| DAST Web | 10 | 0 | 0 | 10 |
| DAST API | 10 | 0 | 0 | 10 |
| Ethical Hacking | 5 | 0 | 0 | 5 |
| Total | 35 | 0 | 0 | 35 |

