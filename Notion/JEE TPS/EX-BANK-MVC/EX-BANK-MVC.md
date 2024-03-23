# **Table des matières**

Table des matières

Projet:

Structure de Projet:

Les Class Java:

CustomerServlet

Customer

CustomerDAO

Les Pages JSP:

index.jsp

finCustomer.jsp

customer.jsp

badCustomer.jsp

unknownCustomer.jsp

vipCustomer.jsp

# Projet:

Premier Page:

![[Untitled 38.png|Untitled 38.png]]

Si nous saisissons l'identifiant pour un client ayant un solde inférieur à 0 :

![[Untitled 1 17.png|Untitled 1 17.png]]

Pour les clients standards :

![[Untitled 2 15.png|Untitled 2 15.png]]

Pour les client VIP:

![[Untitled 3 15.png|Untitled 3 15.png]]

## Structure de Projet:

Structure comprend plusieurs répertoires et fichiers :

- `pom.xml` : fichier de configuration Maven pour votre projet.
- `src/main/java/controllers` : répertoire contenant les classes de contrôleurs, notamment `CustomerServlet.java`.
- `src/main/java/models` : répertoire contenant les classes de modèles, telles que `Customer.java` et `CustomerDAO.java`.
- `src/main/webapp` : répertoire contenant les ressources web, notamment le dossier `WEB-INF` qui contient les configurations et les pages JSP.
- `target` : répertoire contenant les fichiers générés lors de la compilation, comme les fichiers `.class` et les artefacts de déploiement.
- `target/classes` : répertoire contenant les fichiers compilés de vos classes Java.
- `target/demo` : répertoire contenant une version déployable de votre application.
- `target/demo.war` : fichier WAR de votre application web.
- Divers répertoires `generated-sources`, `maven-archiver`, `maven-status` : contenant des fichiers générés par Maven lors de la construction du projet.

```XML
.
├── pom.xml
├── src
│   └── main
│       ├── java
│       │   ├── controllers
│       │   │   └── CustomerServlet.java
│       │   └── models
│       │       ├── Customer.java
│       │       └── CustomerDAO.java
│       └── webapp
│           ├── WEB-INF
│           │   ├── views
│           │   │   ├── badCustomer.jsp
│           │   │   ├── customer.jsp
│           │   │   ├── findCustomer.jsp
│           │   │   ├── unknownCustomer.jsp
│           │   │   └── vipCustomer.jsp
│           │   └── web.xml
│           └── index.jsp
└── target
    ├── classes
    │   ├── controllers
    │   │   └── CustomerServlet.class
    │   └── models
    │       ├── Customer.class
    │       └── CustomerDAO.class
    ├── demo
    │   ├── META-INF
    │   ├── WEB-INF
    │   │   ├── classes
    │   │   │   ├── controllers
    │   │   │   │   └── CustomerServlet.class
    │   │   │   └── models
    │   │   │       ├── Customer.class
    │   │   │       └── CustomerDAO.class
    │   │   ├── views
    │   │   │   ├── badCustomer.jsp
    │   │   │   ├── customer.jsp
    │   │   │   ├── findCustomer.jsp
    │   │   │   ├── unknownCustomer.jsp
    │   │   │   └── vipCustomer.jsp
    │   │   └── web.xml
    │   └── index.jsp
    ├── demo.war
    ├── generated-sources
    │   └── annotations
    ├── maven-archiver
    │   └── pom.properties
    └── maven-status
        └── maven-compiler-plugin
            └── compile
                └── default-compile
                    ├── createdFiles.lst
                    └── inputFiles.lst
```

## Les Class Java:

### `CustomerServlet`

Ce Class est un servlet Java utilisé dans une application web. Voici une explication de ce qu'il fait :

