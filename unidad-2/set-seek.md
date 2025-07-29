# Unidad 2

## 🔎 Fase: Set + Seek

### Actividad 01

El código ensamblandor sería el siguiente 🐤

``` asm
@SCREEN
M=1
```

Para este código primero se penso en el resultado que se quería lograr el cual era poner un 1 en la posición de @SCREEN, y después se llamo la dirección. En la siguiente imagen se muestra como se ejecutó el programa.

<img width="894" height="330" alt="image" src="https://github.com/user-attachments/assets/738f99c8-08b3-4872-9273-b958a179b5bf" />

#### ¿Cómo se vería en c++? 

``` c++
screen = 1; // Suponiendo que screen ya tiene asignada la dirección de memoria -> 16384
```

### Actividad 02

El código ensamblandor sería el siguiente 🐤

``` asm
@SCREEN
M=-1
```

Para este codigo era necesario que en el codigo binario tiodo fuera un uno, es decir, la mejor forma de hacerlos sería si se ingresa el número -1 en la dirección de menoria @SCREEN, lo cual llenaba los 16 pixeles de esta posición de color negro. 

<img width="881" height="329" alt="image" src="https://github.com/user-attachments/assets/f7902286-65ac-42f0-8e7d-2cfbb299f803" />

#### ¿Cómo se vería en c++? 

``` c++
screen = -1; // Suponiendo que screen ya tiene asignada la dirección de memoria -> 16384
```
o también puede verse como

``` c++
screen = 0xFFFF; // Esto también combierte todos los números binarios en 1
```

### Actividad 03

El código ensamblandor sería el siguiente 🐤

``` asm
@SCREEN
M=-1
@CONTADOR
M=0

(LEER)

@KBD
D=M
//la letra d tiene codigo 100 y la i tiene codigo 105
@100
D=D-A
@DERECHA
D;JEQ

@KBD
D=M
//la letra d tiene codigo 100 y la i tiene codigo 105
@105
D=D-A
@IZQUIERDA
D;JEQ

@LEER
0;JMP

(DERECHA)

//DIRECCION SCREEN + N
//BORRO LA POSICION ACTUAL
@CONTADOR
D=M
@SCREEN
A=D+A
M=0
//
@CONTADOR
M=M+1
D=M
@SCREEN
A=D+A
M=-1

@LEER
0;JMP

(IZQUIERDA)
@CONTADOR
D=M
@SCREEN
A=D+A
M=0
//
@CONTADOR
M=M-1
D=M
@SCREEN
A=D+A
M=-1

@LEER
0;JMP
```

<img width="881" height="292" alt="image" src="https://github.com/user-attachments/assets/c607473b-3ecd-4450-b350-febe793f91ef" />

Para este código primero se verifico que se pintara la linea en la pantalla, después que se moviera a la derecha o a la izquierda aumentando el contador para que suba a otra dirección de memoria, finalmente se programo para que respondiera a las direcciones de teclado correspondientes a las teclas "i" y "d", para que así la linea se mueva según lo indicado.

#### ¿Cóme se vería esto en c++?
