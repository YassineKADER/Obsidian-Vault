**Encadré par :**

**M. Karami Fahd  
Mme. Bendaida Fatiha  
**

**Réalisateur :**

**Kader Yassine**

# Introduction:

Java Enterprise Edition (JEE), aujourd'hui renommée Jakarta EE, est une plateforme de développement pour la construction d'applications d'entreprise robustes et évolutives en utilisant la plateforme Java. Associée à un serveur d'applications , elle offre un environnement puissant pour le déploiement et l'exécution d'applications web.

![[Untitled 35.png|Untitled 35.png]]

Tomcat est un serveur web open-source développé par la fondation Apache, conçu pour exécuter des applications web basées sur les technologies Java Servlet, JavaServer Pages (JSP), et WebSocket. Il fournit un environnement d'exécution robuste et léger pour héberger des applications Java sur des serveurs web.

![[Untitled 1 14.png|Untitled 1 14.png]]

Dans ces exercices, nous explorons le potentiel de Jakarta EE en utilisant Apache Tomcat comme serveur d'application. Cependant, au préalable, il est important de mentionner un aspect crucial : le changement de nom de Java EE à Jakarta EE.

Ce changement découle d'une évolution complexe de l'écosystème Java. Initialement connue sous le nom de Java 2 Platform, Enterprise Edition (J2EE), cette technologie a subi plusieurs itérations et développements au fil des ans. Cependant, en raison de questions de propriété intellectuelle, le projet a dû changer de nom et adopter le terme Jakarta EE.

Par conséquent, dans ce projet, nous utilisons Jakarta EE, qui est la suite logique et juridiquement correcte de J2EE pour le développement d'applications d'entreprise Java.

De plus, pour faciliter le déploiement et les tests de nos applications Jakarta EE, nous avons opté pour l'utilisation d'un conteneur Docker hébergeant Apache Tomcat. Cette approche nous permet de créer un environnement de développement isolé et portable, garantissant la reproductibilité et la facilité de déploiement de nos applications.

Dans les sections suivantes, nous explorerons en détail les différentes facettes de Jakarta EE, en mettant l'accent sur son utilisation avec Apache Tomcat dans un environnement Dockerisé. Nous examinerons les fonctionnalités offertes par Jakarta EE pour le développement d'applications web robustes et les défis spécifiques rencontrés lors de la transition de J2EE à Jakarta EE. Enfin, nous présenterons des exemples pratiques illustrant l'utilisation de Jakarta EE avec Apache Tomcat dans un conteneur Dockerisé.

# Ex 1&2:

**Objectif:**

- Créer une servlet simple qui répond à une requête GET en affichant "Hi Guys" dans le navigateur.

**Détails:**

- La servlet `**HWorld**` répond à une requête GET en envoyant "Hi Guys" en tant que réponse HTML.

`HWorld` Class code:

```Java
import java.io.IOException;
import java.io.PrintWriter;
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

public class HWorld extends HttpServlet{
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        resp.setContentType("text/html");
        PrintWriter out = resp.getWriter();
        out.println("<h1>Hi Guys</h1>");
        
    }
}
```

web.xml file

```XML
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <servlet>
        <servlet-name>HelloWorldServlet</servlet-name>
        <servlet-class>HWorld</servlet-class>
    </servlet>
    
    <servlet-mapping>
        <servlet-name>HelloWorldServlet</servlet-name>
        <url-pattern>/servlet/*</url-pattern>
    </servlet-mapping>
</web-app>
```

build commands:

```Bash
mvn clean package
```

```Plain
servlets
├── pom.xml
└── servlet
    ├── pom.xml
    ├── src
    │   ├── main
    │   │   ├── java
    │   │   │   └── HWorld.java
    │   │   └── webapp
    │   │       └── WEB-INF
    │   │           ├── index.jsp
    │   │           └── web.xml
    │   └── test
    │       └── java
    └── target
        ├── classes
        │   ├── HWorld.class
        │   └── TestingServlet.class
        ├── generated-sources
        │   └── annotations
        ├── maven-archiver
        │   └── pom.properties
        ├── maven-status
        │   └── maven-compiler-plugin
        │       ├── compile
        │       │   └── default-compile
        │       │       ├── createdFiles.lst
        │       │       └── inputFiles.lst
        │       └── testCompile
        │           └── default-testCompile
        │               └── inputFiles.lst
        ├── servlet-1.0-SNAPSHOT
        │   ├── META-INF
        │   └── WEB-INF
        │       ├── classes
        │       │   ├── HWorld.class
        │       │   └── TestingServlet.class
        │       ├── index.jsp
        │       ├── lib
        │       │   ├── mysql-connector-j-8.0.33.jar
        │       │   └── protobuf-java-3.21.9.jar
        │       └── web.xml
        ├── servlet-1.0-SNAPSHOT.war
        └── test-classes
```

