# 01 - Comandos SAST

## Objetivo

Ejecutar revision estatica sobre codigo, configuraciones y dependencias del proyecto FirmaloPe-Platform.

## 1. Validar ubicacion

pwd
dir

## 2. Validar estructura del proyecto

dir .\SedeElectronicaMJM
dir .\Firmalo.Api.Web

## 3. Compilar Web

MSBuild.exe "SedeElectronicaMJM\SedeElectronicaMJM.csproj" /p:Configuration=Debug /v:minimal

Guardar evidencia:

MSBuild.exe "SedeElectronicaMJM\SedeElectronicaMJM.csproj" /p:Configuration=Debug /v:minimal > "C:\Users\Carhu\Documents\EH-Firmalo\01-build\build-web.txt"

## 4. Compilar API

dotnet build "Firmalo.Api.Web\Firmalo.Api.Web.csproj" -c Debug --no-restore

Guardar evidencia:

dotnet build "Firmalo.Api.Web\Firmalo.Api.Web.csproj" -c Debug --no-restore > "C:\Users\Carhu\Documents\EH-Firmalo\01-build\build-api.txt"

## 5. Revisar paquetes vulnerables

dotnet list "Firmalo.Api.Web\Firmalo.Api.Web.csproj" package --vulnerable

Guardar evidencia:

dotnet list "Firmalo.Api.Web\Firmalo.Api.Web.csproj" package --vulnerable > "C:\Users\Carhu\Documents\EH-Firmalo\02-sast\nuget-vulnerables-api.txt"

## 6. Buscar secretos o configuracion sensible

Select-String -Path ".\**\*.config",".\**\*.json",".\**\*.cs" -Pattern "password","Password","Pwd","connectionString","JwtSecret","secret","token","apikey","User ID" -CaseSensitive:$false

## 7. Buscar trazas JavaScript

Select-String -Path ".\**\*.js" -Pattern "console.log","debugger","localStorage","sessionStorage","token","password" -CaseSensitive:$false

## 8. Buscar Swagger y DeveloperExceptionPage

Select-String -Path ".\**\*.cs",".\**\*.json",".\**\*.config" -Pattern "Swagger","DeveloperExceptionPage","UseSwagger","UseDeveloperExceptionPage" -CaseSensitive:$false

## 9. Buscar headers de disclosure

Select-String -Path ".\**\*.cs",".\**\*.config" -Pattern "X-Powered-By","X-AspNet-Version","X-AspNetMvc-Version","Server","X-SourceFiles","Headers.Remove","OnStarting" -CaseSensitive:$false
