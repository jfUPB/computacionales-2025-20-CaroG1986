# Unidad 2


## 🤔 Fase: Reflect

### Actividad 07

**Explica cómo se representa y manipula un puntero en el lenguaje ensamblador de Hack. Describe las operaciones equivalentes a ```p = &a```(asignar dirección) y ```*p = 20``` (escribir a través del puntero) usando instrucciones de ensamblador.**

El puntero en el lenguaje ensamblador de Hack se representa poniendo primero una @ y después como se quiera llamar, y este entonces va a ocupar una dirección en la memoria. Esas operaciones la primera se trata de guardar la dirección de a en el puntero y para representarla en lenguaje ensamblador sería: 

``` asm
@a
D=A
@p
M=D
```

La segunda instrucción se trata de escribir a través del puntero y se vería así:

``` asm
