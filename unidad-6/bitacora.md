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

El patrón observer se implementa por medio del polimorfismo, permitiendo que otras clases, las que serían entonces los observadores concretos, se "suscriban" a una clase sujeto, en otras palabras, es como si estuvieran suscritos a un periodico o una plataforma de noticias y les llegaran notificaciones cada vez que sale un nuevo reporte. Esto permite que cada uno de los observadores concretos se comporten dependiendo de la información que llegue del sujeto. Si se piensa de una forma más cotidiana, es como cuando una noticia causa histeria colectiva, afectado el comportamiento de las personas, y este ejemplo lo veo como que la información que llega permite a los observadores definir como se van a comportar respecto al mouse. 

**Dibuja un diagrama que muestre la relación entre Subject, Observer, ofApp y Particle en el caso de estudio, indicando quién es el Sujeto y quiénes los Observadores.**

<img width="593" height="577" alt="image" src="https://github.com/user-attachments/assets/ac79e72f-9345-4fa5-b950-2be6167ef1eb" />

Yo lo quise representar de una forma más sencilla, en el que Subject y OfApp, que son algo así como el sujeto y el sujeto concreto respectivamente, son los politicos y medios de comunicación, mientras que observer y particle, que son el observador y el observador concreto, son todos aquellos que recicen dicha información.

**Construye un diagrama de secuencia que muestre cómo funciona el patrón Observer al presionar una tecla.**

Ejemplo con la tecla 'a'
> Primero hice un diagrama yo con como me imaginaba que funcionaba la secuancia en ste evento 
<img width="1138" height="656" alt="image" src="https://github.com/user-attachments/assets/d1752a97-e5db-4007-9621-420cc8e2f9de" />

>Depués le dije a chat gpt que lo hiciera y lo pase a mermeid para ver que tan diferente era
<img width="1366" height="800" alt="image" src="https://github.com/user-attachments/assets/1566a2bc-db07-4163-beca-4ebea3c5b6b8" />

Con este experimiento siento que si logre comprender muyr bien la secuencia, es cierto que hay algunos detalles diferentes, pero en terminos generales ambos dicen prácticamante lo mismo y siguen el mismo "flujo"

**¿Qué ventajas crees que ofrece usar el patrón Observer en esta aplicación en comparación con, por ejemplo, que ofApp::update recorriera todas las partículas y les dijera directamente que cambien su comportamiento basado en una variable global? Piensa en términos de acoplamiento y extensibilidad.**

Yo creo que las ventajas es que el que las particulas sean observadores significa que estas simplemente reciben notificaciones de eventos, por lo que no es necesario ir particula por particula revisando su comportamiento, esto significa que para agregar algo despúes al programa esto sería beneficioso y más sencillo en el caso de trabajar en un equipo donde cada persona haga algo por separado.

## Actividad 03

**Explica con tus propias palabras el propósito del patrón Factory Method (o Simple Factory, en este caso). ¿Qué problema principal aborda en la creación de objetos?**

Yo diría que el proposito principal de un Factory Method es tener un lugar donde esten organizadas las instancias de los objetos que sean necesarios, ya que así permite que si se quiere modificar por ejemplo la camtidad que es creada en el método setup esto se pueda hacer sin necesidad de hacer cambios en la particula como tal, ya que estas van a seguir estando compuesta spor la smismas variables. Básicamente Hace más fácil el proceso de creación de objetos isn tener que estar llamado en otras partes new object(). 

**¿Qué ventajas aporta el uso de ParticleFactory en ofApp::setup en comparación con instanciar y configurar las partículas directamente allí? Piensa en términos de organización del código (SRP - Single Responsibility Principle), legibilidad y facilidad para añadir nuevos tipos de partículas en el futuro.**

Es lo que estaba mencionando en el punto anterior. La verdad al ver esta funión setup siento que es mucho más simple y leible a comparación de si tuviera que instanciar cada particula en esta, teniendo que asignar en el setup las características de cada una. Así como esta el método se ve más corte, sencillo y no hay necesidad de estar buscando entre el código para cambiarle algún detalle al programa, si quiero cambiar la cantidad que se instancia voy a setuo y si quiere cambiar algo del color o tamaño voy a Factory.

**Imagina que quieres añadir un nuevo tipo de partícula llamada "black_hole" que tiene tamaño grande, color negro y velocidad muy lenta. Describe los pasos que necesitarías seguir para implementar esto utilizando la ParticleFactory existente. ¿Tendrías que modificar ofApp::setup? ¿Por qué sí o por qué no?**

