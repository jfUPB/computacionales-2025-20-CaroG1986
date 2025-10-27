# Bitácora de aprendizaje de la unidad 8

## Actividad 01

**Ejecuta el programa y haz clic en la ventana. Observa lo que sucede. ¿Qué es lo que ves? ¿Qué es lo que esperabas ver? ¿Por qué crees que sucede esto?**

<img width="1467" height="759" alt="image" src="https://github.com/user-attachments/assets/f1bf817f-fc13-4ef2-a609-15e61684a9ac" />

<img width="1467" height="745" alt="image" src="https://github.com/user-attachments/assets/081f2a09-7700-447e-af48-7107067eea1f" />

Lo que ocurrió al ejecutar fue que apareció un círculo en la pantalla y al darle clic, se pausó, espero un rato y después cambió de tamaño. Supongo que esto sucede porque el programa tiene mucho que procesar al mismo tiempo y por esto hace primero el calculo y luego se ocupa del circulo. 

**Ejecuta el programa y haz clic en la ventana. Observa lo que sucede. ¿Qué es lo que ves? ¿Qué es lo que esperabas ver? ¿Por qué crees que sucede esto?**

<img width="1485" height="760" alt="image" src="https://github.com/user-attachments/assets/363aedf6-c16a-4661-ae39-e8b47c25c1b7" />

Ahora se puede ver cómo el círculo continúa con su movimiento sin necesidad de detenerse por tanto tiempo y por el otro lado se ve en la consola lo que está ocurriendo en la parte de la computación pesada, es decir, los cálculos.

**Observa que el programa ahora no se congela, pero el círculo no cambia de tamaño inmediatamente. ¿Por qué crees que sucede esto? ¿Qué es lo que está pasando?**

Creo que esto sucede por lo que se menciona antes de darnos el código, y es que se añade un nuevo hilo que se encarga de la función heavyComputation(), así que este hilo es el encargado de los calculos más complejos y así se puede continuar con la parte grafíca en otro lado.

**En tus propias palabras, explica la diferencia entre concurrencia y paralelismo. ¿Por qué es importante entender esta diferencia al trabajar con hilos?**

La concurrencia es que las actividades están divididas entre los hilos, pero estos no las ejecutan al mismo tiempo, sino que se intercalan para completar sus tareas. Por otro lado, el paralelismo Se trata de una simultaneidad verdadera y una distribución qué permite mejor administración.

## Actividad 02

**Analiza de nuevo el código de la actividad anterior. ¿En qué partes del código se está protegiendo el acceso a la variable circleSize?**

Creo que la parte del código que protege el acceso es la siguiente:

En el heavyComputation()
```c++
lock();
ofSeedRandom();
circleSize = ofRandom(20, 70);
unlock();
std::cout << "Circle size: " << circleSize << std::endl;
```

En el draw()
```
lock();
ofDrawCircle(x, ofGetHeight() / 2, circleSize);
unlock();
x = fmod(x + speed, ofGetWidth());
```

En esta parte se ve que bloquea el acceso a la información del tamaño del circulo, lo cambia o utiliza y ya despúes abre el acceso para el otor hilo.

**Según lo que te he venido comentando, los hilos te permiten ejecutar tareas en paralelo; sin embargo, piensa qué ocurre con el paralelismo cuando se sincroniza el acceso a un recurso compartido. ¿Qué ocurre con el rendimiento del programa? ¿Es posible que el rendimiento se vea afectado por el uso de mutex? ¿Por qué?**

Supongo que sí hoy no se protege bien el acceso a ciertas variables esto generaría un gran desorden en el programa y causaría que cada hilo trabajé con la misma información, así que en realidad no la estaría modificando y luego usando el resultado, sino que se crearía una respuesta distinta a la esperada.

**Ejecuta el código y observa el resultado. ¿Qué ocurre si cambias el valor de la variable useLock? ¿Por qué crees que ocurre esto?**

Con Lock
<img width="1026" height="810" alt="image" src="https://github.com/user-attachments/assets/54e480c8-e900-4384-b5f1-cd4ea7a3076c" />

