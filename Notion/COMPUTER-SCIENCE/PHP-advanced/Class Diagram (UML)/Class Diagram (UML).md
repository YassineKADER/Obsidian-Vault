The [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language) Class diagram is a graphical notation used to construct and visualize object oriented systems. A class diagram in the Unified Modeling Language (UML) is a type of static structure diagram that describes the structure of a system by showing the system's:

- classes,
- their attributes,
- operations (or methods),
- and the relationships among objects.

**What is a Class?**

A Class is a blueprint for an object. Objects and classes go hand in hand. We can't talk about one without talking about the other. And the entire point of Object-Oriented Design is not about objects, it's about classes, because we use classes to create objects. So a class describes what an object will be, but it isn't the object itself.

In fact, classes describe the type of objects, while objects are usable instances of classes. Each Object was built from the same set of blueprints and therefore contains the same components (properties and methods). The standard meaning is that an object is an instance of a class and object - Objects have states and behaviors.

![[Untitled 54.png|Untitled 54.png]]

**Example:**

A dog has states - color, name, breed as well as behaviors -wagging, barking, eating. An object is an instance of a class.

[![](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/01-uml-base-class-and-object-explained.png)](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/01-uml-base-class-and-object-explained.png)

## UML Class Notation

A class represent a concept which encapsulates state (**attributes**) and behavior (**operations**). Each attribute has a type. Each **operation** has a **signature**. _The class name is the_ _**only mandatory information**_.

![[Untitled 1 30.png|Untitled 1 30.png]]

**Class Name:**

- The name of the class appears in the first partition.

**Class Attributes:**

- Attributes are shown in the second partition.
- The attribute type is shown after the colon.
- Attributes map onto member variables (data members) in code.

**Class Operations (Methods):**

- Operations are shown in the third partition. They are services the class provides.
- The return type of a method is shown after the colon at the end of the method signature.
- The return type of method parameters are shown after the colon  
    following the parameter name. Operations map onto class methods in code  
    

![[Untitled 2 28.png|Untitled 2 28.png]]

### Class Visibility

The +, - and # symbols before an attribute and operation name in a class denote the visibility of the attribute and operation.

![[Untitled 3 28.png|Untitled 3 28.png]]

