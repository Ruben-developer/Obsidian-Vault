En este ejemplo, la clase `Singleton` tiene un constructor privado y una variable estática `instance`, que se inicializa como `null`. El método `getInstance()` comprueba si `instance` es `null`, y si lo es, crea una nueva instancia de `Singleton`. El método devuelve la instancia existente o la recién creada. El método `showMessage()` imprime un mensaje simple.

En el método `main()`, se llama al método `getInstance()` para obtener una instancia única del Singleton, y luego se llama al método `showMessage()` de esa instancia para imprimir el mensaje. Como hay sólo una instancia de `Singleton`, el mensaje se imprimirá sólo una vez.

```java
public class Singleton {
	private static Singleton instance;
	 
	private Singleton() {}
	
	public static Singleton getInstance() {
		if (instance == null) {
	        instance = new Singleton();
	    }
	    return instance;
	}
	
	public void showMessage() {
	    System.out.println("Hola, soy un Singleton");
	}
}
```

```java
public class Main {
	public static void main(String[] args) {
	    Singleton singleton = Singleton.getInstance();
	    singleton.showMessage();
	}
}
```