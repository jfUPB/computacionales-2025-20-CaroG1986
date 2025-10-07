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

