# 02 - Comandos DAST API

## Objetivo

Ejecutar pruebas dinamicas sobre la API local.

URL objetivo:

http://localhost:61590

## 1. Validar que la API responde

Invoke-WebRequest -Uri "http://localhost:61590" -UseBasicParsing

Guardar evidencia:

Invoke-WebRequest -Uri "http://localhost:61590" -UseBasicParsing > "C:\Users\Carhu\Documents\EH-Firmalo\04-dast-api\api-home.txt"

## 2. Revisar Swagger

Invoke-WebRequest -Uri "http://localhost:61590/swagger" -UseBasicParsing

Guardar evidencia:

Invoke-WebRequest -Uri "http://localhost:61590/swagger" -UseBasicParsing > "C:\Users\Carhu\Documents\EH-Firmalo\04-dast-api\api-swagger.txt"

## 3. Revisar headers de la API

$response = Invoke-WebRequest -Uri "http://localhost:61590" -UseBasicParsing
$response.Headers

Guardar evidencia:

$response = Invoke-WebRequest -Uri "http://localhost:61590" -UseBasicParsing
$response.Headers | Out-File "C:\Users\Carhu\Documents\EH-Firmalo\04-dast-api\api-headers.txt"

## 4. Probar endpoint protegido sin JWT

Invoke-WebRequest -Uri "http://localhost:61590/api/ENDPOINT" -UseBasicParsing

Resultado esperado:

401 Unauthorized o respuesta controlada.

## 5. Probar endpoint con JWT invalido

Invoke-WebRequest -Uri "http://localhost:61590/api/ENDPOINT" -Headers @{ Authorization = "Bearer token_falso" } -UseBasicParsing

Resultado esperado:

401 Unauthorized sin stacktrace.

## 6. Probar parametros invalidos

Invoke-WebRequest -Uri "http://localhost:61590/api/ENDPOINT?pageSize=999999&pageNumber=-1" -UseBasicParsing

Resultado esperado:

400 Bad Request o validacion controlada.
