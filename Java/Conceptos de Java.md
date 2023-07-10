## Multiplataforma

Significa que una aplicación o programa desarrollado en Java puede ser ejecutado en diferentes plataformas y sistemas operativos sin necesidad de hacer cambios en el código fuente . Un programa escrito para Java se compila a un bytecode que luego se puede ejecutar en cualquier sistema que tenga una JVM (Java Virtual Machine) instalada, lo que permite su portabilidad y reutilización en diferentes sistemas y dispositivos. Esto facilita la tarea de desarrollar y distribuir aplicaciones que funcionen en múltiples plataformas, lo que a su vez se traduce en una mayor accesibilidad y satisfacción del usuario final.

## Programación orientada a Objetos

Es un paradigma de programación que se basa en la creación de objetos, los cuales se pueden definir como una unidad de datos que combina atributos (variables) y métodos (funciones) para interactuar con el mundo exterior. [[Principios de la POO]]

## Modularidad

La modularidad es la propiedad de un sistema que permite descomponerlo en partes más pequeñas y manejables. En informática, la modularidad se refiere específicamente a la propiedad que permite dividir una aplicación en módulos o unidades autónomas que pueden interactuar entre sí, sin que sea necesario conocer los detalles de implementación de cada uno. La modularidad hace que el diseño, la construcción, la depuración y el mantenimiento de una aplicación sea más sencillo, ya que cada módulo puede ser desarrollado, probado y mantenido de forma independiente.

## Inmutabilidad

La inmutabilidad en Java se refiere a la propiedad de un objeto cuyo estado no se puede modificar una vez que se ha creado. En otras palabras, los objetos inmutables en Java son aquellos que no pueden cambiar su estado después de la construcción. Esta característica se logra al definir todos los atributos de la clase como "final" y proporcionar sólo constructor que inicialice todos los atributos. Los objetos inmutables son muy útiles en la programación concurrente ya que son seguros de compartir entre múltiples threads sin necesidad de locking y también facilitan el diseño de software, reduciendo la complejidad del código y mejorando la eficiencia.

Threads: Se refieren a los hilos de ejecución o tareas concurrentes que se pueden crear en un programa Java utilizando la clase Thread. Los hilos permiten que un programa realice varias tareas al mismo tiempo, lo que aumenta la eficiencia y rendimiento del programa.

Locking: Se refiere a la técnica que utiliza Java para garantizar que los threads accedan a los recursos compartidos de manera sincronizada.

___

## [[Clases]]

Una clase en Java es una plantilla para la creación de objetos que define los atributos y los métodos comunes a esos objetos. Es uno de los elementos fundamentales de la programación orientada a objetos en Java y permite crear objetos de un tipo determinado con los mismos atributos y comportamientos.

## Objeto

Es el concepto que consiste en ocultar atributos de un objeto de manera que solo se pueda cambiar mediante operaciones definidas en ese objeto

## Instancia

Creación en tiempo de ejecución de un clase. Se realiza con la palabra reservada "new"

## [[Interfaces]]

Una interfaz en Java es una colección de métodos abstractos y propiedades constantes que se utilizan para definir y especificar qué debe hacer una clase sin proporcionar implementación detallada. En resumen, una interfaz en Java es como un contrato que una clase debe cumplir.

## [[Colecciones]]

En Java, las colecciones son estructuras de datos que permiten almacenar y manipular grupos de objetos. Las colecciones pueden almacenar cualquier tipo de objeto y se pueden utilizar para realizar una amplia variedad de operaciones, como la búsqueda, la ordenación, la eliminación y la inserción de elementos. 

El framework de colecciones de Java proporciona varias estructuras de datos genéricas, como listas, conjuntos y mapas, que se pueden utilizar para almacenar diferentes tipos de objetos y realizar diferentes tipos de operaciones sobre ellos.

## [[Exceptions]]

Las excepciones en Java son eventos que ocurren durante la ejecución de un programa y que interrumpen el flujo normal del mismo. Java utiliza excepciones para manejar situaciones de error y para proporcionar una forma estructurada de tratar problemas en el código. Cuando se produce una excepción, el programa puede capturarla y manejarla de forma adecuada para asegurarse de que el programa continúe ejecutándose sin problemas. Las excepciones en Java se pueden lanzar manualmente mediante el uso de la palabra clave "throw" y se pueden capturar y controlar mediante el uso de las palabras clave "try" y "catch".

## Garbage collector y el manejo de memoria

El garbage collector es un mecanismo automático que se encarga de gestionar la memoria en algunos lenguajes de programación, incluyendo Java. El manejo de memoria en Java se refiere al proceso de asignar y liberar recursos de memoria durante la ejecución del programa. 

Su función es liberar la memoria utilizada por objetos que ya no son referenciados ni utilizados por el programa, con el objetivo de evitar fugas de memoria y mejorar el rendimiento del programa. En resumen, el garbage collector es una herramienta importante para el manejo de memoria en los programas modernos en Java

## Pruebas Unitarias y de integración

Las pruebas unitarias en Java son un tipo de prueba que se utiliza para asegurarse de que pequeñas porciones de código funcionen correctamente, de manera individual y desacoplada de otras partes del programa. Por otro lado, las pruebas de integración en Java son un tipo de prueba que se utiliza para asegurarse de que diferentes componentes de un programa trabajen correctamente juntos, después de ser integrados. En resumen, las pruebas unitarias se centran en una parte específica del programa, mientras que las pruebas de integración se centran en el conjunto de componentes. algunas de las herramientas son [[Junit]], [[Mockito]], [[Mockserver]]

