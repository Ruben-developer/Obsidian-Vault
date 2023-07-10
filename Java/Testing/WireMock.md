WireMock es una biblioteca de código abierto escrita en Java que se utiliza para crear mocks (burlas) de servicios web y APIs. La herramienta es utilizada principalmente para crear una API falsa en modo de simulación para su uso en pruebas de integración. WireMock tiene la capacidad de funcionar como un servidor proxy y se utiliza para registrar y reproducir solicitudes HTTP, lo que permite la creación de escenarios de comportamiento no convencionales para pruebas de integración. Además, WireMock ofrece una API simple y flexible que puede ser usada para configurar y personalizar el comportamiento de los mocks durante su uso en las pruebas.

Ejemplo 1: Configuración básica de un servidor WireMock con una respuesta simple.

```java
import static com.github.tomakehurst.wiremock.client.WireMock.*;
import static org.hamcrest.Matchers.equalTo;
import static org.junit.Assert.*;

import org.junit.Rule;
import org.junit.Test;

import com.github.tomakehurst.wiremock.junit.WireMockRule;

public class EjemploWireMockTest {
	
	@Rule 
	//Puerto de escucha de WireMock.
    public WireMockRule wireMockRule = new WireMockRule(8888);
    
    @Test
    public void ejemploTest(){
	    
    //Crea un stub (un esquema), que estará en http://localhost:8888/stub-path
        stubFor(get(urlEqualTo("/stub-path"))
                .willReturn(aResponse()
                        .withStatus(200)
                        .withBody("Respuesta de ejemplo")));
                        
        // Envía una solicitud a la URL esperada y comprueba que la respuesta.
        String response = new EjemploHttpClient().sendGet("http://localhost:8888/stub-path");
        assertThat(response, equalTo("Respuesta de ejemplo"));
    }
}
```

Ejemplo 2: Creación de un Mock con una respuesta dinámica utilizando una función.

```java
import static com.github.tomakehurst.wiremock.client.WireMock.*;
import static org.hamcrest.MatcherAssert.assertThat;
import static org.hamcrest.Matchers.equalTo;

import org.junit.Rule;
import org.junit.Test;

import com.github.tomakehurst.wiremock.junit.WireMockRule;
import com.github.tomakehurst.wiremock.client.MappingBuilder;
import com.github.tomakehurst.wiremock.http.HttpHeader;
import com.github.tomakehurst.wiremock.http.HttpHeaders;

public class EjemploWireMockDinamicoTest {
	
    @Rule
    //Puerto de escucha de WireMock.
    public WireMockRule wireMockRule = new WireMockRule(8888); 

    @Test
    public void ejemploTest(){
// Se crea una función que devuelve una respuesta dinámica basada en la solicitud.
        ResponseDefinitionBuilder responseBuilder = aResponse()
                .withBody("{ \"resultado\": \"" +
                        "{{request.pathSegments.[0]}}\"" +
                        "}");
        // Se crea el stub que utilizará la función en http://localhost
```