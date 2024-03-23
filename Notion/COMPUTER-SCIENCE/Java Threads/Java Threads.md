Threads allows a program to operate more efficiently by doing multiple things at the same time .

Threads can be used to perform complicated tasks in the background without interrupting the main program.

(we can change the ==Thread.currentThread()== with the thread name we create)

to see how many actives threads:

```Java
System.out.println(Thread.activecount());
```

to get the name of a thread:

```Java
System.out.println(Thread.currentThread().getname());
```

change thread name:

```Java
Thread.currentThread().setName("new name");
```

to show the priority of a thread:

```Java
System.out.println(Thread.curentThread().getPriority());
```

to change the priority:

```Java
Thread.curentThread().setPriority("value between 1 and 10");
```

check if the thread alive or not:

```Java
System.out.println(Thread.currentThread().isalive());
```

pause a thread:

```Java
Thread.sleep(1000);//ause for one second
/*put it into a try and catch block */
```

  

### **Creating a Thread:**

There are two ways to create a thread.

It can be created by extending the `Thread` class and overriding its `run()` method:

```Java
public class Main extends Thread {
  public void run() {
    System.out.println("This code is running in a thread");
  }
}
```

Another way to create a thread is to implement the `Runnable` interface:

```Java
public class Main implements Runnable {
  public void run() {
    System.out.println("This code is running in a thread");
  }
}
```

### **Running Threads:**

  

if the class extands the `Thread` class, the thread can be run by creating an instance of the class and call its `start()` method:

```Java
public class Main extends Thread {
  public static void main(String[] args) {
    Main thread = new Main();
    thread.start();
    System.out.println("This code is outside of the thread");
  }
  public void run() {
    System.out.println("This code is running in a thread");
  }
}
```

If the class implements the `Runnable` interface, the thread can be run by passing an instance of the class to a `Thread` object's constructor and then calling the thread's `start()` method:

```Java
public class Main implements Runnable {
  public static void main(String[] args) {
    Main obj = new Main();
    Thread thread = new Thread(obj);
    thread.start();
    System.out.println("This code is outside of the thread");
  }
  public void run() {
    System.out.println("This code is running in a thread");
  }
}
```

  

## Daemon Thread:

> [!important]  
> Daemon thread in Java is a low-priority thread that runs in the background to perform tasks such as garbage collection. Daemon thread in Java is also a service provider thread that provides services to the user thread. Its life depends on the mercy of user threads i.e. when all the user threads die, JVM terminates this thread automatically.  

make a daemon thread:

```Java
thread.SetDaemon(true);
```

check if it a daemon thread:

```Java
thread.isDaemon(true);
```

# MultiThreading:

to start a thread:

```Java
thread.start()
```

pause the main thread until a thread finish then resume other threads:

```Java
thread.join()
```