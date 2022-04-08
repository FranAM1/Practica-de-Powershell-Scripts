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
Resultado de la ejecución del script.
```
PS C:\Users\Fran> C:\Users\Fran\Desktop\Scripts Powershell\1.ps1
The number is:  1
The number is:  2
The number is:  3
The number is:  4
```

# Script 2
Este script se divide en diferentes formas de recorrer bucles.
## Primer Bucle
Aqui se utilizan dos variables junto a una estructura *for* para imprimir el string 'hello' tantas veces hasta que el valor de *counter* sea igual al de *repeat* (5 en este caso).
```
[int]$repeat = 5

for ($counter = 0; $counter -lt $repeat; $counter++) {
    Write-Host "hello"
} 
```

## Segundo Bucle
Es igual que el [primer bucle](#primer-bucle) pero esta vez utiliza una estrcutra *while*.
```
[int]$repeat = 5
[int]$counter = 0

while ($counter -lt $repeat) {
    Write-Host "hello"
    $counter++
}
```

## Tercer Bucle
Es igual que el [segundo bucle](#segundp-bucle) pero utilizando una estructura *do...while*
```
[int]$repeat = 5
[int]$counter = 0
do {
    Write-Host "hello"
    $counter++
}
while ($counter -lt $repeat)
```

## Cuarto Bucle
En esta parte se utiliza una estructura y variables distintas de los anteriores, primer se guarda dentro de *stringOfCharacters* el texto en cuestion para luego en un bucle *foreach*, utilizando la variable *character*, ir imprimiendo por pantalla los diferentes caracteres que conforman el string, el cual se paso a formato array de caracteres.
```
[string]$stringOfCharacters = "PowerShell for Beginners"

foreach ($character in $stringOfCharacters.ToCharArray()) {
    Write-Host $character
} 
```
## Quinto Bucle
Se hace lo mismo que en el [cuarto bucle](#cuarto-bucle), pero ahorrandose la variable *character* ya que lo hace directamente utilizando pipes y la variable ```$_```, para hacer referencia a cada caracter del array.

```
[string]$stringOfCharacters = "PowerShell for Beginners"
$stringOfCharacters.ToCharArray() | ForEach-Object { Write-Host "$_" }
```

Ejecucion del script
```
PS C:\Users\Fran> C:\Users\Fran\Desktop\Scripts Powershell\2.ps1
hello
hello
hello
hello
hello
hello
hello
hello
hello
hello
hello
hello
hello
hello
hello
P
o
w
e
r
S
h
e
l
l
 
f
o
r
 
B
e
g
i
n
n
e
r
s
P
o
w
e
r
S
h
e
l
l
 
f
o
r
 
B
e
g
i
n
n
e
r
s
```
