# Bitácora de aprendizaje de la unidad 6

## Actividad 01

>**Explicación del código**
>
>Primero la aplicación como tal:
>
>```c++
>class ofApp : public ofBaseApp, public Subject {
>public:
>	~ofApp() override;
>	void setup() override;
>	void update() override;
>	void draw() override;
>	void keyPressed(int key) override;
>
>private:
>	std::vector<Particle *> particles;
>};
>```
>Aquí se ve como la App no hereda solo de la base de la App, si no también de la clase Subject, lo cual es posible gracias a la herencia multiple que se puede usar en c++
>
>```c++
>class Subject {
>public:
>	void addObserver(Observer * observer);
>	void removeObserver(Observer * observer);
>
>protected:
>	void notify(const std::string & event);
>
>private:
>	std::vector<Observer *> observers;
>};
>```
>Esta es la clase subject, esta clase tiene dentro de si la estructura como tal de la aplicación, la cual funciona por medio de los observadores (por lo que se añaden y se remueven durante el código) y las notificaciones, que informan en el caso de que ocurra un evento.
>```c++
>void ofApp::keyPressed(int key) {
>	switch (key) {
>	case 's':
>		notify("stop");
>		break;
>	case 'a':
>		notify("attract");
>		break;
>	case 'r':
>		notify("repel");
>		break;
>	case 'n':
>		notify("normal");
>		break;
>	default:
>		break;
>	}
>}
>```
>Aquí se puede ver un ejemplo donde se usa el método notificar, que en este caso para infomar un  cambio de estado dependiendo de que tecla se presione.
>
>**¿Por qué se usan estos patrones de diseño?**
>principalmente porque permiten mayor eficiencia al trabajar en equipo.

**¿Cómo puedes interactuar con la aplicación? Menciona específicamente las teclas y qué efecto parecen tener sobre las partículas.**

- Con la s, para el movimiento de las particulas.
- Con la a, "ataca" al mouse, es decir, busca la ubicación del mouse y se juntan ahí todas las particulas.
- Con la r, "repele" el mouse, por lo que intenta alejarse todo lo posible.
- Con la n, se vuelve a la normalidad, así que las particulas simplemente vuelven a como se comportaban en el estado inicial.

**¿Observas los diferentes tipos de “partículas”? ¿Se comportan todas igual inicialmente?**

Hay 3 tipos de particulas y las mayores diferencias entre estas son: el color (Rojo,Verde,Azul), el tamaño y en algunas la velocidad (las shooting stars son mas rápidas que las demás particulas.

**Toma algunas capturas de pantalla de la aplicación en diferentes momentos (estado inicial, después de presionar ‘a’, ‘r’, ‘s’, ‘n’) y añádelas a tu bitácora.**

Al inicio o al presionar 'n' 
<img width="1025" height="802" alt="image" src="https://github.com/user-attachments/assets/cd6ae7b8-1107-4c79-8d6c-a4425b788d30" />
Al presionar 's' (se para el movimiento de las particulas)
<img width="1023" height="801" alt="image" src="https://github.com/user-attachments/assets/ed0c502f-f590-40cd-b48d-ff7dc9be667a" />
Al presionar 'a'
<img width="1030" height="802" alt="image" src="https://github.com/user-attachments/assets/9ec8f63d-8589-40d4-a785-fdf242b86eba" />
Al presionar 'r'
<img width="1037" height="794" alt="image" src="https://github.com/user-attachments/assets/fdba447f-acbb-4522-971f-bae6019a0233" />

**¿Qué crees que está pasando “detrás de cámaras” cuando presionas las teclas? Formula una hipótesis inicial sobre cómo la aplicación cambia el comportamiento de las partículas.**

Creo que lo que ocurre al presionar las teclas es que el método notify informa a los demás un cambio de estado, para que así las particulas se comporten según el estado actual en el que se encuentre. 

## Actividad 02

**Explica con tus propias palabras el propósito del patrón Observer. ¿Qué problema resuelve?**



**Dibuja un diagrama que muestre la relación entre Subject, Observer, ofApp y Particle en el caso de estudio, indicando quién es el Sujeto y quiénes los Observadores.**

**Construye un diagrama de secuencia que muestre cómo funciona el patrón Observer al presionar una tecla.**

**¿Qué ventajas crees que ofrece usar el patrón Observer en esta aplicación en comparación con, por ejemplo, que ofApp::update recorriera todas las partículas y les dijera directamente que cambien su comportamiento basado en una variable global? Piensa en términos de acoplamiento y extensibilidad.**

## Actividad 03

**Explica con tus propias palabras el propósito del patrón Factory Method (o Simple Factory, en este caso). ¿Qué problema principal aborda en la creación de objetos?**

**¿Qué ventajas aporta el uso de ParticleFactory en ofApp::setup en comparación con instanciar y configurar las partículas directamente allí? Piensa en términos de organización del código (SRP - Single Responsibility Principle), legibilidad y facilidad para añadir nuevos tipos de partículas en el futuro.**

**Imagina que quieres añadir un nuevo tipo de partícula llamada "black_hole" que tiene tamaño grande, color negro y velocidad muy lenta. Describe los pasos que necesitarías seguir para implementar esto utilizando la ParticleFactory existente. ¿Tendrías que modificar ofApp::setup? ¿Por qué sí o por qué no?**

**El método createParticle en el ejemplo es estático. ¿Qué implicaciones (ventajas/desventajas) tiene esto comparado con tener una instancia de ParticleFactory y un método de instancia createParticle()?.**

## Actividad 04

**Explica con tus propias palabras el propósito del patrón State. ¿Cuándo es útil aplicarlo?**

**Dibuja un diagrama de estados simple para la clase Particle. Muestra los diferentes estados (Normal, Attract, Repel, Stop) como nodos y las transiciones entre ellos como flechas etiquetadas con el evento que las causa (p. ej., la tecla presionada: ‘n’, ‘a’, ‘r’, ‘s’).**

**Describe las ventajas de usar el patrón State en Particle en lugar de tener un miembro std::string estadoActual y usar un gran if/else if/else o switch dentro de Particle::update() para cambiar el comportamiento. Piensa en cohesión, extensibilidad (añadir nuevos estados) y el Principio Abierto/Cerrado (Open/Closed Principle).**

**¿Qué responsabilidad tienen los métodos onEnter y onExit en el patrón State? Proporciona un ejemplo de por qué podrían ser útiles (incluso si no se usan mucho en todos los estados de este caso de estudio). Por ejemplo, ¿Qué podrías hacer en onEnter para AttractState o en onExit para StopState?**
