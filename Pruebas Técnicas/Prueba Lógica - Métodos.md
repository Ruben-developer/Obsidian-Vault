## 1. Invertir Texto

Este código define un método llamado `reverseText` que toma una cadena de texto como argumento y la invierte, es decir, devuelve la cadena con los caracteres en orden inverso.

Primero, la cadena de texto se divide en un array de strings utilizando el método `split()`, que utiliza un string vacío como delimitador, lo que significa que cada carácter de la cadena original se convierte en un elemento del array.

A continuación, se inicializa un `StringBuilder` llamado `newText` para almacenar el texto invertido.

Se utiliza un bucle `for` para iterar sobre el array de texto desde el final hasta el principio. Para cada elemento en el array, se agrega el elemento al `StringBuilder` utilizando el método `append()`.

Finalmente, se imprime la cadena invertida utilizando el método `toString()` del `StringBuilder`.

En resumen, el método `reverseText()` devuelve una nueva cadena que contiene la cadena original en orden inverso.

```java
private void reverseText(String text){
	String[] array = text.split("");
	StringBuilder newText = new StringBuilder();
	for (int i = array.length; i > 0; i--) {
		newText.append(array[i-1]);
	}
	System.out.println(newText.toString());
}

```

## 2. Es Palindromo

Este código implementa un método llamado `isPalindrome` que toma un número entero como argumento y comprueba si es capicúa o no. Un número es capicúa si se lee igual de izquierda a derecha que de derecha a izquierda.

El método convierte el número en una cadena de texto utilizando el método `String.valueOf(number)`, y luego invierte la cadena utilizando un `StringBuilder`. Esta nueva cadena invertida se almacena en la variable `reverseNumber`.

A continuación, se compara si la cadena original `numberText` es igual a la cadena invertida `reverseNumber` utilizando el método `equals()`. Si las dos cadenas son iguales, el número es capicúa y se imprime un mensaje "El número es capicúa". Si no son iguales, el número no es capicúa y se imprime un mensaje "El número no es capicúa".

En resumen, el método `isPalindrome` determina si un número dado es capicúa o no, y devuelve un mensaje indicando si lo es o no.

```java
private void isPalindrome(int number){
	String numberText = String.valueOf(number);
	String reverseNumber = new StringBuilder(numberText).reverse().toString();
	if (numberText.equals(reverseNumber)){
		System.out.println("El número es capicúa");
	}else{
		System.out.println("El número no es capicúa");
	}
}

```

## 3. Contador de caracter

Este código implementa un método llamado `counterChar` que cuenta la cantidad de veces que un caracter aparece en una cadena de texto.

El método crea un array `counter` de tamaño 256 para almacenar el número de veces que aparece cada caracter. Luego, se utiliza un bucle `for` para iterar sobre cada caracter de la cadena de texto y se incrementa el contador correspondiente en el array `counter`.

Finalmente, se utiliza otro bucle `for` para iterar sobre los elementos del array `counter` y se imprime el número de veces que aparece cada caracter en la cadena de texto, junto con el caracter correspondiente utilizando el método `char()` para convertir el índice numérico del caracter en un caracter legible.

En resumen, el método `counterChar` cuenta la cantidad de veces que cada caracter aparece en una cadena de texto y lo imprime por pantalla.

```java
private void counterChar(String text) {
	int i, length, counter[] = new int[256];
	length = text.length();
	for (i = 0; i < length; i++) {
		counter[text.charAt(i)]++;
	}
	for (i = 0; i < 256; i++) {
		if (counter[i] != 0) {
					System.out.println("El caracter " + (char) i + " aparece " + counter[i] + " veces");
		}
	}
}

```

## 4. Eliminar duplicados

El código muestra un método llamado `removeDuplicates` que toma una lista de enteros como argumento. El objetivo del método es eliminar cualquier elemento duplicado en la lista y luego imprimir la lista sin duplicados.

Para hacer esto, el método primero crea un nuevo conjunto vacío de enteros llamado `set` utilizando la implementación `HashSet`. La lista se utiliza para inicializar el conjunto utilizando el constructor que acepta una colección.

El uso de un conjunto es una forma fácil de eliminar duplicados ya que los conjuntos no permiten elementos duplicados.

Luego, el método utiliza el método `forEach` del conjunto para recorrer cada elemento del conjunto y imprimirlo llamando al método `System.out.println`.

En general, este método es una forma sencilla y efectiva de eliminar elementos duplicados de una lista de enteros.

```java
private void removeDuplicates(List<Integer> list) {
	Set<Integer> set = new HashSet<>(list);
	set.forEach(System.out::println);
}
```

## 5. FizzBuzz

Este código implementa la solución de un popular problema de programación llamado el "FizzBuzz". El objetivo de este problema es imprimir en consola los números del 1 al 100, pero para múltiplos de 3 se debe imprimir "Fizz" en lugar del número y para múltiplos de 5 se debe imprimir "Buzz". Además, para aquellos números que son múltiplos de ambos, es decir, múltiplos de 3 y 5, se debe imprimir "FizzBuzz".

El código comienza por un bucle `for` que itera sobre los números del 1 al 100. En cada iteración, se verifica si el número actual es divisible por 3 y 5. Si esto es cierto, se imprime "FizzBuzz" y se usa la palabra clave `continue` para saltar a la siguiente iteración del bucle. Si el número no es divisible por 3 y 5, se verifica si es divisible por 3 y se imprime "Fizz". De manera similar, si el número no es divisible por 3, se verifica si es divisible por 5 y se imprime "Buzz". Si el número actual no es múltiplo de 3 ni de 5, entonces se imprime el número en sí.

Finalmente, después de 100 iteraciones del bucle `for`, el método `prueba()` se completa y el programa termina su ejecución.

```java
private void prueba(){
	for(int i = 1; i <= 100; i++){
		if(i % 3 == 0 && i % 5 == 0){
			System.out.println("FizzBuzz");
			continue;
		}
		if(i % 3 == 0){
			System.out.println("Fizz");
			continue;
		}
		if(i % 5 == 0){
			System.out.println("Buzz");
			continue;
		}
		System.out.println(i);
	}
}
```

## 5.1. FizzBuzz Refactorizado con Operadores ternarios

En este código, la expresión `output` se inicializa con el valor que corresponde según las condiciones del operador ternario. En este caso, se utiliza el operador ternario anidado para comprobar primero si el número es divisible por ambos 3 y 5.

Luego se comprueba si es divisible solo por 3 o solo por 5. Si ninguna de estas condiciones se cumple, se convierte el número actual en un String utilizando `Integer.toString()` y se asigna a `output`.

Luego simplemente se imprime `output` en la consola utilizando `System.out.println()`.

```java
private void prueba(){
    for(int i=1; i<=100; i++){
        String output = (i % 3 == 0 && i % 5 == 0) ? "FizzBuzz" :
                        (i % 3 == 0) ? "Fizz" :
                        (i % 5 == 0) ? "Buzz" : Integer.toString(i);
        System.out.println(output);
    }
}
```