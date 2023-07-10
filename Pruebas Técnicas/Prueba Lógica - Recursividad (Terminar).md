## 1. Cálculo del factorial de un número:

Este es un código en Java que define una función factorial utilizando una llamada recursiva.

La función toma un número entero como entrada y devuelve su factorial como resultado. El factorial de un número es el resultado de multiplicar ese número por cada número entero anterior a él, hasta llegar a 1.

La función utiliza una operación ternaria para comprobar si el número es igual a 0. Si es así, devuelve 1 (ya que el factorial de 0 es 1). Si el número es diferente de 0, utiliza una llamada recursiva a sí misma para calcular el factorial del número n-1 y lo multiplica por el número original. Esto se repite hasta que se llega al caso base de 0.

En resumen, esta función es una forma eficiente y elegante de calcular el factorial de un número utilizando una llamada recursiva.

```java
public static int factorial(int num) {
	return (num == 0) ? 1 : num * factorial(num - 1)
}
```

## 2. Cálculo de la serie de Fibonacci

Este código es una función en Java que calcula el enésimo número de la serie de Fibonacci utilizando una llamada recursiva.

La serie de Fibonacci es una secuencia de números enteros en la que cada número después de los dos primeros es la suma de los dos números anteriores. Es decir, que la secuencia comienza con 0 y 1, y cada número siguiente es la suma de los dos números anteriores (0, 1, 1, 2, 3, 5, 8, 13, 21, y así sucesivamente).

La función toma un número entero como entrada y devuelve el número en la serie de Fibonacci correspondiente a ese índice.

La función utiliza una declaración `if` para comprobar si el número es igual a 0 o igual a 1, en cuyo caso devuelve directamente ese número. Si no, utiliza una llamada recursiva a sí misma para obtener el número en la serie que corresponde al índice n-1 y el número en la serie que corresponde al índice n-2, y luego los suma para obtener el número en la serie correspondiente al índice n.

En resumen, esta función es una forma simple y elegante de calcular el número en la serie de Fibonacci correspondiente a un índice dado utilizando una llamada recursiva y la definición matemática de la serie.

```java
public static int fibonacci(int num) {
	if (num == 0) {
		return 0;
	}
	if (num == 1) {
		return 1;
	}
	return fibonacci(num - 1) + fibonacci(num - 2);
}
```

## 2.1. Cálculo de la serie de Fibonacci con Op. ternarios

Este código es una función en Java que calcula el enésimo número de la serie de Fibonacci utilizando una llamada recursiva y la sintaxis de la operación ternaria.

La serie de Fibonacci es una secuencia de números enteros en la que cada número después de los dos primeros es la suma de los dos números anteriores. Es decir, que la secuencia comienza con 0 y 1, y cada número siguiente es la suma de los dos números anteriores (0, 1, 1, 2, 3, 5, 8, 13, 21, y así sucesivamente).

La función toma un número entero como entrada y devuelve el número en la serie de Fibonacci correspondiente a ese índice.

La función utiliza una operación ternaria para comprobar si el número es igual a 0 o igual a 1, en cuyo caso devuelve directamente ese número. Si no, utiliza una llamada recursiva a sí misma para obtener el número en la serie que corresponde al índice n-1 y el número en la serie que corresponde al índice n-2, y luego los suma para obtener el número en la serie correspondiente al índice n.

En resumen, esta función es una forma simple y compacta de calcular el número en la serie de Fibonacci correspondiente a un índice dado utilizando una llamada recursiva y la definición matemática de la serie.

```java
public static int fibonacci(int num) {
	return (num == 0) ? 0 : 
		(num == 1) ? 1 :
		fibonacci(num - 1) + fibonacci(num - 2);
}
```

## 3. Cálculo de la suma de los dígitos de un número:

Este es un código en Java que calcula la suma de los dígitos de un número utilizando una llamada recursiva.

La función toma un número entero como entrada y devuelve la suma de sus dígitos como resultado.

La función utiliza una declaración `if` para comprobar si el número es menor que 10 (es decir, si tiene un solo dígito), en cuyo caso devuelve directamente ese número. Si no, utiliza una llamada recursiva a sí misma para obtener la suma de los dígitos de la parte entera del número dividida por 10 (es decir, todos los dígitos excepto el dígito más a la derecha) y luego suma el dígito más a la derecha (obtenido a través del operador `%`) a esta suma para obtener la suma total.

En resumen, esta función es una forma eficiente y elegante de calcular la suma de los dígitos de un número utilizando una llamada recursiva.

```java
public static int addDigits(int num) {
	if (num < 10) {
		return num;
	}
	return num % 10 + addDigits(num / 10);
}
```

## 3.1 Cálculo de la suma de los dígitos de un número (Ref)