Sin lock 
<img width="1026" height="804" alt="image" src="https://github.com/user-attachments/assets/c0fc2482-3bfa-4132-9f17-f3d3d736d0c0" />

Lo que pasa es que sin el lock el programa suele mostrar como resultado números distintos pero es cierto que, en un tiempo mucho menor, mientras que con el lock muestra el número deseado pero se demoró un poco más. Eso es debido a que la unión no está protegida todos los hilos usa la misma información por lo que el programa se vuelve impredecible y al mismo tiempo más rápido, pero al estar bloqueado se toman turnos para ver la información por lo que se demora más pero el resultado es correcto.

**Explica en tus propias palabras ¿Cómo puede presentarse la condición de carrera en este caso? ¿Qué es lo que está pasando? Te pido que propongas un ejemplo.**

En este caso la condición de carrera se ve ya que como no existe un orden en cuanto a La información que recibe cada hilo, estos pueden muchas veces interferir con los demás por lo que afectan al resultado. Por ejemplo, si viéramos eso no hubiera cotidiana sería como intentar cocinar una sopa entre varias personas y que todas la condimenten, entonces en lugar de esperar a que uno le ponga sal y ver qué tanta sal hay ahora, todos le ponen ahora al mismo tiempo y el resultado es insatisfactorio.

## Actividad 03

**Ejecuta el código y observa el resultado.**

Secuencial
<img width="1026" height="901" alt="image" src="https://github.com/user-attachments/assets/ef690cdf-bdd4-4a67-95a6-9a0ccf27be04" />

Palalera
<img width="1031" height="812" alt="image" src="https://github.com/user-attachments/assets/185a4f1f-a562-410b-8a2a-13b6b9759f48" />

**Analiza el código y estudia detenidamente su funcionamiento. En la fase de aplicación tendrás que retomar este código para resolver un reto.**

En ese ejercicio, aunque sea secuencial o de forma paralela la base es la misma donde se usan el número de iteraciones para definir el color de cada píxel. Lo que los diferencian sería entonces la velocidad y el número de hilos que se utilizan, ya que en el primer caso todo es con el mismo hilo Y por el enorme trabajo que esto conlleva le toma más tiempo, sin embargo en el otro caso estaba usando 16 hilos y esta enorme diferencia permite una mayor velocidad.

**Experimenta modificando, PERO, no olvides cómo investigamos en este curso:**

**- Realiza cambios pequeños y específicos.**

Máximo de iteraciones = 40
<img width="1028" height="819" alt="image" src="https://github.com/user-attachments/assets/149e8fc3-647c-42b4-8ceb-6dc1b2aea3ad" />

Máximo de iteraciones = 10
<img width="1034" height="816" alt="image" src="https://github.com/user-attachments/assets/905d2d2e-bbb7-4141-b33c-ae2520b2e956" />

Cambio de color
<img width="1028" height="811" alt="image" src="https://github.com/user-attachments/assets/9b86b243-358d-4d03-955c-8e0e11bfdc0c" />

**- Lanza una hipótesis sobre lo que crees que va a pasar.**

1. Para el primer experimento quería alterar el número de las iteraciones para ver cómo esto podría afectar a la imagen final. yo supongo que la forma cambia.
2. Para el segundo experimento quería variar su color. 

**- Ejecuta el código y observa lo que ocurre.**

1. Primero cambié el número de iteraciones a 40 y como se ve la imagen sí cambia, pero no era un cambio muy drástico, así que para ver mejor en qué afectaba este número lo reduje aún más a 10. Entonces lo que ocurrió fue que la imagen es mucho menos compleja ahora y en sí es una figura más sencilla.
2. Para el segundo experimento esperaba que el fondo cambiará otro color que no fuera rojo pero lo que pasó en realidad es que ahora es aún más rojo entonces supongo que fue porque cambié el número del hue a 10 lo que le da menos variación y por lo que termina siendo principalmente de color 

**- ¿Tu hipótesis era correcta? ¿Por qué crees que ocurre esto?**

1. Efectivmente la forma cambio y como mencione ahora es más sencilla.
2. No se cumplió mi hipotesis ya que esperaba que al cambiar el hue el color sería diferente, peor si logró un resultado interesante.

