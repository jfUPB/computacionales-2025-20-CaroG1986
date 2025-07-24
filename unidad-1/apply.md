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

La elaboración de este programa necesito de comprender bien cómo funcionan las etiquetas en el computador Hack, debido a que en los primeros intentos no se dio el resultado esperado debido a que las etiquetas no fueron llamadas en los lugares adecuados; sin embargo, después se siguió la lógica de que el programa solo saltara si detectaba que el número en el espacio de memoria era menor, de caso contrario solo seguiría con el curso normal del instructivo.

### Actividad 04

#### Implementación de un ciclo simple

_Crea un programa que use un ciclo para sumar los números del 1 al 5 y guarde el resultado en la dirección de memoria 12._
``` asm
@1
D=A
@0
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

El mayor reto de este programa era encontrar la manera de almacenar el resultado de la suma para poder continuar con los otros números, para esto en la dirección de memoria 0 se utilizó como contador para ir aumentando los números mientras que la memoria 1 almacenaba los resultados de las operaciones; Además cada que se repetía el LOOP se le restaba al dato almacenado en 0 el número 6, con el fin de que en el momento que se llegara al número 6 el programa dejará de sumar y pasará a la etiqueta END donde se almacenaba en resultado en la dirección de memoria 12.
