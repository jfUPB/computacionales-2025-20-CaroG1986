# Bitácora de aprendizaje de la unidad 5 

## 1.  **Diagnóstico inicial** 🧘‍♀️

### Parte 1 🕯️

**¿Qué es el encapsulamiento para ti? Describe una situación en la que te haya sido útil o donde hayas visto su importancia.**

El encapsulamiento es una forma de proteger el código para controlar los datos que se pueden cambiar o no de alguna parte, esto se hace con get y set, get para configurar la información que necesita el código y set para devolver lo que de cierta firma se pued "modificar" o leer. Personalmente, ha sido util cuando quiero que una variable de una clase no sea modificada, sino que se mantenga a través del código. 

**¿Qué es la herencia? ¿Por qué un programador decidiría usarla? Da un ejemplo simple.**

La herencia es un proceso en el cual clases hijas heredan las caracteristicas de una clase padre. Un programador podría usarla para asociar clases entre si y poder economizar código en clases con los mismos atributos. Por ejemplo: hay una clase padre llamada vehículos y esta tiene las siguientes clases hijas: Taxi, particular y bus; estas clases tienen características en común como sus partes y todas se pueden identificar como vehículos, sin embargo, también pueden tener ligeras diferencias como su tamaño o si es de ambito publico o privado.

**¿Qué es el polimorfismo? Describe con tus palabras qué significa que un código sea “polimórfico”.**

El polimorfismo es una caracteríatica que permite a alguna cosa ser capaz de adaptarse dependindo de la situación en la que este, algo así como un camaleon que se adapta según el ambiente. Cuando se describe un código como polimórfico normalmente nos referimos a que este es tan general que se puede adaptar, usando en mismo código para distintos resultados.

### Parte 2 🕯️

**Encapsulamiento**
> Señala una línea de código que sea un ejemplo claro de encapsulamiento y explica por qué lo es.
``` c#
  public string Nombre
    {
        get { return nombre; }
        protected set { nombre = value; }
    }
```
Este línea es claramente un encapsulamiento, debido a que se ve el uso de get-set y con esto se llama los datos que definen a "Nombre" y como van a estar representados para el resto del código.
>¿Por qué crees que el campo nombre es private pero la propiedad Nombre es public? ¿Qué problema se evita con esto?

Creo que la razón por la que el campo de nombre es private es porque este debe estar definido solo en la clase que la contiene y no deberia editarse fuera de este segmento, pero la propiedad Nombre es public para que use y muestre el nombre dependiendo de la clase en la que este, básicamente es gracias a esto que sin importar el caso da el nombre de la figura actual.

**Herencia**
>¿Cómo se evidencia la herencia en la clase Circulo?
``` c#
public class Circulo : Figura
{
    public double Radio { get; private set; }

    public Circulo(double radio) : base("Círculo")
    {
        this.Radio = radio;
    }

    public override void Dibujar()
    {
        Console.WriteLine($"Dibujando un {Nombre} de radio {Radio}.");
    }
}
```
En esta clase se ve evidenciada la herencia en tres partes, primero cuando se crea la clase se indica que esta hereda de la clase padre Figura, segundo cuando en el contructor se le da un valor a al atributo de la base llamado "Nombre", y tercero cuando sobre escribe el método "Dibujar" de la base.
>Un objeto de tipo Circulo, además de Radio, ¿Qué otros datos almacena en su interior gracias a la herencia?

Además del radio se almacena la variable de Nombre, la cual es un atributo heredado de la base.

**Polimorfismo**
>Observa el bucle foreach. La variable fig es de tipo Figura, pero a veces contiene un Circulo y otras un Rectangulo. Cuando se llama a fig.Dibujar(), el programa ejecuta la versión correcta. En tu opinión, ¿Cómo crees que funciona esto “por debajo”? No necesitas saber la respuesta correcta, solo quiero que intentes razonar cómo podría ser.
```c#
  foreach (Figura fig in misFiguras)
        {
            fig.Dibujar();
        }
```
 la verdad no estoy muy segura del funcionamiento pero supongo que dependiendo de la figura actual que este llamando, se usa el método "Dibujar", es decir, las figuras ya sean circulo o cuadrado toman el lugar de la variable fig en el for each.

 ### Parte 3 🕯️

 **Memoria y herencia: cuando creas un objeto Rectangulo, este tiene Base, Altura y también Nombre. ¿Cómo te imaginas que se organizan esos tres datos en la memoria del computador para formar un solo objeto?**

 <img width="407" height="244" alt="image" src="https://github.com/user-attachments/assets/20f7a29f-24d4-44ea-84bc-beaa40c81fa7" />

