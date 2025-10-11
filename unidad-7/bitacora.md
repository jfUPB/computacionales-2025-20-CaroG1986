# Bitácora de aprendizaje de la unidad 7

## Actividad 01

**Incluye una captura de pantalla del ejemplo funcionando en tu máquina.**

<img width="1123" height="636" alt="image" src="https://github.com/user-attachments/assets/cd907b29-d549-4b92-ae58-3b0f3b14326b" />

**Observa el proyecto, trata de entenderlo, pero ten presente que lo analizaremos más adelante.**

Lo primero que vi es que era necesario configurar aspectos de la ventana, como su tamaño y su entrada y salida. Por otra lado tambien se mencionan los shaders (que esta es una parte completamente nueva para mi), los cuales necesitan de "fuentes" (que tampoco estoy segura de que son), y aparte se configura las condiciones de la imagen a proyectar, que es en este caso un triangulo. Ya dentro del int main estan los siguientes pasos: 
1. Inicial el GLFW (no sé que es).
2. Crear la ventana para mostrar el resultado.
3. Lee el tamaño del framebuffer (ni idea)
4. Callbacks (menos)
5. Cargar el GLAD y recursos para window1 (tampoco sé que es un GLAD)
6. Habilita el v-sync (creo que se entiende que no sé muy bien que esta pasando)
7. compila y linkea los shaders (😖)
8. Esta parte de aquí se encarga de lo que se muestra, en este caso el triangulo.
9. Configura el viewport (total)
10. Loop principal: aquí ocurre lo siguiente, se da el manejo de eventos y se procesa la entrada, además se encarga de apectos visibles en la ventana como el color del fondo y la creación del triangulo, llama al shader program (ajá) e intercambia buffers (😕)
11. Limpieza, es decir, se borra todo. 

**¿Qué preguntas te surgen al ver el código?. Anota al menos tres preguntas que te gustaría investigar más adelante (no te preocupes que la idea de esta unidad es que las resuelvas).**
- ¿Qué son los shaders y porque estps necesitan fuentes? ¿Qué es un programa de shaders?
- ¿Qué son los IDs globales y para que son necesarios?
- ¿Que significa GLFW?
- ¿Qué es un framebuffer? ¿Qué es un callback? ¿Qué es un GLAD?

## Actividad 02

**Necesito que hagas digestión de esta información y que la entiendas. Para ello te voy a pedir un resumen en tus propias palabras de lo que acabas de leer. En tu resumen debes tratar de conectar GLFW, opengl32.lib, GLAD, GLM y los drivers de la GPU. ¿Qué rol cumple cada uno? ¿Cómo se relacionan entre sí? Mira, trata de hacer esto de memoria y como si estuvieras contándole a un amigo que quiere aprender OpenGL. Cuando haces el proceso de memoria tu cerebro hace un esfuerzo adicional y eso te ayuda a aprender. Además, si no recuerdas algo quiere decir que no lo entendiste bien y eso es una buena señal para que vuelvas a leerlo.**

<img width="1919" height="1033" alt="image" src="https://github.com/user-attachments/assets/e9eccc93-e977-441e-82f9-01fe2a73325b" />

> lo logré 😃

Para poder crear un proyecto en OpenGL es necesario agregar elementos externos, lo cuales son las dependencias del proyecto. Entre estas hay dos librerías que son fundamentales para OpenGL las cuales son GLFW y GLAD, además en este caso también se descargo una biblioteca llamada GLM (ya voy a explicar estas tres). Para incluirlas simplemente hay que agregar una carpeta dentro de el proyecto, la cual va a contener subcarpetas con la información descargada. 

Ahora, ¿Qué son los elementos externos que descargamos?: 

