## Java I/O Classes

### FileOutputStream

`FileOutputStream` is used to write binary data to a file. If the file does not exist, it is created. If it already exists, its old content is destroyed.

```Java
FileOutputStream f = new FileOutputStream("entiers.dat");
f.write(65); // Writes the byte 'A' to the file
f.close();
```

### DataOutputStream

`DataOutputStream` allows you to write Java primitive types in a structured binary format. It wraps an existing `OutputStream` like `FileOutputStream`.

```Java
FileOutputStream f = new FileOutputStream("entiers.dat");
DataOutputStream sortie = new DataOutputStream(f);
sortie.writeInt(123);
sortie.flush(); // Forces all buffered bytes to be written out
sortie.close();
```

### FileInputStream

`FileInputStream` is used to read binary data from a file.

```Java
FileInputStream f = new FileInputStream("entiers.dat");
int i = f.read(); // Reads a byte of data
f.close();
```

### DataInputStream

`DataInputStream` allows you to read Java primitive types from an input stream in a machine-independent way.

```Java
FileInputStream f = new FileInputStream("entiers.dat");
DataInputStream entree = new DataInputStream(f);
int i = entree.readInt(); // Reads an int from the stream
entree.close();
```

### IOException

`IOException` is a generic exception used to handle I/O errors. It's a checked exception, so it must be declared in a method or constructor's `throws` clause if it can be thrown but not caught.

```Java
try {
    FileInputStream f = new FileInputStream("nonexistentfile.dat");
} catch (IOException e) {
    e.printStackTrace();
}
```

### FileWriter

`FileWriter` is used to write character data to a file. It's essentially a `OutputStreamWriter` that uses the default character encoding.

```Java
FileWriter f = new FileWriter("carres.txt");
f.write("Hello, world!");
f.close();
```

### PrintWriter

`PrintWriter` is used to write formatted text to an output stream. It provides convenient methods for printing all primitive types and objects.

```Java
FileWriter f = new FileWriter("carres.txt");
PrintWriter sortie = new PrintWriter(f);
sortie.println("Hello, world!");
sortie.close();
```

### OutputStream, InputStream, Writer, Reader

These are abstract base classes for all kinds of I/O streams:

- `OutputStream` and `InputStream` are for binary data.
- `Writer` and `Reader` are for character data.

They provide the basic methods that all specific I/O classes implement. For example, `OutputStream` provides a `write(int b)` method, and `Writer` provides a `write(int c)` method.

### OutputStream and InputStream

`OutputStream` and `InputStream` are abstract classes at the top of the hierarchy for classes that handle binary data.

- `OutputStream` has methods like `write(int b)` for writing a single byte of data, and `write(byte[] b)` for writing an array of bytes.
- `InputStream` has methods like `read()` for reading a single byte of data, and `read(byte[] b)` for reading into an array of bytes.

These classes are often wrapped by more specific classes that provide additional functionality. For example, `FileOutputStream` and `FileInputStream` are subclasses that add file-specific behavior.

```Java
OutputStream os = new FileOutputStream("output.txt");
os.write(65); // Writes the byte 'A'
os.close();

InputStream is = new FileInputStream("output.txt");
int data = is.read(); // Reads a byte
is.close();
```

### Writer and Reader

`Writer` and `Reader` are abstract classes at the top of the hierarchy for classes that handle character data.

- `Writer` has methods like `write(int c)` for writing a single character, and `write(char[] cbuf)` for writing an array of characters.
- `Reader` has methods like `read()` for reading a single character, and `read(char[] cbuf)` for reading into an array of characters.

Like with `OutputStream` and `InputStream`, these classes are often wrapped by more specific classes. For example, `FileWriter` and `FileReader` are subclasses that add file-specific behavior.

```Java
Writer writer = new FileWriter("output.txt");
writer.write('A'); // Writes the character 'A'
writer.close();

Reader reader = new FileReader("output.txt");
int data = reader.read(); // Reads a character
reader.close();
```

In your code snippet, `PrintWriter` and `BufferedReader` are used, which are subclasses of `Writer` and `Reader` respectively. `PrintWriter` provides methods for printing formatted representations of objects to a text-output stream. `BufferedReader` reads text from a character-input stream, buffering characters so as to provide for the efficient reading of characters, arrays, and lines.

```Java
Socket socket = new Socket("localhost", 12345);
BufferedReader reader = new BufferedReader(new InputStreamReader(socket.getInputStream()));
PrintWriter writer = new PrintWriter(socket.getOutputStream(), true);
```

Here, `InputStreamReader` and `OutputStreamWriter` are bridge classes that convert between byte streams and character streams. They use the default character encoding if not specified.

# Serialization

```Java
import java.io.*;

class Employee implements Serializable {
    public String name;
    public String address;
    public transient int SSN;
    public int number;
}

public class SerializeDemo {
    public static void main(String[] args) {
        Employee e = new Employee();
        e.name = "John Doe";
        e.address = "123 Street";
        e.SSN = 11122333;
        e.number = 101;

        try {
            FileOutputStream fileOut = new FileOutputStream("/tmp/employee.ser");
            ObjectOutputStream out = new ObjectOutputStream(fileOut);
            out.writeObject(e);
            out.close();
            fileOut.close();
            System.out.printf("Serialized data is saved in /tmp/employee.ser");
        } catch (IOException i) {
            i.printStackTrace();
        }
    }
}
```

