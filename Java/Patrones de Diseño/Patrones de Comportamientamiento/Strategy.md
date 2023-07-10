## Propósito

**Strategy** es un patrón de diseño de comportamiento que te permite definir una familia de algoritmos, colocar cada uno de ellos en una clase separada y hacer sus objetos intercambiables.

##  Problema

Un día decidiste crear una aplicación de navegación para viajeros ocasionales. La aplicación giraba alrededor de un bonito mapa que ayudaba a los usuarios a orientarse rápidamente en cualquier ciudad.

Una de las funciones más solicitadas para la aplicación era la planificación automática de rutas. Un usuario debía poder introducir una dirección y ver la ruta más rápida a ese destino mostrado en el mapa.

La primera versión de la aplicación sólo podía generar las rutas sobre carreteras. Las personas que viajaban en coche estaban locas de alegría. Pero, aparentemente, no a todo el mundo le gusta conducir durante sus vacaciones. De modo que, en la siguiente actualización, añadiste una opción para crear rutas a pie. Después, añadiste otra opción para permitir a las personas utilizar el transporte público en sus rutas.

Sin embargo, esto era sólo el principio. Más tarde planeaste añadir la generación de rutas para ciclistas, y más tarde, otra opción para trazar rutas por todas las atracciones turísticas de una ciudad.

Aunque desde una perspectiva comercial la aplicación era un éxito, la parte técnica provocaba muchos dolores de cabeza. Cada vez que añadías un nuevo algoritmo de enrutamiento, la clase principal del navegador doblaba su tamaño. En cierto momento, la bestia se volvió demasiado difícil de mantener.

Cualquier cambio en alguno de los algoritmos, ya fuera un sencillo arreglo de un error o un ligero ajuste de la representación de la calle, afectaba a toda la clase, aumentando las probabilidades de crear un error en un código ya funcional.

Además, el trabajo en equipo se volvió ineficiente. Tus compañeros, contratados tras el exitoso lanzamiento, se quejaban de que dedicaban demasiado tiempo a resolver conflictos de integración. Implementar una nueva función te exige cambiar la misma clase enorme, entrando en conflicto con el código producido por otras personas.

## Solución

El patrón Strategy sugiere que tomes esa clase que hace algo específico de muchas formas diferentes y extraigas todos esos algoritmos para colocarlos en clases separadas llamadas _estrategias_.

La clase original, llamada _contexto_, debe tener un campo para almacenar una referencia a una de las estrategias. El contexto delega el trabajo a un objeto de estrategia vinculado en lugar de ejecutarlo por su cuenta.

La clase contexto no es responsable de seleccionar un algoritmo adecuado para la tarea. En lugar de eso, el cliente pasa la estrategia deseada a la clase contexto. De hecho, la clase contexto no sabe mucho acerca de las estrategias. Funciona con todas las estrategias a través de la misma interfaz genérica, que sólo expone un único método para disparar el algoritmo encapsulado dentro de la estrategia seleccionada.

De esta forma, el contexto se vuelve independiente de las estrategias concretas, así que puedes añadir nuevos algoritmos o modificar los existentes sin cambiar el código de la clase contexto o de otras estrategias.

![[Pasted image 20230706114631.png]]

En nuestra aplicación de navegación, cada algoritmo de enrutamiento puede extraerse y ponerse en su propia clase con un único método `buildRoute`. El método acepta un origen y un destino y devuelve una colección de puntos de control de la ruta.

Incluso contando con los mismos argumentos, cada clase de enrutamiento puede crear una ruta diferente. A la clase `Navigator` principal no le importa qué algoritmo se selecciona ya que su labor principal es representar un grupo de puntos de control en el mapa. La clase tiene un método para cambiar la estrategia activa de enrutamiento, de modo que sus clientes, como los botones en la interfaz de usuario, pueden sustituir el comportamiento seleccionado de enrutamiento por otro.

## Analogía en el mundo real

Imagina que tienes que llegar al aeropuerto. Puedes tomar el autobús, pedir un taxi o ir en bicicleta. Éstas son tus estrategias de transporte. Puedes elegir una de las estrategias, dependiendo de factores como el presupuesto o los límites de tiempo.

## Estructura

![[Pasted image 20230706115050.png]]

1. La clase **Contexto** mantiene una referencia a una de las estrategias concretas y se comunica con este objeto únicamente a través de la interfaz estrategia.

2. La interfaz **Estrategia** es común a todas las estrategias concretas. Declara un método que la clase contexto utiliza para ejecutar una estrategia.

3. Las **Estrategias Concretas** implementan distintas variaciones de un algoritmo que la clase contexto utiliza.

4. La clase contexto invoca el método de ejecución en el objeto de estrategia vinculado cada vez que necesita ejecutar el algoritmo. La clase contexto no sabe con qué tipo de estrategia funciona o cómo se ejecuta el algoritmo.

