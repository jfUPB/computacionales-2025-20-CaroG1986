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

#### ¿Cóme se vería esto en  c++?

``` c++

 int SCREEN;
int contador = 0;
int pantalla[SCREEN]=-1;

int main ()
{
 for (int i=0; i < SCREEN; i ++)
 pantalla [contador] = -1;

 while (1){
  int tmp = KBD;
  if ( tmp == 100)
 {
   pantalla [contador+SCREEN]= 0;
   contador ++;
   pantalla [contador+SCREEN]= -1;
 }
 else if (tmp== 105)
 {
   pantalla [contador+SCREEN] = 0;
   contador --;
   pantalla [contador+SCREEN]= -1;
 }
}
return 0;
}

### Actividad 04

Entonces ahora para el siguiente ciclo for

``` c++
//Adds 1+...+100.
int sum=0;
for(int i = 1; i <=100; i++){
   sum+= i;
}
```
### Actividad 04

``` asm
// Adds1+...+100.
 @i // i refers to some memory location.
 M=1 // i=1
 @sum // sum refers to some memory location.
 M=0 // sum=0
 (LOOP)
 @i
 D=M // D=i
 @100
 D=D-A // D=i-100
 @END
 D;JGT // If(i-100)>0 gotoEND
 @i
 D=M // D=i
 @sum
 M=D+M // sum=sum+i
 @i
 M=M+1 // i=i+1
 @LOOP
 0;JMP // GotoLOOP
 (END)
 @END
 0;JMP // Infinite loop
```
<img width="853" height="213" alt="image" src="https://github.com/user-attachments/assets/9ff1dc83-d544-416a-9b6f-db68d4e36e41" />

_Así se ve el programa 🐤_

Estos dos ciclos son equivalentes ya que cumplen la misma función y para ser representados en asm es necesario usar las mismas lineas de código. Además ambos indican lo mismo, es decir , que se continuara el ciclo hasta llegar a 100.

### Actividad 05 

_nota: "&" es para invocar una dirección_
_nota: para leer con el puntero sería_
``` c++
int j= *ptr; // *ptr es el punteroen este caso
```
_nota: para escribir con el puntero sería_
``` c++
*ptr=25 // se escribe en el puntero el valor que se quiere ingresar
```
 El enunciado es 🐤
``` c++
int a = 10;
int* p;
p = &a;
*p = 20;
```
Para esta actividad la solución sería la siguiente:
``` asm
@10
D=A
@a
M=D
@a
D=A
@P
M=D
@20
D=A
@P
A=M
M=D
```
Aquí como se ve se usa el puntero para cambiar los datos en la dirección de memoria a usando un puntero o variable.

El siguiente enunciado es 🐤
``` c++
int a = 10;
int b = 5;
int *p;
p = &a;
b = *p;
```
Para esta actividad la solución sería la siguiente:

``` asm
@10
D=A
@a
M=D
@5
D=A
@b
M=D
@a
D=A
@P
M=D
@a
D=M
@P
A=M
M=D
@b
M=D
```

En este código primero se dió los valores para las posiciones a y b, después se le dió al puntero P la dirección de memoria de a, se leyó el valor que estaba en la dirección de memoria de a y finalmente se le dió este valor a través del puntero a la posición b.