deploy the war file

```Bash
docker cp servlets/servlet/target/servlet-1.0-SNAPSHOT.war my-tomcat:/usr/local/tomcat/webapps/test.war
```

![[Untitled 2 12.png|Untitled 2 12.png]]

result:

![[Untitled 3 12.png|Untitled 3 12.png]]

# Ex 3:

**Objectif:**

- Créer une servlet qui affiche la date et l'heure actuelles.

**Détails:**

- La servlet `**TestingServlet**` répond à une requête GET en affichant la date et l'heure actuelles dans le navigateur.

`TestingServlet` class code:

```Java
import java.util.Date;
import jakarta.servlet.http.*;
import jakarta.servlet.ServletException;
import java.io.IOException;
import java.io.PrintWriter;

public class TestingServlet extends HttpServlet {
    @Override
    public void doGet(HttpServletRequest request, HttpServletResponse response)
    throws ServletException, IOException {
    response.setContentType("text/html"); // type MIME pour l'en-tête http
    PrintWriter out = response.getWriter();// création d'un objet PrintWriter
    out.println("<html>");
    out.println("<head><title>Date and time</title></head>");
    out.println("<body>");
    Date date = new Date();// date et heure courante
    out.println(""+date);// affichage de la date et de l'heure
    out.println("</p></b></body></html>");// fin de la page html
    }
}
```

web.xml file

```XML
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <servlet>
        <servlet-name>HelloWorldServlet</servlet-name>
        <servlet-class>TestingServlet</servlet-class>
    </servlet>
    
    <servlet-mapping>
        <servlet-name>HelloWorldServlet</servlet-name>
        <url-pattern>/servlet/*</url-pattern>
    </servlet-mapping>
</web-app>
```

build commands:

```Bash
mvn clean package
```

```Plain
servlets
├── pom.xml
└── servlet
    ├── pom.xml
    ├── src
    │   ├── main
    │   │   ├── java
    │   │   │   └── HWorld.java
    │   │   └── webapp
    │   │       └── WEB-INF
    │   │           ├── index.jsp
    │   │           └── web.xml
    │   └── test
    │       └── java
    └── target
        ├── classes
        │   ├── HWorld.class
        │   └── TestingServlet.class
        ├── generated-sources
        │   └── annotations
        ├── maven-archiver
        │   └── pom.properties
        ├── maven-status
        │   └── maven-compiler-plugin
        │       ├── compile
        │       │   └── default-compile
        │       │       ├── createdFiles.lst
        │       │       └── inputFiles.lst
        │       └── testCompile
        │           └── default-testCompile
        │               └── inputFiles.lst
        ├── servlet-1.0-SNAPSHOT
        │   ├── META-INF
        │   └── WEB-INF
        │       ├── classes
        │       │   ├── HWorld.class
        │       │   └── TestingServlet.class
        │       ├── index.jsp
        │       ├── lib
        │       │   ├── mysql-connector-j-8.0.33.jar
        │       │   └── protobuf-java-3.21.9.jar
        │       └── web.xml
        ├── servlet-1.0-SNAPSHOT.war
        └── test-classes
```

deploy the war file

```Bash
docker cp servlets/servlet/target/servlet-1.0-SNAPSHOT.war my-tomcat:/usr/local/tomcat/webapps/test.war
```

result:

![[Untitled 4 12.png|Untitled 4 12.png]]

# Ex 4:

**Objectif:**

- Créer un formulaire HTML où l'utilisateur peut saisir son nom, prénom et âge, et afficher ces informations avec la date actuelle après soumission du formulaire.

**Détails:**

- La servlet `**TestingServlet**` répond à une requête POST en récupérant les paramètres du formulaire (nom, prénom, âge), puis affiche ces informations avec la date actuelle.

