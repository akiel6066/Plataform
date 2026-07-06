# 02 - Alcance Ethical Hacking

## Objetivo

Definir que componentes forman parte del alcance inicial de la evaluacion de seguridad y que componentes requieren confirmacion antes de ser probados.

## Alcance incluido inicialmente

- Aplicacion Web SedeElectronicaMJM
- API Firmalo.Api.Web
- Login de usuario
- Flujo MFA OTP
- Validacion de JWT
- Headers de seguridad
- Swagger
- Manejo de errores
- Endpoints Web y API ejecutados localmente
- Dependencias NuGet
- Configuracion sensible
- Archivos JavaScript relevantes

## Alcance no confirmado

Los siguientes componentes no deben ser probados directamente hasta recibir autorizacion formal:

- Servidor SQL Server
- Red interna
- Infraestructura cloud
- Hosts externos
- Integracion OTP
- Servicios de 4identity
- services.insolutions.pe
- integrations.insolutions.pe
- Paneles administrativos externos
- Ambientes productivos

## Ambientes identificados

### Local

- Web: http://localhost:51921
- API: http://localhost:61590

### QA/UAT

Pendiente de confirmar.

### Produccion

No incluido en el alcance inicial salvo autorizacion explicita.

## Regla principal

Toda prueba debe ejecutarse solo sobre componentes autorizados. Si un componente no esta confirmado dentro del alcance, se documenta como pendiente y no se prueba de forma directa.
