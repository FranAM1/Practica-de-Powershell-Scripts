# Practica-de-Powershell-Scripts
Practica de Powershell. Analizar y documenta los siguientes scripts de Powershell

# Paso inicial
Por defecto viene desactivado la ejecucion de scripts, por lo que hay que realizar el comando ```Set-ExecutionPolicy Unrestricted``` para activar la opción y luego se puede ejecutar el comando ```Get-ExecutionPolicy``` para asegurse de que se ha cambiado a correctamente: ~~Restricted~~ Unrestricted
```
PS C:\WINDOWS\system32> Set-ExecutionPolicy Unrestricted

Cambio de directiva de ejecución
La directiva de ejecución te ayuda a protegerte de scripts en los que no confías. Si cambias dicha directiva, podrías
exponerte a los riesgos de seguridad descritos en el tema de la Ayuda about_Execution_Policies en
https:/go.microsoft.com/fwlink/?LinkID=135170. ¿Quieres cambiar la directiva de ejecución?
[S] Sí  [O] Sí a todo  [N] No  [T] No a todo  [U] Suspender  [?] Ayuda (el valor predeterminado es "N"): S
PS C:\WINDOWS\system32> Get-ExecutionPolicy
Unrestricted
```

# Script 1
Este script va guardando diferentes valores en la variable *number* y va imprimiendo con el comando  ```Write-Host``` un String concatenado con el valor de variable en ese momento.
```
$number = 1

Write-Host "The number is: " $number

$number = 2

Write-Host "The number is: " $number

$number = 3

Write-Host "The number is: " $number

$number = 4

Write-Host "The number is: " $number
```
Resultado de la ejecución del script
```
PS C:\Users\Fran> C:\Users\Fran\Desktop\Scripts Powershell\1.ps1
The number is:  1
The number is:  2
The number is:  3
The number is:  4
```