`TestingServlet` class code:

```Java
import java.util.Date;
import jakarta.servlet.http.*;
import jakarta.servlet.ServletException;
import java.io.IOException;
import java.io.PrintWriter;

public class TestingServlet extends HttpServlet {
    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse
    response) throws ServletException, IOException {
    response.setContentType("text/html");
    PrintWriter out = response.getWriter();
    String nom = request.getParameter("nom");
    String prenom = request.getParameter("prenom");
    String age = request.getParameter("age");
    LocalDate dateCourante = LocalDate.now();
    out.println("<!DOCTYPE html>");
    out.println("<html>");
    out.println("<head>");
    out.println("<meta charset=\"UTF-8\">");
    out.println("<title>Page d'accueil</title>");
    out.println("</head>");
    out.println("<body>");
    out.println("<h1>Bienvenue " + prenom + " " + nom + "!</h1>");
    out.println("<p>Vous avez " + age + " ans.</p>");
    out.println("<p>Date courante: " + dateCourante + "</p>");
    out.println("</body>");
    out.println("</html>");
    }
}
```

index.jsp:

```XML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulaire</title>
</head>
<body>
    <form action="/test/servlet" method="post">
        <label for="nom">Nom:</label>
        <input type="text" id="nom" name="nom" required><br><br>
        <label for="prenom">Prenom:</label>
        <input type="text" id="prenom" name="prenom" required><br><br>
        <label for="age">Age:</label>
        <input type="number" id="age" name="age" required><br><br>
        <input type="submit" value="Envoyer">
    </form>
</body>
</html>
```

web.xml file

```XML
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <servlet>
        <servlet-name>HelloWorldServlet</servlet-name>
        <servlet-class>TestingServlet</servlet-class>
    </servlet>
    
    <servlet-mapping>
        <servlet-name>HelloWorldServlet</servlet-name>
        <url-pattern>/servlet/*</url-pattern>
    </servlet-mapping>
</web-app>
```

build commands:

```Bash
mvn clean package
```

```Plain
servlets
├── pom.xml
└── servlet
    ├── pom.xml
    ├── src
    │   ├── main
    │   │   ├── java
    │   │   │   └── HWorld.java
    │   │   └── webapp
    │   │       └── WEB-INF
    │   │           ├── index.jsp
    │   │           └── web.xml
    │   └── test
    │       └── java
    └── target
        ├── classes
        │   ├── HWorld.class
        │   └── TestingServlet.class
        ├── generated-sources
        │   └── annotations
        ├── maven-archiver
        │   └── pom.properties
        ├── maven-status
        │   └── maven-compiler-plugin
        │       ├── compile
        │       │   └── default-compile
        │       │       ├── createdFiles.lst
        │       │       └── inputFiles.lst
        │       └── testCompile
        │           └── default-testCompile
        │               └── inputFiles.lst
        ├── servlet-1.0-SNAPSHOT
        │   ├── META-INF
        │   └── WEB-INF
        │       ├── classes
        │       │   ├── HWorld.class
        │       │   └── TestingServlet.class
        │       ├── index.jsp
        │       ├── lib
        │       │   ├── mysql-connector-j-8.0.33.jar
        │       │   └── protobuf-java-3.21.9.jar
        │       └── web.xml
        ├── servlet-1.0-SNAPSHOT.war
        └── test-classes
```

deploy the war file

```Bash
docker cp servlets/servlet/target/servlet-1.0-SNAPSHOT.war my-tomcat:/usr/local/tomcat/webapps/test.war
```

result:

![[Untitled 5 10.png|Untitled 5 10.png]]

# Ex 5:

**Objectif:**

- Créer un formulaire où l'utilisateur peut saisir deux nombres et choisir une opération mathématique (addition, soustraction, multiplication, division) à effectuer sur ces nombres. Afficher le résultat de l'opération.

**Détails:**

- La servlet `**TestingServlet**` répond à une requête GET en affichant un formulaire permettant à l'utilisateur de saisir deux nombres et de choisir une opération mathématique. Après soumission du formulaire, la servlet effectue l'opération sélectionnée et affiche le résultat.

`TestingServlet` class code:

```Java
import java.util.Date;
import jakarta.servlet.http.*;
import jakarta.servlet.ServletException;
import java.io.IOException;
import java.io.PrintWriter;

public class TestingServlet extends HttpServlet {
    @Override
    public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        PrintWriter out = response.getWriter();
        response.setContentType("text/html");
        out.println("<form action=\"/test/test\" method=\"get\">\r\n" + //
                "  Number 1: <input type=\"text\" name=\"num1\" required>\r\n" + //
                "  <br>\r\n" + //
                "  Number 2: <input type=\"text\" name=\"num2\" required>\r\n" + //
                "  <br>\r\n" + //
                "  Operation:\r\n" + //
                "  <br>\r\n" + //
                "  <input type=\"radio\" name=\"operation\" value=\"add\" checked> +\r\n" + //
                "  <input type=\"radio\" name=\"operation\" value=\"subtract\"> -\r\n" + //
                "  <input type=\"radio\" name=\"operation\" value=\"multiply\"> *\r\n" + //
                "  <input type=\"radio\" name=\"operation\" value=\"divide\"> /\r\n" + //
                "  <br>\r\n" + //
                "  <input type=\"submit\" value=\"Calculate\">\r\n" + //
                "</form>");

        if (request.getParameter("num1") != null && request.getParameter("num2") != null) {
            double num1 = Double.parseDouble(request.getParameter("num1"));
            double num2 = Double.parseDouble(request.getParameter("num2"));
            String operation = request.getParameter("operation");

            double result = 0;
            switch (operation) {
                case "add":
                    result = num1 + num2;
                    break;
                case "subtract":
                    result = num1 - num2;
                    break;
                case "multiply":
                    result = num1 * num2;
                    break;
                case "divide":
                    result = num1 / num2;
                    break;
            }

            out.println("<p>Result: " + result + "</p>");
        }
    }
}
```

web.xml file

```XML
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <servlet>
        <servlet-name>HelloWorldServlet</servlet-name>
        <servlet-class>TestingServlet</servlet-class>
    </servlet>
    
    <servlet-mapping>
        <servlet-name>HelloWorldServlet</servlet-name>
        <url-pattern>/test/*</url-pattern>
    </servlet-mapping>
</web-app>
```

build commands:

```Bash
mvn clean package
```

```Plain
servlets
├── pom.xml
└── servlet
    ├── pom.xml
    ├── src
    │   ├── main
    │   │   ├── java
    │   │   │   └── HWorld.java
    │   │   └── webapp
    │   │       └── WEB-INF
    │   │           ├── index.jsp
    │   │           └── web.xml
    │   └── test
    │       └── java
    └── target
        ├── classes
        │   ├── HWorld.class
        │   └── TestingServlet.class
        ├── generated-sources
        │   └── annotations
        ├── maven-archiver
        │   └── pom.properties
        ├── maven-status
        │   └── maven-compiler-plugin
        │       ├── compile
        │       │   └── default-compile
        │       │       ├── createdFiles.lst
        │       │       └── inputFiles.lst
        │       └── testCompile
        │           └── default-testCompile
        │               └── inputFiles.lst
        ├── servlet-1.0-SNAPSHOT
        │   ├── META-INF
        │   └── WEB-INF
        │       ├── classes
        │       │   ├── HWorld.class
        │       │   └── TestingServlet.class
        │       ├── index.jsp
        │       ├── lib
        │       │   ├── mysql-connector-j-8.0.33.jar
        │       │   └── protobuf-java-3.21.9.jar
        │       └── web.xml
        ├── servlet-1.0-SNAPSHOT.war
        └── test-classes
```

deploy the war file

```Bash
docker cp servlets/servlet/target/servlet-1.0-SNAPSHOT.war my-tomcat:/usr/local/tomcat/webapps/test.war
```

result:

![[Untitled 6 9.png|Untitled 6 9.png]]

![[Untitled 7 9.png|Untitled 7 9.png]]

# Ex 6:

**Objectif:**

- Créer une servlet qui permet à l'utilisateur d'ajouter des éléments (titre et description) à une liste et affiche cette liste.

**Détails:**

- La servlet `**TestingServlet**` initialise une HashMap pour stocker les titres et descriptions des éléments. Elle répond à la fois aux requêtes GET et POST. Lorsqu'un utilisateur soumet un nouveau titre et une nouvelle description via POST, la servlet les ajoute à la liste. Ensuite, elle affiche le formulaire pour ajouter de nouveaux éléments ainsi que la liste des éléments existants.

