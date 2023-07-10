## @ComponentScan
La anotación `@ComponentScan` en Spring se utiliza para especificar el package base que se va a escanear en busca de componentes etiquetados con `@Component`, `@Repository`, `@Service` o `@Controller` y así, agregarlos automáticamente al contexto de la aplicación como beans

## @Component
Indica que una clase es un componente de Spring y que debe ser detectado automáticamente en el classpath y configurado como bean dentro del contexto de la aplicación.

## @Bean
La anotación `@Bean` en Spring se utiliza para indicar que un método de una clase anotada con `@Configuration` proporciona un bean que será administrado por el contenedor de Spring y que debe ser registrado en el contexto de la aplicación como tal.

## @Controller
Indica que una clase es un controlador de Spring MVC que puede manejar peticiones HTTP y generar respuestas.

## @RestController
Es una combinación de la anotación ## @Controller y ## @ResponseBody, lo que significa que los métodos en una clase anotada con ## @RestController devuelven objetos en lugar de vistas.

## @Service
Indica que una clase es un servicio de negocio que se utiliza típicamente para llevar a cabo tareas de procesamiento de negocio, como la validación de datos o la coordinación de múltiples repositorios.

## @Repository
Indica que una clase es un repositorio que interactúa con la base de datos y realiza operaciones CRUD (Create, Read, Update, Delete) a través de Hibernate, JPA, u otro framework de persistencia.

## @Configuration
Indica que una clase es una clase de configuración de Spring que puede contener definiciones de beans y configuraciones adicionales.

## @Autowired
Indica que un campo, método o constructor debe ser inyectado por el contenedor Spring en el momento de la creación del objeto.

## @Qualifier
Junto a ## @Autowired, se utiliza para especificar qué implementación de una interfaz debe ser inyectada cuando hay varias implementaciones disponibles.

## @Scope
Indica el alcance del bean (Singleton, Prototype, etc.).

## @RequestMapping
Asocia una URI a un método de controlador.

## @PathVariable
Permite mapear una variable en la URI a una variable en un método de controlador.

## @RequestParam
Permite mapear un parámetro de petición a un parámetro en un método de controlador.