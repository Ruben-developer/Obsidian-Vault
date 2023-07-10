![[Pasted image 20230705114234.png]]

En este ejemplo, se definen las interfaces `Button` y `TextField`, que son implementadas por las clases `WindowsButton`, `LinuxButton`, `WindowsTextField` y `LinuxTextField`.

La interfaz `GUIFactory` define los métodos `createButton()` y `createTextField()`. Las clases `WindowsFactory` y `LinuxFactory` implementan esta interfaz y devuelven objetos `WindowsButton`, `WindowsTextField`, `LinuxButton` y `LinuxTextField`, respectivamente.

La clase `Application` utiliza la fábrica de GUI para crear los objetos `Button` y `TextField`, y luego llama al

```java
interface Button {
   void paint();
}
```

```java
interface TextField {
   void paint();
}
```

```java
class WindowsButton implements Button {
	public void paint() {
	    System.out.println("Se ha creado un botón de Windows.");
	}
}
```
`
```java
class LinuxButton implements Button {
	public void paint() {
	    System.out.println("Se ha creado un botón de Linux.");
	}
}
```

```java
class WindowsTextField implements TextField {
	public void paint() {
	    System.out.println("Se ha creado un campo de texto de Windows.");
	}
}

class LinuxTextField implements TextField {
   public void paint() {
      System.out.println("Se ha creado un campo de texto de Linux.");
   }
}

interface GUIFactory {
   Button createButton();
   TextField createTextField();
}

class WindowsFactory implements GUIFactory {
   public Button createButton() {
      return new WindowsButton();
   }

   public TextField createTextField() {
      return new WindowsTextField();
   }
}

class LinuxFactory implements GUIFactory {
   public Button createButton() {
      return new LinuxButton();
   }

   public TextField createTextField() {
      return new LinuxTextField();
   }
}

class Application {
   private Button button;
   private TextField textField;
   
   public Application(GUIFactory factory) {
      button = factory.createButton();
      textField = factory.createTextField();
   }
   
   public void paint() {
      button.paint();
      textField.paint();
   }
}
```

```java
public class Main {
	public static void main(String[] args) {
	    Application app;
	    GUIFactory factory;
	    
	    String osName = System.getProperty("os.name").toLowerCase();
	    if (osName.contains("windows")) {
	         factory = new WindowsFactory();
		} else {
		    factory = new LinuxFactory();
		}
	    app = new Application(factory);
	    app.paint();
	}
}
```