Es el concepto que consiste en ocultar atributos de un objeto de manera que solo se pueda cambiar mediante operaciones definidas en ese objeto

Ejemplo de una clase básica en Java:
```java
public class Persona {
	// Variables de instancia
	private String nombre;
	private int edad;
	
	// Constructor de la clase
	public Persona(String nombre, int edad) {
		this.nombre = nombre;
		this.edad = edad;
	}
	
	// Métodos de la clase
	public void saludar() {
		System.out.println("Hola, mi nombre es " + this.nombre + " y tengo " + this.edad + " años.");
	}
}
```

```java
// Ejemplo de creación y uso de un objeto de la clase Persona
public static void main(String[] args) {
	Persona juan = new Persona("Juan", 25);
	juan.saludar();
}
```

# Clases Abstractas

Una clase abstracta en Java es una clase que tiene la palabra clave "abstract" en su definición y que no puede ser instanciada directamente, sino que sirve como una plantilla para otras clases que la extienden. Las clases abstractas pueden tener métodos abstractos que deben ser implementados por las clases que las extienden.

Ejemplo de una clase abstracta básica en Java:
```java
public abstract class Animal {
	// Variables de instancia
	private String nombre;
	
	// Constructor de la clase
	public Animal(String nombre) {
	    this.nombre = nombre;
	}
	
	// Métodos abstractos de la clase
	public abstract void hacerSonido();
}
```

Ejemplo de una clase que extiende una clase abstracta:
```java
public class Perro extends Animal {
	// Constructor de la clase
	public Perro(String nombre) {
		super(nombre);
	}
	
	// Implementación del método abstracto
	public void hacerSonido() {
		System.out.println("El perro ladra");
	}
}
```

Ejemplo de creación y uso de un objeto de la clase Perro:
```java
public static void main(String[] args) {
	Perro fido = new Perro("Fido");
	fido.hacerSonido();
}
```