In this example, we have an `Employee` class that implements the `Serializable` interface. We then create an instance of `Employee`, set its fields, and write it to a file using `ObjectOutputStream`. The `transient` keyword is used to indicate that the `SSN` field should not be serialized.

To deserialize the object, you would do something like this:

```Java
public class DeserializeDemo {
    public static void main(String[] args) {
        Employee e = null;
        try {
            FileInputStream fileIn = new FileInputStream("/tmp/employee.ser");
            ObjectInputStream in = new ObjectInputStream(fileIn);
            e = (Employee) in.readObject();
            in.close();
            fileIn.close();
        } catch (IOException i) {
            i.printStackTrace();
            return;
        } catch (ClassNotFoundException c) {
            System.out.println("Employee class not found");
            c.printStackTrace();
            return;
        }
        System.out.println("Deserialized Employee...");
        System.out.println("Name: " + e.name);
        System.out.println("Address: " + e.address);
        System.out.println("Number: " + e.number);
    }
}
```

This reads the serialized object from the file and casts it back to an `Employee` object. Note that the `SSN` field is not restored, because it was marked as `transient`.

# Swing

### ActionListener

An `ActionListener` is an interface in Java that is used to handle action events, such as clicking a button. It has a single method, `actionPerformed(ActionEvent e)`, that you need to implement.

Here's an example of adding an `ActionListener` to a button:

```Java
JButton button = new JButton("Click me");
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        System.out.println("Button clicked");
    }
});
```

### MouseListener

A `MouseListener` is an interface in Java that is used to handle mouse events. It has five methods: `mouseClicked(MouseEvent e)`, `mousePressed(MouseEvent e)`, `mouseReleased(MouseEvent e)`, `mouseEntered(MouseEvent e)`, and `mouseExited(MouseEvent e)`.

Here's an example of adding a `MouseListener` to a panel:

```Java
JPanel panel = new JPanel();
panel.addMouseListener(new MouseAdapter() {
    @Override
    public void mouseClicked(MouseEvent e) {
        System.out.println("Panel clicked");
    }
});
```

Note that we used `MouseAdapter` here, which is a class that implements `MouseListener` with empty methods. This way, we only need to override the methods we're interested in.

### Lambda Expressions

Lambda expressions (also known as arrow functions) are a feature in Java 8 that allow you to write shorter and more readable code for interfaces with a single method, such as `ActionListener` and `MouseListener`.

Here's the previous `ActionListener` example rewritten with a lambda expression:

```Java
JButton button = new JButton("Click me");
button.addActionListener(e -> System.out.println("Button clicked"));
```

Note that lambda expressions can't be used with `MouseListener` directly, because it has more than one method. However, you can still use them with `MouseAdapter`.

```Java
JPanel panel = new JPanel();
panel.addMouseListener(new MouseAdapter() {
    @Override
    public void mouseClicked(MouseEvent e) {
        System.out.println("Panel clicked");
    }
});
```

Remember that lambda expressions can only be used with functional interfaces, which are interfaces with a single abstract method. Both `ActionListener` and `MouseListener` are examples of functional interfaces.

## ServerSocket

A `ServerSocket` is used for listening for incoming client connections. Here's how to create one and accept a connection:

```Java
ServerSocket serverSocket = new ServerSocket(8000); // Create a new server socket that listens on port 8000
Socket clientSocket = serverSocket.accept(); // Wait for a client to connect
```

## Socket

A `Socket` represents a connection to a client. You can use it to send and receive data:

```Java
Socket socket = new Socket("localhost", 8000); // Connect to a server at localhost on port 8000

InputStream in = socket.getInputStream(); // Get the input stream
OutputStream out = socket.getOutputStream(); // Get the output stream
```

## Reading and Writing

You can read from and write to sockets using streams. Here's how to do it:

```Java
BufferedReader reader = new BufferedReader(new InputStreamReader(in)); // Create a reader
PrintWriter writer = new PrintWriter(out, true); // Create a writer

String line = reader.readLine(); // Read a line from the client
writer.println("Hello, client!"); // Send a message to the client
```

## Closing Connections

Don't forget to close your connections when you're done:

```Java
socket.close(); // Close the socket
serverSocket.close(); // Close the server socket
```

## Exception Handling

Most socket methods can throw an `IOException`, so you'll need to handle these:

```Java
try {
    // Socket code here
} catch (IOException e) {
    System.out.println("Error: " + e.getMessage());
}
```

Remember, this is just a basic overview. Real-world socket programming can be much more complex, especially when dealing with multiple clients simultaneously or handling different types of data.

# Sockets + Multi-Threads

A socket is one endpoint of a two-way communication link between two programs running on the network. In Java, `Socket` class represents a socket, and the `ServerSocket` class provides a mechanism for the server program to listen for clients and establish connections with them.

