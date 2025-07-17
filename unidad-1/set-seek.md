# Unidad 1

## 🔎 Fase: Set + Seek

### Actividad 01

El propósito de esta actividad es entender como funciona el Ciclo fetch-decode-execute

``` asm
@1
D=A
@2
D=D+A
@16
M=D
@END
(END)
0;JMP
```

¿Qué crees que haga este programa?

Este es un programa que permite hacer una suma de dos números. Esto lo logra primero leyendo la instrucción en la memoria ROM, luego la interpreta y finalmente la ejecuta.

#### 🧐🧪✍️ Experimento 01 (Observaciones)

Al momento de ejecutar el programa se sigue el orden de las intrucciones y se almacenan los datos en las variables A y D. En el caso de este CPU el registro A es la encargada de dar la dirección de la memoria, por lo que usando instrucciones de tipo A se asigna un número a ambos registros lo que permite después ejecutar la suma. Despúes se le asigna al registro A el número 16, lo cual significa que el resultado será almacenado en la dirección de memoria número 16. El ciclo fetch-decode-execute funciona leyendo primero la información u intruccciones dadas en la memoria ROM, despues interpreta la intrucción y finalmente lo ejecuta, guardandolo en la memoria RAM.

_(En este codigo se utiliza el "(END)" lo cual es una etiqueta encargada de marcar una instrucción)_

#### 🧐🧪✍️ Experimento 02 (Ejecución)

``` asm
@5
D=A
@10
D=D+A
@20
M=D
@END
(END)
0;JMP
```

#### ¿Qué diferencia hay entre los datos almancenados en la memoria ROM y en la RAM?

Los datos que se almacenan en la memoria ROM son las instrucciones que se pueden agregar en diferentes lenguajes (en este caso de ensamblador). pero el CPU lo leera en un codigo binario. mientras que la memoria RAM almacena los datos que surgen de la ejecución del programa.

### Actividad 02

Ahora se analiza el siguiente programa:

``` asm
@SCREEN
D=A
@i
M=D
(READKEYBOARD)
@KBD
D=M
@KEYPRESSED
D;JNE
@i
D=M
@SCREEN
D=D-A
@READKEYBOARD
D;JLE
@i
M=M-1
A=M
M=0
@READKEYBOARD
0;JMP

(KEYPRESSED)
@i
D=M
@KBD
D=D-A
@READKEYBOARD
D;JGE
@16
A=M
M=-1
@i
M=M+1
@READKEYBOARD
0;JMP
```