**El mecanismo del polimorfismo: pensemos de nuevo en la llamada fig.Dibujar(). El compilador solo sabe que fig es una Figura. ¿Cómo decide el programa, mientras se está ejecutando, si debe llamar al Dibujar del Circulo o al del Rectangulo? Lanza algunas ideas o hipótesis.**

Creo que esto se debe a la siguiente parte del código 
``` c#
  List<Figura> misFiguras = new List<Figura>();

        misFiguras.Add(new Circulo(5.0));
        misFiguras.Add(new Rectangulo(4.0, 6.0));
        misFiguras.Add(new Circulo(10.0));
```

**La barrera del encapsulamiento: ¿Cómo crees que el compilador logra que no puedas acceder a un miembro private desde fuera de la clase? ¿Es algo que se revisa cuando escribes el código, o es una protección que existe mientras el programa se ejecuta? ¿Por qué piensas eso?**

Creo que no se puede acceder ya que es una protección que se revisa cuando se escribe el código, ya que si al momento de escribir el código si se intenta llamar a una variable privada por fuera de donde esta contenida empiezan a salir errores.
 
## 2.  **La pregunta inicial**

¿Cómo implementa C++ el encapsulamiento a nivel copilador y memoria?

## 3.  **Registro de exploración:** 
> Aquí documentas cada ciclo de pregunta -> hipótesis -> experimento -> hallazgo -> reflexión.
> Debe ser rico en evidencia visual (código, capturas del depurador con anotaciones, diagramas).

### Actividad 02

<img width="1026" height="804" alt="image" src="https://github.com/user-attachments/assets/44379ba9-5683-4d5c-8fd7-bd378ca9bff7" />
<img width="1020" height="804" alt="image" src="https://github.com/user-attachments/assets/4eb9de07-1942-4d67-8b2a-7e4712bd3354" />

En este código primero en la parte de ofApp.h se crea una clase base tipo partícula, de la cual van a hace más partículas. Esta clase tiene un destructor y varios métodos entre los cuales está update, draw, IsDead, shouldExplode, getPosition y getColor. Entonces todas las clases heredan dichos métodos sí por su parte José pozo tributos como su posición, velocidad, color tiempo de vida o su estado (explotó o no). Finalmente crea los métodos que se van a utilizar en el programa para que este interactué el usuario como por ejemplo presionar una tecla o el mouse.

Ahora en la parte de ofApp.cpp Es dónde se definen estos métodos que fueron creados antes. Primero update, este actualiza lo que esté ocurriendo con las partículas desde que se crea hasta que explotan. Draw es simplemente para dibujar una partícula. createRisingParticle Crea una partícula y le da características aleatorias, como su tamaño, color, etc. Finalmente, mousePressed es para crear la partícula al presionar el mouse, keypressed para generar varias partículas a la vez o salavr una foto y hay un destructor que borra las partículas al final, esto me imagino que para no sobrecargar la memoria.

### Actividad 03

**Antes de ejecutar el experimento, ¿Qué esperas ver en memoria (hipótesis)? Ejecuta el código y muestra una captura de pantalla del objeto en la memoria. ¿Qué puedes observar? ¿Qué información te proporciona el depurador? ¿Qué puedes concluir?**

Espero que en la memoria se vea en donde estan almacenadas la variables y si los punteros que apuntan a las particulas si cumplen con la dirección de memoria necesaria.

<img width="1919" height="1022" alt="image" src="https://github.com/user-attachments/assets/94e730fc-b2af-4aac-98c8-a4e24ecc63cd" />

Al momento de ejecutar el código se puede ver el valor y el tipo de variable, además de su dirección en la memoria. Para esto puse el breakpoint en el método update y así poder ver como se veía en la memoria las particulas.

<img width="1161" height="313" alt="image" src="https://github.com/user-attachments/assets/ab4c904b-5d5d-4324-85bb-dfd2444303a0" />