**Te dejo una idea para comenzar a experimentar: ¿Qué ocurre si cambias el número de hilos? ¿Por qué crees que ocurre esto?**

<img width="1022" height="811" alt="image" src="https://github.com/user-attachments/assets/43c70042-bfe5-42ee-ade8-ad6061d347b1" />

El mayor cambio que noto es el timpo que tomó, ahora le tomó un tiempo más largo hacer los calculos que con 16 hilos.

## Actividad 04

**Observa ambos códigos y responde a las siguientes preguntas:**

Sin hilos
<img width="1033" height="820" alt="image" src="https://github.com/user-attachments/assets/0ccc7beb-1d52-4874-aceb-9502701787a7" />

Con hilos
<img width="1015" height="809" alt="image" src="https://github.com/user-attachments/assets/7d3eef11-5294-4b95-a1d6-fced993ee4f4" />

**¿Cuál es la estructura de datos principal que contiene la información de todos los boids y que es accedida por múltiples hilos (el hilo principal para dibujar, el hilo trabajador para actualizar)?**

La estructura de datos principal con la información es un vector llamado voids que almacena la información de todos los boids y es el que se accede por medio de los hilos.

**- Observa la función Flock::threadedFunction() donde el hilo trabajador calcula el movimiento. ¿Qué operaciones realizan sobre el vector de boids compartido?**

Se bloquea el acceso a la información dentro del vector compartido para poder realizar el calculo aparte.

**- Observa la función ofApp::draw(). ¿Qué operación realiza sobre el vector compartido?**

Esta función primero bloquea el vector y luego dibuja lo que se encuentre en el Flock para poder después desbloquear el vector y que usen otros hilos.

**- Observa Flock::addBoid() y ofApp::mouseDragged(). ¿Qué operación realizan?**

La función Flock::addBoid() básicamente le añade nuevos boids a el vector usando como referencia la posición del mouse, para que despúes la función ofApp::mouseDragged() active esta función y aparescan nuevos boids al arrastrar el mouse.

**Describe un escenario específico y concreto donde la falta de sincronización podría causar un problema.**

Digamos que un hilo se encarga de generar nuevos boids mientras que otro se encarga de pintarlos o dibujarlos, pero como ambos estaban leyendo la misma información el encargado de dibujarlos y los no tendría en cuenta el último agregado, Lo que podría generar una confusión respecto a cuál es el número real de hilos y que esto interfiera con el proceso.

**Localiza todas las llamadas a lock() y unlock() dentro de la clase Flock (o donde se acceda al vector compartido).**

Add boid
``` c++
void Flock::addBoid(int x, int y) {
	lock();
	boids.emplace_back(x, y);
	unlock();
}
```

Theareaded Fuction
```c++
void Flock::threadedFunction() {
	while (isThreadRunning()) {
		lock();
		for (Boid & b : boids) {
			b.run(boids);
		}
		unlock();
		sleep(5);
	}
}
```

Draw
``` c++
void ofApp::draw() {
	ofBackground(0);

	flock.lock();
	for (Boid & b : flock.boids) {
		b.draw();
	}
	flock.unlock();

	ofDrawBitmapStringHighlight("FPS: " + ofToString(ofGetFrameRate()), 20, 20);
	ofDrawBitmapStringHighlight("Boids: " + ofToString(flock.boids.size()), 20, 40);
}
```

**Aunque los locks aseguran la correctitud, ¿Puedes intuir por qué tener muchos hilos esperando para adquirir un lock sobre el mismo vector (alta contención) podría limitar el beneficio de rendimiento del paralelismo en este caso? Justifica tu respuesta.**

Cuándo es el aplicado paralelismo a esta clase de programas con el fin de aumentar su eficiencia la idea es que la información fluya más rápido, sin embargo los locks impiden el flujo por un momento por lo que el proceso vuelve a ser lento así que lo vuelve un poco contradictorio con la idea que se tenía al principio.

**Piensa en la pregunta que te acabo de hacer. ¿Qué pasaría si tuviéramos varios hilos que calculan el movimiento de los boids? ¿Cómo podrías implementar esto? ¿Qué problemas crees que podrían surgir? ¿Cómo podrías solucionarlos?**

