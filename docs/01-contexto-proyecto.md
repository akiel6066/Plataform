# 01 - Contexto del Proyecto

## Proyecto evaluado

FirmaloPe-Platform

## Objetivo de la evaluacion

Realizar una revision de seguridad sobre la aplicacion Web y API del proyecto FirmaloPe-Platform, considerando pruebas SAST, DAST y Ethical Hacking autorizado.

## Componentes identificados

### Aplicacion Web

- Nombre: SedeElectronicaMJM
- Lenguaje: C#
- Framework: ASP.NET MVC 5
- Version: .NET Framework 4.6.2
- Ejecucion local: IIS Express
- Puerto local esperado: 51921
- URL local: http://localhost:51921

### API

- Nombre: Firmalo.Api.Web
- Lenguaje: C#
- Framework: ASP.NET Core 3.1
- Target framework: netcoreapp3.1
- Ejecucion local: dotnet run o IIS Express
- Puerto local esperado: 61590
- URL local: http://localhost:61590

### Capas internas

- Firmalo.Api.Data
- Firmalo.Api.Servicios
- Firmalo.Api.Dto
- Firmalo.Api.Entidades
- Firmalo.Api.Util

### Base de datos

- Motor: SQL Server
- Base identificada: FirmaloBD_Certi
- Uso: ambiente de pruebas/certificacion

## Autenticacion identificada

La aplicacion Web utiliza autenticacion con usuario y contrasena, reCAPTCHA y MFA OTP.

La API utiliza autenticacion basada en JWT.

## Observaciones iniciales

- No se identifico Dockerfile ni docker-compose.
- No se identifico ambiente QA/UAT dedicado dentro del repositorio revisado.
- No se identificaron reportes SAST previos.
- Se identificaron advertencias NuGet en dependencias.
- Se requiere confirmar alcance oficial con BanBif o el equipo responsable.
