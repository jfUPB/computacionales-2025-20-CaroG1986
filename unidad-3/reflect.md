# Unidad 3


## 🤔 Fase: Reflect

### Actividad 11

**Parte 1: recuperación de conocimiento (Retrieval Practice)**

*1.Explica con tus propias palabras qué es el stack y qué es el heap en C++.*

Ambas con partes de la memoria, sin embargo se diferencian porque el stack almacena las variables locales y el heap almacena la información dinamica, la cual se debe inicializar y eliminar para poder administrarla en la memoria.

*2.Describe las tres formas de pasar parámetros a una función en C++ (valor, referencia y puntero). Para cada una, explica qué sucede en memoria y cuándo usarías cada método.*

-Valor: Al llamar algo por el valor se copia la variable en una nueva, por lo que la variable original no se modifica. Este método lo usaría en el caso de querer cambiar un valor dentro de una función pero que este no afecte su valor original.

-Referencia: Esta referencia llama a la misma variable pero con un alias, es decir que el la memoria se modificaría el valor de la original. Este método es util para poder cambiar el valor de la variable original.

-Puntero: Los punteros llaman a una dirección de memoria y modifican lo que este dentro de esta. Este método como el anterior es usado para poder cambiar el valor de la variable original.

*3.¿Qué diferencia hay entre una variable local, una variable global y una variable local estática? ¿En qué segmento del mapa de memoria se almacena cada una?*

Una variable local es aquella que solo se encuentra dentro de una función y se almacena en la memoria stack; por otro lado las variables globales y locales estaticas se almacenan en una dirección de memoria especial para estas, donde siguen existiendo sin importar la parte del programa donde se llamen.

*4.Explica qué es un objeto en C++ desde la perspectiva de memoria. ¿Dónde se almacenan los miembros de instancia y dónde los miembros estáticos?*

Un objeto es una dirección de memoria donde se almacenan ciertos parámetros que lo identifican. Los miembros de instancia, como dice su nombre, deben ser instanciados y por ende eliminados por lo que hacen parte de la memoria heap, mientras que los miembros estaticos existen durante todo el programa, así que se almacenan en la memoria de variables globales y estaticas.

**Parte 2: transferencia y análisis de situación nueva**

``` c++
#include <iostream>
using namespace std;

class Enemigo {
public:
    static int totalEnemigos;
    int vida;
    int* armas;

    Enemigo(int v) : vida(v) {
        totalEnemigos++;
        armas = new int[3];
        armas[0] = 10; armas[1] = 15; armas[2] = 20;
    }
};

int Enemigo::totalEnemigos = 0;

void crearEscuadron() {
    for(int i = 0; i < 5; i++) {
        Enemigo soldado(100);
        soldado.vida -= 10;
    }
    cout << "Escuadrón creado. Total enemigos: " << Enemigo::totalEnemigos << endl;
}

int main() {
    crearEscuadron();
    crearEscuadron();
    return 0;
}
```

*5.Análisis de problemas:*

-Primer problema: No hay destructor para limpiar de la memoria de los miembros instanciados, esto puede puede ser problematico por que a medida de que el juego avance esto podría consumir una enorme cantidad de RAM.

-Segundo problema: Se supone que al crear un nuevpo escuadron se destuyo en anterior para que esto no se acomule y ocupe más espacio en la memoria, sin embargo esto no pasa.

*6.Predicción de comportamiento:*

Al final del programa el total de enemigos mostrará el número 10, ya que esta sumando todos los enemigos sin importar si ya se borró su escuadron.

*7.Propuesta de solución:*

``` c++
class Enemigo {
public:
    static int totalEnemigos;
    int vida;
    int* armas;

    Enemigo(int v) : vida(v) {
        totalEnemigos++;
        armas = new int[3];
        armas[0] = 10; armas[1] = 15; armas[2] = 20;
    }

    ~Enemigo() {

        delete[] armas;
    }
}
```

**Parte 3: reflexión metacognitiva**

*8.De todos los conceptos que exploraste en esta unidad (stack vs heap, paso de parámetros, ciclo de vida de objetos, etc.), ¿Cuál consideras que es el más crítico para evitar errores en programas reales? ¿Por qué?*

Creo que el concepto más fundamental para evitar errores es comprender bien el paso de parámetros, ya que este puede ser el más confuso en ciertos casos.

*9.¿Cómo cambió tu comprensión sobre lo que realmente es un “objeto” después de comparar C++ con C#? ¿Qué implicaciones prácticas tiene esta diferencia?*

Cambió ya que ahora puedo comprender en que parte de memoria se esta almacenando este objeto y cual es su ciclo de vida en caso de crear un programa que lo necesite.

*10.Si tuvieras que explicar a un compañero de semestres anteriores por qué es importante entender la gestión de memoria en programación, ¿Qué le dirías en máximo 3 oraciones?*

Le diria que si no se comprende la gestión de memoria esto puede cuasar problemas como errores de copilación, uso exagerado de la memoria y un mal funcionamiento general del código.