`TestingServlet` class code:

```Java
import java.util.HashMap;
import java.util.Map;
import jakarta.servlet.http.*;
import jakarta.servlet.ServletException;
import java.io.IOException;
import java.io.PrintWriter;

public class TestingServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;
    private Map<String, String> items;

    @Override
    public void init() throws ServletException {
        super.init();
        items = new HashMap<>();
    }

    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // Retrieve form parameters
        String titre = request.getParameter("titre");
        String description = request.getParameter("description");

        // Save the titre and description in the HashMap
        items.put(titre, description);

        // Send a response with the form again
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h2>Add New Item</h2>");
        out.println("<form action='/test/test' method='post'>");
        out.println("Titre: <input type='text' name='titre'><br>");
        out.println("Description: <input type='text' name='description'><br>");
        out.println("<input type='submit' value='Add'>");
        out.println("</form>");
        out.println("<h2>Items List</h2>");
        // Display all items from the HashMap
        if (items.isEmpty()) {
            out.println("<p>No items added yet.</p>");
        } else {
            out.println("<ul>");
            for (Map.Entry<String, String> entry : items.entrySet()) {
                out.println("<li><b>Titre:</b> " + entry.getKey() + ", <b>Description:</b> " + entry.getValue() + "</li>");
            }
            out.println("</ul>");
        }
        out.println("</body></html>");
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // Prepare the HTML response with the form and existing items
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h2>Add New Item</h2>");
        out.println("<form action='/test/test' method='post'>");
        out.println("Titre: <input type='text' name='titre'><br>");
        out.println("Description: <input type='text' name='description'><br>");
        out.println("<input type='submit' value='Add'>");
        out.println("</form>");

        out.println("<h2>Items List</h2>");
        // Display all items from the HashMap
        if (items.isEmpty()) {
            out.println("<p>No items added yet.</p>");
        } else {
            out.println("<ul>");
            for (Map.Entry<String, String> entry : items.entrySet()) {
                out.println("<li><b>Titre:</b> " + entry.getKey() + ", <b>Description:</b> " + entry.getValue() + "</li>");
            }
            out.println("</ul>");
        }
        out.println("</body></html>");
    }
}
```

web.xml file

```XML
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <servlet>
        <servlet-name>HelloWorldServlet</servlet-name>
        <servlet-class>TestingServlet</servlet-class>
    </servlet>
    
    <servlet-mapping>
        <servlet-name>HelloWorldServlet</servlet-name>
        <url-pattern>/test/*</url-pattern>
    </servlet-mapping>
</web-app>
```

build commands:

```Bash
mvn clean package
```

```Plain
servlets
├── pom.xml
└── servlet
    ├── pom.xml
    ├── src
    │   ├── main
    │   │   ├── java
    │   │   │   └── HWorld.java
    │   │   └── webapp
    │   │       └── WEB-INF
    │   │           ├── index.jsp
    │   │           └── web.xml
    │   └── test
    │       └── java
    └── target
        ├── classes
        │   ├── HWorld.class
        │   └── TestingServlet.class
        ├── generated-sources
        │   └── annotations
        ├── maven-archiver
        │   └── pom.properties
        ├── maven-status
        │   └── maven-compiler-plugin
        │       ├── compile
        │       │   └── default-compile
        │       │       ├── createdFiles.lst
        │       │       └── inputFiles.lst
        │       └── testCompile
        │           └── default-testCompile
        │               └── inputFiles.lst
        ├── servlet-1.0-SNAPSHOT
        │   ├── META-INF
        │   └── WEB-INF
        │       ├── classes
        │       │   ├── HWorld.class
        │       │   └── TestingServlet.class
        │       ├── index.jsp
        │       ├── lib
        │       │   ├── mysql-connector-j-8.0.33.jar
        │       │   └── protobuf-java-3.21.9.jar
        │       └── web.xml
        ├── servlet-1.0-SNAPSHOT.war
        └── test-classes
```

deploy the war file

```Bash
docker cp servlets/servlet/target/servlet-1.0-SNAPSHOT.war my-tomcat:/usr/local/tomcat/webapps/test.war
```

result:

![[Untitled 8 8.png|Untitled 8 8.png]]

![[Untitled 9 6.png|Untitled 9 6.png]]