Además si se revisa dentro de particula[i] (es decir el puntero que apunta a la clase particula) se puede ver otros atributos que la componen o definen y cual es su valor. Sin embargo, en cuanto a la memoria que se ve arriba, se ve un poco confuso que es lo que dice ahí y exactamente que me dice eso sobre el programa.

**¿Qué puedes observar en la memoria? ¿Qué información te proporciona el depurador? ¿Qué puedes concluir?**

<img width="1919" height="1020" alt="image" src="https://github.com/user-attachments/assets/e21e2dab-6330-4186-b53c-a156def3eac1" />

Al momento de hacer el experimento con clase de explosión circular esto es lo que me parece en la memoria, en realidad no comprendo muy bien el por qué sale como signos de interrogación, A pesar de ella tener una partícula creada como se puede ver en size=1. 

<img width="1919" height="1021" alt="image" src="https://github.com/user-attachments/assets/f1e29cdc-cee5-4f7b-be66-7148287b1597" />

Entonces volví a hacer el experimento ahora verificando que si esté bien seleccionado y eso es lo que me aparece en la memoria.

**Captura la _vtable de un objeto CircularExplosion, pega la imagen en tu bitácora, pero observa detenidamente la tabla de funciones. ¿Qué puedes observar?**

<img width="1312" height="411" alt="image" src="https://github.com/user-attachments/assets/0ef00441-7ef2-4b7a-ae26-29c46d63e256" />

Aquí se puede observar cómo la clase de explosión circular hereda de explosión de partícula, que al mismo tiempo hereda de partícula y ya dentro de este se ve cuáles son las características o métodos que esté hereda.

**Ahora, captura en memoria la _vtable de un objeto StarExplosion, pega la imagen en tu bitácora y observa detenidamente la tabla de funciones.**

<img width="1313" height="459" alt="image" src="https://github.com/user-attachments/assets/d2c873dc-bd02-497a-b879-57bf9c91855c" />

**Observa de nuevo ambas tablas y compara. ¿Qué puedes ver? ¿Qué puedes concluir? ¿Qué relación existe entre la tabla de funciones y los métodos virtuales? **

Al comparar ambas tablas puedo ver que aquí se evidencia el polimorfismo ya que en ambas se ven los mismos métodos pero algunos vienen directamente de la clase de círculo y estrella mientras otros vienen las clases bases

**¿Para qué crees que pueda servir una tabla de funciones virtuales?**

Yo creo que puede servir para comparar bien como se comporta la herencia y el polimorfismo en un programa, ya que gracias a este se pueden apreciar mejor sus atributos y métodos internos.

### Actividad 04

**¿Qué sucede? ¿Por qué sucede esto? ¿Qué puedes concluir?**

A realizar ese experimento cuando se llamó a la variable pública si se pudo ejecutar, sin embargo en estos dos casos no fue posible y creo que de eso se puede concluir que el llamar a una variable depende de su nivel de protección.

```C++
#include <iostream>

class MyClass {
private:
    int secret1;
    float secret2;
    char secret3;

public:
    MyClass(int s1, float s2, char s3) : secret1(s1), secret2(s2), secret3(s3) {}

    void printMembers() const {
        std::cout << "secret1: " << secret1 << "\n";
        std::cout << "secret2: " << secret2 << "\n";
        std::cout << "secret3: " << secret3 << "\n";
    }
};


int main() {
    MyClass obj(42, 3.14f, 'A');
    // Esta línea causará un error de compilación
    std::cout << obj.secret1 << std::endl;

    obj.printMembers();  // Método público para mostrar los valores
    return 0;
}
```
**¿Qué pasa?**

El programa no copila. Dice que no se puede obtener acceso a MyClass:Secret1.

