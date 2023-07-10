En este ejemplo, se define la interfaz `Product`, que tiene un método `print()` que se implementa en la clase `ConcreteProduct`. La clase abstracta `Creator` tiene un método `factoryMethod()` que devuelve un objeto de tipo `Product`. La clase `ConcreteCreator` extiende `Creator` e implementa el método `factoryMethod()`, devolviendo un objeto de tipo `ConcreteProduct`.

En el método `main()`, se crea un objeto de tipo `ConcreteCreator` y se llama al método `factoryMethod()`, que devuelve un objeto de tipo `ConcreteProduct`. Se llama al método `print()` del objeto `ConcreteProduct` para imprimir "ConcreteProduct" en la consola.

```java
interface Product {
    void print();
}
```

```java
class ConcreteProduct implements Product {
    public void print() {
        System.out.println("ConcreteProduct");
    }
}
```

```java
abstract class Creator {
	public abstract Product factoryMethod();
}
```

```java
class ConcreteCreator extends Creator {
    public Product factoryMethod() {
        return new ConcreteProduct();
    }
}
```

```java
public class Main {
    public static void main(String args[]) {
        Creator creat = new ConcreteCreator();
        Product product = creat.factoryMethod();
        product.print();
    }
}
```