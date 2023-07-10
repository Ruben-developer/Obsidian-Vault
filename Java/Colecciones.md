Ejemplos de Colecciones en java

## ArrayList: 

Es una implementación de la interfaz List y se utiliza para almacenar una lista de objetos. Es rápido para acceder a un elemento en particular, pero puede ser lento para insertar o eliminar elementos en posiciones intermedias.

```java
ArrayList<String> listaFrutas = new ArrayList<String>();
listaFrutas.add("Manzana");
listaFrutas.add("Pera");
listaFrutas.add("Plátano");
System.out.println(listaFrutas.get(1)); // Pera
```

## LinkedList

Es otra implementación de la interfaz List y se utiliza para almacenar una lista de objetos. Es rápido para insertar o eliminar elementos en posiciones intermedias, pero lento para acceder a elementos en posiciones intermedias.

```java
LinkedList<String> listaNombres = new LinkedList<String>();
listaNombres.add("Ana");
listaNombres.add("Javier");
listaNombres.add("Luisa");
System.out.println(listaNombres.getLast()); //Luisa
```

## HashSet:

Es una implementación de la interfaz Set y se utiliza para almacenar un conjunto de objetos únicos (sin duplicados). Los objetos se almacenan en orden aleatorio y no se puede acceder a ellos por índice.

```java
HashSet<String> setAnimales = new HashSet<String>();
setAnimales.add("Perro");
setAnimales.add("Gato");
setAnimales.add("Conejo");
System.out.println(setAnimales.contains("Gato")); //True
```

## HashMap:

Es una implementación de la interfaz Map y utiliza un algoritmo de hashing para almacenar los pares de clave-valor, mientras que TreeMap y TreeSet mantienen los elementos ordenados en un árbol

```java
HashMap<String, Integer> mapaPeliculas = new HashMap<String, Integer>();
mapaPeliculas.put("Titanic", 1997);
mapaPeliculas.put("La La Land", 2016);
mapaPeliculas.put("Forrest Gump", 1994);
System.out.println(mapaPeliculas.get("Forrest Gump")); //1994
```

## TreeSet

Es otra implementación de la interfaz Set que mantiene los elementos ordenados en un árbol. Los objetos se almacenan en orden natural o en un orden definido por el usuario.

```java
TreeSet<Integer> setNumeros = new TreeSet<Integer>();
setNumeros.add(10);
setNumeros.add(5);
setNumeros.add(8);
System.out.println(setNumeros.first()); //5
```