``` c++
#include <iostream>

class MyClass {
private:
    int secret1;
    float secret2;
    char secret3;

public:
    MyClass(int s1, float s2, char s3) : secret1(s1), secret2(s2), secret3(s3) {}

    void printMembers() const {
        std::cout << "secret1: " << secret1 << "\n";
        std::cout << "secret2: " << secret2 << "\n";
        std::cout << "secret3: " << secret3 << "\n";
    }
};

int main() {
    MyClass obj(42, 3.14f, 'A');

    // Usando reinterpret_cast para violar el encapsulamiento
    int* ptrInt = reinterpret_cast<int*>(&obj);
    float* ptrFloat = reinterpret_cast<float*>(ptrInt + 1);
    char* ptrChar = reinterpret_cast<char*>(ptrFloat + 1);

    // Accediendo y mostrando los valores privados
    std::cout << "Accediendo directamente a los miembros privados:\n";
    std::cout << "secret1: " << *ptrInt << "\n";       // Accede a secret1
    std::cout << "secret2: " << *ptrFloat << "\n";     // Accede a secret2
    std::cout << "secret3: " << *ptrChar << "\n";      // Accede a secret3

    return 0;
}
```
**Compila el programa y ejecuta. ¿Qué puedes concluir?**

Que en este caso sí fue posible llamar a las variables debido a que no se llamaron directamente a las que estaban protegidas sino que se utilizaron punteros para de cierta forma violar el encapsulamiento en el que estás se encontraban

**En tus palabras, ¿Qué es el encapsulamiento? ¿Por qué es importante?**

El encapsulamiento es el protegar las variables que se usan en determinada clase o método. Este es importante ya que permite generar cierto nivel de protección a un dato para que no se pueda llamar o cambiar en cualquier parte del código.

>Ahora hice otro experimento para ver más a fondo el concepto del encapsulamiento
>```c++
>#include <iostream>
>using namespace std;
>
>class Persona {
>private:
>    int edad;       // privado
>protected:
>    double altura;  // protegido
>public:
>    string nombre;  // público
>
>    Persona(string n, int e, double a)
>        : nombre(n), edad(e), altura(a) {}
>
>    // Métodos públicos para acceder a lo encapsulado
>    int getEdad() const { return edad; }
>    double getAltura() const { return altura; }
>    void mostrarInfo() const {
>        cout << "Nombre: " << nombre
>             << " | Edad: " << edad
>             << " | Altura: " << altura << endl;
>    }
>};
>
>int main() {
>    Persona p("Carolina", 25, 1.68);
>    p.mostrarInfo();
>
>    // Intenta acceder directamente (NO compila):
>    // cout << p.edad;    // ❌ error: edad es privado
>    // cout << p.altura;  // ❌ error: altura es protegido
>
>    return 0;
>}
>```
><img width="1880" height="490" alt="image" src="https://github.com/user-attachments/assets/36b7c46b-d013-4e68-8caf-0cff8ccaa50d" />
>Cómo se puede ver dentro de la memoria se puede ver toda la información sobre la variables en el depurador, apesar de que estas sean privadas o no.
>Esto porque ahí se ve la memoria del objeto p en sí por lo que se rompe el encapsulamiento. Sin embargo si se intentará solo llamar a las variables por separado aparece un error de compilación por que en el coplilador se respetaría el encapsulamiento.
>En resumen, también me parece interesante que en el depurador se puede ver toda la memoria pero el copilador obedece las reglas del encapsulamiento.


### Actividad 05

**captura de nuevo la memoria que ocupa el objeto CircularExplosion compara la jerarquía de clases con los campos en memoria del objeto. ¿Qué puedes observar? ¿Qué información te proporciona el depurador? ¿Qué puedes concluir?** 

<img width="1313" height="519" alt="image" src="https://github.com/user-attachments/assets/2dabfe0b-a9b6-4283-939b-28f31528c34e" />

Cómo se ve es igual a lo que mencioné antes de que aquí se ven los métodos que está heredando la explosión circular ya sea desde la base directamente o los que sobre escribió para poder cambiar ciertos aspectos.

**¿Cómo se implementa la herencia en C++?**

La herencia en c++ se implementa mencioné antes por medio de la declaración de la herencia y también de lo que se ve en cuanto los métodos de atributos que tiene cada clase. Por ejemplo, qué es lo que dice el constructor de algo respecto al constructor de la base o los métodos que hayan y como estos se pueden sobreescribir para así lograr el polimorfismo. Y al momento de revisarlo en la memoria se puede ver en los métodos virtuales donde se ve con claridad que los métodos salen originalmente de una base y también donde se puede ver la jerarquía de las clases

