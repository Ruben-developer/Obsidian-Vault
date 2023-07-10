Uha API Transferencia de Estado Representacional es una interfaz de programación de aplicaciones que utiliza el protocolo HTTP para enviar y recibir datos. RESTful se refiere a cualquier servicio web que implementa el estilo de arquitectura REST. En otras palabras, REST es un concepto general, mientras que RESTful es una implementación específica de ese concepto.

## Métodos HTTP soportados

- GET: se utiliza para recuperar un recurso existente.
- POST: se utiliza para crear un nuevo recurso.
- PUT: se utiliza para actualizar un recurso existente por completo.
- PATCH: se utiliza para actualizar un recurso existente parcialmente.
- DELETE: se utiliza para eliminar un recurso existente.

## Ejemplos con Spring Boot

Para el método GET:

```java
@GetMapping("/ejemplo/{id}")
public ResponseEntity<Object> getEjemplo(@PathVariable Long id) {
    Ejemplo ejemplo = ejemploService.getEjemploById(id);
    if (ejemplo == null) {
        return ResponseEntity.notFound().build();
    }
    return ResponseEntity.ok(ejemplo);
}
```

Para el método POST:

```java
@PostMapping("/ejemplo")
public ResponseEntity<Object> createEjemplo(@RequestBody Ejemplo ejemplo) {
    ejemploService.createEjemplo(ejemplo);
    URI location = ServletUriComponentsBuilder.fromCurrentRequest()
                                  .path("/{id}")
                                  .buildAndExpand(ejemplo.getId())
                                  .toUri();
    return ResponseEntity.created(location).build();
}
```

Para el método PUT:

```java
@PutMapping("/ejemplo/{id}")
public ResponseEntity<Object> updateEjemplo(@RequestBody Ejemplo ejemplo, @PathVariable Long id) {
    Ejemplo existingEjemplo = ejemploService.getEjemploById(id);
    if (existingEjemplo == null) {
        return ResponseEntity.notFound().build();
    }
    ejemplService.updateEjemplo(ejemplo);
    return ResponseEntity.ok().build();
}
```

Para el método DELETE:

```java
@DeleteMapping("/ejemplo/{id}")
public ResponseEntity<Object> deleteEjemplo(@PathVariable Long id) {
    Ejemplo ejemplo = ejemploService.getEjemploById(id);
    if (ejemplo == null) {
        return ResponseEntity.notFound().build();
    }
    ejemploService.deleteEjemplo(id);
    return ResponseEntity.ok().build();
}
```