<img width="1024" height="756" alt="image" src="https://github.com/user-attachments/assets/157cd0e5-72c5-4937-ab63-d8ca7b360dea" />

Hice el ejemplo para ilustrar mejor esta parte (es blanco porque en fondo negro no se ve), básicamente lo que hice fue en la parte de ParticleFactory le agrege un nuevo tipo de particula, justo así: 

``` c++
Particle * ParticleFactory::createParticle(const std::string & type) {
	Particle * particle = new Particle();

	if (type == "star") {
		particle->size = ofRandom(2.0f, 4.0f);
		particle->color = ofColor(255, 0, 0);
	} else if (type == "shooting_star") {
		particle->size = ofRandom(3.0f, 6.0f);
		particle->color = ofColor(0, 255, 0);
		particle->velocity *= 3.0f;
	} else if (type == "planet") {
		particle->size = ofRandom(5.0f, 8.0f);
		particle->color = ofColor(0, 0, 255);
	} else if (type == "black_hole") {
		particle->size = 100.0f;
		particle->color = ofColor(255, 255, 255);
		particle->velocity /= 5.0f;
	}  

	return particle;
}
```
Después de describirlo y darle su nombre y caracteristicas simplemente en el setup (que si, si es necesario modificarlo) le agrege que creara una de esas particulas. Justo así:

```c++
void ofApp::setup() {
	ofBackground(0);
	particles.reserve(100 + 5 + 10);

	for (int i = 0; i < 100; ++i) {
		Particle * p = ParticleFactory::createParticle("star");
		particles.push_back(p);
		addObserver(p);
	}
	for (int i = 0; i < 5; ++i) {
		Particle * p = ParticleFactory::createParticle("shooting_star");
		particles.push_back(p);
		addObserver(p);
	}
	for (int i = 0; i < 10; ++i) {
		Particle * p = ParticleFactory::createParticle("planet");
		particles.push_back(p);
		addObserver(p);
	}
	for (int i = 0; i < 1; ++i) {
		Particle * p = ParticleFactory::createParticle("black_hole");
		particles.push_back(p);
		addObserver(p);
	}
}
```

**El método createParticle en el ejemplo es estático. ¿Qué implicaciones (ventajas/desventajas) tiene esto comparado con tener una instancia de ParticleFactory y un método de instancia createParticle()?.**

Por lo que comprendo en este ejemplo el usar particle factory como un static queda perfecto porque solo queremos crear particulas, y esto permite que no sea necesario crear nuevas instancias, lo que ahorra memoria y hace que este método sea más sencillo, sin embargo si en lugar de una particula quisiera crear un carro por ejemplo, entonces sería mejor tener distintas estancias para distintas fabricas y que así cada una se encargue de una clase. 

## Actividad 04

**Explica con tus propias palabras el propósito del patrón State. ¿Cuándo es útil aplicarlo?**

El patrón state es una forma de controlar el flujo que va a tener un programa definiendo hoy el patrón de comportamiento que va a tener este según el estado actual en el que se encuentre. Por ejemplo, esto puede verse similar a cuando en unity se le agrega una animación a un personaje y dependiendo de sí está caminando, quieto o realizando alguna acción, la animación va a ser diferente.

Eso es útil aplicarlo ya que hace más fácil controlar los cambios que hay en el programa y facilitan El diseño y el control de los proyectos con relación a los eventos que ocurran.

**Dibuja un diagrama de estados simple para la clase Particle. Muestra los diferentes estados (Normal, Attract, Repel, Stop) como nodos y las transiciones entre ellos como flechas etiquetadas con el evento que las causa (p. ej., la tecla presionada: ‘n’, ‘a’, ‘r’, ‘s’).**



**Describe las ventajas de usar el patrón State en Particle en lugar de tener un miembro std::string estadoActual y usar un gran if/else if/else o switch dentro de Particle::update() para cambiar el comportamiento. Piensa en cohesión, extensibilidad (añadir nuevos estados) y el Principio Abierto/Cerrado (Open/Closed Principle).**

**¿Qué responsabilidad tienen los métodos onEnter y onExit en el patrón State? Proporciona un ejemplo de por qué podrían ser útiles (incluso si no se usan mucho en todos los estados de este caso de estudio). Por ejemplo, ¿Qué podrías hacer en onEnter para AttractState o en onExit para StopState?**
