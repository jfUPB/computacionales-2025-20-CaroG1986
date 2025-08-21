# Unidad 3


## 🛠 Fase: Apply

### Actividad 06

Experimento con la cualculadora: 🍫

<img width="397" height="668" alt="image" src="https://github.com/user-attachments/assets/89a24aa9-2008-4f88-9366-5b3496644b77" />

<img width="398" height="666" alt="image" src="https://github.com/user-attachments/assets/0961f4aa-29b6-44cd-bc5d-e3100cc185dd" />

> Primero se obtiene el valor decimal 10 y despúes el valor decimal 20
> 
> **¿Cuál es la diferencia entre un constructor y un destructor en C++?**
> **Constructor:** Necesario para inicializar o crear objetos de una clase.
> **Destructor:** Este permite eliminar un objeto cuando se deja de usar para liberar el espacio de memoria
>
> **¿Cuál es la diferencia entre un objeto y una clase en C++?**
> Una clase se trata de un conjunto de objetos que cumplen con ciertas carateristicas porteriormente definidas en esta, mientras que un objeto es una creación con estas caracteristicas pero un espacio de memoria aparte de la clase.
>
>**¿Qué diferencia notas entre el objeto Punto en C++ y C#?**
> En c# se usa "new" lo que significa que el objeto fue inicializado en el heap, en cambio en c++ se crea directamente en el stack.
>
> **¿Qué es p en C++ y qué es p en C#? (en uno de ellos p es un objeto y en el otro es una referencia a un objeto).**
> En c++ es un objeto como tal, pero en c# es una referencia del objeto en el heap
>
> **¿En qué parte de memoria se almacena p en C++ y en C#?**
> En c++ p se almacena en el stack, mientras que en c# la variable p se almacena en el stack pero el objeto como tal esta en el heap
>
> **¿Qué observaste con el depurador acerca de p? Según lo que observaste ¿Qué es un objeto en C++?**
> Ya que en este caso se vió como p tenía una dirrección fija, se puede suponer que un obejto en c++ es una zona de memoria estableciada y no una referecia a otra dirección.
>
### Actividad Integradora de Aplicación

**Código problemático:**

``` c++
#include <iostream>
#include <string>

class Personaje {
public:
    std::string nombre;
    int* estadisticas;

    Personaje(std::string n, int vida, int ataque, int defensa) {
        nombre = n;
        estadisticas = new int[3];
        estadisticas[0] = vida;
        estadisticas[1] = ataque;
        estadisticas[2] = defensa;
        std::cout << "Constructor: nace " << nombre << std::endl;
    }

    void imprimir() {
        std::cout << "Personaje " << nombre
            << " [Vida: " << estadisticas[0]
            << ", ATK: " << estadisticas[1]
            << ", DEF: " << estadisticas[2]
            << "]" << std::endl;
    }
};

void simularEncuentro() {
    std::cout << "\n--- Iniciando encuentro ---" << std::endl;
    Personaje heroe("Aragorn", 100, 20, 15);

    Personaje copiaHeroe = heroe;
    copiaHeroe.nombre = "Copia de Aragorn";

    std::cout << "Saliendo del encuentro..." << std::endl;
}

int main() {
    simularEncuentro();
    std::cout << "\nSimulación terminada." << std::endl;
    return 0;
}
```

**1.Diagnóstico del problema (análisis):** 🍰

>Identifica y explica con detalle al menos dos errores críticos de gestión de memoria en la clase Personaje y su uso en simularEncuentro.

- El error mas crítico en la gestión de memoria es que en un punto se inicializa una variable en el heap y esta no se borra después. Esto se ve en la clase de personaje de esta manera:

``` c++
class Personaje {
public:
    std::string nombre;
    int* estadisticas;

    Personaje(std::string n, int vida, int ataque, int defensa) {
        nombre = n;
        estadisticas = new int[3];//NUNCA SE ELIMINA, ES DECIR, FALTA DELETE
        estadisticas[0] = vida;
        estadisticas[1] = ataque;
        estadisticas[2] = defensa;
        std::cout << "Constructor: nace " << nombre << std::endl;
    }
```
> ¿Por qué ocurre?
> 
Esto ocurre porque la variable estadisticas al usar el new se esta almacenando en la dirección de memoria de heap, loq ue significa que no se puede eliminar por si sola, si no que debe tener un delete que se encarge de liberar ese espacio

>¿Cúal es su consecuencia?
>
En este caso el no corregir puede causar que a futuro el juego consuma una tanta RAM que colapse.

- El error en simular encuentro se da ya que se busca modificar heroe usando su valor en lugar de una referencia o puntero, por ende se crea una copia de la variable y la original queda igual. Esto se ve en esta parte:

``` c++
void simularEncuentro() {
    std::cout << "\n--- Iniciando encuentro ---" << std::endl;
    Personaje heroe("Aragorn", 100, 20, 15);

    Personaje copiaHeroe = heroe; //ESTA LLAMANDO AL VALOR
    copiaHeroe.nombre = "Copia de Aragorn"; 

    std::cout << "Saliendo del encuentro..." << std::endl;
}
```
>¿Por qué ocurre?
>
Porque se esta igualando la copiaheroe con el valor de heroe, cuando copia de heroe se trata de un objeto nuevo de la clase personaje, por lo que debería tener su propio constructor

>¿Cuál es su consecuencia?
>
Si no se cambia esto a la hora de borrar o liberar la información de uno de los objetos, el que llama al valor del otro estaría apuntando a un valor inexistente, lo cual daría un error. Pero dejando la eliminación de lado, esto también esta gastando memoria donde no se almacena nada.

**2.Solución y refactorización (síntesis y creación):** 🍾

``` c++
#include <iostream>
#include <string>

class Personaje {
public:
    std::string nombre;
    int* estadisticas;

    Personaje(std::string n, int vida, int ataque, int defensa) {
        nombre = n;
        estadisticas = new int[3];
        estadisticas[0] = vida;
        estadisticas[1] = ataque;
        estadisticas[2] = defensa;
        std::cout << "Constructor: nace " << nombre << std::endl;
    }
	~Personaje() {
		std::cout << "Destructor: muere " << nombre << std::endl;
		delete[] estadisticas;
	}

    void imprimir() {
        std::cout << "Personaje " << nombre
            << " [Vida: " << estadisticas[0]
            << ", ATK: " << estadisticas[1]
            << ", DEF: " << estadisticas[2]
            << "]" << std::endl;
    }
};

void simularEncuentro() {
    std::cout << "\n--- Iniciando encuentro ---" << std::endl;
    Personaje heroe("Aragorn", 100, 20, 15);

    Personaje copiaHeroe("Copia de Aragorn", heroe.estadisticas[0], heroe.estadisticas[1], heroe.estadisticas[2]);

	heroe .imprimir(); 
	copiaHeroe.imprimir();
    std::cout << "Saliendo del encuentro..." << std::endl;
}

int main() {
    simularEncuentro();
    std::cout << "\nSimulación terminada." << std::endl;
    return 0;
}
```

**3.Justificación de la Solución:** 🍡

Básicamente hice dos cambios grandes lo cuales fueron agregar un destructor para que se eliminara la memoria en heap y darle los parámetros la copiaHeroe de forma individual a el objeto heroe, y esto soluciono el problema porque evito el gasto excesivo de memoria, además de crear ambos objetos aparte ayuda para poder manipularlos y eliminarlos por separado y así no hay problemas en la lógica del código a futuro.
