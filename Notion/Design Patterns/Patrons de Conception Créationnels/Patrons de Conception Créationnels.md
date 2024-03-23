# Singleton

Le `Singleton` est un patron de `conception créationnel`, qui garantit qu'un `seul objet de son genre existe` et offre un point d'accès unique à celui-ci pour tout autre code.

  

![[Untitled 42.png|Untitled 42.png]]

Example:

```Java
public final class Singleton {
    private static Singleton instance;
    public String value;

    private Singleton(String value) {
        // The following code emulates slow initialization.
        try {
            Thread.sleep(1000);
        } catch (InterruptedException ex) {
            ex.printStackTrace();
        }
        this.value = value;
    }

    public static Singleton getInstance(String value) {
        if (instance == null) {
            instance = new Singleton(value);
        }
        return instance;
    }
}
```

# Factory

La méthode de fabrique `(Factory Method)` est un patron de `conception de création` qui offre une `interface pour créer des objets` dans une superclasse, mais permet `aux sous-classes de modifier le type d'objets` qui seront créés.

![[Untitled 1 21.png|Untitled 1 21.png]]

Prenons l'exemple d'un jeu avec différents personnages (guerriers, mages, archers). Utilisez le patron Factory Method pour créer des usines de personnages (usine de guerriers, usine de mages, usine d'archers) qui produisent des instances de leurs personnages respectifs, facilitant l'ajout de nouveaux types de personnages à l'avenir.

Example:

![[example.png]]

```Java
//Product
public interface Button {
    void render();
    void onClick();
}
public class HtmlButton implements Button {

    public void render() {
        System.out.println("<button>Test Button</button>");
        onClick();
    }

    public void onClick() {
        System.out.println("Click! Button says - 'Hello World!'");
    }
}
public class WindowsButton implements Button {

    public void render() {
        //''''''''''''''''''''''''''
    }

    public void onClick() {
        //'''''''''''''''''''''''''''
    }
}
```

```Java
//Factory

public abstract class Dialog {

    public void renderWindow() {
        Button okButton = createButton();
        okButton.render();
    }

    /**
     * Subclasses will override this method in order to create specific button
     * objects.
     */
    public abstract Button createButton();
}

public class HtmlDialog extends Dialog {

    @Override
    public Button createButton() {
        return new HtmlButton();
    }
}

public class WindowsDialog extends Dialog {

    @Override
    public Button createButton() {
        return new WindowsButton();
    }
}

public class Main{
		//main class

		public static void main(String[] args){
				Dialog dialog;
				if (System.getProperty("os.name").equals("Windows 10")) {
	          dialog = new WindowsDialog();
        } else {
            dialog = new HtmlDialog();
        }
				dialog.renderWindow();
		}

}
```

# Builder

Le `Builder` est un `patron de conception de création` qui vous permet de `construire des objets complexes étape par étape`. Le modèle vous permet de produire différents types et représentations `d'un objet en utilisant le même code de construction.`

![[Untitled 2 19.png|Untitled 2 19.png]]

Imaginons un système de construction automobile. Utilisez le patron Builder pour créer des voitures et des manuels avec différentes configurations (marque, modèle, année, couleur) sans avoir à créer une multitude de constructeurs, permettant ainsi une construction étape par étape.

![[Untitled 3 19.png|Untitled 3 19.png]]

```Java
// Car class representing the product
class Car {
    private String brand;
    private String model;
    private int year;
    private String color;

    // Constructor for required parameters
    public Car(String brand, String model) {
        this.brand = brand;
        this.model = model;
    }

    // Setters for optional parameters
    public void setYear(int year) {
        this.year = year;
    }

    public void setColor(String color) {
        this.color = color;
    }

    // Method to display car details
    public void displayDetails() {
        System.out.println("Car Details: " + brand + " " + model + " " + year + " " + color);
    }
}

// CarManual class representing the product manual
class CarManual {
    private String manualContent;

    // Method to set manual content
    public void setManualContent(String content) {
        this.manualContent = content;
    }

    // Method to display manual content
    public void displayManual() {
        System.out.println("Car Manual:\n" + manualContent);
    }
}

// Builder interface for building cars and manuals
interface CarBuilder {
    void buildBrand(String brand);
    void buildModel(String model);
    void buildYear(int year);
    void buildColor(String color);
    Car getResult();
    CarManual getManual();
}

// Concrete builder implementing the CarBuilder interface
class CarBuilderImpl implements CarBuilder {
    private Car car = new Car("DefaultBrand", "DefaultModel");
    private CarManual manual = new CarManual();

    public void buildBrand(String brand) {
        car = new Car(brand, car.model);
    }

    public void buildModel(String model) {
        car = new Car(car.brand, model);
    }

    public void buildYear(int year) {
        car.setYear(year);
    }

    public void buildColor(String color) {
        car.setColor(color);
    }

    public Car getResult() {
        return car;
    }

    public CarManual getManual() {
        manual.setManualContent("This is the manual for a " + car.brand + " " + car.model + ".");
        return manual;
    }
}

// Director class to construct cars and manuals using a specific builder
class CarDirector {
    public void constructSportsCar(CarBuilder builder) {
        builder.buildBrand("SportsBrand");
        builder.buildModel("SportsModel");
        builder.buildYear(2022);
        builder.buildColor("Red");
    }
}

// Main class for testing
public class Main {
    public static void main(String[] args) {
        // Using the Builder pattern to construct a sports car and its manual
        CarBuilder builder = new CarBuilderImpl();
        CarDirector director = new CarDirector();

        director.constructSportsCar(builder);

        Car sportsCar = builder.getResult();
        CarManual sportsCarManual = builder.getManual();

        // Displaying details of the constructed sports car and its manual
        sportsCar.displayDetails();
        sportsCarManual.displayManual();
    }
}
```

# Abstract Factory

Le meme principe de `Factory method` mais `Abstract Factory` est un patron de conception de création qui vous permet de produire des `familles d'objets liés` sans `spécifier leurs classes concrètes.`

![[W3sDesign_Abstract_Factory_Design_Pattern_UML.jpg]]

Dans un scénario de fabrication de pizzas, utilisez le patron Abstract Factory pour créer des usines de pizzas pour différents pays (par exemple, ItalianPizzaFactory, AmericanPizzaFactory). Chaque usine produit des pizzas avec leurs styles uniques de pâte, de sauce et de garnitures, vous permettant de passer d'une variété de pizzas internationale à une autre sans modifier le code client.

![[Untitled 4 18.png|Untitled 4 18.png]]

```Java
// Interface representing the Pizza
interface Pizza {
    void prepare();
    void bake();
    void cut();
}

// Concrete class for Italian Pizza
class ItalianPizza implements Pizza {
    public void prepare() {
        System.out.println("Preparing Italian pizza");
    }

    public void bake() {
        System.out.println("Baking Italian pizza");
    }

    public void cut() {
        System.out.println("Cutting Italian pizza");
    }
}

// Concrete class for American Pizza
class AmericanPizza implements Pizza {
    public void prepare() {
        System.out.println("Preparing American pizza");
    }

    public void bake() {
        System.out.println("Baking American pizza");
    }

    public void cut() {
        System.out.println("Cutting American pizza");
    }
}

// Interface representing the PizzaFactory
interface PizzaFactory {
    Pizza createPizza();
}

// Concrete factory for Italian Pizza
class ItalianPizzaFactory implements PizzaFactory {
    public Pizza createPizza() {
        return new ItalianPizza();
    }
}

// Concrete factory for American Pizza
class AmericanPizzaFactory implements PizzaFactory {
    public Pizza createPizza() {
        return new AmericanPizza();
   }

}

// Class representing the PizzaStore
class PizzaStore {
    private PizzaFactory factory;

    public PizzaStore(PizzaFactory factory) {
        this.factory = factory;
    }

    public Pizza orderPizza() {
        Pizza pizza = factory.createPizza();

        // Pizza preparation steps
        pizza.prepare();
        pizza.bake();
        pizza.cut();

        return pizza;
    }
}

// Main class for testing
public class Main {
    public static void main(String[] args) {
        // Creating an Italian Pizza store
        PizzaFactory italianPizzaFactory = new ItalianPizzaFactory();
        PizzaStore italianPizzaStore = new PizzaStore(italianPizzaFactory);
        Pizza italianPizza = italianPizzaStore.orderPizza();

        // Creating an American Pizza store
        PizzaFactory americanPizzaFactory = new AmericanPizzaFactory();
        PizzaStore americanPizzaStore = new PizzaStore(americanPizzaFactory);
        Pizza americanPizza = americanPizzaStore.orderPizza();
    }
}
```

# Prototype

Le `Prototype` est un patron de `conception de création` qui vous permet de `copier des objets existants` `sans rendre votre code dépendant de leurs classes`.

![[Untitled 5 16.png|Untitled 5 16.png]]

Imaginons un jeu avec différents types de joueurs. Utilisez le patron Prototype pour créer des copies d'objets de joueur existants (par exemple, un guerrier expérimenté) sans dépendre de leurs classes spécifiques. Cela vous permet de créer facilement de nouveaux joueurs basés sur des prototypes existants dans le jeu.

![[Untitled 6 15.png|Untitled 6 15.png]]

Example:

![[Untitled 7 14.png|Untitled 7 14.png]]

```Java
public abstract class Shape {
    public int x;
    public int y;
    public String color;

    public Shape() {
    }

    public Shape(Shape target) {
        if (target != null) {
            this.x = target.x;
            this.y = target.y;
            this.color = target.color;
        }
    }

    public abstract Shape clone();

    @Override
    public boolean equals(Object object2) {
        if (!(object2 instanceof Shape)) return false;
        Shape shape2 = (Shape) object2;
        return shape2.x == x && shape2.y == y && Objects.equals(shape2.color, color);
    }
}

public class Circle extends Shape {
    public int radius;

    public Circle() {
    }

    public Circle(Circle target) {
        super(target);
        if (target != null) {
            this.radius = target.radius;
        }
    }

    @Override
    public Shape clone() {
        return new Circle(this);
    }

    @Override
    public boolean equals(Object object2) {
        if (!(object2 instanceof Circle) || !super.equals(object2)) return false;
        Circle shape2 = (Circle) object2;
        return shape2.radius == radius;
    }
}

public class Rectangle extends Shape {
    public int width;
    public int height;

    public Rectangle() {
    }

    public Rectangle(Rectangle target) {
        super(target);
        if (target != null) {
            this.width = target.width;
            this.height = target.height;
        }
    }

    @Override
    public Shape clone() {
        return new Rectangle(this);
    }

    @Override
    public boolean equals(Object object2) {
        if (!(object2 instanceof Rectangle) || !super.equals(object2)) return false;
        Rectangle shape2 = (Rectangle) object2;
        return shape2.width == width && shape2.height == height;
    }
}
```