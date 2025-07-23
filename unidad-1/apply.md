# Unidad 1

## 🛠 Fase: Apply

### Actividad 03

#### Control de flujo de saltos

_Escribe un programa que compare el valor almacenado en la dirección de memoria 5 con el valor 10. Si el valor es menor que 10, guarda el valor 1 en la dirección 7. Si el valor es mayor o igual a 10, guarda el valor 0 en la dirección 7._

El código para este ejercicio es el siguiente:

``` asm
(LOOP)
@5
D=M       
@10
D=D-A
@MENOR
D;JLT 

(MAYOR)
@7
M=0
@LOOP
0;JMP

(MENOR)
@7
M=1
@LOOP
0;JMP
```

### Actividad 04

#### Implementación de un ciclo simple

_Crea un programa que use un ciclo para sumar los números del 1 al 5 y guarde el resultado en la dirección de memoria 12._
``` asm
@1
D=A
@0
M=D
D=0
@1
M=D

(LOOP)
@0
D=M
@6
D=D-A
@END
D;JGE

@0
D=M
@1
M=D+M

@0
M=M+1
@LOOP
0;JMP

(END)
@1
D=M
@12
M=D
```