**C++ permite hacer algo que C# no: herencia múltiple. Realiza un experimento que te permita ver cómo se objeto en memoria cuya clase base tiene herencia múltiple.**

``` c++
#include <iostream>
using namespace std;

class Motor {
public:
    Motor() { cout << "Motor construido\n"; }
    void encender() { cout << "Motor encendido\n"; }
    virtual void info() { cout << "Soy un Motor\n"; }
};

class Ruedas {
public:
    Ruedas() { cout << "Ruedas construidas\n"; }
    void rodar() { cout << "Las ruedas están rodando\n"; }
    virtual void info() { cout << "Tengo Ruedas\n"; }
};
class Coche : public Motor, public Ruedas {
public:
    Coche() { cout << "Coche construido\n"; }
    void info() override {
        cout << "Soy un Coche (Motor + Ruedas)\n";
    }
};
int main() {
    Coche miCoche;

    miCoche.encender();  // viene de Motor
    miCoche.rodar();     // viene de Ruedas
    miCoche.info();      // método sobreescrito en Coche

    // Polimorfismo desde punteros
    Motor* ptrMotor = &miCoche;
    Ruedas* ptrRuedas = &miCoche;

    cout << "\nPolimorfismo:\n";
    ptrMotor->info();   // Llama Coche::info
    ptrRuedas->info();  // Llama Coche::info

    return 0;
}
```

<img width="1309" height="415" alt="image" src="https://github.com/user-attachments/assets/0b6e1b7a-50e1-46ad-a9f1-44a546b05458" />
Lo que pude ver con ese experimento es que es cierto que c++ permite realizar herencia múltiple y al ver la memoria puede identificar que ambas clases están en el mismo nivel de jerarquía, es decir,  no una sobre la otra sino que las dos son del mismo nivel.

### Actividad 06

**Realiza un dibujo con el cuál expliques cómo se implementa el polimorfismo en tiempo de ejecución. Utiliza el concepto de métodos virtuales y la tabla de funciones virtuales. ¿Qué puedes concluir?**

<img width="1176" height="517" alt="image" src="https://github.com/user-attachments/assets/8f9e96bf-cd2b-4a10-b9d5-626770829fcf" />

**¿Qué relación existe entre los métodos virtuales y el polimorfismo?**

Estos se relacionan ya que en estos métodos es posible ver cuales vienen directamente de la clase base y cuales métodos estan sobrescritos, lo cual significa que estos métodos se adaptan de cierta forma dependiendo de la clase en donde se esten utilizando. Por ejemplo, se ve como métodos como obtener el color vienen directamente de la clase base particula, sin embargo en casos como el draw se puede ver como estos métodos estan sobre escritos para ambas clases de explosión. 

### Actividad 07

