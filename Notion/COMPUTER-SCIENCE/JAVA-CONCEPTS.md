# **ArrayList**

The `ArrayList` class is a resizable [array](https://www.w3schools.com/java/java_arrays.asp), which can be found in the `java.util` package.

The difference between a built-in array and an `ArrayList` in Java, is that the size of an array cannot be modified (if you want to add or remove elements to/from an array, you have to create a new one). While elements can be added and removed from an `ArrayList` whenever you want. The syntax is also slightly different:

```Java
import java.util.ArrayList; // import the ArrayList class

ArrayList<String> cars = new ArrayList<String>(); // Create an ArrayList object
```

Add items:

```Java
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
```

Access an item:

```Java
cars.get(0)
```

change an item:

```Java
cars.set(0, "Opel");
```

remove:

```Java
cars.remove(0);
```

remove all elements:

```Java
cars.clear();
```

Another useful class in the `java.util` package is the `Collections` class, which include the `sort()` method for sorting lists alphabetically or numerically:

```Java
import java.util.ArrayList;
import java.util.Collections;  // Import the Collections class

public class Main {
  public static void main(String[] args) {
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    Collections.sort(cars);  // Sort cars
    for (String i : cars) {
      System.out.println(i);
    }
  }
}
```

```Java
import java.util.ArrayList;
import java.util.Collections;  // Import the Collections class

public class Main {
  public static void main(String[] args) {
    ArrayList<Integer> myNumbers = new ArrayList<Integer>(size);
    myNumbers.add(33);
    myNumbers.add(15);
    myNumbers.add(20);
    myNumbers.add(34);
    myNumbers.add(8);
    myNumbers.add(12);

    Collections.sort(myNumbers);  // Sort myNumbers

    for (int i : myNumbers) {
      System.out.println(i);
    }
  }
}
```

# Linkedlist

In the previous chapter, you learned about the [`ArrayList`](https://www.w3schools.com/java/java_arraylist.asp) class. The `LinkedList` class is almost identical to the `ArrayList`:

```Java
// Import the LinkedList class
import java.util.LinkedList;

public class Main {
  public static void main(String[] args) {
    LinkedList<String> cars = new LinkedList<String>(size);
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    System.out.println(cars);
  }
}
```

The `LinkedList` class has all of the same methods as the `ArrayList` class because  
they both implement the  
`List` interface. This means that you can add items, change items, remove items and clear the list in the same way.

### **How the ArrayList works:**

The `ArrayList` class has a regular array inside it. When an element is added, it is placed into the array. If the array is not big enough, a new, larger array is created to replace the old one and the old one is removed.

### **How the LinkedList works:**

The `LinkedList` stores its items in "containers." The list has a link to the first container  
and each container has a link to the next container in the list. To add an element to the list, the element is placed into a new container and that container is linked to one of the other containers in the list.  

### ==When to use:==

Use an `ArrayList` for storing and accessing data, and `LinkedList` to manipulate data.

For many cases, the `ArrayList` is more efficient as it is common to need access to  
random items in the list, but the  
`LinkedList` provides several methods to do certain  
operations more efficiently:  

- addFirst()
- addLast()
- removeFirst()
- removeLast()
- getFirst()
- gatLast()

# ==**Java HashMap: (like concept of dict in python)**==

A `HashMap` however, store items in "**key**/**value**" pairs, and you can access them by an index of another type (e.g. a `String`).

One object is used as a key (index) to another object (value). It can store different types: `String` keys and `Integer` values, or the same type, like: `String` keys and `String` values:

```Java
import java.util.HashMap; // import the HashMap class

HashMap<String, String> capitalCities = new HashMap<String, String>();
/*
Create a HashMap object called capitalCities that will store String keys and String values
*/
```

The `HashMap` class has many useful methods. For example, to add items to it, use the `put()` method:

```Java
// Import the HashMap class
import java.util.HashMap;

public class Main {
  public static void main(String[] args) {
    // Create a HashMap object called capitalCities
    HashMap<String, String> capitalCities = new HashMap<String, String>();

    // Add keys and values (Country, City)
    capitalCities.put("England", "London");
    capitalCities.put("Germany", "Berlin");
    capitalCities.put("Norway", "Oslo");
    capitalCities.put("USA", "Washington DC");
    System.out.println(capitalCities);
  }
}
```

To access a value in the `HashMap`, use the `get()` method and refer to its key:

```Java
capitalCities.get("England");
```

To remove an item, use the `remove()` method and refer to the key:

```Java
capitalCities.remove("England");
```

To remove all items, use the `clear()` method.

To find out how many items there are, use the `size()` method.

### Loop Through a HashMap:

Loop through the items of a `HashMap` with a **for-each** loop.

**Note:** Use the `keySet()` method if you only want the keys, and use the `values()` method if you only want the values:

```Java
// Print keys
for (String i : capitalCities.keySet()) {
  System.out.println(i);
}

// Print values
for (String i : capitalCities.values()) {
  System.out.println(i);
}

// Print keys and values
for (String i : capitalCities.keySet()) {
  System.out.println("key: " + i + " value: " + capitalCities.get(i));
}
```

# **Java HashSet:**

A HashSet is a collection of items where every item is unique, and it is found in the `java.util` package:

```Java
import java.util.HashSet; // Import the HashSet class

HashSet<String> cars = new HashSet<String>();
```

The `HashSet` class has many useful methods. For example, to add items to it, use the `add()` method:

```Java
// Import the HashSet class
import java.util.HashSet;

public class Main {
  public static void main(String[] args) {
    HashSet<String> cars = new HashSet<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("BMW");
    cars.add("Mazda");
    System.out.println(cars);
  }
}
```

To check whether an item exists in a HashSet, use the `contains()` method:

`cars.contains("Mazda");`

To remove an item, use the `remove()` method.

To remove all items, use the `clear()` method.

To find out how many items there are, use the `size` method.

```Java
//Loop Thraough a Hashdet
for (String i : cars) {
  System.out.println(i);
}
```

# Java Iterator:

An `Iterator` is an object that can be used to loop through collections, like [ArrayList](https://www.w3schools.com/java/java_arraylist.asp) and [HashSet](https://www.w3schools.com/java/java_hashset.asp). It is called an "iterator" because "iterating" is the technical term for looping.

To use an Iterator, you must import it from the `java.util` package.

The `iterator()` method can be used to get an `Iterator` for any collection:

```Java
// Import the ArrayList class and the Iterator class
import java.util.ArrayList;
import java.util.Iterator;

public class Main {
  public static void main(String[] args) {

    // Make a collection
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");

    // Get the iterator
    Iterator<String> it = cars.iterator();

    // Print the first item
    System.out.println(it.next());
  }
}
```

```Java
//Loping through a collection
while(it.hasNext()) {
  System.out.println(it.next());
}
```