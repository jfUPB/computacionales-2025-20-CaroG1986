# Unidad 1

## 🤔 Fase: Reflect

### Actividad 05 

#### Parte 1: recuperación de conocimiento (retrieval practice)

_Describe con tus palabras las tres fases del ciclo Fetch-Decode-Execute. ¿Qué rol juega el Program Counter (PC) en este ciclo?_

La fase Fetch se refiere a leer el código o las instrucciones que se le asignan al programa; la fase Decode se traduce a decodificar, es decir, cuando el computador traduce la información que le llega a una instrucción ; finalmente la fase Execute se trata de ejecutar el programa com tal, siguiendo las instrucciones ya codificadas. En todas estas fases el Program Counter (PC) es fundamental ya que su programación es la encargada de leer, decodificar y ejecutar las instrucciones asignadas.

_¿Cuál es la diferencia fundamental entre una instrucción-A (que empieza con @) y una instrucción-C (que involucra D, M, A, etc.) en el lenguaje ensamblador de Hack? Da un ejemplo de cada una._

Las intrucciones tipo A son aquellas que permiten ingresar un número en el registro A, se utilizan para llamar una dirección de memoria RAM, por ejemplo la instrucción @0 cambia el registro A a 0 y llama a la primera dirección de memoria; por otro lado las instrucciones tipo C son aquellas que requieren resolver un problema lógico-matemático, como por ejemplo comparar, sumar, restar, etc.  

_Explica la función de los siguientes componentes del computador Hack: el registro D, el registro A y la ALU._

El registro D es aquel que guarda un dato que después puede ser asignado a una dirección de memoria; el resgistro A llama a una dirección de memoria y la ALU (Arithmetic Logic Unit) se trada de las instrucciones del sistema relacionadas con el procesamiento lógico (+,-,>,etc).

_¿Cómo se implementa un salto condicional en Hack? Describe un ejemplo (p. ej., saltar si el valor de D es mayor que cero)._

En ese caso simplemente se indicaria con el salto respectivo 
``` asm
@0
D;JGT
```
_¿Cómo se implementa un loop en el computador Hack? Describe un ejemplo (p. ej., un loop que decremente un valor hasta que llegue a cero)._

Un loop se implementa marcando una etiqueta que indique el inicio del loop.

``` asm
@5
D=A
@0
M=D

(LOOP)
M=M-1
D=M
@END
D;JLE
@LOOP
0;JMP

(END)
@7
M=D
```
En este ejemplo se usa el número 5 como guia y se va restando hasta que llega a 0 y el ciclo se rompe.

_¿Cuál es la diferencia entre la instrucción D=M y la instrucción M=D?_

La instrucción D=M significa que el registro D toma el valor que se encuentra en la dirección de memoria actual y la instrucción M=D significa que la dirección de memoria actual toma el alor que se encuentra en el resgistro D.

_Describe brevemente qué se necesita para leer un valor del teclado (KBD) y para “pintar” un pixel en la pantalla (SCREEN)._

En este caso se podría leer el número que se encuentra en la dirección de memoria dle teclado y en caso de ser mayor a 0 cambiarian los datos en la memoria RAM de la pantalla para que así los pixeles cambien de color.

#### Parte 2: reflexión sobre tu proceso (metacognición)

_¿Cuál fue el concepto o actividad más desafiante de esta unidad para ti y por qué?_

Para mi fue la actividad 03, porque fue algo confuso la forma en la que organize las etiquetas originalmente para el loop y llegué a enrredarme mucho.

_La metodología de “predecir, ejecutar, observar y reflexionar” fue central en nuestras actividades. ¿En qué momento esta metodología te resultó más útil para entender algo que no tenías claro?_

Ese momento fue en el caso anterior, ya que el ejecutar el código me permitió comprender el porque no funcionaba y tomar una nueva ruta de acción.

_Describe un momento “¡Aha!” que hayas tenido durante estas dos semanas. ¿Qué estabas haciendo cuando ocurrió?_

Cuando al leer el documento comprendi bien los conceptos y herramientas que usa el computador Hack, porque antes sentía que estaba tranajando sobre la nada peor tomarme el tiempo de entender la teoría me ayudo mucho.

_Pensando en la próxima unidad, ¿Qué harás diferente en tu proceso de estudio para aprender de manera más efectiva?_

Personalmente me gustaría tener un tiempo más extenso para poder solucionar de forma oportuna las actividades planteadas en las unidades y poder hacer más ejemplos que me permitan prácticar más.

### Actividad 06

#### Retroalimentación : Sara Ruiz

Actividad 01: Me gusta mucho la forma en la que tiene redactada su bitacora porque se siente como un proceso muy personal, usa un lenguaje informal de modo que pueda entandorlo más fácil despúes. Además la actividad se ve completa, aunque tal vez profundizaría más en algunas respuestas.

Actividad 02: La actividad 2 esta muy clara, se comprende facilmente su análisis y se nota su interes en traducir todo a su propio lenguaje. 

Actividad 03: La actividad cumple con el analizar como funciona el código planteado.

Actividad 04: El código esta muy bien, pero se siente un poco confuso por su forma de organizarlo.

### Actividad 07

_Continuar: ¿Qué aspecto de las actividades, las explicaciones o la dinámica de la clase te ha resultado más útil o te ha gustado más y debería seguir haciendo?_

Me gustó el poder ver línea por línea del código para comprender cuál era su significado ya que nunca antes había trabajado con lenguaje ensamblador y esto logró que se viera más sencillo.

_Dejar de hacer: ¿Qué aspecto de la unidad te ha resultado confuso, poco útil o frustrante? ¿Hay algo que crees que debería eliminar o cambiar drásticamente?_

Creo que no hay algo en específico que esté mal, creo que tal vez el mayor problema sería el tiempo que hay para hacer sus actividades ya que normalmente deben hacerse entre semana y eso hace un poco más complicado sacarles el espacio.

_Empezar a hacer: ¿Qué te habría gustado que hiciéramos que no hicimos? ¿Tienes alguna idea para una actividad o un recurso que podría mejorar el aprendizaje en la próxima unidad?_

Tal vez hacer códigos en clase que incorporen más retos en cuanto a la lógica que se debe usar, ya que a veces es complicado hacer ciertas actividades sin haber practicado o repasado más antes.

_Ritmo y Dificultad: en una escala del 1 (muy fácil/lento) al 5 (muy difícil/rápido), ¿Cómo calificarías el ritmo y la dificultad general de esta unidad? ¿Por qué?_

Yo creo que un tres, es decir, va un buen ritmo ya que como acabamos de empezar no se siente como un gran apuro en cuanto a los temas.

_Comentario Adicional: ¿Hay algo más que te gustaría compartir sobre tu experiencia de aprendizaje en esta unidad?_

En sí está unidad me pareció muy interesante ya que a pesar de que usamos programas súper sencillos se pudo identificar bien cómo funcionaban, cuál era su relación con la cpu y cómo utilizar el lenguaje de ensamblador. Además se comprendió muy bien cómo los computadores leen los códigos y los transforman de forma que estos puedan ejecutar un programa.