When dealing with multiple clients, you would want to handle each client connection in a separate thread. Here's a basic example of a multithreaded server:

```Java
import java.io.*;
import java.net.*;

public class Server {
    public static void main(String[] args) throws IOException {
        ServerSocket serverSocket = new ServerSocket(8000);
        while (true) {
            Socket socket = serverSocket.accept();
            new Thread(new ClientHandler(socket)).start();
        }
    }
}

class ClientHandler implements Runnable {
    private Socket socket;

    public ClientHandler(Socket socket) {
        this.socket = socket;
    }

    @Override
    public void run() {
        try {
            BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
            String request, response;
            while ((request = in.readLine()) != null) {
                response = processRequest(request);
                out.println(response);
            }
        } catch (IOException e) {
            System.out.println("Error handling client: " + e);
        } finally {
            try { socket.close(); } catch (IOException e) { /* ignored */ }
        }
    }

    private String processRequest(String request) {
        // Implement your request handling logic here
        return "Processed: " + request;
    }
}
```

In this example, the server listens for client connections in an infinite loop. When a client connects, the server starts a new thread to handle the client's requests. The `ClientHandler` class implements the `Runnable` interface, so it can be passed to a `Thread` constructor.

Each `ClientHandler` has a `Socket` that it uses to communicate with its client. It reads requests from the client, processes them, and sends responses back to the client. When the client disconnects, the `ClientHandler` closes the socket and the thread terminates.

Remember, when working with threads, you need to be aware of the potential for race conditions and use synchronization where necessary.

# JDBC

## Importing the JDBC package

First, you need to import the JDBC package:

```Java
import java.sql.*;
```

## Loading the Driver

Before you can connect to a database, you need to load the appropriate JDBC driver:

```Java
Class.forName("com.mysql.jdbc.Driver"); // For MySQL
```

## Establishing a Connection

To connect to a database, you need to establish a `Connection`:

```Java
String url = "jdbc:mysql://localhost:3306/mydatabase";
String username = "root";
String password = "password";
Connection conn = DriverManager.getConnection(url, username, password);
```

## Creating a Statement

To execute SQL queries, you need to create a `Statement`:

```Java
Statement stmt = conn.createStatement();
```

## Executing Queries

You can execute SQL queries using the `executeQuery` method for SELECT queries:

```Java
ResultSet rs = stmt.executeQuery("SELECT * FROM mytable");
```

And `executeUpdate` method for INSERT, UPDATE, DELETE queries:

```Java
int rowsAffected = stmt.executeUpdate("UPDATE mytable SET column=value WHERE condition");
```

## Processing the Result

You can process the result of a SELECT query using a `ResultSet`:

```Java
while (rs.next()) {
    String myField = rs.getString("myfield");
    // Process the field here
}
```

## Closing Connections

Don't forget to close your connections when you're done:

```Java
rs.close();
stmt.close();
conn.close();
```

## Exception Handling

Most JDBC methods can throw a `SQLException`, so you'll need to handle these:

```Java
try {
    // JDBC code here
} catch (SQLException e) {
    System.out.println("Error: " + e.getMessage());
}
```

Remember, this is just a basic overview. Real-world JDBC programming can be much more complex, especially when dealing with transactions or stored procedures.

## PreparedStatement

A `PreparedStatement` is a precompiled statement. This means that when the `PreparedStatement` is executed, the DBMS can just run the `PreparedStatement` SQL statement without having to compile it first.

Prepared statements are used when you plan to use the SQL statements many times. The advantage to this is that in most cases, the SQL statement is sent to the DBMS right away where it is compiled. As a result, the `PreparedStatement` object contains not just an SQL statement, but an SQL statement that has been precompiled. This means that when the `PreparedStatement` is executed, the DBMS can just run the `PreparedStatement` SQL statement without having to compile it first.

Here's how to create and use a `PreparedStatement`:

```Java
String sql = "INSERT INTO mytable (column1, column2) VALUES (?, ?)";
PreparedStatement pstmt = conn.prepareStatement(sql);

pstmt.setString(1, "value1");
pstmt.setString(2, "value2");

int rowsAffected = pstmt.executeUpdate();
```

In this example, the `?` characters are placeholders for values that will be bound to the SQL statement before it's executed. The `setString` method binds a `String` value to the first and second placeholders.

Like `Statement`, `PreparedStatement` also needs to be closed after use:

```Java
pstmt.close();
```

And it can also throw a `SQLException`:

```Java
try {
    // PreparedStatement code here
} catch (SQLException e) {
    System.out.println("Error: " + e.getMessage());
}
```

Using `PreparedStatement` can help prevent SQL injection attacks because it automatically escapes the bound values.

# Thread

**1. Thread:**

A thread is a separate path of execution in a program. It's the smallest unit of execution that JVM can schedule.

```Java
Thread thread = new Thread();
thread.start();
```

**2. Runnable:**

Runnable is an interface that represents a task to run concurrently. It has a single method `run()`.

