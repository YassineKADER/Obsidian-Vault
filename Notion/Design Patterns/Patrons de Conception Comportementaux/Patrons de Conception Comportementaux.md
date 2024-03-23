# Command

Le patron de conception `Command` est un modèle de `conception comportemental` qui transforme une `requête en un objet autonome` contenant toutes `les informations sur la requête`. Cette transformation permet `de transmettre des requêtes en tant qu'arguments de méthode`, de différer ou mettre en `file l'exécution d'une requête` et de prendre en charge des opérations annulables.

![[Untitled 44.png|Untitled 44.png]]

Imaginons une application de traitement de texte où l'utilisateur peut effectuer des opérations d'édition, telles que couper, copier et coller du texte. Utilisez le patron de conception Command pour encapsuler ces opérations dans des objets de commande (CutCommand, CopyCommand, PasteCommand) qui contiennent les informations nécessaires pour exécuter ces actions. Cela permettrait de traiter les commandes de manière flexible, de les différer ou de les annuler, si nécessaire.

![[Untitled 1 23.png|Untitled 1 23.png]]

```Java

// Command interface
interface Command {
    void execute();
}

class TextReceiver {
    public void cut() {
        System.out.println("Cutting text");
        // Actual logic for cutting text
    }

    public void copy() {
        System.out.println("Copying text");
        // Actual logic for copying text
    }

    public void paste() {
        System.out.println("Pasting text");
        // Actual logic for pasting text
    }
}

// Concrete command for cutting text
class CutCommand implements Command {
    private TextReceiver receiver;

    public CutCommand(TextReceiver receiver) {
        this.receiver = receiver;
    }

    @Override
    public void execute() {
        receiver.cut();
    }
}

// Concrete command for copying text
class CopyCommand implements Command {
    private TextReceiver receiver;

    public CopyCommand(TextReceiver receiver) {
        this.receiver = receiver;
    }

    @Override
    public void execute() {
        receiver.copy();
    }
}

// Concrete command for pasting text
class PasteCommand implements Command {
    private TextReceiver receiver;

    public PasteCommand(TextReceiver receiver) {
        this.receiver = receiver;
    }

    @Override
    public void execute() {
        receiver.paste();
    }
}

// Invoker class
class TextEditor {
    private Command command;
    private TextReceiver textReceiver;

    public void setCommand(Command command) {
        this.command = command;
    }

    public void setTextReceiver(TextReceiver textReceiver) {
        this.textReceiver = textReceiver;
    }

    public void executeCommand() {
        if (command != null && textReceiver != null) {
            // Pass the TextReceiver to the command
            if (command instanceof TextCommand) {
                ((TextCommand) command).setTextReceiver(textReceiver);
            }
            command.execute();
        }
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        // Create receiver
        TextReceiver textReceiver = new TextReceiver();

        // Create commands with the receiver
        Command cutCommand = new CutCommand(textReceiver);
        Command copyCommand = new CopyCommand(textReceiver);
        Command pasteCommand = new PasteCommand(textReceiver);

        // Create invoker (TextEditor)
        TextEditor textEditor = new TextEditor();

        // Set the receiver for the editor
        textEditor.setTextReceiver(textReceiver);

        // Execute commands through the invoker
        textEditor.setCommand(cutCommand);
        textEditor.executeCommand();

        textEditor.setCommand(copyCommand);
        textEditor.executeCommand();

        textEditor.setCommand(pasteCommand);
        textEditor.executeCommand();
    }
}
```

# Observer

Le patron de conception `Observer` est un modèle `de conception comportemental` qui vous permet de `définir un mécanisme d'abonnement` pour notifier `plusieurs objets` de tout événement survenant sur `l'objet qu'ils observent.`

![[Untitled 2 21.png|Untitled 2 21.png]]

![[Untitled 3 21.png|Untitled 3 21.png]]

Imaginons une station météorologique qui met à jour périodiquement la température, l'humidité et la pression. Implémentez le patron Observer pour notifier divers affichages (conditions actuelles, statistiques, prévisions) à chaque changement de ces paramètres météorologiques. Cela permet aux affichages de refléter automatiquement les informations météorologiques mises à jour sans les coupler étroitement à la station météorologique.

Example:

![[Untitled 4 20.png|Untitled 4 20.png]]

