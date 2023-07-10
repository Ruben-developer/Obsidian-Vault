A continuación se presentan 2 extractos de código en lenguaje Java 1.8, para el desafío de 23People:

## 1. Contar vocales con recursividad

```java
public static int recCountVowels(String text) {
    if (text.length() == 0) {
	    return 0;
    } else {
        char letter = text.charAt(0);
        int count = 0;
        if (letter == 'a' || letter == 'e' || letter == 'i' || letter == 'o' 
			|| letter == 'u' || letter == 'á' || letter == 'é' || letter == 'í' 
			|| letter == 'ó' || letter == 'ú' || letter == 'A' || letter == 'E' 
			|| letter == 'I' || letter == 'O' || letter == 'U') {
            count = 1;
        }
        return contador + recCountVowels(string.substring(1));
    }
}
```

Este código es una función en Java que cuenta el número de vocales en una cadena de texto. La función utiliza un enfoque recursivo para contar las vocales.

La función toma una cadena de texto como entrada y devuelve un entero que representa el número de vocales en la cadena.

Para hacerlo, la función utiliza una llamada recursiva a si misma para contar las vocales en la subcadena de la cadena original que se obtiene al eliminar el primer carácter de la cadena.

## 1.1. Contar vocales con recursividad (Refactorizado)

```java
public static int recCountVowels(String text) {
    if (text.isEmpty()) {
        return 0;
	}
    if ("AEIOUáéíóúaeiou".indexOf(text.charAt(0)) >= 0) {
		return 1 + recCountVowels(text.substring(1));
	}
    return recCountVowels(text.substring(1));
}

```

En la primera línea, se declara una función llamada `recCountVowels` que toma una cadena de texto `text` como entrada y devuelve un entero que representa el número de vocales en la cadena.

Después, utiliza una declaración `if` para comprobar si la cadena `text` está vacía. Si es así, la función devuelve 0, ya que no hay vocales que contar en una cadena vacía.

Si la cadena no está vacía, se utiliza otra declaración `if` para comprobar si el primer carácter de la cadena es una vocal. Si es así, la función devuelve 1 más la llamada recursiva a sí misma con la subcadena de la cadena original que se obtiene al eliminar el primer carácter de la cadena.

Finalmente, si el primer carácter de la cadena no es una vocal, la función devuelve simplemente la llamada recursiva a sí misma con la subcadena de la cadena original que se obtiene al eliminar el primer carácter de la cadena.

Esta versión refactorizada del código permite tratar el caso de cadena vacía en una sola instrucción `if`, eliminando así un nivel de indentación.

## 2. Encontrar el valor mínimo en un arreglo

```java
public static int min(Integer[] arr) {
    if (arr.length == 1) {
        return arr[0];
	}
	Integer[] subArr = new Integer[arr.length-1];
	for (int i = 0; i < subArr.length; i++) {
		subArr[i] = arr[i+1];
	}
	Integer minSubArr = min(subArr);
	return Math.min(arr[0], minSubArr);
}
```

Este código es una función de java que se utiliza para calcular el valor mínimo de un arreglo de enteros. La función utiliza un enfoque recursivo.

El método `min` toma como parámetro un arreglo de enteros llamado `arr`. Comienza con una declaración if. Si el tamaño del arreglo es 1, simplemente devuelve el primer elemento del arreglo `arr` usando `return arr[0];` ya que este es el valor mínimo (en este caso, el único valor en el arreglo).

En caso contrario, crea otro arreglo llamado `subArr` que es un arreglo que contiene todos los elementos de `arr` excepto el primer elemento. Luego, dentro del ciclo for, se transfiere cada elemento del arreglo original `arr` al arreglo `subArr`.

Después de eso, llama recursivamente el método `min` con `subArr` para encontrar el valor mínimo de `subArr`. Esto significa que esto se repetirá constantemente hasta que el arreglo tenga un tamaño de 1.

Finalmente, usa la función `Math.min` para encontrar el mínimo entre el primer elemento del arreglo original `arr` y el valor mínimo encontrado recursivamente en el arreglo `subArr`, y devuelve el valor mínimo de esta operación.

En resumen, el método `min` es un método recursivo que funciona para calcular el valor mínimo de un arreglo de enteros. Utiliza la recursión para romper el arreglo en piezas más pequeñas hasta que se llega al caso base donde el arreglo solo tiene un elemento, y luego utiliza la función `Math.min` para encontrar el mínimo entre los valores del arreglo.