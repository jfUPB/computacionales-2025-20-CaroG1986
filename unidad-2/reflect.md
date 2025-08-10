# Unidad 2


## 🤔 Fase: Reflect

### Actividad 07

#### Parte 1

**Explica cómo se representa y manipula un puntero en el lenguaje ensamblador de Hack. Describe las operaciones equivalentes a ```p = &a```(asignar dirección) y ```*p = 20``` (escribir a través del puntero) usando instrucciones de ensamblador.**

El puntero en el lenguaje ensamblador de Hack se representa poniendo primero una @ y después como se quiera llamar, y este entonces va a ocupar una dirección en la memoria. Esas operaciones la primera se trata de guardar la dirección de a en el puntero y para representarla en lenguaje ensamblador sería: 

``` asm
@a
D=A
@p
M=D
```

La segunda instrucción se trata de escribir a través del puntero y se vería así:

``` asm
@a
D=A
@P
M=D
@20
D=A
@P
A=M
M=D
```

**¿Cómo implementarías el acceso a un elemento de un arreglo, como ```arr[j]```, en lenguaje ensamblador? Describe el rol de la dirección base del arreglo y el índice ```j```en esta operación.**

Para acceder a un elemento de un arreglo es importante comprender qué dichos arreglos y de una dirección base que en estos casos suelen ser a partir de la dirección de memoria 16 y que está se va sumando o restando gracias al índice j. Entonces si por ejemplo quisiera cambiar algo en algún elemento dentro del arreglo eso se podría lograr sumándole o restándole al índice, que es el encargado de buscar la dirección de memoria.

#### Parte 2

**¿Cuál fue el concepto más abstracto o difícil de “traducir” de C++ a ensamblador en esta unidad (punteros, ciclos, arreglos)? ¿Qué hiciste para lograr entenderlo?**

Para mí el concepto más difícil fueron los punteros, ya que muchas veces cuando te viaje hacer un ejercicio a través de estos no comprendía muy bien cómo funcionaba el que llamaban a otra dirección de memoria es por esto que muchas veces terminaba logrando lo que necesitaba el código, pero sin el puntero.

**En la Actividad 06 se sugirió construir el programa “PASO A PASO mediante pruebas”. ¿Cómo te ayudó este enfoque a manejar la complejidad del problema?**

El enfoque paso a paso me ayudó principalmente a la organización del código, ya que en un inicio logré hacer un código funcional sin embargo me di cuenta que tenía muchas partes sobrantes e innecesarias, y el poder después ver primero lo más básico y después volver lo más complejo logró que el código surgiera más rápido e incluso más corto y comprensible.

**Esta unidad fue el “puente” hacia C++. ¿Qué concepto de bajo nivel te sientes más seguro de poder identificar cuando lo veas implementado en C++?**

Para mí el concepto que va a ser más sencillo identificar serían los arreglos y los ciclos, ya que esos se ve muy claramente representados en el lenguaje de c++.

### Actividad 08

**Bitácora de Sara Ruíz Arboleda**

El código que ella plantea es funcional, sin embargo, es poco eficiente y aún más teniendo en cuenta que en el lenguaje ensamblador sí se puede generar un arreglo sin tener que escribir manualmente los números en cada dirección de memoria, y aún más sí dicho arreglo guardar números con cierto orden, como en este ejemplo donde sólo es que sumarle uno al dato anterior. Es por eso que creo que una mejora necesaria para ese trabajo sería cambiar la parte inicial en donde llena manualmente todas las direcciones memoria por una función más rápida y corta.

### Actividad 09

**Continuar: ¿Qué actividad, problema o explicación de esta unidad te ayudó más a entender la conexión entre el bajo y el alto nivel? ¿Qué debería mantener sin cambios?**

La actividad que me sirvió más para comprender las diferencias y conexión entre bajo y alto nivel fue la actividad de apply, ya que me ayudó a comprender cómo un computador leería una instrucción que era un lenguaje de alto nivel se ve tan sencilla como lo es un arreglo. 

**Dejar de hacer: ¿Hubo alguna actividad o concepto que te pareció redundante, demasiado confuso o que aportó poco valor a tu aprendizaje? ¿Qué eliminarías o modificarías?**

No, en realidad no creo que haya algo redundante o un poco importante, en general todo me ayudó.

**Empezar a hacer: ¿Qué idea tienes para mejorar la próxima unidad? ¿Hay algún tipo de recurso que te habría ayudado a entender mejor los punteros o los arreglos?**

Cómo que algo quería empezar a hacer para la próxima unidad es que si vamos a profundizar más en el lenguaje c++ debería empezar a comprender que símbolos se suelen utilizar para este código, ya que he trabajado con c# pero supongo que debe haber algunas diferencias entre los dos.

**Ritmo y Dificultad: en una escala del 1 (muy fácil/lento) al 5 (muy difícil/rápido), ¿Cómo calificarías el salto de dificultad de la Unidad 1 a la Unidad 2? ¿El ritmo fue adecuado? Justifica tu calificación.**

Creo que le daría un 3, es decir, fue un ritmo normal ya que no se sintió como algo tan pesado pero menos como algo repetitivo.

**Comentario Adicional: ¿Alguna otra cosa que quieras compartir sobre cómo te sentiste aprendiendo estos conceptos?**

En realidad creo que trabajar con el lenguaje ensamblador fue muy divertido, ya que a pesar de ser complejo pude darme la oportunidad de “desmenuzar” la lógica que se usa normalmente en la programación y tener una comprensión más profunda de cómo funciona la relación entre la máquina y el programa. 