Sí se utilizará otros hilos para hacer los cálculos de la posición los problemas serían muy similares a los que se veían en ejemplos anteriores donde necesario agregarle bloqueos a la información para qué así no haya problemas de interferencia entre los hilos, pero con esos looks surge el problema de que disminuye la velocidad con la que se ejecuta el programa pero en estos casos no se prioriza tanto la velocidad, ya que como se ve al ejecutar el ejemplo sin importar sí se usan o la rapidez de ejecución no es muy distinta.

**Analiza el código del Flocking sin hilos y el Flocking con hilos. ¿Qué diferencias encuentras? ¿Por qué crees que es importante la sincronización en el segundo caso?**

Al revisar ambos códigos peramente las principales diferencias que logró detectar son la falta de bloqueos en el primer código ya que en ese caso no hay tanta probabilidad de que se desorganice la información y se altere del programa. Por otro lado, otra diferencia que encuentro es que cuando se usan hilos ay varias funciones encargadas de que dichos hilos inician su ejecución esperen al otro y finalicen las ejecuciones.

**¿Por qué al añadir un nuevo boid la simulación se ralentiza? ¿Qué ocurre si añades muchos boids?**

La operación no se ralentiza por qué es más información que procesar y el vector crece mucho más así que las operaciones que se hacen para cada parte del vector ahora son más largas. Si se añaden muchos directamente va como a 1 frame y se deja de apreciar el movimiento.

**Notaste que la versión con hilos tiene un sleep(5) en el hilo trabajador. ¿Por qué crees que se ha añadido? ¿Qué pasaría si lo eliminamos?**

Para comprobar qué ocurriría lo intenté en el programa e iba demasiado lento, tipo a un frame por segundo, Por lo que supongo que ese sleep está ahí para que decía esta forma la información no llegue toda al mismo tiempo a ese hilo sino por intervalos para que pueda “pensar”.

**Compara el rendimiento de ambos enfoques. ¿Cuál crees que es más eficiente? ¿Por qué?**

En realidad, ambos casos tienen sus pros y sus contras y son útiles dependiendo del efecto que se quiera realizar, pero supongo que si es por la distribución de tareas la versión con hilos hace un buen trabajo restándole a la sobrecarga de actividades que debe realizar qué programa.

**El uso de lock y unlock en la versión con hilos es crucial para evitar condiciones de carrera. ¿Qué pasaría si no se usaran? ¿Cómo afectaría esto al comportamiento del programa? (No olvides por favor que las condiciones de carrera son difíciles de reproducir, así que no te preocupes si no puedes verlas en acción).**

Cómo vimos en experimentos anteriores lo que pasaría es que la información la verían todos los hilos y esto afectaría la armonía entre ellos ya que intentarían hacer todo al mismo tiempo y puede que muchas veces alteren en el curso del proyecto logrando así distintos resultados.

**¿Qué ocurre si mientras el hilo trabajador está calculando el movimiento de los boids, el hilo principal intenta añadir un nuevo boid? ¿Se congelará la aplicación? ¿Por qué?**

Lo más probable es que si esto ocurre no sé si pararía la aplicación por completo, pero creo que el hilo que está calculando la posición no tomaría en cuenta el nuevo valor de el dato que se añadió por lo que se desincronizaría lo que se ve en la pantalla.

## Actividad 05

**Pega la parte clave de tu función modificada que calcula el píxel para el conjunto de Julia. Recuerda utilizar un bloque cpp.**

**Muestra cómo mapeaste la posición del mouse a la constante k.**

**Describe brevemente cómo reutilizaste la estructura de hilos de la versión Mandelbrot. ¿Tuviste que cambiar mucho esa parte?**

**¿Cómo te aseguraste de que la imagen se recalculara cuando el mouse se movía?**

**Incluye al menos dos capturas de pantalla que muestren diferentes fractales de Julia generados al mover el mouse en tu aplicación.**

**¿Encontraste algún desafío particular al implementar la interacción o modificar el cálculo?**
