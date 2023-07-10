Una interfaz en Java es una colección de métodos abstractos y propiedades constantes que se utilizan para definir y especificar qué debe hacer una clase sin proporcionar implementación detallada. En resumen, una interfaz en Java es como un contrato que una clase debe cumplir

Ejemplo de interfaz:
```java 
interface Animal {
	// Métodos abstractos
	public void hacerSonido();
	public void comer();
}
```

Clase que implementa una interfaz:
```java
class Perro implements Animal {
	// Implementación de los métodos abstractos
	public void hacerSonido() {
	System.out.println("El perro ladra");
	}
	
	public void comer() {
		System.out.println("El perro come croquetas");
	}
}
```

Clase que utiliza la interfaz como parámetro:
```java
class Veterinario {
	public void curar(Animal animal) {
	// Realizar acciones de curación del animal
	}
}
```


# Interfaces funcionales 

Una interfaz funcional en Java es una interfaz que tiene exactamente un método abstracto y puede ser implementada mediante la expresión lambda.

```java
@FunctionalInterface
interface Saludador {
	public void saludar(String nombre);
}
```

```java
// Ejemplo de implementación de una interfaz funcional con expresión lambda
Saludador saludarEnConsola = (nombre) -> System.out.println("Hola " + nombre);
```

```java
// Ejemplo de uso de una interfaz funcional
public static void main(String[] args) {
  saludarEnConsola.saludar("Juan");
}
```

# Interfaces Más usadas de Java

## Runnable

Esta interfaz define un único método `run()` que se utiliza para encapsular un proceso que puede ejecutarse en segundo plano.

```java
public class MyRunnable implements Runnable{
    public void run(){
        // Código a ejecutar en segundo plano
    }
}

// Creando un nuevo hilo usando el objeto MyRunnable
Thread t = new Thread(new MyRunnable());
t.start();
```

## Comparable

Esta interfaz se utiliza para comparar dos objetos y se utiliza con frecuencia para ordenar objetos.

```java
public class Person implements Comparable<Person>{
	int age;
    String name;
    
    public int compareTo(Person p){
        return this.age - p.age;
    }
}

// Crear una ArrayList de objetos Person y ordenarlos
ArrayList<Person> people = new ArrayList<Person>();
people.add(new Person("John", 30));
people.add(new Person("Mary", 25));
Collections.sort(people);  // Ordena según la edad
```

## Iterable

Esta interfaz se utiliza para definir una iteración sobre un objeto, como por ejemplo un bucle foreach.

```java
public class MyIterable implements Iterable<String>{
    String[] strings = {"John", "Mary", "Tom"};
    
    public Iterator<String> iterator(){
        return new MyIterator();
    }
    
    private class MyIterator implements Iterator<String>{
        int current = 0;
        
        public boolean hasNext(){
            return current < strings.length;
        }
        
        public String next(){
            return strings[current++];
        }
        
        public void remove(){
            throw new UnsupportedOperationException();
        }
    }
}

// Usando foreach para iterar sobre el objeto MyIterable
MyIterable iterable = new MyIterable();
for(String s : iterable){
    System.out.println(s);
}
```

