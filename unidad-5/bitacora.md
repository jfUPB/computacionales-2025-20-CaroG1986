# Bitácora de aprendizaje de la unidad 5

## 1.  **Diagnóstico inicial**

### Parte 1

**¿Qué es el encapsulamiento para ti? Describe una situación en la que te haya sido útil o donde hayas visto su importancia.**

El encapsulamiento es una forma de proteger el código para controlar los datos que se pueden cambiar o no de alguna parte, esto se hace con get y set, get para configurar la información que necesita el código y set para devolver lo que de cierta firma se pued "modificar" o leer. Personalmente, ha sido util cuando quiero que una variable de una clase no sea modificada, sino que se mantenga a través del código. 

**¿Qué es la herencia? ¿Por qué un programador decidiría usarla? Da un ejemplo simple.**

La herencia es un proceso en el cual clases hijas heredan las caracteristicas de una clase padre. Un programador podría usarla para asociar clases entre si y poder economizar código en clases con los mismos atributos. Por ejemplo: hay una clase padre llamada vehículos y esta tiene las siguientes clases hijas: Taxi, particular y bus; estas clases tienen características en común como sus partes y todas se pueden identificar como vehículos, sin embargo, también pueden tener ligeras diferencias como su tamaño o si es de ambito publico o privado.

**¿Qué es el polimorfismo? Describe con tus palabras qué significa que un código sea “polimórfico”.**

El polimorfismo es una caracteríatica que permite a alguna cosa ser capaz de adaptarse dependindo de la situación en la que este, algo así como un camaleon que se adapta según el ambiente. Cuando se describe un código como polimórfico normalmente nos referimos a que este es tan general que se puede adaptar, usando en mismo código para distintos resultados.

### Parte 2

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

Creo que la razón por la que el campo de nombre es private es porque este debe estar definido solo en la clase que la contiene y no deberia editarse fuera de este segmento, pero la propiedad Nombre es public para que use e muestre el nombre dependiendo de la clase en la que este, básicamente es gracias a esto que sin importar el caso da el nombre de la figura actual.

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

 ### Parte 3 

 **Memoria y herencia: cuando creas un objeto Rectangulo, este tiene Base, Altura y también Nombre. ¿Cómo te imaginas que se organizan esos tres datos en la memoria del computador para formar un solo objeto?**
 
**El mecanismo del polimorfismo: pensemos de nuevo en la llamada fig.Dibujar(). El compilador solo sabe que fig es una Figura. ¿Cómo decide el programa, mientras se está ejecutando, si debe llamar al Dibujar del Circulo o al del Rectangulo? Lanza algunas ideas o hipótesis.**

Creo que esto se debe a la siguiente parte del código 
``` c#
  List<Figura> misFiguras = new List<Figura>();

        misFiguras.Add(new Circulo(5.0));
        misFiguras.Add(new Rectangulo(4.0, 6.0));
        misFiguras.Add(new Circulo(10.0));
```

**La barrera del encapsulamiento: ¿Cómo crees que el compilador logra que no puedas acceder a un miembro private desde fuera de la clase? ¿Es algo que se revisa cuando escribes el código, o es una protección que existe mientras el programa se ejecuta? ¿Por qué piensas eso?**

### Parte 4


 
## 2.  **La pregunta inicial**

## 3.  **Registro de exploración:** 
> Aquí documentas cada ciclo de pregunta -> hipótesis -> experimento -> hallazgo -> reflexión.
> Debe ser rico en evidencia visual (código, capturas del depurador con anotaciones, diagramas).

## 4.  **Consolidación, autoevaluación y cierre:**
> [!CAUTION]
> Esta sección es OBLIGATORIA y central para tu evaluación
