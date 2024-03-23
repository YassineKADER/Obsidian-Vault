## Table Des Matières:

Table Des Matières:

Structure de TP

EX1

Result

EX2

Result

EX3

Result

EX4

Result

EX5

Result

# Structure de TP

Structure d'un projet Java Web (servlets et JSP) construit avec Maven. Voici une explication des différents éléments et répertoires :

1. **pom.xml** : Fichier de configuration Maven pour le projet. Il définit les dépendances, les plugins, et d'autres configurations nécessaires à la construction du projet.
2. **src/main/java** : Répertoire contenant les fichiers Java source du projet, notamment les servlets (`ex2.java`, `ex4.java`) et leurs classes associées.
3. **src/main/resources** : Répertoire contenant les ressources du projet, telles que les fichiers de propriétés pour la localisation (`languages/text_en.properties`, `languages/text_fr.properties`).
4. **src/main/webapp** : Répertoire contenant les fichiers web du projet, notamment les fichiers JSP (`ex1.jsp`, `ex2.jsp`, `ex3.jsp`, `ex4.jsp`, `ex5.jsp`, `index.jsp`), ainsi que les descripteurs de déploiement comme `WEB-INF/web.xml`.
5. **target** : Répertoire de sortie Maven contenant les fichiers générés lors de la construction du projet, tels que les fichiers compilés (`classes`), les bibliothèques (`jstl/WEB-INF/lib`), et les fichiers WAR (`jstl.war`).
6. **target/classes** : Répertoire contenant les fichiers Java compilés (`.class`) résultant de la compilation des sources.
7. **target/jstl** : Répertoire similaire à `target`, mais spécifique au projet déployé, avec une structure similaire à celle du répertoire `src/main/webapp`.
8. **target/jstl.war** : Fichier WAR généré, prêt à être déployé sur un serveur Web compatible avec Java EE (comme Tomcat, GlassFish, etc.).

```XML
.
├── pom.xml
├── src
│   └── main
│       ├── java
│       │   └── com
│       │       └── jstltp
│       │           ├── ex2.java
│       │           └── ex4.java
│       ├── resources
│       │   └── languages
│       │       ├── text_en.properties
│       │       └── text_fr.properties
│       └── webapp
│           ├── META-INF
│           │   └── context.xml
│           ├── WEB-INF
│           │   └── web.xml
│           ├── ex1.jsp
│           ├── ex2.jsp
│           ├── ex3.jsp
│           ├── ex4.jsp
│           ├── ex5.jsp
│           └── index.jsp
└── target
    ├── classes
    │   ├── com
    │   │   └── jstltp
    │   │       ├── ex2$Promo.class
    │   │       ├── ex2.class
    │   │       └── ex4.class
    │   └── languages
    │       ├── text_en.properties
    │       └── text_fr.properties
    ├── generated-sources
    │   └── annotations
    ├── jstl
    │   ├── META-INF
    │   │   └── context.xml
    │   ├── WEB-INF
    │   │   ├── classes
    │   │   │   ├── com
    │   │   │   │   └── jstltp
    │   │   │   │       ├── ex2$Promo.class
    │   │   │   │       ├── ex2.class
    │   │   │   │       └── ex4.class
    │   │   │   └── languages
    │   │   │       ├── text_en.properties
    │   │   │       └── text_fr.properties
    │   │   ├── lib
    │   │   │   ├── glassfish-jstl-11.0.20.jar
    │   │   │   ├── jakarta.el-api-5.0.1.jar
    │   │   │   ├── jakarta.servlet.jsp.jstl-3.0.0.jar
    │   │   │   ├── jakarta.servlet.jsp.jstl-api-3.0.0.jar
    │   │   │   ├── mysql-connector-j-8.3.0.jar
    │   │   │   └── protobuf-java-3.25.1.jar
    │   │   └── web.xml
    │   ├── ex1.jsp
    │   ├── ex2.jsp
    │   ├── ex3.jsp
    │   ├── ex4.jsp
    │   ├── ex5.jsp
    │   └── index.jsp
    ├── jstl.war
    ├── maven-archiver
    │   └── pom.properties
    └── maven-status
        └── maven-compiler-plugin
            └── compile
                └── default-compile
                    ├── createdFiles.lst
                    └── inputFiles.lst

30 directories, 41 files
```

# EX1

Ce code est un exemple de JSP (JavaServer Pages) utilisant des balises JSTL (JavaServer Pages Standard Tag Library) pour générer une liste d'éléments HTML représentant des nombres pairs et impairs.