5. El **Cliente** crea un objeto de estrategia específico y lo pasa a la clase contexto. La clase contexto expone un modificador _set_ que permite a los clientes sustituir la estrategia asociada al contexto durante el tiempo de ejecución.

##  Pseudocódigo

En este ejemplo, el contexto utiliza varias **estrategias** para ejecutar diversas operaciones aritméticas.

La interfaz `Strategy` declara operaciones comunes a todas las versiones soportadas de algún algoritmo. El contexto utiliza esta interfaz para invocar el algoritmo definido por las estrategias concretas. 
```java
public interface Strategy {
    public int execute(int a, int b);
}
```

Las estrategias concretas implementan el algoritmo mientras siguen la interfaz estrategia base. La interfaz las hace intercambiables en el contexto.

```java
public class ConcreteStrategyAdd implements Strategy {
    public int method execute(int a, int b){
	    return a + b;
    }
}
```

```java
public class ConcreteStrategySubtract implements Strategy {
    public int method execute(int a, int b){
	    return a - b;
    }
}
```

```java
public class ConcreteStrategyMultiply implements Strategy {
    public int method execute(int a, int b){
	    return a ** b;
    }
}
```

El contexto define la interfaz de interés para los clientes.
 
El contexto mantiene una referencia a uno de los objetos de estrategia. El contexto no conoce la clase concreta de una estrategia. Debe trabajar con todas las estrategias a través de la interfaz estrategia.

Normalmente, el contexto acepta una estrategia a través del constructor y también proporciona un setter (modificador) para poder cambiar la estrategia durante el tiempo de ejecución.

El contexto delega parte del trabajo al objeto de estrategia en lugar de implementar varias versiones del algoritmo por su cuenta.
 
```java
public class Context {
	
	private Strategy strategy;
	   
	public void setStrategy(Strategy strategy) {
		this.strategy = strategy;
	}
	   
    public int executeStrategy(int a, int b) {
        return strategy.execute(a, b);
    }
}
```

El código cliente elige una estrategia concreta y la pasa al contexto. El cliente debe conocer las diferencias entre estrategias para elegir la mejor opción.

```java
public class ExampleApplication {
    public static void main(String[] args) {
        
        // Crear objeto Contexto.
        Context context = new Context();
		
        // Leer el primer número.
		Scanner scanner = new Scanner(System.in);
        System.out.print("Ingrese el primer número: ");
        int num1 = scanner.nextInt();
		
        // Leer el segundo número.
        System.out.print("Ingrese el segundo número: ");
        int num2 = scanner.nextInt();
		
        // Leer la acción deseada.
        System.out.print("Ingrese la acción deseada (1 suma, 2 resta, 3 multiplicación): ");
        int action = scanner.nextInt();
		
        // Elegir la estrategia adecuada.
        if (action == 1) {
            context.setStrategy(new ConcreteStrategyAdd());
        } else if (action == 2) {
            context.setStrategy(new ConcreteStrategySubtract());
        } else if (action == 3) {
            context.setStrategy(new ConcreteStrategyMultiply());
        } else {
            System.out.println("Acción no válida.");
            return;
        }
		
		// Ejecutar la estrategia y mostrar el resultado.
        int result = context.executeStrategy(num1, num2);
        System.out.println("El resultado es: " + result);
    }
}
```

##  Aplicabilidad

 Utiliza el patrón Strategy cuando quieras utiliza distintas variantes de un algoritmo dentro de un objeto y poder cambiar de un algoritmo a otro durante el tiempo de ejecución.

 El patrón Strategy te permite alterar indirectamente el comportamiento del objeto durante el tiempo de ejecución asociándolo con distintos subobjetos que pueden realizar subtareas específicas de distintas maneras.

 Utiliza el patrón Strategy cuando tengas muchas clases similares que sólo se diferencien en la forma en que ejecutan cierto comportamiento.

 El patrón Strategy te permite extraer el comportamiento variante para ponerlo en una jerarquía de clases separada y combinar las clases originales en una, reduciendo con ello el código duplicado.

 Utiliza el patrón para aislar la lógica de negocio de una clase, de los detalles de implementación de algoritmos que pueden no ser tan importantes en el contexto de esa lógica.

 El patrón Strategy te permite aislar el código, los datos internos y las dependencias de varios algoritmos, del resto del código. Los diversos clientes obtienen una interfaz simple para ejecutar los algoritmos y cambiarlos durante el tiempo de ejecución.

 Utiliza el patrón cuando tu clase tenga un enorme operador condicional que cambie entre distintas variantes del mismo algoritmo.

 El patrón Strategy te permite suprimir dicho condicional extrayendo todos los algoritmos para ponerlos en clases separadas, las cuales implementan la misma interfaz. El objeto original delega la ejecución a uno de esos objetos, en lugar de implementar todas las variantes del algoritmo.