- GLFW: esta es una biblioteca que es la que nos permite crear ventanas y eventos de entrada, tales como las del teclado o mouse.
- Opengl32.lib: Es una biblioteca incluida en Windows que permite iniciar cualquier programa en open gl.
-  GLAD: biblioteca con funciones de openGL y permite acceder a ellas en tiempo de ejecución.
-  Drivers GPU: Software que sirve como puente entre el sistema operativo y las aplicaciones se comuniquen con la tarjeta gráfica de la computadora.
-  GLM: es una biblioteca matemática para gráficos vectoriales, matrices y transformaciones que consiste en un solo código fuente.

## Actividad 03 

**Cambia los valores de bufferWidth y bufferHeight: divide por 2, por 4, multiplica por 2, por 4, etc. ¿Qué pasa? ¿Qué observas? ¿Qué crees que está pasando?** 

Lo que pasa aquí es que la imagen en sí se dibuja en el framebuffer, sin embargo se ve proyectado en la ventana. Es como si se viera adentro de una casa y hubiéramos otra vez de la ventana de la casa lo que está al interior es de un tamaño diferente sin embargo solo podemos ver lo que es a través de la ventana. Si por alguna razón el espacio tiempo las cosas en la casa cambiaran su tamaño se verían distorsionadas desde la ventana se verían distintas desde la ventana es por esto que cuando se cambió el tamaño del framebuffer se veía desordenado. Pero como hay una función que se encarga de actualizar todo y cambiarlo entonces si se cambia el tamaño vuelve a su estado original.

**Entonces hagamos “digestión”: en tu bitácora, escribe un resumen de lo que has aprendido hasta ahora y piensa en un experimento del tipo ¿Qué pasaría si?**

Básicamente lo que he aprendido hasta ahora es que para hacer un programa de openGL es necesario tener en cuenta varios aspectos que deben ser incluidos dentro del proyecto. De hecho es por esto que este se ve tan complejo porque se divide en muchas partes. Entonces están las partes externas que son las bibliotecas que se instalaron al inicio. Eso lo expliqué bien cada una de qué se trata sin embargo voy a profundizar específicamente en GLFW qué fue la que usamos para esta actividad. Entonces ¿de que de encarga esa biblioteca?, básicamente de crear ventanas y manejar eventos y esto no es útil porque así no tenemos que poner código en cada proyecto para crear ventanas sino que ya tenemos de dónde sacar esa información.

Ahora cómo se conecta esto con lo demás, con el contexto de OpenGL se conecta ya que este es el que contiene todas las funciones de dicha interfaz. Por otro lado hay dos partes fundamentales de la ventana que se crea el framebuffer y el viewport. El framebuffer es como el escenario en donde va a estar dibujado o pintado cada Pixel que hace el Open GL, mientras que el viewport es la parte de este framebuffer que es visible, por ende el área donde se estará dibujando.

Para estos experimentos primero cambie la variable SCR_WIDTH de 400 a 250, al cambiarlo se ve así:

<img width="1446" height="737" alt="image" src="https://github.com/user-attachments/assets/91f865ae-4733-45c0-8aa2-3eea294ea799" />

después quería ver que pasaba al cambiar SCR_HEIGHT por lo que lo cambie a 200 y se ve así 

<img width="1391" height="684" alt="image" src="https://github.com/user-attachments/assets/f4e5e60d-f0d3-49c9-8032-d65e86278d3d" />

**¿Qué pasa si cambias el primer parámetro de glDrawArrays a GL_LINES? ¿Qué pasa si lo cambias a GL_POINTS? ¿Qué pasa si cambias el tercer parámetro a 2? ¿Qué pasa si lo cambias a 4?** 

CON 2:
Okay, para esto intenté haciendo el experimento dentro del programa cuando lo ejecuté con solo dos vértices no me apareció nada en la ventana.
<img width="1380" height="659" alt="image" src="https://github.com/user-attachments/assets/960e942e-fa9e-41fc-af92-df0fd1b37836" />

CON 4: 
Después lo cambié a cuatro vértices y si se ve pero ese mismo triángulo.
<img width="1423" height="673" alt="image" src="https://github.com/user-attachments/assets/4af47156-ef0a-4ea0-9877-80f7ee874aa5" />

