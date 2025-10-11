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