##  Cómo implementarlo

1. En la clase contexto, identifica un algoritmo que tienda a sufrir cambios frecuentes. También puede ser un enorme condicional que seleccione y ejecute una variante del mismo algoritmo durante el tiempo de ejecución.

2. Declara la interfaz estrategia común a todas las variantes del algoritmo.

3. Uno a uno, extrae todos los algoritmos y ponlos en sus propias clases. Todas deben implementar la misma interfaz estrategia.

4. En la clase contexto, añade un campo para almacenar una referencia a un objeto de estrategia. Proporciona un modificador _set_ para sustituir valores de ese campo. La clase contexto debe trabajar con el objeto de estrategia únicamente a través de la interfaz estrategia. La clase contexto puede definir una interfaz que permita a la estrategia acceder a sus datos.

5. Los clientes de la clase contexto deben asociarla con una estrategia adecuada que coincida con la forma en la que esperan que la clase contexto realice su trabajo principal.

## Pros 

-  Puedes intercambiar algoritmos usados dentro de un objeto durante el tiempo de ejecución.
-  Puedes aislar los detalles de implementación de un algoritmo del código que lo utiliza.
-  Puedes sustituir la herencia por composición.
-  _Principio de abierto/cerrado_. Puedes introducir nuevas estrategias sin tener que cambiar el contexto.

## Contras

- Si sólo tienes un par de algoritmos que raramente cambian, no hay una razón real para complicar el programa en exceso con nuevas clases e interfaces que vengan con el patrón.
-  Los clientes deben conocer las diferencias entre estrategias para poder seleccionar la adecuada.
-  Muchos lenguajes de programación modernos tienen un soporte de tipo funcional que te permite implementar distintas versiones de un algoritmo dentro de un grupo de funciones anónimas. Entonces puedes utilizar estas funciones exactamente como habrías utilizado los objetos de estrategia, pero sin saturar tu código con clases e interfaces adicionales.

##  Relaciones con otros patrones

- [Bridge](https://refactoring.guru/es/design-patterns/bridge), [State](https://refactoring.guru/es/design-patterns/state), [Strategy](https://refactoring.guru/es/design-patterns/strategy) (y, hasta cierto punto, [Adapter](https://refactoring.guru/es/design-patterns/adapter)) tienen estructuras muy similares. De hecho, todos estos patrones se basan en la composición, que consiste en delegar trabajo a otros objetos. Sin embargo, todos ellos solucionan problemas diferentes. Un patrón no es simplemente una receta para estructurar tu código de una forma específica. También puede comunicar a otros desarrolladores el problema que resuelve.

- [Command](https://refactoring.guru/es/design-patterns/command) y [Strategy](https://refactoring.guru/es/design-patterns/strategy) pueden resultar similares porque puedes usar ambos para parametrizar un objeto con cierta acción. No obstante, tienen propósitos muy diferentes.
    
    - Puedes utilizar _Command_ para convertir cualquier operación en un objeto. Los parámetros de la operación se convierten en campos de ese objeto. La conversión te permite aplazar la ejecución de la operación, ponerla en cola, almacenar el historial de comandos, enviar comandos a servicios remotos, etc.
    
    - Por su parte, _Strategy_ normalmente describe distintas formas de hacer lo mismo, permitiéndote intercambiar estos algoritmos dentro de una única clase contexto.
    
- [Decorator](https://refactoring.guru/es/design-patterns/decorator) te permite cambiar la piel de un objeto, mientras que [Strategy](https://refactoring.guru/es/design-patterns/strategy) te permite cambiar sus entrañas.

- [Template Method](https://refactoring.guru/es/design-patterns/template-method) se basa en la herencia: te permite alterar partes de un algoritmo extendiendo esas partes en subclases. [Strategy](https://refactoring.guru/es/design-patterns/strategy) se basa en la composición: puedes alterar partes del comportamiento del objeto suministrándole distintas estrategias que se correspondan con ese comportamiento. _Template Method_ trabaja al nivel de la clase, por lo que es estático. _Strategy_ trabaja al nivel del objeto, permitiéndote cambiar los comportamientos durante el tiempo de ejecución.

- [State](https://refactoring.guru/es/design-patterns/state) puede considerarse una extensión de [Strategy](https://refactoring.guru/es/design-patterns/strategy). Ambos patrones se basan en la composición: cambian el comportamiento del contexto delegando parte del trabajo a objetos ayudantes. _Strategy_ hace que estos objetos sean completamente independientes y no se conozcan entre sí. Sin embargo, _State_ no restringe las dependencias entre estados concretos, permitiéndoles alterar el estado del contexto a voluntad.