```Java
import java.util.ArrayList;
import java.util.List;

// Observer interface
interface Observer {
    void update(float temperature, float humidity, float pressure);
}

// Subject interface
interface Subject {
    void addObserver(Observer observer);
    void removeObserver(Observer observer);
    void notifyObservers();
}

// Concrete Subject: WeatherStation
class WeatherStation implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private float temperature;
    private float humidity;
    private float pressure;

    @Override
    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    @Override
    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    @Override
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(temperature, humidity, pressure);
        }
    }

    public void setMeasurements(float temperature, float humidity, float pressure) {
        this.temperature = temperature;
        this.humidity = humidity;
        this.pressure = pressure;
        notifyObservers();
    }
}

// Concrete Observer: CurrentConditionsDisplay
class CurrentConditionsDisplay implements Observer {
    private float temperature;
    private float humidity;

    @Override
    public void update(float temperature, float humidity, float pressure) {
        this.temperature = temperature;
        this.humidity = humidity;
        display();
    }

    public void display() {
        System.out.println("Current conditions: Temperature = " + temperature + "°C, Humidity = " + humidity + "%");
    }
}

// Concrete Observer: StatisticsDisplay
class StatisticsDisplay implements Observer {
    @Override
    public void update(float temperature, float humidity, float pressure) {
        // Update statistics display logic
    }

    public void display() {
        // Display statistics
    }
}

// Concrete Observer: ForecastDisplay
class ForecastDisplay implements Observer {
    @Override
    public void update(float temperature, float humidity, float pressure) {
        // Update forecast display logic
    }

    public void display() {
        // Display forecast
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        WeatherStation weatherStation = new WeatherStation();

        // Create observers
        Observer currentConditionsDisplay = new CurrentConditionsDisplay();
        Observer statisticsDisplay = new StatisticsDisplay();
        Observer forecastDisplay = new ForecastDisplay();

        // Register observers with the weather station
        weatherStation.addObserver(currentConditionsDisplay);
        weatherStation.addObserver(statisticsDisplay);
        weatherStation.addObserver(forecastDisplay);

        // Simulate weather changes
        weatherStation.setMeasurements(25.5f, 60.0f, 1010.2f);
    }
}
```

# Strategy

Le patron de conception `Strategy` est un modèle de conception `comportemental` qui vous permet de `définir une famille d'algorithmes`, de placer chacun `d'eux dans une classe distincte`, et de `rendre leurs objets interchangeables`.

![[Untitled 5 18.png|Untitled 5 18.png]]

Suppose you are developing a payment system where different payment methods (credit card, PayPal, and bank transfer) need to be implemented. Utilize the Strategy pattern to encapsulate each payment method in a separate class, allowing the system to dynamically switch between payment strategies without altering the client code.

![[Untitled 6 17.png|Untitled 6 17.png]]

```Java
// Strategy interface
interface PaymentStrategy {
    void processPayment();
}

// Concrete Strategy: CreditCardPayment
class CreditCardPayment implements PaymentStrategy {
    @Override
    public void processPayment() {
        System.out.println("Processing payment using Credit Card");
        // Additional logic for credit card payment
    }
}

// Concrete Strategy: PayPalPayment
class PayPalPayment implements PaymentStrategy {
    @Override
    public void processPayment() {
        System.out.println("Processing payment using PayPal");
        // Additional logic for PayPal payment
    }
}

// Concrete Strategy: BankTransferPayment
class BankTransferPayment implements PaymentStrategy {
    @Override
    public void processPayment() {
        System.out.println("Processing payment using Bank Transfer");
        // Additional logic for bank transfer payment
    }
}

// Context class
class PaymentContext {
    private PaymentStrategy paymentStrategy;

    public void setPaymentStrategy(PaymentStrategy paymentStrategy) {
        this.paymentStrategy = paymentStrategy;
    }

    public void executePayment() {
        if (paymentStrategy != null) {
            paymentStrategy.processPayment();
        }
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        PaymentContext paymentContext = new PaymentContext();

        // Use CreditCardPayment strategy
        PaymentStrategy creditCardPayment = new CreditCardPayment();
        paymentContext.setPaymentStrategy(creditCardPayment);
        paymentContext.executePayment();

        // Use PayPalPayment strategy
        PaymentStrategy payPalPayment = new PayPalPayment();
        paymentContext.setPaymentStrategy(payPalPayment);
        paymentContext.executePayment();

        // Use BankTransferPayment strategy
        PaymentStrategy bankTransferPayment = new BankTransferPayment();
        paymentContext.setPaymentStrategy(bankTransferPayment);
        paymentContext.executePayment();
    }
}
```

# Visitor

