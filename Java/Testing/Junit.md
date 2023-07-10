Crear una prueba para asegurarse que un método de una clase funciona correctamente:

```java
@Test
public void test_sum() {
	MyClass myClass = new MyClass();
	int result = myClass.sum(2, 3);
	assertTrue(result == 5);
}
```

Crear una prueba para asegurarse que una excepción es lanzada cuando se proporciona un valor inválido:

```java
@Test(expected = IllegalArgumentException.class)
public void test_divide_by_zero() {
	MyClass myClass = new MyClass();
	myClass.divide(5, 0);
}
```

Crear un mock de una dependencia en una clase y simular su comportamiento:

```java
@Test
public void test_createOrder() {
}

```

Crear un mock de un objeto de una dependencia:

```java
OrderDao orderDao = mock(OrderDao.class);
```