- Public (+)
- Private (-)
- Protected (#)
- Package (~)
- Derived (/)
- Static (underlined)

### Parameter Directionality

Each parameter in an operation (method) may be denoted as in, **out** or **inout** which specifies its direction with respect to the caller. This directionality is shown before the parameter name.

![[Untitled 4 26.png|Untitled 4 26.png]]

## Perspectives of Class Diagram

The choice of perspective depends on how far along you are in the development process. During the formulation of a **domain model**, for example, you would seldom move past the **conceptual perspective**. **Analysis models** will typically feature a mix of **conceptual and specification perspectives**. **Design model** development will typically start with heavy emphasis on the **specification perspective**, and evolve into the **implementation perspective**.

A diagram can be interpreted from various perspectives:

- **Conceptual**: represents the concepts in the domain
- **Specification**: focus is on the interfaces of Abstract Data Type (ADTs) in the software
- **Implementation**: describes how classes will implement their interfaces

The perspective affects the amount of detail to be supplied and the  
kinds of relationships worth presenting. As we mentioned above, the  
class name is the only mandatory information.  

![[Untitled 5 23.png|Untitled 5 23.png]]

## **Active Classes:**

![[Untitled 6 20.png|Untitled 6 20.png]]

An Active Class indicates that, when instantiated, the Class controls its own execution. Rather than being invoked or activated by other objects, it can operate standalone and define its own thread of behavior.

## Interface:

![[Untitled 7 18.png|Untitled 7 18.png]]

An **interface** is a [classifier](https://www.uml-diagrams.org/classifier.html) that declares of a set of coherent public features and obligations.  
An interface specifies a  
**contract**.  
Any instance of a classifier that  
**realizes** (implements) the interface must fulfill that contract and thus provides **services** described by contract.

Since interfaces are declarations, they are not instantiable. Instead, an interface specification is implemented by an instance of an instantiable classifier, which means that the instantiable classifier presents a public facade that conforms to the interface specification.

Any given classifier may implement more than one interface. Interface may be implemented by a number of different classifiers.

An [association](https://www.uml-diagrams.org/association.html?context=class-diagrams) between an interface and any other classifier implies that a conforming association must exist between any implementation of that interface and that other classifier. In particular, an association between interfaces implies that a conforming association must exist between implementations of the interfaces.

## Relationships between classes

UML is not just about pretty pictures. If used correctly, UML precisely conveys how code should be implemented from diagrams. If precisely interpreted, the implemented code will correctly reflect the  
intent of the designer. Can you describe what each of the relationships mean relative to your target programming language shown in the Figure below?  

If you can't yet recognize them, no problem this section is meant to help you to understand UML class relationships. A class may be involved in one or more relationships with other classes. A relationship can be one of the following types:

![[Untitled 8 15.png|Untitled 8 15.png]]

### Inheritance (or Generalization):

A generalization is a taxonomic relationship between a more general classifier and a more specific classifier. Each instance of the specific classifier is also an indirect instance of the general classifier. Thus, the specific classifier inherits the features of the more general classifier.

- Represents an "is-a" relationship.
- An abstract class name is shown in italics.
- SubClass1 and SubClass2 are specializations of SuperClass.

The figure below shows an example of inheritance hierarchy. SubClass1 and SubClass2 are derived from SuperClass. The relationship is displayed as a solid line with a hollow arrowhead that points from the child element to the parent element.

![[Untitled 9 12.png|Untitled 9 12.png]]

### Inheritance Example - Shapes

The figure below shows an inheritance example with two styles. Although the connectors are drawn differently, they are semantically equivalent.

![[Untitled 10 11.png|Untitled 10 11.png]]

### Association

Associations are relationships between classes in a UML Class Diagram. They are represented by a solid line between classes. Associations are typically named using a verb or verb phrase which reflects the real world problem domain.

### Simple Association

- A structural link between two peer classes.
- There is an association between Class1 and Class2

The figure below shows an example of simple association. There is an association that connects the <<control>> class Class1 and <<boundary>> class Class2. The relationship is displayed as a solid line connecting the two classes.

![[Untitled 11 7.png|Untitled 11 7.png]]

### Cardinality

Cardinality is expressed in terms of:

- one to one
- one to many
- many to many

![[Untitled 12 6.png|Untitled 12 6.png]]

### Aggregation

A special type of association.

- It represents a "part of" relationship.
- Class2 is part of Class1.
- Many instances (denoted by the *) of Class2 can be associated with Class1.
- Objects of Class1 and Class2 have separate lifetimes.

The figure below shows an example of aggregation. The relationship is displayed as a solid line with a unfilled diamond at the association end, which is connected to the class that represents the aggregate.

[![](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/12-aggregation.png)](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/12-aggregation.png)

### Composition

- A special type of aggregation where parts are destroyed when the whole is destroyed.
- Objects of Class2 live and die with Class1.
- Class2 cannot stand by itself.

The figure below shows an example of composition. The relationship is displayed as a solid line with a filled diamond at the association end, which is connected to the class that represents the whole or composite.

[![](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/13-composition.png)](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/13-composition.png)

### Dependency

An object of one class might use an object of another class in the code of a method. If the object is not stored in any field, then this is modeled as a dependency relationship.

- A special type of association.
- Exists between two classes if changes to the definition of one may cause changes to the other (but not the other way around).
- Class1 depends on Class2

The figure below shows an example of dependency. The relationship is displayed as a dashed line with an open arrow.

[![](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/14-dependency.png)](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/14-dependency.png)

The figure below shows another example of dependency. The Person  
class might have a hasRead method with a Book parameter that returns  
true if the person has read the book (perhaps by checking some  
database).  

[![](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/15-dependency-example.png)](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/15-dependency-example.png)

### Realization

Realization is a relationship between the blueprint class and the object containing its respective implementation level details. This object is said to realize the blueprint class. In other words, you can understand this as the relationship between the interface and the implementing class.

For example, the Owner interface might specify methods for acquiring property and disposing of property. The Person and Corporation classes need to implement these methods, possibly in very different ways.

[![](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/16-realization.png)](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/16-realization.png)

## Class Diagram Example: Order System

[![](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/17-class-diagram-example-order-system.png)](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/17-class-diagram-example-order-system.png)

## Class Diagram Example: GUI

A class diagram may also have notes attached to classes or relationships.

[![](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/18-uml-class-diagram-example-gui.png)](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/18-uml-class-diagram-example-gui.png)