Le patron de conception Visitor est un modèle de conception `comportemental` qui vous permet de séparer les `algorithmes` des objets sur lesquels ils `opèrent`.

![[Untitled 7 15.png|Untitled 7 15.png]]

Imaginons une hiérarchie de formes géométriques, comprenant des cercles et des rectangles. Implémentez le patron de conception Visitor pour calculer la surface de chaque forme sans modifier leurs classes individuelles. Cela permet d'ajouter de nouvelles opérations, telles que le calcul de la surface, sans altérer les classes de forme, favorisant la maintenabilité et l'extensibilité.

![[Untitled 8 12.png|Untitled 8 12.png]]

```Java
// Shape interface
interface Shape {
    void accept(ShapeVisitor visitor);
}

// Concrete Circle class
class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    public double getRadius() {
        return radius;
    }

    @Override
    public void accept(ShapeVisitor visitor) {
        visitor.visitCircle(this);
    }
}

// Concrete Rectangle class
class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    public double getWidth() {
        return width;
    }

    public double getHeight() {
        return height;
    }

    @Override
    public void accept(ShapeVisitor visitor) {
        visitor.visitRectangle(this);
    }
}

// ShapeVisitor interface
interface ShapeVisitor {
    void visitCircle(Circle circle);
    void visitRectangle(Rectangle rectangle);
}

// Concrete visitor for calculating area
class AreaCalculator implements ShapeVisitor {
    @Override
    public void visitCircle(Circle circle) {
        double area = Math.PI * Math.pow(circle.getRadius(), 2);
        System.out.println("Area of Circle: " + area);
    }

    @Override
    public void visitRectangle(Rectangle rectangle) {
        double area = rectangle.getWidth() * rectangle.getHeight();
        System.out.println("Area of Rectangle: " + area);
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        Shape circle = new Circle(5.0);
        Shape rectangle = new Rectangle(3.0, 4.0);

        ShapeVisitor areaCalculator = new AreaCalculator();

        circle.accept(areaCalculator);
        rectangle.accept(areaCalculator);
    }
}
```

> Le `double dispatch` est un mécanisme où `la méthode à appeler` est déterminée en fonction des types de deux objets impliqués. En Java, il peut être réalisé en utilisant la méthode accept dans le visiteur et `en passant l'instance du visiteur` à la `méthode accept de l'objet visitable`. Cela permet d'atteindre une exécution dynamique de la méthode, en tenant compte des types dynamiques de l'objet visitable et du visiteur.

# Memento

Le patron de conception `Memento` est un modèle de `conception comportemental` qui permet de `sauvegarder et restaurer l'état précédent` d'un objet sans `révéler les détails` de son implémentation.

![[Untitled 9 9.png|Untitled 9 9.png]]

Imagine a text editor where users can undo and redo text changes. Apply the Memento pattern to create a system that saves snapshots of the editor's state, allowing users to revert to previous versions and restore the document's history without exposing the internal details of the text editor. This enhances user experience and supports seamless undo/redo functionality.

![[Untitled 10 8.png|Untitled 10 8.png]]

```Java
import java.util.ArrayList;
import java.util.List;

// Memento: TextMemento
class Memento {
    private String state;

    public Memento(String state) {
        this.state = state;
    }

    public String getState() {
        return state;
    }
}

// Originator: TextEditor
class Originator {
    private String state;

    public void setState(String state) {
        this.state = state;
    }

    public String getState() {
        return state;
    }

    public Memento createMemento() {
        return new Memento(state);
    }

    public void restoreMemento(Memento memento) {
        this.state = memento.getState();
    }
}

// Caretaker: History
class Caretaker {
    private List<Memento> mementos = new ArrayList<>();

    public void addMemento(Memento memento) {
        mementos.add(memento);
    }

    public Memento getMemento(int index) {
        return mementos.get(index);
    }
}

// Client Code
public class Main {
    public static void main(String[] args) {
        Originator originator = new Originator();
        Caretaker caretaker = new Caretaker();

        // User makes changes
        originator.setState("State 1");
        caretaker.addMemento(originator.createMemento());

        originator.setState("State 2");
        caretaker.addMemento(originator.createMemento());

        // Restore to previous state
        originator.restoreMemento(caretaker.getMemento(0));

        System.out.println("Current State: " + originator.getState());
    }
}
```

  

# State