```Java
Runnable runnable = () -> System.out.println("Running in Runnable");
new Thread(runnable).start();
```

**3. Callable:**

Callable is similar to Runnable but it can return a result and throw a checked exception.

```Java
Callable<Integer> callable = () -> {
    Thread.sleep(1000);
    return 2;
};
```

**4. Future:**

Future represents the result of a computation that may have not completed yet.

```Java
ExecutorService executor = Executors.newFixedThreadPool(1);
Future<Integer> future = executor.submit(callable);
Integer result = future.get();  // blocks until the task is complete
```

**5. FutureTask:**

FutureTask is a concrete class that implements both Runnable and Future, so it can be passed to a Thread or Executor.

```Java
FutureTask<Integer> futureTask = new FutureTask<>(callable);
new Thread(futureTask).start();
```

**6. Executor:**

Executor is an interface that decouples task submission from the mechanics of how each task will be run.

```Java
Executor executor = Executors.newFixedThreadPool(10);
executor.execute(runnable);
```

**7. ExecutorService:**

ExecutorService is a higher-level replacement for working with threads directly. It provides methods to manage termination and methods that can produce a Future for tracking progress of tasks.

```Java
ExecutorService executorService = Executors.newFixedThreadPool(10);
executorService.submit(runnable);
executorService.shutdown();
```

**8. Executors:**

Executors is a utility class that provides factory methods for various kinds of executor services.

```Java
ExecutorService fixedThreadPool = Executors.newFixedThreadPool(10);
ExecutorService singleThreadExecutor = Executors.newSingleThreadExecutor();
ExecutorService cachedThreadPool = Executors.newCachedThreadPool();
```

Remember, these are just the basics. Java's concurrency utilities are a broad and complex topic, and it's important to understand how to use them correctly to avoid common concurrency issues.

# Other things….

In Java, an anonymous object is an object that is instantiated but not stored in a reference variable. It's used if you want to use an object only once. Here's an example:

```Java
new MyClass().myMethod();
```

In this case, `new MyClass()` is an anonymous object.

An anonymous class, on the other hand, is a class defined without a name in a single line of code, usually in the context where it is used. Anonymous classes are often used in GUI programming. Here's an example:

```Java
button.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        System.out.println("Button clicked");
    }
});
```

In this case, `new ActionListener() {...}` is an anonymous class. It's a subclass of `ActionListener` with an overridden `actionPerformed` method.

  

A class in Java is a blueprint for creating objects. It can contain fields (variables) and methods to describe the behavior of an object.

```Java
public class Animal {
    public void eat() {
        System.out.println("The animal eats");
    }
}
```

An abstract class in Java is a class that cannot be instantiated, meaning you cannot create an object of an abstract class. It is used to provide a base for subclasses to extend and implement the abstract methods. Abstract classes can contain both abstract methods (methods without a body) and concrete methods (regular methods with a body).

```Java
public abstract class Animal {
    public abstract void eat();
}
```

In this case, any class that extends `Animal` would need to provide an implementation for the `eat` method.

The main differences between a regular class and an abstract class in Java are:

1. You can create an instance of a class, but not of an abstract class.
2. A class can contain only concrete methods, while an abstract class can contain both concrete and abstract methods.
3. A class can extend only one other class and implement multiple interfaces, while an abstract class can extend another class (including another abstract class) and implement multiple interfaces.

  

In Java, there are several ways to create objects. Here are two common methods:

**1. Using the** `**new**` **keyword:**

This is the most common way to create an object in Java. Almost 99% of objects are created in this way.

```Java
ClassName object = new ClassName();
```

**2. Using Class.forName():**

If we know the name of the class & if it has a public default constructor we can create an object in this way.

```Java
try {
    Class cls = Class.forName("ClassName");
    ClassName object = (ClassName) cls.newInstance();
} catch (ClassNotFoundException | InstantiationException | IllegalAccessException e) {
    e.printStackTrace();
}
```

In this method, we are using the reflection concept to create an object.

In addition to these two methods, objects in Java can also be created using the `clone()` method, deserialization, and factory methods.

  

In Java, the `synchronized` keyword is used to control the access of multiple threads to a shared resource. Here's a cheat sheet:

**1. Synchronized Method:**

If a method is declared as synchronized, then only one thread at a time can access this method. This is useful when the method modifies a shared resource.

```Java
public synchronized void increment() {
    count++;
}
```

**2. Synchronized Block:**

A synchronized block in Java is synchronized on some object. All synchronized blocks synchronized on the same object can only have one thread executing inside them at a time.

```Java
public void increment() {
    synchronized(this) {
        count++;
    }
}
```

**3. Static Synchronization:**

If you make any static method as synchronized, the lock will be on the class, not on the object.

```Java
public static synchronized void increment() {
    count++;
}
```

**4. Synchronized Collections:**

Java provides thread-safe collection classes that you can use if multiple threads are accessing your collections.

```Java
List<String> list = Collections.synchronizedList(new ArrayList<>());
```

Remember, synchronization can lead to thread contention, which happens when two or more threads try to access the same resource simultaneously and cause the Java runtime to execute one or more threads more slowly, or even suspend their execution. So, use synchronization wisely and only when necessary.

  

