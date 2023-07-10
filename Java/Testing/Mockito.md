1. Configuración básica de Mockito en una clase de prueba:

```java
import static org.mockito.Mockito.*;

import org.junit.Test;

public class MyClassTest {
	
	@Test
	public void test() {
		// Crear un mock object
		MyClass mock = mock(MyClass.class);
		
		// Definir el comportamiento del mock object
		when(mock.myMethod()).thenReturn("Hello World");
		
		// Verificar que el mock object se utilizó correctamente
		verify(mock).myMethod();
	}
}
```

1. Verificación del número de llamadas a un método en un mock object:

```java
import static org.mockito.Mockito.*;

import java.util.List;
import org.junit.Test;

public class ListTest {
	
	@Test
	public void test() {
		// Crear un mock object para la clase List
		List<String> mock = mock(List.class);
		
		// Llamar al método add dos veces
		mock.add("Hello");
		mock.add("World");
		
		// Verificar que el método add se llamó dos veces
		verify(mock, times(2)).add(anyString());
	}
}
```

3. Uso de argumentos capturados en un mock object:

```java
import static org.junit.Assert.*;
import static org.mockito.Mockito.*;

import org.junit.Test;
import org.mockito.ArgumentCaptor;

public class MyClassTest {

	@Test
	public void test() {
		
		// Crear un mock object para la clase MyClass
		MyClass mock = mock(MyClass.class);
		
		// Llamar al método myMethod con un argumento
		mock.myMethod("Hello World");
		
		// Capturar el argumento pasado al método
		ArgumentCaptor<String> captor = ArgumentCaptor.forClass(String.class);
		verify(mock).myMethod(captor.capture());
		
		// Verificar que el argumento capturado es "Hello World"
		assertEquals("Hello World", captor.getValue());
	}
}
```