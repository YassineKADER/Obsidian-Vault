  

# JAVA-ACCESS-MODIFIERS:

## For Classes:

|   |   |
|---|---|
|`public`|The class is accessible by any other class|
|_default_|The class is only accessible by classes in the same package. This is used when you don't specify a modifier.|

## For Attributes, methods and constructors:

|   |   |
|---|---|
|`public`|The code is accessible for all classes|
|`private`|The code is only accessible within the declared class|
|_default_|The code is only accessible in the same package. This is used when you don't specify a modifier.|
|`protected`|The code is accessible in the same package and **subclasses.**|

### **Non-Access Modifiers:**

For **classes**, you can use either `final` or `abstract`:

For **attributes and methods**, you can use the one of the following:

|   |   |
|---|---|
|`final`|The class cannot be inherited by other classes (You will learn more about inheritance in the [Inheritance chapter](https://www.w3schools.com/java/java_inheritance.asp)  <br>  <br>)|
|`abstract`|The class cannot be used to create objects (To access an abstract class, it must be inherited from another class. You will learn more about inheritance and abstraction in the [Inheritance](https://www.w3schools.com/java/java_inheritance.asp) and [Abstraction](https://www.w3schools.com/java/java_abstract.asp) chapters)|

|   |   |
|---|---|
|`final`|Attributes and methods cannot be overridden/modified|
|`static`|Attributes and methods belongs to the class, rather than an object|
|`abstract`|Can only be used in an abstract class, and can only be used on methods. The method does not have a body, for example  <br>  <br>**abstract void run();** The body is provided by the subclass (inherited from). You will learn more about inheritance and abstraction in the [Inheritance](https://www.w3schools.com/java/java_inheritance.asp) and [Abstraction](https://www.w3schools.com/java/java_abstract.asp) chapters|
|`transient`|Attributes and methods are skipped when serializing the object containing them|
|`synchronized`|Methods can only be accessed by one thread at a time|
|`volatile`|The value of an attribute is not cached thread-locally, and is always read from the "main memory”|

# Encapsulation:

The meaning of **Encapsulation**, is to make sure that "sensitive" data is hidden from users. To achieve this, you must:

- declare class variables/attributes as `private`
- provide public **get** and **set** methods to access and update the value of a `private` variable (getters and setters)
    
    ### **Why Encapsulation?**
    
    - Better control of class attributes and methods
    - Class attributes can be made **read-only** (if you only use the `get` method), or **write-only** (if you only use the `set` method)
    - Flexible: the programmer can change one part of the code without affecting other parts
    - Increased security of data

# **Inheritance (Subclass and Superclass):**

In Java, it is possible to inherit attributes and methods from one class to another. We group the "inheritance concept" into two categories:

- **subclass** (child) - the class that inherits from another class
- **superclass** (parent) - the class being inherited from

To inherit from a class, use the `extends` keyword.

In the example below, the `Car` class (subclass) inherits the attributes and methods from the `Vehicle` class (superclass):

```Java
class Vehicle {
  protected String brand = "Ford";        // Vehicle attribute
  public void honk() {                    // Vehicle method
    System.out.println("Tuut, tuut!");
  }
}

class Car extends Vehicle {
  private String modelName = "Mustang";    // Car attribute
  public static void main(String[] args) {

    // Create a myCar object
    Car myCar = new Car();

    // Call the honk() method (from the Vehicle class) on the myCar object
    myCar.honk();

    // Display the value of the brand attribute (from the Vehicle class) and the value of the modelName from the Car class
    System.out.println(myCar.brand + " " + myCar.modelName);
  }
}
```

### **The final Keyword:**

If you try to access a `final` class, Java will generate an error:

```Java
final class Vehicle {
  ...
}

class Car extends Vehicle {
  ...
}
```

```Plain
Main.java:9: error: cannot inherit from final Vehicle
class Main extends
  Vehicle {
       ^
1 error)
```

# **Java Polymorphism:**

Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance.

Like we specified in the previous chapter;  
  
[**Inheritance**](https://www.w3schools.com/java/java_inheritance.asp) lets us inherit attributes and methods from another class. **Polymorphism** uses those methods to perform different tasks. This allows us to perform a single action in different ways.

For example, think of a superclass called `Animal` that has a method called `animalSound()`.Subclasses of Animals could be Pigs, Cats, Dogs, Birds - And they also have their own implementation of an animal sound (the pig oinks, and the cat meows, etc.):

```Java
class Animal {
  public void animalSound() {
    System.out.println("The animal makes a sound");
  }
}

class Pig extends Animal {
  public void animalSound() {
    System.out.println("The pig says: wee wee");
  }
}

class Dog extends Animal {
  public void animalSound() {
    System.out.println("The dog says: bow wow");
  }
}
```

# JAVA Inner Classes:

In Java, it is also possible to nest classes (a class within a class). The purpose of nested classes is to group classes that belong together, which makes your code more readable and maintainable.

```Java
class OuterClass {
  int x = 10;

  class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}
```

> [!important]  
> Unlike a "regular" class, an inner class can be private or protected. If you don't want outside objects to access the inner class, declare the class as private .  

### Static Inner Classes:

An inner class can also be `static`, which means that you can access it without creating an object of the outer class:

```Java
class OuterClass {
  int x = 10;

  static class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass.InnerClass myInner = new OuterClass.InnerClass();
    System.out.println(myInner.y);
  }
}

// Outputs 5
```

### **Access Outer Class From Inner Class:**

```Java
class OuterClass {
  int x = 10;

  class InnerClass {
    public int myInnerMethod() {
      return x;
    }
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.myInnerMethod());
  }
}

// Outputs 10
```

# **Abstract Classes and Methods:**

Data **abstraction** is the process of hiding certain details and showing only essential information to the user.

Abstraction can be achieved with either **abstract classes** or [**interfaces**](https://www.w3schools.com/java/java_interface.asp) (which you will learn more about in the next chapter).

The `abstract` keyword is a non-access modifier, used for classes and methods:

- **Abstract class:** is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class).
- **Abstract method:** can only be used in an abstract class, and it does not have a body. The body is provided by the subclass (inherited from).

an abstract class can have both abstract and regular methods:

```Java
abstract class Animal {
  public abstract void animalSound();
  public void sleep() {
    System.out.println("Zzz");
  }
}
```

From the example above, it is not possible to create an object of the Animal class;

```Java
// Abstract class
abstract class Animal {
  // Abstract method (does not have a body)
  public abstract void animalSound();
  // Regular method
  public void sleep() {
    System.out.println("Zzz");
  }
}

// Subclass (inherit from Animal)
class Pig extends Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
}

class Main {
  public static void main(String[] args) {
    Pig myPig = new Pig(); // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```

# **Java Interface:**

Another way to achieve abstraction in java, is with interfaces.

An `interface` is a completely “**abstract class**” that is used to group related methods with empty bodies:

```Java
// interface
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void run(); // interface method (does not have a body)
}
```

To access the interface methods, the interface must be "implemented"  
(kinda like inherited) by another class with the  
`implements`keyword (instead of `extends`). The body of the interface method is provided by the "implement" class:

```Java
// Pig "implements" the Animal interface
class Pig implements Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // The body of sleep() is provided here
    System.out.println("Zzz");
  }
}

class Main {
  public static void main(String[] args) {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```

To implement multiple interfaces, separate them with a comma:

```Java
interface FirstInterface {
  public void myMethod(); // interface method
}

interface SecondInterface {
  public void myOtherMethod(); // interface method
}

class DemoClass implements FirstInterface, SecondInterface {
  public void myMethod() {
    System.out.println("Some text..");
  }
  public void myOtherMethod() {
    System.out.println("Some other text...");
  }
}

class Main {
  public static void main(String[] args) {
    DemoClass myObj = new DemoClass();
    myObj.myMethod();
    myObj.myOtherMethod();
  }
}
```

# **Enums:**

An `enum` is a special "class" that represents a group of **constants** (unchangeable variables, like `final` variables). To create an `enum`, use the `enum` keyword (instead of class or interface), and separate the constants with a comma. Note that they should be in uppercase letters:

```Java
enum Level {
  LOW,
  MEDIUM,
  HIGH
}
```

You can access `enum` constants with the **dot** syntax:

```Java
Level myVar = Level.MEDIUM;
```

**Enum inside a Class** (You can also have an `enum` inside a class):

```Java
public class Main {
  enum Level {
    LOW,
    MEDIUM,
    HIGH
  }

  public static void main(String[] args) {
    Level myVar = Level.MEDIUM;
    System.out.println(myVar);
  }
}
//Output MEDIUM
```

Enums are often used in `switch` statements to check for corresponding values:

```Java
enum Level {
  LOW,
  MEDIUM,
  HIGH
}

public class Main {
  public static void main(String[] args) {
    Level myVar = Level.MEDIUM;

    switch(myVar) {
      case LOW:
        System.out.println("Low level");
        break;
      case MEDIUM:
         System.out.println("Medium level");
        break;
      case HIGH:
        System.out.println("High level");
        break;
    }
  }
}
```

The enum type has a `values()` method, which returns an array of all enum constants. This method is useful when you want to loop through the constants of an enum:

```Java
for (Level myVar : Level.values()) {
  System.out.println(myVar);
}
```

# JAVA DATE AND TIME

Java does not have a built-in Date class, but we can import the `java.time`  
package to work with the date and time API. The package includes many date and time classes.  
For example:  

![[Untitled 25.png|Untitled 25.png]]

display current date:

```Java
import java.time.LocalDate; // import the LocalDate class

public class Main {
  public static void main(String[] args) {
    LocalDate myObj = LocalDate.now(); // Create a date object
    System.out.println(myObj); // Display the current date
  }
}
//output 2022-10-14
```

display current time:

```Java
import java.time.LocalTime; // import the LocalTime class

public class Main {
  public static void main(String[] args) {
    LocalTime myObj = LocalTime.now();
    System.out.println(myObj);
  }
}
```

display current date and time:

```Java
import java.time.LocalDateTime; // import the LocalDateTime class

public class Main {
  public static void main(String[] args) {
    LocalDateTime myObj = LocalDateTime.now();
    System.out.println(myObj);
  }
}
```

formatting date and time:

```Java
import java.time.LocalDateTime; // Import the LocalDateTime class
import java.time.format.DateTimeFormatter; // Import the DateTimeFormatter class

public class Main {
  public static void main(String[] args) {
    LocalDateTime myDateObj = LocalDateTime.now();
    System.out.println("Before formatting: " + myDateObj);
    DateTimeFormatter myFormatObj = DateTimeFormatter.ofPattern("dd-MM-yyyy HH:mm:ss");

    String formattedDate = myDateObj.format(myFormatObj);
    System.out.println("After formatting: " + formattedDate);
  }
}
/*
Before Formatting: 2022-10-14T21:43:39.586359
After Formatting: 14-10-2022 21:43:39
*/
```

![[Untitled 1 6.png|Untitled 1 6.png]]