Este es un código en Java para encontrar la suma de los dígitos de un número utilizando una llamada recursiva y la sintaxis de la operación ternaria.

La función toma un número entero como entrada y devuelve la suma de los dígitos de ese número como resultado.

El código utiliza una operación ternaria para comprobar si el número es menor que 10 (es decir, si tiene un solo dígito), en cuyo caso devuelve directamente ese número. Si no, utiliza una llamada recursiva para calcular la suma de los dígitos de la parte entera del número dividida por 10 (es decir, todos los dígitos excepto el dígito más a la derecha) y luego suma el dígito más a la derecha (obtenido mediante el operador `%`) a esta suma para obtener la suma total.

En resumen, este código es otra forma eficiente y compacta de calcular la suma de los dígitos de un número utilizando una llamada recursiva y la definición matemática de la suma de dígitos.

```java
public static int addDigits(int num) {
	return (num < 10) ? num : num % 10 + addDigits(num / 10);
}
```

## 4. Cálculo del número de combinaciones:

El código dado es una implementación en Java de la función que calcula el número de combinaciones de "n" objetos tomados de "k" en "k". La función utiliza la técnica de la recursión para encontrar el resultado.

La función toma dos parámetros enteros "n" y "k", que representan el número total de objetos y la cantidad de objetos que se van a tomar, respectivamente.

La función verifica si "k" es igual a cero o igual a "n", en cuyo caso devuelve 1, porque solo hay una combinación posible. Si no se cumple ninguna de estas condiciones, la función utiliza una llamada recursiva a sí misma para encontrar el número de combinaciones de "n - 1" objetos tomados de "k - 1" en "k", y luego suma esto con el número de combinaciones de "n - 1" objetos tomados de "k" en "k".

En resumen, este código utiliza la técnica de recursión para calcular el número de combinaciones de "n" objetos tomados de "k" en "k" de una manera eficiente.

```java
public static int combinations(int n, int k) {
	if (k == 0 || k == n) {
		return 1;
	}
	return combinations(n - 1, k - 1) + combinations(n - 1, k);
}
```

## 4. Cálculo del número de combinaciones con op ternario:

El código que proporcionas es otra implementación en Java de la función que calcula el número de combinaciones de "n" objetos tomados de "k" en "k", también utilizando la técnica de operador ternario.

La función toma dos parámetros enteros "n" y "k", que representan el número total de objetos y la cantidad de objetos que se van a tomar, respectivamente.

La función utiliza una operación ternaria para comprobar si "k" es igual a cero o igual a "n", en cuyo caso devuelve 1, porque solo hay una combinación posible. Si no se cumple ninguna de estas condiciones, la función sigue utilizando la técnica de recursión para encontrar el número de combinaciones de "n - 1" objetos tomados de "k - 1" en "k", y luego suma esto con el número de combinaciones de "n - 1" objetos tomados de "k" en "k".

En resumen, este código es otra implementación eficiente y compacta de la función que utiliza la operación ternaria para determinar los casos base y utiliza la recursión para calcular el número de combinaciones de "n" objetos tomados de "k" en "k".

```java
public static int combinations(int n, int k) {
	return (k == 0 || k == n) ? 1 : combinations(n - 1, k - 1) + combinations(n - 1, k);
}
```

## 5. Cálculo del máximo común divisor (MCD):

```java
public static int mcd(int a, int b) {
	if (b == 0) {
		return a;
	}
	return mcd(b, a % b);
}
```

## 5.1 Cálculo del máximo común divisor (MCD):

```java
public static int mcd(int a, int b) {
	return (b == 0) ? a : mcd(b, a % b);
}
```

## 6. Impresión de números en orden inverso:

```java
public static void printReverse(int[] arr, int index) {
	if (index >= 0) {
		System.out.print(arr[index] + " ");
		printReverse(arr, index - 1);
	}
}
```

## 7. Cálculo del número de elementos en una lista enlazada:

```java
public static int countNodes(ListNode node) {
	if (node == null) {
		return 0;
	}
	return 1 + countNodes(node.next);
}
```

## 7.1. Cálculo del número de elementos en una lista enlazada:

```java
public static int countNodes(ListNode node) {
	return (node == null) ? 0 : 1 + countNodes(node.next)
}
```

## 8. Impresión de un árbol binario en orden:

```java
public static void printInOrder(TreeNode node) {
	if (node != null) {
		printInOrder(node.left);
		System.out.print(node.val + " ");
		printInOrder(node.right);
	}
}
```

## 9. Cálculo de la potencia de un número:

```java
public static int power(int base, int exponent) {
	if (exponent == 0) {
		return 1;
	}
	return base * power(base, exponent - 1);
}
```

## 9.1 Cálculo de la potencia de un número (Ref):