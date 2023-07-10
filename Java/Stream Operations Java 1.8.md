## _Método map():_

_Este método se usa para transformar un objeto en otro usando una función. Por ejemplo, si tienes una lista de números enteros y quieres crear una nueva lista donde cada número se multiplique por dos, puedes usar el método map(). Aquí te muestro un ejemplo de código:_

```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

// Multiplicar cada número por dos usando el método map()
List<Integer> numerosDobles = numeros.stream()
	.map(numero -> numero * 2)
	.collect(Collectors.toList());
```

## _Método filter():_

_Este método se utiliza para filtrar los objetos en una colección basándose en una condición. Por ejemplo, si tienes una lista de cadenas y quieres crear una nueva lista que contenga solo aquellas cadenas que empiecen con una letra en particular, puedes usar el método filter(). Aquí tienes un ejemplo:_

```java
List<String> nombres = Arrays.asList("Ana", "Alejandra", "Juan", "María");

// Filtrar las cadenas que empiezan con la letra "A" usando el método filter()
List<String> nombresConA = nombres.stream()
.filter(nombre -> nombre.startsWith("A"))
.collect(Collectors.toList());
```

## _Método reduce():_

_Este método se utiliza para reducir una colección de objetos a un solo valor. Por ejemplo, si tienes una lista de números enteros y quieres calcular la suma de todos ellos, puedes usar el método reduce(). Aquí tienes un ejemplo:_

```java
List<Integer> numeros = Arrays.asList(5, 10, 15);

// Calcular la suma de los números usando el método reduce()
int suma = numeros.stream()
.reduce(0, (a, b) -> a + b);
```