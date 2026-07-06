# 01 - Comandos DAST Web

## Objetivo

Ejecutar pruebas dinamicas sobre la aplicacion Web local.

URL objetivo:

http://localhost:51921

## 1. Validar que la Web responde

Invoke-WebRequest -Uri "http://localhost:51921" -UseBasicParsing

Guardar evidencia:

Invoke-WebRequest -Uri "http://localhost:51921" -UseBasicParsing > "C:\Users\Carhu\Documents\EH-Firmalo\03-dast-web\web-home.txt"

## 2. Revisar headers de la Web

$response = Invoke-WebRequest -Uri "http://localhost:51921" -UseBasicParsing
$response.Headers

Guardar evidencia:

$response = Invoke-WebRequest -Uri "http://localhost:51921" -UseBasicParsing
$response.Headers | Out-File "C:\Users\Carhu\Documents\EH-Firmalo\03-dast-web\web-headers.txt"

## 3. Pruebas manuales Web

- WEB-001: Cargar pantalla de login.
- WEB-002: Login sin contrasena.
- WEB-003: Login con usuario invalido.
- WEB-004: Login valido debe exigir MFA.
- WEB-005: Validar reCAPTCHA.
- WEB-006: Acceder endpoint sensible sin sesion.
- WEB-007: Forzar parametros invalidos.
- WEB-008: Revisar headers HTTP.

## 4. Carpeta de capturas

C:\Users\Carhu\Documents\EH-Firmalo\05-screenshots