1. **Directive d'importation de la librairie JSTL :** Cette directive importe la librairie JSTL Core et définit le préfixe `c` pour les balises JSTL Core dans ce fichier JSP.
2. **Déclaration du type de document et configuration des EL (Expression Language) :** Cette directive indique que les expressions EL (`${...}`) doivent être évaluées dans ce fichier JSP.
3. **Structure HTML :** Le reste du code est du code HTML standard encapsulé dans des balises `<html>`, `<head>`, et `<body>`.
4. **Balises CSS :** Ces balises définissent deux classes CSS, `.even` pour les nombres pairs et `.odd` pour les nombres impairs, avec des styles différents pour chacun.
5. **Balise** `**<c:forEach>**` **:** Cette balise JSTL Core itère sur les nombres de 1 à 10 et définit une variable `number` à chaque itération.
6. **Balise** `**<c:choose>**` **et** `**<c:when>**`**/**`**<c:otherwise>**` **:** Dans chaque itération de la boucle, `<c:choose>` est utilisé pour effectuer un choix basé sur une condition. Si le nombre est pair (testé avec `\${number % 2 == 0}`), il est affiché avec la classe `even`, sinon il est affiché avec la classe `odd`.
7. **Affichage des nombres dans la liste :** Les nombres pairs sont affichés avec un fond gris clair (`background-color: lightgrey;`), tandis que les nombres impairs sont affichés avec un fond noir et du texte blanc (`background-color: black; color: white;`).

```Java
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
<!DOCTYPE html>
<%@ page isELIgnored="false" %> 
<html>
<head>
    <meta charset="UTF-8">
    <title>Numbers</title>
    <style>
        .even {
            background-color: lightgrey;
        }
        .odd {
            background-color: black;
            color: white;
        }
    </style>
</head>
<body>
    <h1>Numbers</h1>
    <ul>
        <c:forEach begin="1" end="10" var="number">
            <c:choose>
                <c:when test="${number % 2 == 0}">
                    <li class="even">${number}</li>
                </c:when>
                <c:otherwise>
                    <li class="odd">${number}</li>
                </c:otherwise>
            </c:choose>
        </c:forEach>
    </ul>
</body>
</html>
```

## Result

![[Untitled 40.png|Untitled 40.png]]

# EX2

`servlet` code:

Ce code Java représente une servlet utilisant les fonctionnalités de JSTL (JavaServer Pages Standard Tag Library) pour afficher une liste de noms d'étudiants en fonction de la sélection d'une promotion dans un formulaire HTML.

1. **Importations de packages et directives Servlet :** Les packages importés incluent les classes nécessaires pour créer une servlet, gérer les requêtes et les réponses HTTP, et utiliser les annotations Servlet. La classe `ex2` étend `HttpServlet` pour gérer les requêtes HTTP GET et POST.
2. **Méthode** `**doGet(HttpServletRequest request, HttpServletResponse response)**` **:** Cette méthode est invoquée lorsqu'une requête GET est reçue par la servlet. Elle configure la réponse HTTP en générant un formulaire HTML pour sélectionner une promotion parmi plusieurs options.
3. **Classe interne** `**Promo**` **:** Cette classe interne déclare une structure de données pour stocker les étudiants par promotion. Elle initialise une carte (`Map`) associant le nom de la promotion à une liste de noms d'étudiants.
4. **Méthode** `**getPromo(String promoName)**` **:** Cette méthode de la classe `Promo` récupère la liste des noms d'étudiants pour une promotion donnée à partir de la carte `promoMap`. Si la promotion spécifiée n'existe pas dans la carte, elle renvoie une liste vide.
5. **Méthode** `**doPost(HttpServletRequest request, HttpServletResponse response)**` **:** Cette méthode est invoquée lorsqu'une requête POST est reçue par la servlet (lorsque le formulaire est soumis). Elle récupère le nom de la promotion sélectionnée à partir des paramètres de la requête, utilise la classe `Promo` pour obtenir la liste des étudiants pour cette promotion, puis passe cette liste à une page JSP pour l'affichage.

```Java
package com.jstltp;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
import java.io.IOException;
import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

@WebServlet("/ex2")
public class ex2 extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        response.getWriter().println("<html><head><title>Select Promo</title></head><body>");
        response.getWriter().println("<h1>Select Promo</h1>");
        response.getWriter().println("<form action='ex2' method='post'>");
        response.getWriter().println("<label for='promo'>Select Promo:</label>");
        response.getWriter().println("<select name='promo' id='promo'>");
        response.getWriter().println("<option value='promo1'>Promo 1</option>");
        response.getWriter().println("<option value='promo2'>Promo 2</option>");
        response.getWriter().println("<option value='promo3'>Promo 3</option>");
        response.getWriter().println("</select>");
        response.getWriter().println("<input type='submit' value='Submit'>");
        response.getWriter().println("</form>");
        response.getWriter().println("</body></html>");
    }

    public class Promo {
    private Map<String, List<String>> promoMap;

    public Promo() {
        promoMap = new HashMap<>();
        List<String> promo1Students = new ArrayList<>();
        promo1Students.add("John Doe");
        promo1Students.add("Jane Smith");
        List<String> promo2Students = new ArrayList<>();
        promo2Students.add("Michael Johnson");
        promo2Students.add("Emily Brown");
        List<String> promo3Students = new ArrayList<>();
        promo3Students.add("David Wilson");
        promo3Students.add("Emma Davis");
        promoMap.put("promo1", promo1Students);
        promoMap.put("promo2", promo2Students);
        promoMap.put("promo3", promo3Students);
    }

    public List<String> getPromo(String promoName) {
        return promoMap.getOrDefault(promoName, new ArrayList<>());
    }
}

    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String promoName = request.getParameter("promo");
        Promo promo = new Promo();
        List<String> result = promo.getPromo(promoName);
        request.setAttribute("promoList", result); // Set attribute for JSP
        request.getRequestDispatcher("ex2.jsp").forward(request, response); // Forward to JSP
    }
}
```

  

`jsp` file:  
Ce code représente une page JSP qui utilise les balises JSTL pour  
afficher une liste de noms d'étudiants. La directive d'importation de la  
librairie JSTL est incluse, ainsi qu'une boucle  
`<c:forEach>` qui parcourt la liste `promoList` (transmise depuis une servlet) pour afficher chaque élément dans un paragraphe `<p>` distinct.  
  

```Java
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ page isELIgnored="false" %> 
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Result Page</title>
</head>
<body>
    <h1>Students</h1>
    <c:forEach items="${promoList}" var="promoItem">
        <p>${promoItem}</p> <!-- Display each item in the list -->
    </c:forEach>
</body>
</html>
```

## Result

![[Untitled 1 19.png|Untitled 1 19.png]]

![[Untitled 2 17.png|Untitled 2 17.png]]

# EX3

`jsp` file:

Le code utilise également la balise `<jsp:useBean>` pour créer une instance de la classe `java.util.Date` appelée `now`.

Le reste du code se compose de balises HTML normales et de balises JSTL pour le formatage :

1. La balise `<fmt:setLocale>` est utilisée pour définir la locale (`en_US` ou `fr_FR`) pour le formatage.
2. La balise `<fmt:formatDate>` est utilisée pour formater la date en utilisant le modèle spécifié.
3. La balise `<fmt:formatNumber>` est utilisée pour formater un nombre (dans cet exemple, 12345.67) en tant que devise selon la locale spécifiée.

En résumé, cette page JSP illustre comment utiliser les balises JSTL pour formater la date et les nombres dans différentes langues (anglais et français) en fonction de la locale définie.

```Java
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
<%@ page contentType="text/html; charset=UTF-8" %>
<%@ page isELIgnored="false" %> 
<!DOCTYPE html>
<jsp:useBean id="now" class="java.util.Date" />
<html>
<head>
    <meta charset="UTF-8">
    <title>Formatage</title>
</head>
<body>
    <h1>Formatage ENGLISH US</h1>
    <fmt:setLocale value="en_US" />
    <p>Date formatée : <fmt:formatDate value="${now}" pattern="yy-MMM-dd"/></p>
    <p>Montant formaté : <fmt:formatNumber value="12345.67" type="currency" /></p>
    <h1>Formatage FRANCAIS</h1>
 <fmt:setLocale value="fr_FR" />
    <p>Date formatée : <fmt:formatDate value="${now}" pattern="yy-MMM-dd"/></p>
    <p>Montant formaté : <fmt:formatNumber value="12345.67" type="currency" /></p>
</body>
</html>
```

## Result

![[Untitled 3 17.png|Untitled 3 17.png]]

# EX4

code `servlet`:

Ce code Java représente une servlet qui gère les requêtes GET et POST pour afficher un formulaire de choix de langue. L'utilisateur peut sélectionner entre l'anglais et le français, puis soumettre le formulaire pour être redirigé vers une page JSP (`ex4.jsp`) qui traitera le choix de langue.

Voici une explication du code :

1. **Importations et annotation de servlet :** Le code importe les classes nécessaires pour créer une servlet et utilise l'annotation `@WebServlet` pour spécifier le chemin d'accès à cette servlet (`/ex4`).
2. **Méthode** `**doGet(HttpServletRequest request, HttpServletResponse response)**` **:** Cette méthode est invoquée lorsque la servlet reçoit une requête GET. Elle configure la réponse HTML en générant un formulaire de choix de langue avec deux options : anglais et français.
3. **Méthode** `**doPost(HttpServletRequest request, HttpServletResponse response)**` **:** Cette méthode est invoquée lorsque la servlet reçoit une requête POST (lorsque le formulaire est soumis). Elle récupère la langue sélectionnée à partir des paramètres de la requête, la stocke dans un attribut de requête (`lang`) et redirige vers la page JSP `ex4.jsp` pour le traitement ultérieur.

```Java
package com.jstltp;
import java.io.IOException;
import java.io.PrintWriter;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

@WebServlet("/ex4")
public class ex4 extends HttpServlet {
    private static final long serialVersionUID = 1L;
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html; charset=UTF-8");
        PrintWriter out = response.getWriter();
        out.println("<!DOCTYPE html>");
        out.println("<html>");
        out.println("<head>");
        out.println("<meta charset=\"UTF-8\">");
        out.println("<title>Choix de langue</title>");
        out.println("</head>");
        out.println("<body>");
        out.println("<h1>Choix de langue</h1>");
        out.println("<form method=\"post\">");
        out.println("<label for=\"lang\">Choisissez votre langue :</label>");
        out.println("<select name=\"lang\" id=\"lang\">");
        out.println("<option value=\"en\">English</option>");
        out.println("<option value=\"fr\">Français</option>");
        out.println("</select>");
        out.println("<input type=\"submit\" value=\"Valider\">");
        out.println("</form>");
        out.println("</body>");
        out.println("</html>");
    }
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String lang = request.getParameter("lang");
        request.setAttribute("lang", lang);
        request.getRequestDispatcher("ex4.jsp").forward(request, response);
    }
}
```

`jsp` file:

Voici une explication du code :

1. **Directives de page :**
    - La directive `<%@ page language="java" contentType="text/html; charset=UTF-8" %>` spécifie la langue de la page et le type de contenu comme HTML avec encodage UTF-8.
    - La directive `<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>` importe la librairie JSTL pour le formatage international.
2. **Balises JSTL :**
    - `<fmt:setLocale value="${param.lang}" />` définit la locale à utiliser en fonction du paramètre `lang` envoyé par le formulaire.
    - `<fmt:setBundle basename="languages.text" />` charge le bundle de messages à partir du fichier `languages.text`, qui contient les traductions des messages dans différentes langues.
3. **Contenu HTML :**
    - Le formulaire HTML permet à l'utilisateur de choisir entre l'anglais (`en`) et le français (`fr`) en sélectionnant une option dans un menu déroulant (`<select>`).
    - Lorsque l'utilisateur soumet le formulaire, la page est rechargée avec la langue sélectionnée grâce à la balise `<fmt:setLocale>`.
4. **Messages multilingues :**
    - `<fmt:message key="languageselection" />`, `<fmt:message key="textselection" />`, `<fmt:message key="greeting" />`, `<fmt:message key="welcome" />` sont des balises JSTL qui affichent les messages multilingues en fonction de la locale définie.

```Java
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
<%@ page isELIgnored="false" %> 
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Language Selection</title>
</head>
<body>
    <fmt:setLocale value="${param.lang}" />
    <fmt:setBundle basename="languages.text" />
    <h1><fmt:message key="languageselection" /></h1>
    <form action="" method="post">
        <label for="lang"><fmt:message key="textselection" /></label>
        <select name="lang" id="lang">
            <option value="en">English</option>
            <option value="fr">Français</option>
        </select>
        <input type="submit" value="Submit">
    </form>
    <h2>Greetings:</h2>
    <h1><fmt:message key="greeting" /></h1>
    <h2><fmt:message key="welcome" /></h2>
</body>
</html>
```

## Result

![[Untitled 4 16.png|Untitled 4 16.png]]

![[Untitled 5 14.png|Untitled 5 14.png]]

![[Untitled 6 13.png|Untitled 6 13.png]]

# EX5

`context.xml`:

Le fichier XML que vous avez fourni semble être un fichier de configuration pour définir une ressource de base de données dans un environnement Java EE (Java Enterprise Edition) ou Tomcat. Voici une explication des éléments présents dans ce fichier :

1. `<?xml version="1.0" encoding="UTF-8"?>`: Cela indique que le fichier est au format XML et utilise l'encodage UTF-8 pour les caractères.
2. `<Context>`: C'est l'élément racine du fichier de configuration. Il contient la définition de la ressource de base de données.
3. `<Resource>`: Cet élément définit la ressource de base de données avec plusieurs attributs :
    - `name`: Le nom de la ressource, qui sera utilisé pour la récupérer dans le code Java.
    - `auth`: Le mécanisme d'authentification à utiliser pour accéder à la base de données (dans ce cas, `Container` indique que l'authentification est gérée par le conteneur Tomcat).
    - `type`: Le type de la ressource, dans ce cas une source de données (`javax.sql.DataSource`).
    - `driverClassName`: Le nom de la classe du pilote JDBC à utiliser pour se connecter à la base de données (par exemple, `com.mysql.cj.jdbc.Driver` pour MySQL).
    - `url`: L'URL de connexion à la base de données.
    - `username` et `password`: Les identifiants (nom d'utilisateur et mot de passe) pour se connecter à la base de données.
    - `maxTotal`, `maxIdle`, `maxWaitMillis`: Ces attributs définissent les paramètres de connexion pool pour la source de données (nombre maximal de connexions, nombre maximal de connexions inactives, durée maximale d'attente pour une connexion, etc.).

```XML
<?xml version="1.0" encoding="UTF-8"?>
<Context>
    <Resource name="jdbc/test" auth="Container"
              type="javax.sql.DataSource" driverClassName="com.mysql.cj.jdbc.Driver"
              url="jdbc:mysql://172.19.0.3:3306/test"
              username="root" password="root"
              maxTotal="100" maxIdle="30" maxWaitMillis="10000" />
</Context>
```

`jsp` file:

Ce code représente une page JSP qui utilise les balises JSTL SQL pour interagir avec une base de données et afficher les résultats dans un tableau HTML. Voici une explication du code :

1. **Directives d'importation de balises :**
    - `<%@ taglib uri="http://java.sun.com/jsp/jstl/sql" prefix="sql" %>` : Importe la librairie JSTL SQL pour utiliser des fonctionnalités SQL dans la page JSP.
    - `<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>` : Importe la librairie JSTL Core pour utiliser des fonctionnalités de base telles que les boucles (`<c:forEach>`).
2. **Directive de page :**
    - `<%@ page isELIgnored="false" %>` : Indique que les expressions EL (`${...}`) doivent être évaluées dans cette page JSP.
3. **Contenu HTML et JSTL :**
    - La page HTML standard est encadrée dans les balises `<html>`, `<head>` et `<body>`.
    - La balise `<sql:setDataSource dataSource="jdbc/test"/>` définit la source de données à utiliser pour accéder à la base de données. Ici, `jdbc/test` fait référence à la ressource de base de données définie dans le fichier de configuration du conteneur.
    - La balise `<sql:query sql="SELECT * FROM users" var="result"/>` exécute une requête SQL pour sélectionner toutes les colonnes de la table `users` et stocke les résultats dans la variable `result`.
    - La boucle `<c:forEach>` itère sur chaque ligne du résultat (`${result.rows}`) et affiche les valeurs des colonnes `id`, `name` et `lastname` dans un tableau HTML.

```Java
<%@ taglib uri="http://java.sun.com/jsp/jstl/sql" prefix="sql" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<%@ page isELIgnored="false" %> 
<!DOCTYPE html>
<html>
<head>
   <meta charset="UTF-8">
   <title>Users List</title>
</head>
<body>
   <h1>Users List</h1>

   <sql:setDataSource dataSource="jdbc/test"/>
   <sql:query sql="SELECT * FROM users" var="result"/>
<table border="1">
<tr><th>ID</th> <th>name</th> <th>lastname</th></tr>
<c:forEach var="row" items="${result.rows}">
  <tr>
    <td>${row.id}</td>
    <td>${row.name}</td>
    <td>${row.lastname}</td> </tr>
</c:forEach>
</table>
</body>
</html>
```

## Result

![[Untitled 7 12.png|Untitled 7 12.png]]