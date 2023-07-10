Excepciones de tiempo de ejecución (RuntimeException): estas excepciones suelen ser causadas por errores en tiempo de ejecución y no se comprueban en tiempo de compilación. Algunos ejemplos incluyen NullPointerException, ArrayIndexOutOfBoundsException y ClassCastException.

Excepciones comprobadas (Checked Exceptions): estas excepciones se deben manejar explícitamente en el código. Algunos ejemplos incluyen IOException, SQLException y ClassNotFoundException.

```java
// Ejemplo de excepción de tiempo de ejecución
String s = null;
System.out.println(s.length()); // Esto lanzará una excepción NullPointerException
```

```java 
// Ejemplo de excepción comprobada
try {
	FileReader reader = new FileReader("archivo.txt");
    // Leer el archivo aquí
} catch (FileNotFoundException e) {
    e.printStackTrace();
}
```

## Otros ejemplos de exception 

- Excepciones de entrada/salida (IOException): se lanzan cuando ocurren errores en la entrada o salida de datos. Por ejemplo:

```java
try {
    FileReader reader = new FileReader("archivo.txt");
    // Leer el archivo aquí
} catch (IOException e) {
    e.printStackTrace();
}
```

- Excepciones aritméticas (ArithmeticException): se lanzan cuando ocurren errores matemáticos, como división por cero. Por ejemplo:

```java
int a = 5;
int b = 0;
try {
    int resultado = a / b;
} catch (ArithmeticException e) {
    e.printStackTrace();
}
```

- Excepciones de conversión de tipo (ClassCastException): se lanzan cuando intentas hacer una conversión de objetos entre clases que no son compatibles. Por ejemplo:

```java
Object x = new Integer(0);
String s = (String) x; // Esto lanzará una excepción de ClassCastException
```

- Excepciones personalizadas: también puedes crear tus propias excepciones personalizadas en Java. Por ejemplo:

```java
class MiExcepcion extends Exception {
    // Código de la excepción personalizada aquí
}
```

![[Pasted image 20230705114108.png]]