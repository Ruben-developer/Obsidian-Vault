Configuración de MockServer para simular una solicitud HTTP GET:

```java
MockServerClient mockServerClient = new MockServerClient("localhost", 1080);
mockServerClient.when(request()
	.withMethod("GET")
	.withPath("/example")
	.withQueryStringParameter("id", "1234"))
	.respond(response().withBody(""{\\"name\\":\\"example\\",\\"id\\":\\"1234\\"}")
	.withStatusCode(200)
	.withHeader("Content-Type", "application/json")
);
```

Verificación de que se realiza una solicitud a MockServer:

```java
MockServerClient mockServerClient = new MockServerClient("localhost", 1080);
...
verify(request()
	.withMethod("POST")
	.withPath("/example")
	.withBody(json("{id: 1234, name: 'example'}")),
once()
);
```

Configuración de MockServer para simular un servicio RESTful:

```java
MockServerClient mockServerClient = new MockServerClient("localhost", 1080);
mockServerClient.when(request()
	.withMethod("POST")
	.withPath("/api/objects")
	.withBody(json("{name: 'example', type: 'object'}")))
	.respond(response()
	.withStatusCode(201)
	.withHeader("Location", "/api/objects/1234")
);
```