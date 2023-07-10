**Descripción del ejercicio:** 
El objetivo de este ejercicio es crear una API RESTful para una aplicación de notas utilizando Java 17, gradle con Quarkus y MongoDB.

**Requerimientos del ejercicio:**
- Configurar un proyecto Java 17 y gestionar las dependencias.
- Utilizar MongoDB como base de datos para almacenar las notas.
- Implementar las operaciones básicas CRUD (crear, leer, actualizar y eliminar) en la base de datos de notas.
- Validar los datos de entrada en las solicitudes HTTP para prevenir errores y asegurar la integridad de los datos almacenados.

**Especificaciones técnicas:**
- Java 17, Gradle y Quarkus
- MongoDB
- Utilizar Clean Architecture
- Cualquier biblioteca que consideres.

**Pasos para completar el ejercicio:**
1. Configura un proyecto [quarkus.io](http://quarkus.io/) y añade las dependencias necesarias.
2. Crea un servidor que escuche las solicitudes HTTP en el puerto 8080.
3. Crea un modelo de datos para las notas, que incluya los campos "titulo", "contenido" y "fecha de creación".
4. Implementa las rutas CRUD para las notas en tu servidor utilizando los métodos HTTP adecuados.
5. Implementa la validación de datos en las solicitudes HTTP para prevenir errores y asegurar la integridad de los datos almacenados.
6. Implementar testing con junit y mockito
___