Yes, you can synchronize on the class object instead of the instance (`this`). When you synchronize on the class object, you're controlling access at the class level instead of the instance level.

Here's how you can do it:

```Java
public void increment() {
    synchronized(MyClass.class) {
        count++;
    }
}
```

In this case, `MyClass.class` is a `Class` object representing the `MyClass` class itself.

The difference between synchronizing on `this` vs `MyClass.class` is scope:

- When you synchronize on `this`, you're controlling access to the object instance. Two threads can call `increment()` on two different instances of the class at the same time.
- When you synchronize on `MyClass.class`, you're controlling access to the class itself. Only one thread can call `increment()`, regardless of the instance of the class it's called on.

So, if `count` is a static variable and you want to ensure that only one thread across all instances modifies `count`, you would synchronize on the class. If `count` is an instance variable, you would typically synchronize on `this`.

  

**1. JNDI (Java Naming and Directory Interface):**

JNDI is an API provided by Java for accessing naming and directory services. It allows Java software clients to discover and look up data and objects via a name.

```Java
Context initialContext = new InitialContext();
DataSource ds = (DataSource)initialContext.lookup("java:comp/env/jdbc/myDB");
Connection conn = ds.getConnection();
```

In this example, we're using JNDI to look up a `DataSource` object, which we can then use to get a database connection.

**2. JDBC (Java Database Connectivity):**

JDBC is an API for connecting and executing queries on a database. It provides methods for querying and updating data in a database, and is oriented towards relational databases.

```Java
String url = "jdbc:mysql://localhost:3306/myDB";
String username = "root";
String password = "password";
Connection conn = DriverManager.getConnection(url, username, password);
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM myTable");
```

In this example, we're using JDBC to connect to a MySQL database, create a `Statement`, and execute a SQL query.

Remember, these are just the basics. JNDI and JDBC are broad topics and there's a lot more to them than just these examples.

  

Sure, here's an example of how you might use an XML file to configure a JNDI DataSource in a Java EE environment. This is typically done in the `context.xml` file of your application:

```XML
<Context>
    <Resource name="jdbc/myDB"
              auth="Container"
              type="javax.sql.DataSource"
              maxActive="100"
              maxIdle="30"
              maxWait="10000"
              username="root"
              password="password"
              driverClassName="com.mysql.jdbc.Driver"
              url="jdbc:mysql://localhost:3306/myDB"/>
</Context>
```

In this example, a `DataSource` is configured with the JNDI name `jdbc/myDB`. The `username`, `password`, `driverClassName`, and `url` attributes are used to configure the database connection.

You can then use JNDI in your Java code to look up the `DataSource`:

```Java
Context initialContext = new InitialContext();
DataSource ds = (DataSource)initialContext.lookup("java:comp/env/jdbc/myDB");
Connection conn = ds.getConnection();
```

This will give you a `Connection` object that you can use to interact with the database. The `Connection` object is automatically configured with the settings from the `DataSource` in the `context.xml` file.

# Spring

1. **`ApplicationContext`****:**

In Spring Framework, the `ApplicationContext` is the central interface within a Spring application for providing configuration information to the application.

Here is a simple example of how to use `ApplicationContext`:

```Java
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class MainApp {
   public static void main(String[] args) {
      ApplicationContext context = new ClassPathXmlApplicationContext("Beans.xml");

      HelloWorld obj = (HelloWorld) context.getBean("helloWorld");
      obj.getMessage();
   }
}
```

In this example, `Beans.xml` is the configuration file which contains the information about the beans to be managed. `helloWorld` is the id of a bean defined in `Beans.xml`. The `getBean()` method of `ApplicationContext` is used to get the bean.

The `HelloWorld` class might look like this:

```Java
public class HelloWorld {
   private String message;

   public void setMessage(String message){
      this.message  = message;
   }

   public void getMessage(){
      System.out.println("Your Message : " + message);
   }
}
```

And the `Beans.xml` file might look like this:

```XML
<beans xmlns="<http://www.springframework.org/schema/beans>"
   xmlns:xsi="<http://www.w3.org/2001/XMLSchema-instance>"
   xsi:schemaLocation="<http://www.springframework.org/schema/beans>
   <http://www.springframework.org/schema/beans/spring-beans-3.0.xsd>">

   <bean id="helloWorld" class="com.tutorialspoint.HelloWorld">
      <property name="message" value="Hello World!"/>
   </bean>

</beans>
```

In this configuration file, a bean with id `helloWorld` is defined, which has a property `message` set to `Hello World!`.

2.`Dependencies Injection DI`:

Dependency Injection (DI) can be done in two ways: Setter Injection and Constructor Injection.

**1. Setter Injection:**

In Setter Injection, the IoC container invokes a setter method to inject the dependency. Here's an example:

```Java
public class TextEditor {
   private SpellChecker spellChecker;

   // a setter method to inject the dependency.
   public void setSpellChecker(SpellChecker spellChecker) {
      this.spellChecker = spellChecker;
   }

   public void spellCheck() {
      spellChecker.checkSpelling();
   }
}
```

