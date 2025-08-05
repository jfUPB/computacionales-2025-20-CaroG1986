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
Si se implementa el programa anterior en lenguaje ensamblador se vería así:
```asm
@ARR
D=A
@0
M=D
A=D
M=1
(LOOP)
@0
M=D+1
A=M
D=M+1
M=D
D=A
@LOOP
0;JMP
```
```asm
@1
D=A
@ARR
M=D
@ARR
D=A
@0
M=D
(LOOP)
@0
A=A+1
D=A
D=D+1
@0
A=M+1
M=D
@LOOP
0;JMP
```
