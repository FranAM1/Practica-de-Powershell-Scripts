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
## Ejecución del script.
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

## Ejecución del script
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
# Script 3
Este script tambien es mejor dividirlo por partes.
## Parte 1
Aqui muestra unos ejemplos para ver el funcionamiento del operador ```-eq```.
```
if (4 -eq 4) {
    Write-Host "4 is equal to 4"
}

if ("hello" -eq "hello") {
    Write-Host "Both strings are equal to each other"
} 
```
## Parte 2
Se muestra como segun los valores que le pongas a las variables se cumplira la condicion del equals o no.
```
[int]$x = 10
[int]$y = 10

if ($x -eq $y) {
    Write-Host "the x and y variables are equal to each other"
}
else {
    Write-Host "The x and y variables are NOT equal to each other"
}
```

## Parte 3
Lo mismo que la [parte 2](#parte-2), pero utilizando un string como variable.
```
$yourName = "Ian"

if ($yourName -eq "Ian") {
    Write-Host "Hay my name is Ian too!"
}
else {
    Write-Host "Hi $yourName, nice to meet you!"
}
```

## Parte 4
Esta parte es un poco distinta, ya que guarda el input del usuario dentro de la variable *playerInput* para luego hacer la comprobacion segun el valor puesto.
```
$playerInput = Read-Host -Prompt "You walk into a room with two doorways. One to the left and one to the right. Type 'left' or 'Right' to walk through one of the doors."

if ($playerInput -eq "left") {
    Write-Host "Player typed left"
}
elseif ($playerInput -eq "right") {
    Write-Host "Player typed right"
}
else {
    Write-Host "Player typed something we didn't understand"
}
```