In the Spring configuration file, you would wire these together like this:

```XML
<bean id="textEditor" class="com.example.TextEditor">
   <property name="spellChecker" ref="spellChecker" />
</bean>

<bean id="spellChecker" class="com.example.SpellChecker">
</bean>
```

**2. Constructor Injection:**

In Constructor Injection, the IoC container invokes a class constructor with arguments to inject the dependency. Here's an example:

```Java
public class TextEditor {
   private SpellChecker spellChecker;

   // a constructor to inject the dependency.
   public TextEditor(SpellChecker spellChecker) {
      this.spellChecker = spellChecker;
   }

   public void spellCheck() {
      spellChecker.checkSpelling();
   }
}
```

In the Spring configuration file, you would wire these together like this:

```XML
<bean id="textEditor" class="com.example.TextEditor">
   <constructor-arg ref="spellChecker" />
</bean>

<bean id="spellChecker" class="com.example.SpellChecker">
</bean>
```

In both cases, the `TextEditor` doesn't need to create the `SpellChecker` itself, it's being supplied (injected) by the Spring framework. This makes the code easier to test and more modular.

### Other examples of DI:

here are examples of how to inject List, Map, and other classes using Spring Dependency Injection.

**1. Injecting List:**

```Java
public class Library {
   private List<String> books;

   public void setBooks(List<String> books) {
      this.books = books;
   }

   public void printBooks() {
      for (String book : books) {
         System.out.println(book);
      }
   }
}
```

Spring configuration:

```XML
<bean id="library" class="com.example.Library">
   <property name="books">
      <list>
         <value>Book 1</value>
         <value>Book 2</value>
         <value>Book 3</value>
      </list>
   </property>
</bean>
```

**2. Injecting Map:**

```Java
public class Dictionary {
   private Map<String, String> words;

   public void setWords(Map<String, String> words) {
      this.words = words;
   }

   public void printWords() {
      for (Map.Entry<String, String> entry : words.entrySet()) {
         System.out.println("Word: " + entry.getKey() + " Meaning: " + entry.getValue());
      }
   }
}
```

Spring configuration:

```XML
<bean id="dictionary" class="com.example.Dictionary">
   <property name="words">
      <map>
         <entry key="Hello" value="A greeting"/>
         <entry key="Bye" value="A farewell"/>
      </map>
   </property>
</bean>
```

**3. Injecting Other Classes:**

```Java
public class Car {
   private Engine engine;

   public void setEngine(Engine engine) {
      this.engine = engine;
   }

   public void printEngineDetails() {
      System.out.println("Engine Model: " + engine.getModel());
   }
}

public class Engine {
   private String model;

   public void setModel(String model) {
      this.model = model;
   }

   public String getModel() {
      return this.model;
   }
}
```

Spring configuration:

```XML
<bean id="engine" class="com.example.Engine">
   <property name="model" value="V8"/>
</bean>

<bean id="car" class="com.example.Car">
   <property name="engine" ref="engine"/>
</bean>
```

In these examples, the `setBooks`, `setWords`, and `setEngine` methods are used to inject dependencies. The Spring configuration file defines the beans and their dependencies.

```Java
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class MainApp {
   public static void main(String[] args) {
      ApplicationContext context = new ClassPathXmlApplicationContext("Beans.xml");

      Library library = (Library) context.getBean("library");
      library.printBooks();

      Dictionary dictionary = (Dictionary) context.getBean("dictionary");
      dictionary.printWords();

      Car car = (Car) context.getBean("car");
      car.printEngineDetails();
   }
}
```

1. `Annotations`:

**1. @Component:**

The `@Component` annotation in Spring Framework is a class-level annotation indicating that a class is a Spring-managed component. When a class is annotated with `@Component`, Spring will automatically create an instance of that class (a bean) and manage its lifecycle.

> `Component` equivalent dyal tdir <bean> f `xml file` y3ni had l3iba `<bean id="myBean" class="com.example.MyBean"/>` hiya nefssha
> 
> `@Component public class MyBean { // Class implementation... }`

Here's an example:

```Java
import org.springframework.stereotype.Component;

@Component
public class MyComponent {
    // ...
}
```

In this example, `MyComponent` is a Spring-managed component. When the application context is loaded, Spring will create an instance of `MyComponent` and manage it. This instance can then be injected into other components using `@Autowired`.

The `@Component` annotation is a generic stereotype for any Spring-managed component. Other stereotypes like `@Repository`, `@Service`, and `@Controller` are specialized forms of `@Component` that are used for more specific cases.

**2. @Autowired:**

The `@Autowired` annotation in Spring Framework is used for automatic dependency injection. This means that Spring will automatically find a bean in the application context that matches the type of the field, constructor parameter, or method parameter that is annotated with `@Autowired`, and it will inject that bean.

