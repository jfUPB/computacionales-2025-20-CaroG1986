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

**Experimento 4:** No se pudo modificar la variable debido a que esta indicada como una variable estatica. Por ende no se puede acceder para escritura ni para lectura.

**Experimento 5:** La variable estatica si aumento, an cambio la no estatica siempre fue 100. Esto puede ser debido a que la variable no estatica se mantiene solo en el espacio de variables locales.

**Experimento 6:** En esta parte del código se usa new y delete para generar y liberar espacio en la memoria del Heap.

### Actividad 05

Según el siguiente código: 🧃

``` python
#include <iostream>

int contador_global = 100;

void ejecutarContador() {
    static int contador_estatico = 0;
    contador_estatico++;
    std::cout << "  -> Llamada a ejecutarContador. Valor de contador_estatico: " << contador_estatico << std::endl;
}

void sumaPorValor(int a) {
    a = a + 10;
    std::cout << "  -> Dentro de sumaPorValor, 'a' ahora es: " << a << std::endl;
}

void sumaPorReferencia(int& a) {
    a = a + 10;
    std::cout << "  -> Dentro de sumaPorReferencia, 'a' ahora es: " << a << std::endl;
}

void sumaPorPuntero(int* a) {
    *a = *a + 10;
    std::cout << "  -> Dentro de sumaPorPuntero, '*a' ahora es: " << *a << std::endl;
}

int main() {
    int val_A = 20;
    int val_B = 20;
    int val_C = 20;

    std::cout << "--- Experimento con paso de parámetros ---" << std::endl;
    std::cout << "Valor inicial de val_A: " << val_A << std::endl;
    sumaPorValor(val_A);
    std::cout << "Valor final de val_A: " << val_A << std::endl << std::endl;

    std::cout << "Valor inicial de val_B: " << val_B << std::endl;
    sumaPorReferencia(val_B);
    std::cout << "Valor final de val_B: " << val_B << std::endl << std::endl;

    std::cout << "Valor inicial de val_C: " << val_C << std::endl;
    sumaPorPuntero(&val_C);
    std::cout << "Valor final de val_C: " << val_C << std::endl << std::endl;

    std::cout << "--- Experimento con variables estáticas ---" << std::endl;
    ejecutarContador();
    ejecutarContador();
    ejecutarContador();

    return 0;
}
```

**¿Cuál será la salida final en la consola de este programa?**

Para mi al final el programa se vería como uno de los primeros ejercicios que hicimos, en donde veíamos como se comportaban las variables según el parametro que se llamara en la función. Por ejemplo, en el primer que es por valor no cambiaria la viariable original, sin embargo en los otros dos el valor original si cambiará. Por otro lado el valor de la variable estatica tambien va a cambiar con la función ejecutar contador.

**Escribe la salida completa que esperas.**

Valor original de A: 20

Dentro de sumar por valor: 30

Valor final de A: 20

Valor original de B: 20

Dentro de sumar por referencia: 30

Valor final de B: 30

Valor original de C: 20

Dentro de sumar por puntero: 30

Valor final de C: 30

VARIABLE_ESTATICA=1

VARIABLE_ESTATICA=2

VARIABLE_ESTATICA=3

**Dibuja un mapa de memoria conceptual de este programa justo antes de que main finalice.**

<img width="438" height="628" alt="image" src="https://github.com/user-attachments/assets/fd747775-700a-4381-9351-126482ff5e38" />

**Compara la salida real con tu predicción**

La salida fue la siguiente:

<img width="739" height="690" alt="image" src="https://github.com/user-attachments/assets/7619e094-13be-42fb-b9ce-cfe201dfb753" />

Al compararlas siento que no hay mucha diferencia en cuanto los valores esperados, creo que la diferencia principal se encuentra en la presentación, sin embargo se podría decir que mi predicciónn fue acertada. Entonces como un analisis más detallado tenemos que:

**Primero en suma por valor**

Antes:

<img width="554" height="61" alt="image" src="https://github.com/user-attachments/assets/0a115158-e41a-4b94-ab0e-1fcabb678dc9" />

Despúes:

<img width="555" height="108" alt="image" src="https://github.com/user-attachments/assets/e30af366-4e89-4f65-85f3-d395ec9142bb" />

**Ahora suma por referencia**

Antes:

<img width="567" height="87" alt="image" src="https://github.com/user-attachments/assets/e259b89f-a2b2-44a1-841d-1d87093a6186" />

Despúes:

<img width="573" height="121" alt="image" src="https://github.com/user-attachments/assets/550adfdc-317b-4a8c-8bc4-da96fa9810fb" />

**Por último, suma por puntero**

Antes:

<img width="550" height="97" alt="image" src="https://github.com/user-attachments/assets/ae7fc64c-48e5-431d-a2c7-0e5fd8b6dd41" />

Despúes:

<img width="557" height="114" alt="image" src="https://github.com/user-attachments/assets/d3ac7885-886c-48e7-9623-6ed007486a16" />

**Describe qué demuestran estas capturas sobre la diferencia entre los diferentes tipos de paso por parámetros analizados.**

Estas capturas demuestran la importancia que saber que llamar para poder modificar una variable. Iniciando por el valor, al llamarlo solo se va a modificar la variable local que esta en la función sumaPorValor, pero al usar la suma por referencia esta llama a la variable val_B directamente como si lo hiciera con un apodo, y al usar el puntero se llama a modificar lo que este en la dirección de memoria de la variable val_C, cambiado en si el valor de la variable.

**Explica con tus propias palabras el comportamiento de contador_estatico. ¿Por qué “recuerda” su valor entre llamadas a la función ejecutarContador? ¿En qué se diferencia de una variable local normal?**

Este lo recuerda ya que esta en la sección de memoria de variables globales y estaticas, las cuales almacenan su información sin depender de una función, es decir, que su memoria no se borra despúes. Es por esto que almacena la información del último cambio que se le fue realizado.