1. `@WebServlet("/customer")` : Cette annotation indique que ce servlet répondra aux requêtes HTTP sur le chemin "/customer".
2. `public class CustomerServlet extends HttpServlet` : Cette classe étend la classe HttpServlet, ce qui signifie qu'elle est capable de gérer les requêtes HTTP.
3. `private CustomerDAO customerDAO;` : Cette ligne déclare une variable `customerDAO` qui sera utilisée pour interagir avec la base de données ou le stockage des clients.
4. `@Override public void init() throws ServletException` : Cette méthode est appelée lors de l'initialisation du servlet. Elle crée une instance de `CustomerDAO`.
5. `@Override protected void doGet(HttpServletRequest req, HttpServletResponse resp)` : Cette méthode est appelée lorsqu'une requête GET est reçue. Elle prend en paramètres les objets `HttpServletRequest` et `HttpServletResponse`.
6. `String id = req.getParameter("id");` : Cela récupère le paramètre "id" de la requête, qui est l'identifiant du client à rechercher.
7. `Customer customer = customerDAO.findCustomer(id);` : Cette ligne utilise l'objet `customerDAO` pour rechercher le client correspondant à l'ID fourni.
8. `req.setAttribute("customer", customer);` : Cela ajoute l'objet `customer` à l'attribut "customer" de la requête, ce qui le rend accessible dans les vues JSP.
9. Le code qui suit détermine l'adresse de la page JSP à afficher en fonction du client trouvé ou non, ainsi que de son solde. Si le client n'est pas trouvé, il redirige vers la page de recherche (`findCustomer.jsp`). Si le solde du client est inférieur à zéro, il redirige vers la page `badCustomer.jsp`. Si le solde du client est supérieur à 9999, il redirige vers la page `vipCustomer.jsp`. Sinon, il redirige vers la page `customer.jsp`.
10. `RequestDispatcher dispatcher = req.getRequestDispatcher(address);` : Cette ligne crée un objet `RequestDispatcher` pour dispatcher la requête vers la page JSP correspondante.
11. `dispatcher.forward(req, resp);` : Cela transfère la requête et la réponse vers la page JSP spécifiée par `address`.

```Java
@WebServlet("/customer")
public class CustomerServlet extends HttpServlet{
    private CustomerDAO customerDAO;
    @Override
    public void init() throws ServletException {
        customerDAO = new CustomerDAO();
    }
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        String id = req.getParameter("id");
        // System.out.println("id: " + id+id.getClass());
        Customer customer = customerDAO.findCustomer(id);
        req.setAttribute("customer", customer);
        String address = "";
        if (customer == null) {
            if (id == null)
                address = "/WEB-INF/views/findCustomer.jsp";
            else{
                req.setAttribute("badid", id);
            }
        } else {
            if(customer.getBalance()<0){
                address = "/WEB-INF/views/badCustomer.jsp";
            }
            else if(customer.getBalance()>9999){
                address = "/WEB-INF/views/vipCustomer.jsp";
            }
            else{
                address = "/WEB-INF/views/customer.jsp";
            }
        } 
        RequestDispatcher dispatcher = req.getRequestDispatcher(address);
        dispatcher.forward(req, resp);
    }
}
```

### `Customer`

Cette classe `Customer` représente un client avec ses attributs tels que l'identifiant (`id`), le prénom (`firstname`), le nom de famille (`lastname`), et le solde (`balance`). Voici une explication de ses méthodes et attributs :

- `private String id, firstname, lastname;` : Ce sont les variables membres qui stockent l'identifiant, le prénom et le nom de famille du client.
- `private double balance;` : C'est la variable membre qui stocke le solde du client.
- `public Customer(String id, String firstname, String lastname, double balance)` : C'est le constructeur de la classe `Customer` qui prend en paramètres l'identifiant, le prénom, le nom de famille et le solde du client, puis initialise les variables membres de la classe.
- `public String getId()` : Cette méthode permet de récupérer l'identifiant du client.
- `public String getFirstName()` : Cette méthode permet de récupérer le prénom du client.
- `public String getLastName()` : Cette méthode permet de récupérer le nom de famille du client.
- `public double getBalance()` : Cette méthode permet de récupérer le solde du client.
- `public double getBalanceNoSign()` : Cette méthode permet de récupérer la valeur absolue du solde du client en utilisant la fonction `Math.abs()`.