> `Autowired` y3ni mathtajech t3ti wahed valeur bach lhad constructeur y3ni n9ed nssayeb objet men MyComponent bla manpasser MyDependency f constructeur aykon object, ola ila kan chi bean deja mssayeb f class configuration likhdamin bih aymchi ka default object f blasst null, y3ni `autowired` kat9leb automatecly 3la beans likaynin f configuration class w kat7thom tmak directly ila makanoch kathet null object

Here's an example:

```Java
@Component
public class Car {
    private final Engine engine;

    @Autowired
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void printEngineDetails() {
        System.out.println("Engine Model: " + engine.getModel());
    }
}
@Component
public class Engine {
    private String model;

    public Engine() {
    }

    public void setModel(String model) {
        this.model = model;
    }

    public String getModel() {
        return this.model;
    }
}

@Configuration
@ComponentScan(basePackages = "com.example")
public class Main {
    @Bean
    public Engine engine() {
        Engine engine = new Engine();
        engine.setModel("V8");
        return engine;
    }
    public static void main(String[] args) {

        ApplicationContext context = new AnnotationConfigApplicationContext(Main.class);

        Car car = context.getBean(Car.class);

        car.printEngineDetails();//V8 and if the bean not defined the output will be null
    }
}
```

In this example, `MyComponent` has a dependency on `MyDependency`. The `@Autowired` annotation on the constructor tells Spring to automatically inject an instance of `MyDependency` when it creates an instance of `MyComponent`.

When Spring creates an instance of `MyComponent`, it will look for a bean of type `MyDependency` in the application context. If it finds one, it will inject it into the constructor. If it doesn't find one, or if it finds more than one, it will throw an exception (unless you've specified that it's okay to not find a bean, or okay to find more than one, using the `required` attribute of `@Autowired`).

**3. @Service, @Repository, @Controller:**

These annotations are used in specific layers.

```Java
@Service
public class EmployeeService {
    // service methods
}

@Repository
public class EmployeeRepository {
    // Database interaction methods
}

@Controller
public class EmployeeController {
    // Handle HTTP requests
}
```

**4. @Configuration & @Bean:**

In Spring Framework, the `@Configuration` annotation is used on classes which define beans. `@Configuration` is a class-level annotation indicating that an object is a source of bean definitions. The methods annotated with `@Bean` within a class annotated with `@Configuration` will define the beans.

> COnfiguration ymken ndifiniw fih values bach nkhdmo fihom like defualt values b7al lblan d di f examples lifhom xml files, w blasst ma tloader xml file a tloader l configuration class sf wb9a tdir getBeans

Here's an example:

```Java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {

    @Bean
    public MyBean myBean() {
        return new MyBean();
    }
}
```

In this example, the `AppConfig` class is marked with `@Configuration` to indicate that it's a source of bean definitions. The `myBean` method is marked with `@Bean` to indicate that it returns a bean to be managed by the Spring container. When the application context is loaded, it will create an instance of `MyBean` and keep it to inject wherever needed in your application.

**5. @ComponentScan:**

The `@ComponentScan` annotation in Spring Framework is used to specify the packages to scan for annotated components. Spring can automatically recognize classes annotated with `@Component`, `@Service`, `@Repository`, or `@Controller` as beans and register them in the application context.

Here's an example:

```Java
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;

@Configuration
@ComponentScan(basePackages = "com.example.myapp")
public class AppConfig {
}
```

In this example, the `AppConfig` class is marked with `@Configuration` to indicate that it's a source of bean definitions. The `@ComponentScan` annotation tells Spring to scan the `com.example.myapp` package for any classes annotated with `@Component`, `@Service`, `@Repository`, or `@Controller`, and automatically register them as beans in the application context.

This feature is used to simplify the configuration of your Spring application. Instead of manually defining each bean in your configuration, you can just tell Spring where to look for them, and it will automatically find and register them for you. This is particularly useful in large applications with many components.

**Component Scanning:**

here is an example of how to use component scanning in XML configuration:

```XML
<beans xmlns="<http://www.springframework.org/schema/beans>"
       xmlns:xsi="<http://www.w3.org/2001/XMLSchema-instance>"
       xmlns:context="<http://www.springframework.org/schema/context>"
       xsi:schemaLocation="<http://www.springframework.org/schema/beans>
       <http://www.springframework.org/schema/beans/spring-beans.xsd>
       <http://www.springframework.org/schema/context>
       <http://www.springframework.org/schema/context/spring-context.xsd>">

    <context:component-scan base-package="com.example" />

</beans>
```

In this example, Spring will scan the "com.example" package for any classes annotated with @Component, @Service, @Repository, or @Controller.

this code is the same as defining the `beans inside the xml file`, but Note that is necessary to use `annotations` if you want to use this code.

6**. @Qualifier:**

1. **Basic Usage**: The `@Qualifier` annotation is used along with `@Autowired` to specify which bean should be autowired when there are multiple beans of the same type.

```Java
@Autowired
@Qualifier("beanName")
private SomeClass someClass;
```