Esto es algo fuera de lo previsto ya que habría pensado normalmente que a poner dos aparecería una línea y al poner cuatro aparecería un cuadrado. Mi teoría es que como todo el resto del código está diseñado para que se genere un triángulo y ahí dice como que genera un triángulo entonces por eso cuando uno cambia el valor, si lee dos vértices pues siente que no es suficiente y si lee cuatro dice no pues me sobra uno ese no va a valer y voy a poner tres, esa es  mi teoría. Además ahí se muestra que hay una primitiva de hacer un triángulo entonces por eso supongo que es el resultado.

**¿Qué es el contexto OpenGL?**

estructura de datos que contiene los recursos y la conexión de ventana donde se dibujarán los gráficos

**¿Cuál es el rol de la biblioteca GLFW y qué ventaja tiene usarla?**

Es la que nos permite crear las ventanas y recibir sus eventos, así como también eventos de entrada. Se encarga de los datos como el tamaño de la ventana o si pulsamos la tecla Esc para cerrarla. La ventaja de utilizar esa biblioteca es que nos permite reutilizar código para no tener que diseñar el uso de las ventanas en cada programa.

**¿Por qué crees que OpenGL necesita un contexto (recuerda la analogía del taller de arte)?**

El contexto le otorga las herramientas a OpenGL para que haga las cosas que queremos que haga. Como indicaba el ejemplo,  un artista no puede pintar si no tiene si quiera un espacio donde hacerlo y mucho menos si no tiene sus herramientas, eso es lo que nos otorga el contexto

**¿En últimas qué será el framebuffer y a qué te recuerda de las dos primeras unidades del curso?**

El frame Buffer es el área sobre el cual open gl (en realidad es la GPU bajo las órdenes de openGL) dibuja lo que pedimos. El cual se ajusta a la ventana que creamos. Esto me recuerda a las dos primeras unidades ya que en estas aprendimos a pintar una pantalla usando la dirección de memoria de esta, y eso es lo que hace el framebuffer. Es decir, almacenar la información sobre que hay en cada Pixel de la imagen (como su color)

**¿Qué relación entre en el viewport y el framebuffer?**

El framebuffer contiene la información del dibujo realizado, el viewport es la ventana que proyecta el dibujo.

**¿En todo la analizado hasta ahora qué rol juega los drivers de la GPU y la GPU misma?**

Los drivers de la GPU son un conjunto de programas que permiten a las aplicaciones comunicarse con la GPU. Mientras que la GPU es la encargada de procesar la creación de dicha imágenes. Para este caso en Open GL lo que ocurre es que por medio de esta API se utilizan los drivers de la GPU y estos traducen el lenguaje que usemos (en este caso c++) para que sea ejecutable para la GPU.

**¿Por qué crees que sea necesario activar el VSync? ¿Si no lo activas y la imagen es estática qué crees que pase, y si es dinámica?**

El VSync se encarga de limitar el refresco de la ventana al mismo refresco del monitor 
Es decir, sincroniza ambos procesos de refresco para evitar que haga tearing y que tenga un movimiento natural 

Si no lo usamos probablemente haya algo de tearing (es decir que la pantalla se vea como rota de cierta forma).Si la imagen fuese estática supongo que permanecería igual, si fuese dinámica creo que se congelaria o no sería capaz de cargar bien su dinamismo. Por ejemplo en este caso, sin esta parte del código supongo que no se actualizaría correctamente en caso de cambiar el tamaño del viewport.

**En esta unidad estamos usando OpenGL moderno, pero ¿Qué es OpenGL Legacy? ¿Qué diferencias hay entre ambos?**

OpenGL legacy es una implementación antigua del OpenGL que utiliza pipelines (entradas secuenciales donde la salida de una etapa, es la entrada de la siguiente) de funciones fijas en lugar de Shaders programables 

Su diferencia principal con el moderno es que los Shaders son programables en el moderno, ofreciendo también los buffers de vértices para otorgar más control.