```Java
public class Customer {
    private String id, firstname, lastname;
    private double balance;
    public Customer(String id, String firstname, String lastname, double balance) {
        this.id = id;
        this.firstname = firstname;
        this.lastname = lastname;
        this.balance = balance;
    }
    public String getId() {
        return id;
    }
    public String getFirstName() {
        return firstname;
    }
    public String getLastName() {
        return lastname;
    }
    public double getBalance() {
        return balance;
    }
    public double getBalanceNoSign() {
        return Math.abs(balance);
    }
}
```

### `CustomerDAO`

Cette classe `CustomerDAO` représente un objet d'accès aux données (DAO) pour les clients. Voici une explication de ses méthodes et attributs :

- `private ArrayList<Customer> customers;` : C'est une liste qui stocke les objets `Customer` représentant les clients.
- `public CustomerDAO()` : C'est le constructeur de la classe `CustomerDAO` qui initialise la liste `customers` avec plusieurs instances de la classe `Customer`, représentant différents clients avec des identifiants, des prénoms, des noms de famille et des soldes prédéfinis.
- `public Customer findCustomer(String id)` : Cette méthode prend en paramètre l'identifiant d'un client et recherche dans la liste `customers` un client ayant cet identifiant. Si un client correspondant est trouvé, il est renvoyé; sinon, la méthode renvoie `null`.

```Java
public class CustomerDAO {
    private ArrayList<Customer> customers;
    public CustomerDAO() {
          this.customers = new ArrayList<Customer>();
          customers.add(new Customer("1", "John", "Doe", -1000.00));
          customers.add(new Customer("2", "Jane", "Doe", 2000.00));
          customers.add(new Customer("3", "Jim", "Doe", -3000.00));
          customers.add(new Customer("4", "Jill", "Doe", -4000.00));
          customers.add(new Customer("5", "Jack", "Doe", 50000.00));
          customers.add(new Customer("6", "Jenny", "Doe", 600.00));
          customers.add(new Customer("7", "Jerry", "Doe", 79000.00));
    }
    public Customer findCustomer(String id) {
        for (Customer customer : customers) {
            if (customer.getId().equals(id)) {
                return customer;
            }
        }
        return null;
    } 
}
```

## Les Pages JSP:

### `index.jsp`

Cette page JSP est une partie d'une application web qui semble inclure le contenu de `findCustomer.jsp`. Voici une explication de ce que fait cette page JSP :

- `<html>` : C'est la balise de début de la page HTML.
- `<body>` : C'est la balise de début du corps de la page HTML, où le contenu principal de la page est généralement placé.
- `<%@ include file="/WEB-INF/views/findCustomer.jsp"%>` : C'est une directive d'inclusion JSP qui inclut le contenu de la page `findCustomer.jsp`. Cette directive est utilisée pour inclure le contenu d'une autre page JSP dans la page actuelle. Dans ce cas, le chemin spécifié mène vers le répertoire `WEB-INF/views` où se trouve le fichier `findCustomer.jsp`.
- `</body>` : C'est la balise de fin du corps de la page HTML.
- `</html>` : C'est la balise de fin de la page HTML.

```Java
<html>
<body>
<%@ include file="/WEB-INF/views/findCustomer.jsp"%>
</body>
</html>
```

### `finCustomer.jsp`

