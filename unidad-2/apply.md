# Unidad 2

## 🛠 Fase: Apply

### Actividad 06 

El enunciado es:
```c++
int arr[] = {1,2,3,4,5,6,7,8,9,10};
int sum = 0;

for (int j = 0; j < 10; j++) {
    sum = sum + arr[j];
}
```
Primero hice una prueba para generar el arreglo, en esta prueba verifique si podía crear un arreglo usando el @0 como puntero y el @1 para almacenar el último número del arreglo: 🥦
```asm
@ARR
D=A
@0
M=D
A=D
M=1 //Hasta aqui la idea es iniciar la dirección del arreglo y poner en la primera dirección el 1
(LOOP)
A=D
D=M
@1
M=D //Aqui se inicia el @1 para almacenar el ultimo valor
@0
D=M
M=D+1 //aqui se aumenta el valor del puntero
@1
D=M+1 //aqui se aumenta el ultimo valor del arreglo
M=D //se guarda esto en la memoria
@0
A=M
M=D //aqui se guarda el ultimo número en la dirección de memoria siguiente del arreglo
D=A
@1
D=M+1 //Esto sobra porque esta sumando dos veces en el mismo ciclo
M=D
@1
D=M //Esto también sobra porque ya la D es igual a la dirección de memoria
@10
D=D-A //esto es para verificar que no se pasa de 10
@END
D;JGT
@1
D=M // para que D vuelva a ser el último múmero
@0
A=M //Para que A siga al puntero
D=A // Almacenar el valor del puntero en D
@LOOP
0;JMP
(END)
```
Sin embargo, este código al revisarlo mejor me di cuenta que, a pesar de funcionar, tenía muchos errores en el orden y partes que sobraban, así que decidí seguir la idea del puntero y el almacen de los números pero por partes: 🫐
``` asm
//En esta primera parte llame a la dirección de memoria del arreglo para iniciar el puntero y después guardar en @1 los valores del arreglo
@ARR
D=A
@0
M=D
@1
M=1
(LOOP)
//Primero verificar que no sea mayor a 10
@1
D=M
@10
D=D-A
@END
D;JGT
//Despúes guarde el valor que tengo en @1 en el arreglo
@1
D=M
@0
A=M
M=D
//sumarle 1 al valor que tengo en @1 
@1
M=M+1
// Sumarle también la puntero para que se almacenen lo números en otras direcciones de memoria
@0
M=M+1
@LOOP
@1
D=M
0;JMP
(END)
```
Aquí lo que hice fue agrupar las partes que antes se encargaban de ciertas labores, por ejemplo, poner en una sola parte el aumentar el último númeRO del arreglo en lugar de repetirlo dos veces, y ahora voy a usar el @2 para almacenar la suma deL arreglo: 🌯
``` asm
@ARR
D=A
@0
M=D
@1
M=1
@2
M=0
(LOOP)
@1
D=M
@10
D=D-A
@END
D;JGT
@1
D=M
@0
A=M
M=D
//Almacenar la suma del arreglo
@2
M=D+M
@1
M=M+1
@0
M=M+1
@1
D=M
@LOOP
0;JMP
(END)
```
Ahora en la dirección de memoria 2 se almacena la suma de los números en el arreglo y así se ve en el programa: 🥑

<img width="369" height="119" alt="image" src="https://github.com/user-attachments/assets/e0ca23aa-50d0-4bcc-830a-46243a73d017" />

<img width="380" height="426" alt="image" src="https://github.com/user-attachments/assets/639c8917-c078-4440-8f65-0b3db32e18f3" />

