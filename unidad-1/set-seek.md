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

Los datos que se almacenan en la memoria ROM son las instrucciones que se pueden agregar en diferentes lenguajes (en este caso de ensamblador), pero el CPU lo leera en un codigo binario, en resumen son datos almacenados que solo se pueden leer. Mientras que la memoria RAM almacena los datos que surgen de la ejecución del programa, dicha memoria guarda variables, datos intermedios y estructuras como arreglos, y es la memoria principal del CPU, estos datos se pueden cambiar o modificar por que son temporales.

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
#### 🧐🧪✍️ Experimento 03 (observaciones)

Este programa llama tanto a la pantalla cómo al teclado, por lo que es válido suponer que en el momento de presionar alguna tecla va a ocurrir algún cambio visible en la pantalla. En este caso lo que ocurrió fue que cada vez que se le presiona una tecla la pantalla cambia de color a negro. Si se ve en una velocidad rápida parece que la pantalla cambia de color inmediatamente, sin embargo al verlo a una velocidad normal es posible ver como cambia la pantalla pixel por pixel.

#### Identifica una instrucción que use la ALU y explica qué hace.

Las instrucciones ALU son aquellas encargadas de las operaciones aritmérticas y lógicas en el programa. Un ejemplo de estas instrucciones en el ejercicio anterior sería el siguiente: 

```asm
D=D-A
```
En este se almacena en el registro D la diferencia entre el registro D actual y el registro A, siendo la instrucción ALU la resta.

#### ¿Para qué sirve el registro PC?

El registro PC es el contador del programa. Dicho registro guarda la dirección de la próxima instrucción, es decir, permite identificar el orden en el cual se ejecuta el programa.

#### ¿Cuál es la diferencia entre @i y @READKEYBOARD?

La mayor diferencia entre los dos es el hecho de que @i es una variable que guarda datos mientras que @READKEYBORAD es una etiqueta que indica un punto para saltar dentro del código. La variable @i suele indicar un resgistro en RAM despúes de RAM [16] o el siguiente disponible, y en este programa lo usa para cambiar los valores a partir de la dirección de la pantalla a -1, lo que pinta los pixeles a negro. La etiqueta @READKEYBOARD regresa el código a lo que esté después de la etiqueta (READKEYBOARD).

#### Describe qué se necesita para leer el teclado y mostrar información en la pantalla.

Primero para leer el teclado necesita ir a la dirección de memoria @KBD (RAM [24576]) y en caso de que se presione una tecla el número que representa dicha tecla se verá en el espacio de memoria RAM del teclado. Por ejemplo al presionar la tecla espacio se vería así:

<img width="402" height="46" alt="image" src="https://github.com/user-attachments/assets/f63ffd0d-1b18-407f-9f59-0af75c86aa43" />

Después para mostrar información en la pantalla se llama a la dirección de memoria @SCREEN (RAM[16384–24575]) y en este segmento se cambian los datos para presentar el resultado en pantalla. En este caso se cambia a M=-1 lo cual indica que se pintan los pixeles de negro. Después se regresa en los pixeles y los devuelve a su color original, así:

<img width="1101" height="363" alt="image" src="https://github.com/user-attachments/assets/b43827ea-9e6d-4a51-a64f-c47876b28054" />

#### Identifica un bucle en el programa y explica su funcionamiento.

En este programa hay dos bucles, pero como ejemplo vamos a usar el bucle con la etiqueta (READKEYBOARD), el cual siempre se encuentra activo, ya que la función de leer el teclado es una de las principales en este plantamiento. 

``` asm
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
```
Este bucle primero llama a la RAM del teclado, luego verifica si se esta presionando alguna tecla, en caso de ser así va al bucle (KEYPRESSED), si no hay nada presionado entonces borra la pantalla hasta que la pantalla está en blanco, cuando se borra el programa vuelve a iniciar el bucle.

#### Identifica una condición en el programa y explica su funcionamiento.

Es este programa hay varias condiciones y un ejemplo de estas JNE, la cual significa _"Jump if not equal"_, es decir, que salte si dato ≠ 0. En este caso se utiliza para decir que vaya el bucle (KEYPRESSED) si se oprime alguna tecla (D ≠ 0), en caso contrario sigue en bucle actual.