- `<title>Bank MCV</title>`: Sets the title of the webpage to "Bank MCV".
- `<h1>Welcome to Bank MCV</h1>`: Displays a main heading, welcoming the user to the Bank MCV application.
- `<p>Please find the customer:</p>`: Provides a simple instruction to the user, prompting them to find a customer.
- `<form action="/bankmvc/customer" method="get">`: Defines a form where the user can input a customer ID. When submitted, the data will be sent to the "/bankmvc/customer" URL using the HTTP GET method.
- `<label for="customerId">Enter Customer ID:</label>`: Labels the input field with the text "Enter Customer ID:". The "for" attribute specifies which input field this label is associated with.
- `<input type="text" id="id" name="id">`: Creates a text input field where the user can enter the customer ID. The "id" attribute is used for identification within the document, and the "name" attribute identifies the input field in the data sent when the form is submitted.
- `<input type="submit" value="Find Customer">`: Creates a submit button with the text "Find Customer". When clicked, it submits the form data.

```Java
<html>
<head>
    <title>Bank MCV</title>
</head>
<body>
    <h1>Welcome to Bank MCV</h1>
    <p>Please find the customer:</p>
    <form action="/bankmvc/customer" method="get">
        <label for="customerId">Enter Customer ID:</label>
        <input type="text" id="id" name="id">
        <input type="submit" value="Find Customer">
    </form>
</body>
</html>
```

### `customer.jsp`

This JSP page is designed to display personalized information to a customer after they have been found in the system. Here's a breakdown of the code:

- `<%@ page import="models.Customer"%>`: This directive imports the `Customer` class from the `models` package, allowing the JSP page to access and use it.
- `<html>`, `<head>`, `<title>`: These tags define the structure and title of the HTML page.
- `<body>`: Begins the body of the HTML page, where the main content is placed.
- `<h1>Welcome, dear valued <%= ((Customer)(request.getAttribute("customer"))).getFirstName()+" "+ ((Customer)(request.getAttribute("customer"))).getLastName()%></h1>`: This line displays a personalized welcome message to the customer. It retrieves the `Customer` object stored as an attribute in the request, gets the first and last names using the `getFirstName()` and `getLastName()` methods, and concatenates them to form the greeting.
- `<p>Your current balance is: <%= ((Customer)(request.getAttribute("customer"))).getBalance() %></p>`: This line displays the customer's current balance. It retrieves the `Customer` object stored as an attribute in the request and calls the `getBalance()` method to display the balance.
- `</body>`, `</html>`: Ends the body and HTML tags, respectively.

```Java
<%@ page import="models.Customer"%>
<html>
<head>
    <title>Welcome Customer</title>
</head>
<body>
    <h1>Welcome, dear valued <%= ((Customer)(request.getAttribute("customer"))).getFirstName()+" "+ ((Customer)(request.getAttribute("customer"))).getLastName()%></h1>
    <p>Your current balance is: <%= ((Customer)(request.getAttribute("customer"))).getBalance() %></p>
</body>
</html>
```

### `badCustomer.jsp`

This JSP page seems to be notifying a customer with a negative balance that there's a problem with their account. Let's break down the code:

- `<%@ page import="models.Customer"%>`: This directive imports the `Customer` class from the `models` package, allowing the JSP page to use it.
- `<html>`, `<head>`, `<title>`: These tags define the structure and title of the HTML page.
- `<body>`: Begins the body of the HTML page, where the main content is placed.
- `<h1>Hello dear bad Client</h1>`: This line greets the customer, addressing them as a "bad client".
- `<p>Hello <%= ((Customer)(request.getAttribute("customer"))).getFirstName() %> return the money or we will use our ways to get what we want </p>`: This paragraph notifies the customer to return the money they owe. It retrieves the first name of the customer using the `getFirstName()` method of the `Customer` object stored as a request attribute.
- `Mondey that you need to return <%= ((Customer)(request.getAttribute("customer"))).getFirstName() %> is <%= ((Customer)(request.getAttribute("customer"))).getBalance() %>`: This line specifies the amount of money the customer needs to return. It retrieves the first name and balance of the customer using the `getFirstName()` and `getBalance()` methods of the `Customer` object stored as a request attribute.
- `</body>`, `</html>`: Ends the body and HTML tags, respectively.

