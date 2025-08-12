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

(TERMINAR)

``` c++
#include <iostream>

using namespace std;

// Función que modifica el parámetro pasado por valor
void swapPorValor(int a, int b) {
    cout << "Dentro de modificarPorValor, valor inicial de b: " << b << "Valor inicial de a"<< a << endl;
    int tmp = b;
    b = a;
    a = tmp;
    cout << "Dentro de swapPorValor, valor modificado: " << a <<","<< b << endl;
}

// Función que modifica el parámetro pasado por referencia
void modificarPorReferencia(int& n, int& m) {
    cout << "Dentro de modificarPorReferencia, valor inicial: " << n << endl;
    n += 5;
    cout << "Dentro de modificarPorReferencia, valor modificado: " << n << endl;
}

// Función que modifica el parámetro utilizando punteros
void modificarPorPuntero(int* n, int* m) {
    cout << "Dentro de modificarPorPuntero, valor inicial: " << *n << endl;
    *n += 5;
    cout << "Dentro de modificarPorPuntero, valor modificado: " << *n << endl;
}

int main() {
    int a = 10;
    int b = 20;

    cout << "Valor inicial de a (paso por valor): " << a << " y el valor inicial de b (paso por valor) "<< b << endl;
    cout << "Valor inicial de a (paso por referencia): " << a << "y el valor inicial de b (paso por referencia)"<< b << endl;
    cout << "Valor inicial de a (paso por puntero): " << a << "y el valr inicial de b (paso por puntero)" << b << endl;

    cout << "\nLlamando a modificarPorValor(a)..." << endl;
    swapPorValor(a,b);
    cout << "Después de modificarPorValor, valor de a,b: " << a << "," << b << endl;

    cout << "\nLlamando a modificarPorReferencia(b)..." << endl;
    modificarPorReferencia(a,b);
    cout << "Después de modificarPorReferencia, valor de b: " << b << endl;

    cout << "\nLlamando a modificarPorPuntero(&c)..." << endl;
    modificarPorPuntero(&a,&b);
    cout << "Después de modificarPorPuntero, valor de c: " << a << endl;

    return 0;
}
```
