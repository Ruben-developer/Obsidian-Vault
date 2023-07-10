Es un patrón de diseño en la programación que permite inyectar dependencias entre diferentes clases, lo que disminuye el acoplamiento entre ellas. En lugar de que una clase cree sus dependencias internamente, se le proporcionan desde el exterior.

Un ejemplo en Java sería el uso de la anotación @Autowired de Spring, que permite inyectar automáticamente dependencias en una clase. Por ejemplo, se podría tener una clase UserService con una dependencia de UserRepository que se inyecta automáticamente usando @Autowired.

```java
public class UserService {
    @Autowired
    private UserRepository userRepository;
    // Métodos usando UserRepository
}
```

Otro ejemplo sería mediante la creación de objetos de una interfaz en tiempo de ejecución, en lugar de crearlos en tiempo de compilación, utilizando una biblioteca como Guice. Por ejemplo, se podría tener una clase ServiceModule que defina cómo se deben crear las dependencias en tiempo de ejecución, y luego usar como sigue:

```java
public interface PaymentGateway {
    void processPayment();
}

public class CreditCardPayment implements PaymentGateway {
    public void processPayment() {
        // Lógica para procesar el pago con tarjeta de crédito
    }
}

public class PayPalPayment implements PaymentGateway {
    public void processPayment() {
        // Lógica para procesar el pago con PayPal
    }
}

public class ServiceModule extends AbstractModule {
    protected void configure() {
        // Vincular la implementación de PaymentGateway a PayPalPayment
        bind(PaymentGateway.class).to(PayPalPayment.class);
    }
}

public class PaymentProcessor {
    @Inject
    private PaymentGateway paymentGateway;
 
    public void processPayment() {
        paymentGateway.processPayment();
    }
}

public class Main {
    public static void main(String[] args) {
        Injector injector = Guice.createInjector(new ServiceModule());
        PaymentProcessor paymentProcessor = injector.getInstance(PaymentProcessor.class);
        paymentProcessor.processPayment();
    }
}
```