```Java
<%@ page import="models.Customer"%>
<html>
<head>
    <title>Sorry, We Have a Problem</title>
</head>
<body>
    <h1>Hello dear bad Client</h1>
    <p>Hello <%= ((Customer)(request.getAttribute("customer"))).getFirstName() %> return the money or we will use our ways to get what we want </p>
    Mondey that you need to return <%= ((Customer)(request.getAttribute("customer"))).getFirstName() %> is <%= ((Customer)(request.getAttribute("customer"))).getBalance() %>
</body>
</html>
```

### `unknownCustomer.jsp`

This JSP page is displaying an error message to notify the user that there was a problem finding a customer with a specific ID. Let's break down the code:

- `<%@ page import="models.Customer"%>`: This directive imports the `Customer` class from the `models` package, enabling the JSP page to use it.
- `<head>`, `<title>`: These tags define the structure and title of the HTML page.
- `<body>`: Begins the body of the HTML page, where the main content is placed.
- `<h1>Oops! Something went wrong...</h1>`: This line displays a heading indicating that there was an error.
- `<p>It seems we couldn't find the customer with ID <%= request.getAttribute("badid") %>!</p>`: This paragraph informs the user that the customer with the provided ID couldn't be found. It retrieves the "badid" attribute from the request and displays it in the message.
- `<p>Please try again with a valid ID.</p>`: This paragraph advises the user to try again with a valid ID.
- `</body>`, `</html>`: Ends the body and HTML tags, respectively.

```Java
<html>
<%@ page import="models.Customer"%>
<head>
    <title>Sorry, We Have a Problem</title>
</head>
<body>
    <h1>Oops! Something went wrong...</h1>
    <p>It seems we couldn't find the customer with ID <%= request.getAttribute("badid") %>!</p>
    <p>Please try again with a valid ID.</p>
</body>
</html>
```

### `vipCustomer.jsp`

This JSP page is designed to welcome a VIP customer and display their information. Here's a breakdown of the code:

- `<%@ page import="models.Customer"%>`: This directive imports the `Customer` class from the `models` package, allowing the JSP page to use it.
- `<head>`, `<title>`: These tags define the structure and title of the HTML page.
- `<body>`: Begins the body of the HTML page, where the main content is placed.
- `<h1>Welcome, VIP customer!</h1>`: This line displays a greeting specifically for VIP customers.
- `<p>ID: <%= ((Customer)(request.getAttribute("customer"))).getId() %></p>`: This paragraph displays the ID of the customer retrieved from the `Customer` object stored as a request attribute.
- `<p>Name: <%= ((Customer)(request.getAttribute("customer"))).getFirstName() %> <%= ((Customer)(request.getAttribute("customer"))).getLastName() %></p>`: This paragraph displays the first name and last name of the customer retrieved from the `Customer` object stored as a request attribute.
- `<p>Balance: <%= ((Customer)(request.getAttribute("customer"))).getBalance() %></p>`: This paragraph displays the balance of the customer retrieved from the `Customer` object stored as a request attribute.
- `</body>`, `</html>`: Ends the body and HTML tags, respectively.

```Java
<html>
<%@ page import="models.Customer"%>
<head>
    <title>Welcome VIP Customer</title>
</head>
<body>
    <h1>Welcome, VIP customer!</h1>
    <p>ID: <%= ((Customer)(request.getAttribute("customer"))).getId() %></p>
    <p>Name: <%= ((Customer)(request.getAttribute("customer"))).getFirstName() %> <%= ((Customer)(request.getAttribute("customer"))).getLastName() %></p>
    <p>Balance: <%= ((Customer)(request.getAttribute("customer"))).getBalance() %></p>
</body>
</html>
```