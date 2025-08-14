# Unidad 3

## 🔎 Fase: Set + Seek

### Actividad 01

**¿Para qué sirven los breakpoints?**

Sirve para detener un programa en algún punto, paa así poder enfocarse en este.

**¿Para qué se usa la ventana de depuración Autos?**

Esta sirve para ver como las variables locales se instancian, es decir, poder ver como se representan los valores en las variables.

### Actividad 02

Nota: Por valor crea una nueva variable y guarda el nuevo valor en esta, si embargo no cambia la variable original

Nota: La referencia llama a la variable original

Nota: El puntero llama a la dirección de memoria original y la modifica.


``` c++
#include <iostream>

using namespace std;

// Función que modifica el parámetro pasado por valor
void swapPorValor(int a, int b) {
    cout << "Dentro de swapPorValor, valor inicial de a: " << a << " Valor inicial de b: " << b << endl;
    int tmp = b;
    b = a;
    a = tmp;
    cout << "Dentro de swapPorValor, valor modificado a: " << a << " ,b: " << b << endl;
}

// Función que modifica el parámetro pasado por referencia
void swapPorReferencia(int& a, int& b) {
    cout << "Dentro de swapPorReferencia, valor inicial de a: " << a << " Valor inicial de b: "<< b << endl;
	int tmp = b;
	b = a;
	a = tmp;
    cout << "Dentro de swapPorReferencia, valor modificado de a: " << a << "Valor modificado de b: "<< b << endl;
}

// Función que modifica el parámetro utilizando punteros
void swapPorPuntero(int* a, int* b) {
    cout << "Dentro de swapPorPuntero, valor inicial a: " << *a << " y valor inicial  de b"<< *b << endl;
	int tmp = *b;
	*b = *a;
	*a = tmp;
    cout << "Dentro de swapPorPuntero, valor modificado de a: " << *a << " Valor modificado de b: "<< *b <<endl;
}

int main() {
    int a = 10;
    int b = 20;

    cout << "Valor inicial de a (paso por valor): " << a << " y el valor inicial de b (paso por valor) " << b << endl;
    cout << "Valor inicial de a (paso por referencia): " << a << " y el valor inicial de b (paso por referencia) " << b << endl;
    cout << "Valor inicial de a (paso por puntero): " << a << " y el valor inicial de b (paso por puntero) " << b << endl;

    cout << "\nLlamando a swapPorValor(a)..." << endl;
    swapPorValor(a, b);
    cout << "Después de swapPorValor, valor de a,b: " << a << " , " << b << endl;

    cout << "\nLlamando a swapPorReferencia(b)..." << endl;
    swapPorReferencia(a, b);
    cout << "Después de swapPorReferencia, valor de a,b: " << a <<" , " <<b << endl;

    cout << "\nLlamando a swapPorPuntero(&c)..." << endl;
    swapPorPuntero(&a, &b);
    cout << "Después de swapPorPuntero, valor de a: " << a << " y valor modificado de b: "<< b << endl;

    return 0;
}
```

### Actividad 04

Realizar los siguientes experimentos en el código anterior

**Experimento 1:** sale una excepción ya que esta intentando modificar el área de solo lectura, en este caso, la función main.

**Experimento 2:** No se puede hacer tampoco ya que intenta modificar una constante

**Experimento 3:** al inicio la variable inicializada se ve con el número asignado y la no inicializada tiene un 0. Después la variable inicializada cambia de número al igual que la inicializada.

**Experimento 4:** No se pudo modificar la variable dibido a que esta indicada como una variable estatica. Por ende no se puede acceder para escritura ni para lectura.

**Experimento 5:** (TERMINAR)