Le patron de conception `State` est un modèle de conception `comportemental` qui permet à un objet de modifier son `comportement` lorsque son `état interne change.` Il donne l'impression que `l'objet a changé de classe.`

![[Untitled 11 6.png|Untitled 11 6.png]]

Considérez un lecteur de média capable de jouer différents formats (audio et vidéo). Implémentez le patron de conception State pour permettre au lecteur de changer son comportement en fonction de l'état actuel, par exemple, en passant du mode lecture audio au mode lecture vidéo. Cela facilite l'extension de nouveaux états sans altérer la logique principale du lecteur, améliorant ainsi la flexibilité du système.

![[Untitled 12 5.png|Untitled 12 5.png]]

```Java
// Context: MediaPlayer
class MediaPlayer {
    private State state;

    public MediaPlayer() {
        this.state = new StoppedState(this);
    }

    public void setState(State state) {
        this.state = state;
    }

    public void play() {
        state.play();
    }

    public void pause() {
        state.pause();
    }

    public void stop() {
        state.stop();
    }
}

// State interface
interface State {
    void play();
    void pause();
    void stop();
}

// Concrete State: StoppedState
class StoppedState implements State {
    private final MediaPlayer mediaPlayer;

    public StoppedState(MediaPlayer mediaPlayer) {
        this.mediaPlayer = mediaPlayer;
    }

    @Override
    public void play() {
        System.out.println("Playing media");
        mediaPlayer.setState(new PlayingState(mediaPlayer));
    }

    @Override
    public void pause() {
        System.out.println("Cannot pause, already stopped");
    }

    @Override
    public void stop() {
        System.out.println("Already stopped");
    }
}

// Concrete State: PlayingState
class PlayingState implements State {
    private final MediaPlayer mediaPlayer;

    public PlayingState(MediaPlayer mediaPlayer) {
        this.mediaPlayer = mediaPlayer;
    }

    @Override
    public void play() {
        System.out.println("Already playing");
    }

    @Override
    public void pause() {
        System.out.println("Pausing media");
        mediaPlayer.setState(new StoppedState(mediaPlayer));
    }

    @Override
    public void stop() {
        System.out.println("Stopping media");
        mediaPlayer.setState(new StoppedState(mediaPlayer));
    }
}

// Client Code
public class Main {
    public static void main(String[] args) {
        MediaPlayer mediaPlayer = new MediaPlayer();

        mediaPlayer.play();
        mediaPlayer.pause();
        mediaPlayer.stop();
        mediaPlayer.play();
    }
}
```

Another example:

![[Untitled 13 4.png|Untitled 13 4.png]]

```Java
// Context: CommandContext
class CommandContext {
    private CommandState state;

    public void setState(CommandState state) {
        this.state = state;
    }

    public void prepare() {
        state.prepare(this);
    }

    public void ship() {
        state.ship(this);
    }

    public void deliver() {
        state.deliver(this);
    }
}

// State interface
interface CommandState {
    void prepare(CommandContext context);
    void ship(CommandContext context);
    void deliver(CommandContext context);
}

// Concrete State: PreparedState
class PreparedState implements CommandState {
    @Override
    public void prepare(CommandContext context) {
        System.out.println("Command is already prepared");
    }

    @Override
    public void ship(CommandContext context) {
        System.out.println("Shipping the command");
        context.setState(new ShippedState());
    }

    @Override
    public void deliver(CommandContext context) {
        System.out.println("Cannot deliver, command is not shipped yet");
    }
}

// Concrete State: ShippedState
class ShippedState implements CommandState {
    @Override
    public void prepare(CommandContext context) {
        System.out.println("Cannot prepare, command is already shipped");
    }

    @Override
    public void ship(CommandContext context) {
        System.out.println("Command is already shipped");
    }

    @Override
    public void deliver(CommandContext context) {
        System.out.println("Delivering the command");
        context.setState(new DeliveredState());
    }
}

// Concrete State: DeliveredState
class DeliveredState implements CommandState {
    @Override
    public void prepare(CommandContext context) {
        System.out.println("Cannot prepare, command is already delivered");
    }

    @Override
    public void ship(CommandContext context) {
        System.out.println("Cannot ship, command is already delivered");
    }

    @Override
    public void deliver(CommandContext context) {
        System.out.println("Command is already delivered");
    }
}

// Client Code
public class Main {
    public static void main(String[] args) {
        CommandContext commandContext = new CommandContext();

        // Set and execute PreparedState
        commandContext.setState(new PreparedState());
        commandContext.prepare();
        commandContext.ship();
        commandContext.deliver();
    }
}
```