**¿Qué es el shader program? ¿Por qué es importante en OpenGL moderno?**

Un programa shader es un programa que se ejecuta en la GPU para controlar la apariencia visual de lo que se dibuja, es importante ya que reemplazó los pipelines fijos por unos programables, cediendo más control. Es fundamental para iluminación, texturas y sombras, lo que recuerda a programas de diseño gráfico, donde el renderizado es de vital importancia, como blender por ejemplo.

**Trata de revisar el código setupTriangle(), intuitivamente ¿Qué crees que hace? ¿Qué crees que es el VAO y el VBO?**

setupTriangle lo que configura los datos del triángulo (como los vértices) y los manda a la GPU, definiendo como se va a ver en pantalla 

El VAO es un objeto que encapsula todos los estados de los buffers y atributos de vértices para crear el triángulo. Mientras que un VBO se trata de un espacio en la memoria de la GPU en donde está la información de los vértices sobre las figuras que se van a proyectar en la pantalla. Es decir eso es lo que define si lo que vemos es 3D o 2D. Por ejemplo aquí se aplica si uno lo ve como el encargado de los vértices del triángulo.

**En el ciclo principal (game loop) de OpenGL, notaste que en cada frame (cuadro) le decimos a openGL que use el shader program y el VAO. Si le indicas esto antes del game loop ¿Será necesario seguirlo haciendo en cada loop? Si no es necesario ¿En qué casos crees que esto puede ser útil?**

Lo más probable es que no se tenga que estar llamando constantemente, ya que siempre es la misma figura: un triángulo, independientemente de cuanto volteemos el canvas. Adicionalmente , desde antes ya había una función triángulo. Reforzando la idea de que basta con que los Shaders apliquen una sola vez en este caso de código, ya que el triángulo es siempre el mismo.En un caso en el que esto podría ser útil sería por ejemplo si fuera necesario modificar constantemente las visuales del objeto de queremos crear. Por ejemplo modificar el número de sus vértices o su color.

**Finalmente, recuerda lo que hace glfwSwapBuffers(mainWindow); ¿Por qué crees que es importante? ¿Qué pasaría si no lo llamas? ¿Cómo explicas lo que pasa si no lo llamas? (experimenta)**

La función se encarga de intercambiar el buffer trasero por el delantero asegurando una imagen fluida. Si no se llama hipotéticamente deberían suceder parpadeos... Veamos que pasa si quitamos la línea: (Aquí lo probamos y el computador colapso)
<img width="1011" height="658" alt="image" src="https://github.com/user-attachments/assets/05362e38-966b-46d9-8bb4-86329accd6a1" />
La importancia está en que depende de esa función la fluidez del programa. En este caso como el programa colapso el computador lo siguió.

## Actividad 04 

**¿Cuál es la diferencia entre una CPU y una GPU?**

La CPU actúa como el cerebro del computador, siendo un procesador que lidia con las tareas básicas de este y el funcionamiento del sistema. No obstante, la GPU es un procesador de ejecución masiva. Es decir, el adecuado para las tareas específicamente pesadas. Por eso es que es necesario tener GPUs potentes para los juegos o programas 3D, porque requieren de miles de cálculos en tiempo real para si correcta ejecución

**¿Cuáles son los tres pasos claves del pipeline de OpenGL? Explica en tus propias palabras cuál es el objetivo de cada paso.**

- Vertex shading 
Se encarga de calcular todo lo necesario en la escena 
Cada uno de los objetivos, sus caras y vértices, al igual que la información de cada una de las caras traducidas en píxeles y aplica los colores en RGB y carga sus texturas. Además de que para ahorrar recursos, calcula las distancias de cada objeto, de modo en que solo renderiza las cosas que estén al frente y que sean visibles desde la perspectiva de la cámara. Es decir, calcula todo lo 3D a 2D

