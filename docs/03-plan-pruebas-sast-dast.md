# 03 - Plan de Pruebas SAST y DAST

## Objetivo

Definir el plan inicial para ejecutar pruebas de seguridad sobre el proyecto FirmaloPe-Platform.

## Que es SAST

SAST significa Static Application Security Testing.

Consiste en revisar codigo fuente, configuraciones y dependencias sin necesidad de ejecutar ataques contra la aplicacion.

## Actividades SAST

- Revisar dependencias NuGet vulnerables.
- Revisar Web.config y appsettings.json.
- Buscar secretos, passwords, tokens o connection strings expuestos.
- Revisar configuracion JWT.
- Revisar configuracion Swagger.
- Revisar uso de DeveloperExceptionPage.
- Revisar headers configurados en Web y API.
- Revisar flujo de Login.
- Revisar flujo MFA.
- Revisar archivos JavaScript con console.log o debugger.
- Revisar frameworks fuera de soporte.

## Que es DAST

DAST significa Dynamic Application Security Testing.

Consiste en probar la aplicacion funcionando, enviando requests reales contra la Web y la API.

## Actividades DAST Web

- Validar carga de login.
- Probar login sin contrasena.
- Probar login con usuario invalido.
- Probar login valido y obligatoriedad de MFA.
- Validar reCAPTCHA.
- Probar endpoints AJAX sin sesion.
- Revisar respuestas HTTP.
- Revisar errores tecnicos visibles.
- Revisar headers de seguridad.

## Actividades DAST API

- Probar endpoint protegido sin JWT.
- Probar endpoint protegido con JWT invalido.
- Probar JWT expirado.
- Probar parametros invalidos.
- Validar respuestas 401, 403 y 400.
- Verificar que no existan respuestas HTML 200 en endpoints sensibles.
- Revisar Swagger.
- Revisar manejo de excepciones.

## Estados de prueba

- OK: La prueba paso correctamente.
- OBSERVADO: Existe algo por mejorar.
- REVISAR: No se pudo confirmar completamente.
- PENDIENTE: Aun no se ejecuta.
- NO APLICA: No corresponde al alcance.

## Entregables esperados

- Matriz de pruebas.
- Evidencias de ejecucion.
- Capturas de pantalla.
- Salidas de comandos.
- Reporte tecnico.
- Resumen ejecutivo.