```Java
//Prev Example
@Component
public class Car {
    private final Engine engine;

    @Autowired
		@Qualifier("engineserntkjsbrjhgbsjhdgfsdhbfjshdbfjshdb")
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void printEngineDetails() {
        System.out.println("Engine Model: " + engine.getModel());
    }
}
@Component
public class Engine {
    private String model;

    public Engine() {
    }

    public void setModel(String model) {
        this.model = model;
    }

    public String getModel() {
        return this.model;
    }
}

@Configuration
@ComponentScan(basePackages = "com.example")
public class Main {
    @Bean
    public Engine engineserntkjsbrjhgbsjhdgfsdhbfjshdbfjshdb() {
        Engine engine = new Engine();
        engine.setModel("V8");
        return engine;
    }
    public static void main(String[] args) {

        ApplicationContext context = new AnnotationConfigApplicationContext(Main.class);

        Car car = context.getBean(Car.class);

        car.printEngineDetails();//V8 and if the bean not defined the output will be null
    }
}
```

DI Esamples:

Here are some examples of Dependency Injection (DI) with annotations in Spring:

1. Field Injection:

```Java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

@Component
public class MyClass {
    @Autowired
    private MyDependency myDependency;

    public void doSomething() {
        myDependency.execute();
    }
}
```

In this example, `MyClass` has a dependency on `MyDependency`. The `@Autowired` annotation on the field tells Spring to automatically inject an instance of `MyDependency` into `MyClass`.

1. Constructor Injection:

```Java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

@Component
public class MyClass {
    private final MyDependency myDependency;

    @Autowired
    public MyClass(MyDependency myDependency) {
        this.myDependency = myDependency;
    }

    public void doSomething() {
        myDependency.execute();
    }
}
```

In this example, `MyClass` has a dependency on `MyDependency`. The `@Autowired` annotation on the constructor tells Spring to automatically inject an instance of `MyDependency` into `MyClass` when it is being created.

1. Setter Injection:

```Java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

@Component
public class MyClass {
    private MyDependency myDependency;

    @Autowired
    public void setMyDependency(MyDependency myDependency) {
        this.myDependency = myDependency;
    }

    public void doSomething() {
        myDependency.execute();
    }
}
```

In this example, `MyClass` has a dependency on `MyDependency`. The `@Autowired` annotation on the setter method tells Spring to automatically inject an instance of `MyDependency` into `MyClass`.

In all these examples, Spring will look for a bean of type `MyDependency` in the application context and inject it into `MyClass`. If it doesn't find one, or if it finds more than one, it will throw an exception.

`DI` Examples:

**1. AppConfig for List Injection:**

```Java
javaCopy code
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import java.util.Arrays;
import java.util.List;

@Configuration
public class AppConfig {

    @Bean
    public Library library() {
        Library library = new Library();
        library.setBooks(Arrays.asList("Book 1", "Book 2", "Book 3"));
        return library;
    }
}

```

**2. AppConfig for Map Injection:**

```Java
javaCopy code
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import java.util.HashMap;
import java.util.Map;

@Configuration
public class AppConfig {

    @Bean
    public Dictionary dictionary() {
        Dictionary dictionary = new Dictionary();
        Map<String, String> words = new HashMap<>();
        words.put("Hello", "A greeting");
        words.put("Bye", "A farewell");
        dictionary.setWords(words);
        return dictionary;
    }
}

```

**3. AppConfig for Other Classes Injection:**

```Java
javaCopy code
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {

    @Bean
    public Engine engine() {
        Engine engine = new Engine();
        engine.setModel("V8");
        return engine;
    }

    @Bean
    public Car car(Engine engine) {
        Car car = new Car();
        car.setEngine(engine);
        return car;
    }
}

```

In these configurations:

- The `**@Configuration**` annotation indicates that the class contains bean definitions.
- `**@Bean**` annotations are used to define individual beans.
- For the List and Map injection, the values are set directly in the configuration class.
- For the Other Classes injection, beans are created and configured in the configuration class, and dependencies are injected using method parameters.

Adjust the package names, class names, and values according to your actual project structure and requirements.

To use these configurations with Dependency Injection, you can create a main class that loads the Spring context and retrieves the beans. Below are examples for each of the configurations:

**1. Using List Injection:**

```Java
javaCopy code
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class ListInjectionExample {
    public static void main(String[] args) {
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);

        Library library = context.getBean(Library.class);
        library.printBooks();
    }
}

```

**2. Using Map Injection:**

```Java
javaCopy code
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class MapInjectionExample {
    public static void main(String[] args) {
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);

        Dictionary dictionary = context.getBean(Dictionary.class);
        dictionary.printWords();
    }
}

```

**3. Using Other Classes Injection:**

```Java
javaCopy code
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class OtherClassesInjectionExample {
    public static void main(String[] args) {
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);

        Car car = context.getBean(Car.class);
        car.printEngineDetails();
    }
}

```

In these examples:

- The `**AnnotationConfigApplicationContext**` is used to create a Spring context based on the Java configuration in the `**AppConfig**` classes.
- The `**getBean**` method is then used to retrieve instances of the configured beans.
- The methods in the `**Main**` classes demonstrate how to use the injected dependencies.

Run these main classes to see the DI in action for each of the configurations. Adjust the package names, class names, and values according to your actual project structure and requirements.