- Rasterization 
Se encarga de optimizar al máximo el plano 2D creado por el Vertex shading y aplicarle correctamente los colores, también como asegurarse de que no se hagan las texturas traseras innecesarias que no se vean en ese momento en el modelo

- Fragment shading 
Esta se encarga del cálculo de la posición de las normales (hacia que lado están mirando las caras de la malla de polígonos) para así establecer el rango de color que se debe aplicar. En otras palabras, si la cara en ese contexto en específico debe ir muy claro porque le está dando toda la luz o muy oscuro porque está en las sombras, haciendo escenas mucho más realistas

**La gran novedad que introduce OpenGL moderno es el pipeline programable. ¿Qué significa esto? ¿Qué diferencia hay entre el pipeline fijo y el programable? ¿Qué ventajas le ves a esto? y si el pipeline es programable, ¿Qué tengo que programar?**


La novedad del pipeline programable es que ciertas etapas del pipeline de renderizado, que antes estaban fijas y controladas por hardware, ahora se pueden personalizar con los Shaders. La diferencia entre el pipeline fijo y el programable, es que en el fijo sus etapas son predefinidas con un control demasiado limitado. Mientras que con el pipeline programable es que puedes crear Shaders para las estampas más importantes, como la transformación de píxeles y su coloración. Facilitando la creación de gráficos complejos. Las ventajas principales están en que ofrecen mayor flexibilidad y rendimiento, volviéndose un estándar de la industria y lo que se debe programar principalmente es el Vertex shader, el Fragment shading y la rasterization. 

**Si fueras a describir el proceso de rasterización ¿Qué dirías?**

Divide las imágenes en fragmentos que a su vez están divididos por pixeles. Esto le permite ser el encargado de la optimización de los colores y elimina lo innecesario a la vista de la cámara. 

**¿Qué son los fragmentos? ¿Es lo mismo un fragmento que un pixel? ¿Por qué?**

No son lo mismo, los fragmentos contienen pixeles. Los fragmentos son conjuntos que forman triángulos, estos triángulos dividen cada parte de las imágenes que serán visibles al final y son estos los que ayudan a optimizar el proceso, ya que en lugar de pensar en billones de pixeles ahora pensamos en millones de framentos. 

**Explica qué problema resuelve el Z-buffer y ¿Qué es el depth test?**

El Z-BUFFER es el encargado de la profundidad. Es gracias a este que se identifican cuáles píxeles se encuentran más lejos desde la perspectiva de la cámara, eso es lo que permite que se vean principalmente los elementos más cercanos a la cámara.

**¿Por qué se presenta el problema de la aliasing? ¿Qué es el anti-aliasing?**

El Aliasing es un caso en el que las aristas de los fragmentos interceptan a los píxeles por la mitad lo que genera que se vea irregular la forma. Es por esto que existe el anti-aliasing, que divide los píxeles con 16 puntos distintos y dependiendo de cuántos puntos se ven cubiertos será el valor del color que se encuentran en el Pixel. Es por eso que muchas veces los píxeles las orillas suelen ser más transparentes.

**¿Qué relación hay entre la iluminación y el fragment shader? Siempre es necesario tener en cuenta la iluminación en un fragment shader? o puedo hacer un fragment shader sin iluminación? Explica que implicaciones tiene esto.**

El Fragment shading es el encargado de calcular el color final de cada píxel basándose en diferentes factores como la iluminación. No es obligatorio llevar iluminación si lo que se desea es simular colores planos (cosa poco común). De resto es necesario para darle profundidad al objeto. La principal implicación de no ponerle la luz es que se vea un color plano cutre y también podría afectar a como percibimos las texturas ya que muchas dependen de la posición de la luz para que se vean

**¿Qué implica para la GPU que una aplicación tenga múltiples fuentes de iluminación?**

el hecho de que un programa tenga múltiples iluminaciones, requiere de que se generen miles de cálculos instantáneos para poder variar la tonalidad de cada una de las caras que conforman el fragmento de modelo visible a la cámara