ofApp.h
```c++
#pragma once
#include "ofMain.h"
#include <vector>

// -------------------------------------------------
// Clase base abstracta: Particle
// -------------------------------------------------
class Particle {
public:
	virtual ~Particle() { }
	virtual void update(float dt) = 0;
	virtual void draw() = 0;
	virtual bool isDead() const = 0;
	// Nuevo método para saber si la partícula (tipo RisingParticle) debe explotar
	virtual bool shouldExplode() const { return false; }
	// Métodos para obtener posición y color, para usarlos en explosiones
	virtual glm::vec2 getPosition() const { return glm::vec2(0, 0); }
	virtual ofColor getColor() const { return ofColor(255); }
};

// -------------------------------------------------
// RisingParticle: Partícula que nace en la parte inferior central y sube
// -------------------------------------------------
class RisingParticle : public Particle {
protected:
	glm::vec2 position;
	glm::vec2 velocity;
	ofColor color;
	float lifetime; // tiempo máximo antes de explotar
	float age;
	bool exploded;

public:
	RisingParticle(const glm::vec2 & pos, const glm::vec2 & vel, const ofColor & col, float life)
		: position(pos)
		, velocity(vel)
		, color(col)
		, lifetime(life)
		, age(0)
		, exploded(false) {
	}

	void update(float dt) override {
		position += velocity * dt;
		age += dt;
		// Aumenta la desaceleración para dar sensación de recorrido largo
		velocity.y += 9.8f * dt * 8;
		// Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura
		float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
		if (position.y <= explosionThreshold || age >= lifetime) {
			exploded = true;
		}
	}

	void draw() override {
		ofSetColor(color);
		// Partícula más grande
		ofDrawCircle(position, 10);
	}

	bool isDead() const override { return exploded; }
	bool shouldExplode() const override { return exploded; }
	glm::vec2 getPosition() const override { return position; }
	ofColor getColor() const override { return color; }
};
//--------------------------------------------------------
//Particula nueva
//--------------------------------------------------------
class SpiralParticle : public Particle {
protected:
	glm::vec3 position;
	float yvelocity;
	float avelocity;
	float radius;
	ofColor color;
	float lifetime; // tiempo máximo antes de explotar
	float age;
	bool exploded;

public:
	SpiralParticle(const glm::vec3 & pos, float  vel, float w, float r, const ofColor & col, float life)
		: position(pos)
		, radius(r)
		, avelocity(w)
		, yvelocity(vel)
		, color(col)
		, lifetime(life)
		, age(0)
		, exploded(false) {
	}

	void update(float dt) override {
		age += dt;
		float angle = avelocity * age;
		// Aumenta la desaceleración para dar sensación de recorrido largo
		position.x = radius * cos(angle)*8;
		position.y = radius * sin(angle)*8;
		position.z -= yvelocity * dt;
		// Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura
		float explosionThreshold = ofGetHeight() * 0.8; // o cualquier valor en Y que consideres
		if (position.y >= explosionThreshold || age >= lifetime) {
			exploded = true;
		}
	}

	void draw() override {
		ofSetColor(color);
		// Partícula más grande
		ofDrawSphere(position, 10);
	}

	bool isDead() const override { return exploded; }
	bool shouldExplode() const override { return exploded; }
	glm::vec2 getPosition() const override {
		return glm::vec2(position.x, position.y);
	}
	ofColor getColor() const override { return color; }
};
//------------------------------------------------------
//Segunda particula
//-----------------------------------------------------
class RandomParticle : public Particle {
protected:
	glm::vec2 position;
	glm::vec2 velocity;
	float angle;
	ofColor color;
	float lifetime; // tiempo máximo antes de explotar
	float age;
	bool exploded;
	float xo;
	float fase;
	float fangular ;
	float amplitud ;

public:
	RandomParticle(const glm::vec2 & pos, const glm::vec2 & vel, const ofColor & col, float life)
		: position(pos)
		, velocity(vel)
		, color(col)
		, lifetime(life)
		, age(0)
		, exploded(false) {
		
		position = glm::vec2(ofGetWidth()/10, ofGetHeight());

		velocity = glm::vec2(0, -200);

		// parámetros de oscilación
		xo = position.x* ofRandom(2,15); // centro en el medio
		amplitud = ofRandom(30, 80); // oscilación horizontal
		float frecuencia = ofRandom(0.5, 2.0);
		fangular = 2 * PI * frecuencia; // frecuencia angular
		fase = ofRandom(0, TWO_PI);   
	}

	void update(float dt) override {
		age += dt;
		float g = 9.8f; 

		position.x = xo + amplitud * sin(fangular * age + fase);
		position.y += velocity.y * dt;
		velocity.y += g * dt;
		
		float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
		if (position.y <= explosionThreshold || age >= lifetime) {
			exploded = true;
		}
	}

	void draw() override {
		ofSetColor(color);
		// Partícula más grande
		ofDrawCircle(position, 10);
	}

	bool isDead() const override { return exploded; }
	bool shouldExplode() const override { return exploded; }
	glm::vec2 getPosition() const override { return position; }
	ofColor getColor() const override { return color; }
};


// -------------------------------------------------
// Clase base para explosiones: ExplosionParticle
// -------------------------------------------------
class ExplosionParticle : public Particle {
protected:
	glm::vec2 position;
	glm::vec2 velocity;
	ofColor color;
	float age;
	float lifetime;
	float size; // tamaño de la partícula de explosión
public:
	ExplosionParticle(const glm::vec2 & pos, const glm::vec2 & vel, const ofColor & col, float life, float sz)
		: position(pos)
		, velocity(vel)
		, color(col)
		, age(0)
		, lifetime(life)
		, size(sz) {
	}

	void update(float dt) override {
		position += velocity * dt;
		age += dt;
		float alpha = ofMap(age, 0, lifetime, 255, 0, true);
		color.a = alpha;
	}

	bool isDead() const override { return age >= lifetime; }
};

// -------------------------------------------------
// CircularExplosion: Explosión en patrón circular
// -------------------------------------------------
class CircularExplosion : public ExplosionParticle {
public:
	CircularExplosion(const glm::vec2 & pos, const ofColor & col)
		: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.2f, ofRandom(16, 32)) {
		float angle = ofRandom(0, TWO_PI);
		float speed = ofRandom(80, 200);
		velocity = glm::vec2(cos(angle), sin(angle)) * speed;
	}

	void draw() override {
		ofSetColor(color);
		ofDrawCircle(position, size);
	}
};

// -------------------------------------------------
// RandomExplosion: Explosión con direcciones aleatorias
// -------------------------------------------------
class RandomExplosion : public ExplosionParticle {
public:
	RandomExplosion(const glm::vec2 & pos, const ofColor & col)
		: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.5f, ofRandom(16, 32)) {
		velocity = glm::vec2(ofRandom(-200, 200), ofRandom(-200, 200));
	}

	void draw() override {
		ofSetColor(color);
		ofDrawRectangle(position.x, position.y, size, size);
	}
};

// -------------------------------------------------
// StarExplosion: Explosión en forma de estrella
// -------------------------------------------------
class StarExplosion : public ExplosionParticle {
public:
	StarExplosion(const glm::vec2 & pos, const ofColor & col)
		: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.3f, ofRandom(20, 40)) {
		float angle = ofRandom(0, TWO_PI);
		float speed = ofRandom(90, 180);
		velocity = glm::vec2(cos(angle), sin(angle)) * speed;
	}

	void draw() override {
		ofSetColor(color);
		int rays = 5;
		float outerRadius = size;
		float innerRadius = size * 0.5;
		ofPushMatrix();
		ofTranslate(position);
		for (int i = 0; i < rays; i++) {
			float theta = ofMap(i, 0, rays, 0, TWO_PI);
			float xOuter = cos(theta) * outerRadius;
			float yOuter = sin(theta) * outerRadius;
			float xInner = cos(theta + PI / rays) * innerRadius;
			float yInner = sin(theta + PI / rays) * innerRadius;
			ofDrawLine(0, 0, xOuter, yOuter);
			ofDrawLine(xOuter, yOuter, xInner, yInner);
		}
		ofPopMatrix();
	}
};

// -------------------------------------------------
// ofApp: Manejo de la escena y eventos
// -------------------------------------------------
class ofApp : public ofBaseApp {
public:
	void setup();
	void update();
	void draw();
	void mousePressed(int x, int y, int button);
	void keyPressed(int key);

	std::vector<Particle *> particles;
	~ofApp();

private:
	void createRisingParticle();
	void createSpiralParticle();
	void createRandomParticle();
};
```
ofApp.cpp 
```c++
#include "ofApp.h"

// --------------------------------------------------------------
void ofApp::setup() {
	ofSetFrameRate(60);
	ofBackground(0);
}

// --------------------------------------------------------------
void ofApp::update() {
	float dt = ofGetLastFrameTime();

	// Actualiza todas las partículas
	for (int i = 0; i < particles.size(); i++) {
		particles[i]->update(dt);
	}

	// Procesa las partículas (iteración en reversa para facilitar eliminación)
	for (int i = particles.size() - 1; i >= 0; i--) {
		// Si la partícula debe explotar, generamos nuevas explosiones
		if (particles[i]->shouldExplode()) {
			int explosionType = (int)ofRandom(3); // 0: Circular, 1: Random, 2: Star
			int numParticles = (int)ofRandom(20, 30);
			for (int j = 0; j < numParticles; j++) {
				if (explosionType == 0) {
					particles.push_back(new CircularExplosion(particles[i]->getPosition(), particles[i]->getColor()));
				} else if (explosionType == 1) {
					particles.push_back(new RandomExplosion(particles[i]->getPosition(), particles[i]->getColor()));
				} else {
					particles.push_back(new StarExplosion(particles[i]->getPosition(), particles[i]->getColor()));
				}
			}
			delete particles[i];
			particles.erase(particles.begin() + i);
		} else if (particles[i]->isDead()) {
			delete particles[i];
			particles.erase(particles.begin() + i);
		}
	}
}

// --------------------------------------------------------------
void ofApp::draw() {
	for (int i = 0; i < particles.size(); i++) {
		particles[i]->draw();
	}
}

// --------------------------------------------------------------
void ofApp::createRisingParticle() {
	// Genera una RisingParticle cerca del centro inferior (con variación horizontal)
	float minX = ofGetWidth() * 0.35;
	float maxX = ofGetWidth() * 0.65;
	float spawnX = ofRandom(minX, maxX);
	glm::vec2 pos(spawnX, ofGetHeight());
	// La partícula apunta hacia un objetivo en la parte superior central
	glm::vec2 target(ofGetWidth() / 2 + ofRandom(-300, 300), ofGetHeight() * 0.10 + ofRandom(-30, 30));
	glm::vec2 direction = glm::normalize(target - pos);
	// Velocidad ajustada para recorrer una mayor distancia
	glm::vec2 vel = direction * ofRandom(250, 350);
	ofColor col;
	col.setHsb(ofRandom(255), 220, 255);
	float lifetime = ofRandom(1.5, 3.5); // Tiempo de vida antes de explotar
	particles.push_back(new RisingParticle(pos, vel, col, lifetime));
}
void ofApp::createSpiralParticle() {
	
	float minX = ofGetWidth() * 2;
	float maxX = ofGetWidth() * 2;
	float spawnX = ofRandom(minX, maxX);
	glm::vec3 pos(spawnX, ofGetHeight(), 0);

	float vel = ofRandom(100, 200); 
	float w = ofRandom(2, 6); 
	float r = ofRandom(50, 120); 
	ofColor col;
	col.setHsb(ofRandom(255), 220, 255);

	float lifetime = ofRandom(2.0, 10.0);

	particles.push_back(new SpiralParticle(pos, vel, w, r, col, lifetime));
}
void ofApp::createRandomParticle() {
	// Genera una RisingParticle cerca del centro inferior (con variación horizontal)
	float minX = ofGetWidth() * 0.35;
	float maxX = ofGetWidth() * 0.65;
	float spawnX = ofRandom(minX, maxX);
	glm::vec2 pos(spawnX, ofGetHeight());
	// La partícula apunta hacia un objetivo en la parte superior central
	glm::vec2 target(ofGetWidth() / 2 + ofRandom(-300, 300), ofGetHeight() * 0.10 + ofRandom(-30, 30));
	glm::vec2 direction = glm::normalize(target - pos);
	// Velocidad ajustada para recorrer una mayor distancia
	glm::vec2 vel = direction * ofRandom(250, 350);
	ofColor col;
	col.setHsb(ofRandom(255), 220, 255);
	float lifetime = ofRandom(1.5, 3.5); // Tiempo de vida antes de explotar
	particles.push_back(new RandomParticle(pos,vel, col, lifetime));
}

// --------------------------------------------------------------
void ofApp::mousePressed(int x, int y, int button) {
	createRisingParticle();
}

// --------------------------------------------------------------
void ofApp::keyPressed(int key) {
	if (key == ' ') {
		for (int i = 0; i < 1000; i++) {
			createRisingParticle();
		}
	}
	if (key == 's') {
		ofSaveScreen("screenshot_" + ofToString(ofGetFrameNum()) + ".png");
	}
	if (key == 'a') {
		createSpiralParticle();
	}
	if (key == 'r') {
		createRandomParticle();
	}
}

// --------------------------------------------------------------
ofApp::~ofApp() {
	for (int i = 0; i < particles.size(); i++) {
		delete particles[i];
	}
	particles.clear();
}
```
**¿Cómo y por qué de la implementación de cada una de las extensiones solicitadas al caso de estudio?**

**¿Cómo y por qué de la implementación de los conceptos de encapsulamiento, herencia y polimorfismo en tu código?**

**Explica cómo verificaste que cada una de las extensiones funciona correctamente, muestra capturas de pantalla del depurador donde evidencias lo anterior, en particular el polimorfismo en tiempo de ejecución.**

## 4.  **Consolidación, autoevaluación y cierre:**
> [!CAUTION]
> Esta sección es OBLIGATORIA y central para tu evaluación
