## Table Des Matières:

Table Des Matières:

Vue a propos le projet:

Struture De BD:

Structure De Projet:

WEB.XML

Class Singleton:

Class MessageDAO:

Class UserDAO:

Class Message:

Class User:

Les Pages JSP:

index.jsp:

header.jsp:

inscription.jsp

Login.jsp :

logout.jsp:

Conclusion:

# Vue a propos le projet:

Page principale affichée lorsqu'aucune connexion n'est établie, elle rend la page de connexion pour vous. De plus, il y a l'en-tête qui est également une page qui inclus des lien sur toutes les pages JSP.

![[Untitled 39.png|Untitled 39.png]]

Vous pouvez vous inscrire directement ici. Si l'utilisateur possède déjà un compte, vous recevrez ce message d'erreur : 'L'utilisateur existe déjà !’

![[Untitled 1 18.png|Untitled 1 18.png]]

![[Untitled 2 16.png|Untitled 2 16.png]]

Lorsque vous vous connectez, vous recevrez ces messages :

![[Untitled 3 16.png|Untitled 3 16.png]]

Enfin, lorsque vous cliquez sur 'Déconnexion', cela supprime les variables de session et vous déconnecte de votre compte.

![[Untitled 4 15.png|Untitled 4 15.png]]

# Struture De BD:

La table "users" dans la base de données a la structure suivante :

- "name" : champ de type VARCHAR(10), pouvant être NULL, utilisé pour stocker le prénom de l'utilisateur.
- "lastname" : champ de type VARCHAR(10), pouvant être NULL, utilisé pour stocker le nom de famille de l'utilisateur.
- "id" : champ de type VARCHAR(16), pouvant être NULL, utilisé pour stocker l'identifiant unique de l'utilisateur.
- "password" : champ de type TEXT, pouvant être NULL, utilisé pour stocker le mot de passe de l'utilisateur.

Cette table est conçue pour stocker les informations des utilisateurs, notamment leur nom, prénom, identifiant et mot de passe.

![[Untitled 5 13.png|Untitled 5 13.png]]

La table "messagerie" dans la base de données a la structure suivante :

- "id" : champ de type INT, non NULL, clé primaire, auto-incrémenté, utilisé comme identifiant unique pour chaque message.
- "sender_id" : champ de type INT, pouvant être NULL, utilisé pour stocker l'identifiant de l'expéditeur du message.
- "receiver_id" : champ de type INT, pouvant être NULL, utilisé pour stocker l'identifiant du destinataire du message.
- "message" : champ de type TEXT, pouvant être NULL, utilisé pour stocker le contenu du message. Le format du message est structuré comme suit : "sujet\#message".
- "sent_at" : champ de type TIMESTAMP, pouvant être NULL, par défaut à CURRENT_TIMESTAMP, utilisé pour enregistrer la date et l'heure d'envoi du message.

Cette table est conçue pour stocker les messages échangés entre les utilisateurs, enregistrant l'expéditeur, le destinataire, le contenu du message, ainsi que la date et l'heure d'envoi.

![[Untitled 6 12.png|Untitled 6 12.png]]

# Structure De Projet:

1. **pom.xml** : Ce fichier est le modèle d'objet de projet (POM) pour Maven. Il contient les détails de configuration et les dépendances du projet.
2. **src** : Ce répertoire contient le code source et les ressources du projet.
    - **main** : Ce répertoire contient le code source principal et les ressources du projet.
        - **java** : Ce répertoire contient les packages de code source Java du projet.
            - **com** : Ce répertoire représente le package racine du projet.
                - **messagerie** : Ce répertoire contient les packages Java du projet.
                    - **db** : Ce package contient les classes liées aux opérations de base de données.
                        - **Main.java** : Cette classe pourrait contenir la méthode principale pour exécuter l'application.
                        - **MessageDAO.java** : Cette classe est responsable de la gestion des opérations de base de données liées aux messages.
                        - **Singleton.java** : Cette classe représente une implémentation du modèle Singleton pour les connexions de base de données.
                        - **UserDAO.java** : Cette classe est responsable de la gestion des opérations de base de données liées aux utilisateurs.
                    - **models** : Ce package contient les classes représentant les modèles de données utilisés dans l'application.
                        - **Message.java** : Cette classe représente le modèle de message.
                        - **User.java** : Cette classe représente le modèle d'utilisateur.
        - **webapp** : Ce répertoire contient les ressources web telles que les fichiers JSP, les fichiers HTML, les fichiers CSS, etc.
            - **WEB-INF** : Ce répertoire contient des ressources qui ne sont pas directement accessibles par les clients, telles que les fichiers de configuration et les classes compilées.
                - **web.xml** : Ce fichier est le descripteur de déploiement pour l'application web.
            - **header.jsp**, **index.jsp**, **inscription.jsp**, **login.jsp**, **logout.jsp** : Ces fichiers JSP représentent différentes pages de l'application web.
3. **target** : Ce répertoire contient les sorties générées par le processus de construction.
    - **classes** : Ce répertoire contient les classes Java compilées.
    - **generated-sources** : Ce répertoire contient le code source généré.
    - **maven-archiver** : Ce répertoire contient les fichiers de métadonnées générés par Maven.
    - **maven-status** : Ce répertoire contient les fichiers d'état générés par Maven.
4. **messagerie.war** : Il s'agit du fichier d'archive de l'application web qui peut être déployé sur un conteneur de servlet comme Apache Tomcat.

```SQL
.
├── pom.xml
├── src
│   └── main
│       ├── java
│       │   └── com
│       │       └── messagerie
│       │           ├── db
│       │           │   ├── MessageDAO.java
│       │           │   ├── Singleton.java
│       │           │   └── UserDAO.java
│       │           └── models
│       │               ├── Message.java
│       │               └── User.java
│       └── webapp
│           ├── WEB-INF
│           │   └── web.xml
│           ├── header.jsp
│           ├── index.jsp
│           ├── inscription.jsp
│           ├── login.jsp
│           └── logout.jsp
└── target
    ├── classes
    │   └── com
    │       └── messagerie
    │           ├── db
    │           │   ├── Main.class
    │           │   ├── MessageDAO.class
    │           │   ├── Singleton.class
    │           │   └── UserDAO.class
    │           └── models
    │               ├── Message.class
    │               └── User.class
    ├── generated-sources
    │   └── annotations
    ├── maven-archiver
    │   └── pom.properties
    ├── maven-status
    │   └── maven-compiler-plugin
    │       └── compile
    │           └── default-compile
    │               ├── createdFiles.lst
    │               └── inputFiles.lst
    ├── messagerie
    │   ├── META-INF
    │   ├── WEB-INF
    │   │   ├── classes
    │   │   │   └── com
    │   │   │       └── messagerie
    │   │   │           ├── db
    │   │   │           │   ├── Main.class
    │   │   │           │   ├── MessageDAO.class
    │   │   │           │   ├── Singleton.class
    │   │   │           │   └── UserDAO.class
    │   │   │           └── models
    │   │   │               ├── Message.class
    │   │   │               └── User.class
    │   │   ├── lib
    │   │   │   ├── mysql-connector-j-8.3.0.jar
    │   │   │   └── protobuf-java-3.25.1.jar
    │   │   └── web.xml
    │   ├── header.jsp
    │   ├── index.jsp
    │   ├── inscription.jsp
    │   ├── login.jsp
    │   └── logout.jsp
    └── messagerie.war
```

## WEB.XML

- La balise `<web-app>` définit le début et la fin du descripteur de déploiement. Elle spécifie également la version de la spécification Servlet (dans ce cas, 4.0).
- La balise `<welcome-file-list>` indique la liste des fichiers de bienvenue pour l'application web. Dans cet exemple, seul `index.jsp` est déclaré comme fichier de bienvenue.
- Les balises `<servlet>` déclarent les servlets utilisés dans l'application. Chaque servlet est associé à un fichier JSP correspondant.
- Les servlets sont nommés avec `<servlet-name>`. Par exemple, `LoginServlet`, `InscriptionServlet` et `LogoutServlet`.
- Les chemins vers les fichiers JSP correspondants sont spécifiés à l'aide de la balise `<jsp-file>`.
- Les balises `<servlet-mapping>` déclarent les mappings entre les URL et les servlets correspondants. Chaque servlet est associé à un pattern URL spécifique.
- Les noms de servlet spécifiés dans `<servlet-name>` doivent correspondre aux noms définis dans les balises `<servlet>`.
- Les patterns URL spécifiés dans `<url-pattern>` indiquent les URL qui déclenchent l'exécution des servlets correspondants.

```XML
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
    version="4.0">

    <!-- Welcome file list -->
    <welcome-file-list>
        <welcome-file>index.jsp</welcome-file>
    </welcome-file-list>

    <!-- Servlet mappings for JSP pages -->
    <servlet>
        <servlet-name>LoginServlet</servlet-name>
        <jsp-file>/login.jsp</jsp-file>
    </servlet>
    <servlet>
        <servlet-name>InscriptionServlet</servlet-name>
        <jsp-file>/inscription.jsp</jsp-file>
    </servlet>
    <servlet>
        <servlet-name>LogoutServlet</servlet-name>
        <jsp-file>/logout.jsp</jsp-file>
    </servlet>

    <!-- Servlet mapping declarations -->
    <servlet-mapping>
        <servlet-name>LoginServlet</servlet-name>
        <url-pattern>/login</url-pattern>
    </servlet-mapping>
    <servlet-mapping>
        <servlet-name>InscriptionServlet</servlet-name>
        <url-pattern>/inscription</url-pattern>
    </servlet-mapping>
    <servlet-mapping>
        <servlet-name>LogoutServlet</servlet-name>
        <url-pattern>/logout</url-pattern>
    </servlet-mapping>

</web-app>
```

### `Class Singleton:`

```SQL
public class Singleton {
    private static final String URL = "jdbc:mysql://172.19.0.2:3306/test";
    private static final String USERNAME = "root";
    private static final String PASSWORD = "root";
    private static Connection connection;
    private Singleton() {
    }
    public static Connection getConnection() throws SQLException {
        if (connection == null || connection.isClosed()) {
            synchronized (Singleton.class) {
                if (connection == null || connection.isClosed()) {
                    try {
                        Class.forName("com.mysql.cj.jdbc.Driver");
                        connection = DriverManager.getConnection(URL, USERNAME, PASSWORD);
                        System.out.println("Connected to the database");
                    } catch (ClassNotFoundException | SQLException e) {
                        e.printStackTrace();
                        throw new SQLException("Failed to establish database connection."+e.getMessage()+e.getCause());
                    }
                }
            }
        }
        return connection;
    } 
}
```

### `Class MessageDAO:`

- Elle contient un champ privé `connection` de type `Connection` pour représenter la connexion à la base de données.
- Le constructeur de la classe initialise la connexion en appelant la méthode `getConnection()` de la classe Singleton.
- La méthode `getMessages()` récupère tous les messages de la table "messagerie" dans la base de données.
- À l'aide d'une requête SQL, elle récupère toutes les colonnes de la table "messagerie".
- En utilisant un PreparedStatement, elle exécute la requête et récupère le résultat dans un ResultSet.
- Elle parcourt ensuite chaque ligne du ResultSet pour extraire les informations sur chaque message, telles que l'identifiant, l'expéditeur, le destinataire, le contenu et la date d'envoi.
- Elle crée ensuite des objets Message à partir des données extraites et les ajoute à une liste de messages.
- Enfin, elle retourne la liste de messages.

```SQL
public class MessageDAO {
    private final Connection connection;

    public MessageDAO() throws SQLException {
        this.connection = Singleton.getConnection();
    }

    public List<Message> getMessages() throws SQLException {
        List<Message> messages = new ArrayList<>();
        String query = "SELECT * FROM messagerie";
        try (PreparedStatement statement = connection.prepareStatement(query)) {
            ResultSet resultSet = statement.executeQuery();
            while (resultSet.next()) {
                String id = resultSet.getString("id");
                String senderId = resultSet.getString("sender_id");
                String messageContent = resultSet.getString("message");
                String receiverId =resultSet.getString("receiver_id");
                Date sentAt = resultSet.getTimestamp("sent_at");
                messages.add(new Message(id, senderId,receiverId ,messageContent, sentAt));
            }
        }
        return messages;
    }
}
```

### `Class UserDAO:`

- La classe contient un champ privé `connection` de type `Connection` pour représenter la connexion à la base de données.
- Le constructeur de la classe initialise la connexion en appelant la méthode `getConnection()` de la classe Singleton.
- La méthode `saveUser(User user)` permet de sauvegarder un nouvel utilisateur dans la base de données. Elle utilise une requête SQL d'insertion pour ajouter les informations de l'utilisateur dans la table "users".
- La méthode `getUserByNameAndLastname(String name, String lastname)` permet de récupérer un utilisateur à partir de son prénom et de son nom de famille. Elle utilise une requête SQL de sélection pour rechercher l'utilisateur correspondant dans la table "users".
- La méthode `userExists(String firstName, String lastName)` vérifie si un utilisateur avec le prénom et le nom de famille spécifiés existe déjà dans la base de données. Elle utilise une requête SQL de comptage pour compter le nombre d'occurrences de l'utilisateur dans la table "users" et retourne vrai si le compte est supérieur à zéro, sinon faux.

```SQL
public class UserDAO {
    private final Connection connection;

    public UserDAO() throws SQLException {
        this.connection = Singleton.getConnection();
    }

    public void saveUser(User user) throws SQLException {
        String query = "INSERT INTO users (name, lastname, id, password) VALUES (?, ?, ?, ?)";
        try (PreparedStatement statement = connection.prepareStatement(query)) {
            statement.setString(1, user.getName());
            statement.setString(2, user.getLastname());
            statement.setString(3, user.getId());
            statement.setString(4, user.getPassword());
            statement.executeUpdate();
        }
    }
    public User getUserByNameAndLastname(String name, String lastname) throws SQLException {
        String query = "SELECT * FROM users WHERE name=? AND lastname=?";
        try (PreparedStatement statement = connection.prepareStatement(query)) {
            statement.setString(1, name);
            statement.setString(2, lastname);
            ResultSet resultSet = statement.executeQuery();
            if (resultSet.next()) {
                String id = resultSet.getString("id");
                String password = resultSet.getString("password");
                return new User(name, lastname, id, password);
            }
        }
        return null;
    }
    public boolean userExists(String firstName, String lastName) throws SQLException {
        String query = "SELECT COUNT(*) AS count FROM users WHERE name=? AND lastname=?";
        try (PreparedStatement statement = connection.prepareStatement(query)) {
            statement.setString(1, firstName);
            statement.setString(2, lastName);
            ResultSet resultSet = statement.executeQuery();
            resultSet.next();
            int count = resultSet.getInt("count");
            return count > 0;
        }
    }
}
```

### `Class Message:`

- Elle contient des champs pour l'identifiant du message (`id`), l'identifiant de l'expéditeur (`sender_id`), l'identifiant du destinataire (`receiver_id`), le contenu du message (`message`), et la date d'envoi (`sent_at`).
- Le constructeur de la classe prend ces champs comme arguments et initialise les valeurs correspondantes.
- Des méthodes d'accès (getters et setters) sont fournies pour chaque champ, permettant de lire et de modifier les valeurs des champs de l'objet `Message`.
- La méthode `toString()` est redéfinie pour renvoyer une représentation textuelle de l'objet `Message`, affichant les valeurs de tous les champs.
- Cette classe encapsule les données d'un message et fournit des méthodes pour accéder et manipuler ces données. Elle peut être utilisée pour créer, modifier et afficher des messages dans le système.

```SQL
public class Message {
    String id;
    String sender_id;
    String receiver_id;
    String message;
    Date sent_at;
    public Message(String id, String sender_id, String receiver_id, String message, Date sent_at) {
        this.id = id;
        this.sender_id = sender_id;
        this.receiver_id = receiver_id;
        this.message = message;
        this.sent_at = sent_at;
    }
    public String getId() {
        return id;
    }
    public void setId(String id) {
        this.id = id;
    }
    public String getSender_id() {
        return sender_id;
    }
    public void setSender_id(String sender_id) {
        this.sender_id = sender_id;
    }
    public String getReceiver_id() {
        return receiver_id;
    }
    public void setReceiver_id(String receiver_id) {
        this.receiver_id = receiver_id;
    }
    public String getMessage() {
        return message;
    }
    public void setMessage(String message) {
        this.message = message;
    }
    public Date getSent_at() {
        return sent_at;
    }
    public void setSent_at(Date sent_at) {
        this.sent_at = sent_at;
    }
    @Override
    public String toString() {
        return "Message [id=" + id + ", sender_id=" + sender_id + ", receiver_id=" + receiver_id + ", message="
                + message + ", sent_at=" + sent_at + "]";
    }
}
```

### `Class User:`

- Elle contient des champs privés pour le prénom (`name`), le nom de famille (`lastname`), l'identifiant (`id`), et le mot de passe (`password`) de l'utilisateur.
- La classe possède plusieurs constructeurs :
    - Un constructeur prenant le prénom, le nom de famille, l'identifiant et le mot de passe comme arguments et initialisant les champs correspondants.
    - Un constructeur sans arguments qui initialise tous les champs à des valeurs par défaut.
    - Un constructeur prenant le prénom, le nom de famille et le mot de passe comme arguments, générant un identifiant unique à l'aide de la méthode `generateUniqueId()`, et initialisant les champs correspondants.
- Des méthodes d'accès (getters et setters) sont fournies pour chaque champ, permettant de lire et de modifier les valeurs des champs de l'objet `User`.
- La méthode statique `generateUniqueId()` génère un identifiant unique à l'aide de la classe `UUID` et le retourne sous forme de chaîne de caractères.
- La méthode `toString()` est redéfinie pour renvoyer une représentation textuelle de l'objet `User`, affichant les valeurs de tous les champs.

```SQL
public class User {
   private String name;
   private String lastname;
   private String id;
   private String password;
   
   public User(String name, String lastname, String id, String password) {
    this.name = name;
    this.lastname = lastname;
    this.id = id;
    this.password = password;
}

public User(){
    this.name="";
    this.lastname="";
    this.id="";
    this.password="";
   }

   public User(String name, String lastname,String password){
    this.name = name;
    this.lastname = lastname;
    this.id = generateUniqueId();
    this.password = password;
   }

public String getName() {
    return name;
}

public String getLastname() {
    return lastname;
}

public String getId() {
    return id;
}

public String getPassword() {
    return password;
}

public void setName(String name) {
    this.name = name;
}

public void setLastname(String lastname) {
    this.lastname = lastname;
}

public void setId(String id) {
    this.id = id;
}

public void setPassword(String password) {
    this.password = password;
}
public static String generateUniqueId() {
        // Generate a UUID (Universally Unique Identifier)
        UUID uuid = UUID.randomUUID();
        
        // Convert UUID to string and remove hyphens
        String uuidString = uuid.toString().replaceAll("-", "");
        
        // Trim or pad with zeros to ensure the length is exactly 16 characters
        if (uuidString.length() < 16) {
            uuidString = String.format("%-16s", uuidString).replace(' ', '0');
        } else if (uuidString.length() > 16) {
            uuidString = uuidString.substring(0, 16);
        }
        
        return uuidString;
    }

@Override
public String toString() {
    return "User [name=" + name + ", lastname=" + lastname + ", id=" + id + ", password=" + password + "]";
}
}
```

# Les Pages JSP:

### `index.jsp`:

- Tout d'abord, la page importe les classes nécessaires, notamment celles pour gérer les sessions, les utilisateurs et les messages, ainsi que la liste des messages.
- La session actuelle est récupérée à l'aide de `request.getSession(false)`. Si aucune session n'existe ou si aucun utilisateur n'est connecté (représenté par l'attribut "user" dans la session), l'utilisateur est redirigé vers la page de connexion.
- Si un utilisateur est connecté, ses informations sont extraites de la session et stockées dans la variable `currentuser`.
- Un objet `MessageDAO` est créé pour interagir avec la base de données et récupérer les messages de l'utilisateur actuellement connecté.
- La liste des messages est récupérée à l'aide de la méthode `getMessages()` de `MessageDAO`.
- Ensuite, la page inclut le contenu de l'en-tête à l'aide de la directive `<%@ include file="header.jsp"%>`.
- Un message de bienvenue est affiché, indiquant le nom de l'utilisateur connecté.
- La liste des messages est affichée dans un tableau HTML, avec deux colonnes pour le sujet et le contenu de chaque message.
- Pour chaque message dans la liste, le contenu du message est séparé en deux parties (sujet et contenu) à l'aide de la méthode `split()` et affiché dans le tableau.

```SQL
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="jakarta.servlet.http.HttpSession" %>
<%@ page import="com.messagerie.models.User" %>
<%@ page import="com.messagerie.models.Message" %>
<%@ page import="com.messagerie.db.MessageDAO" %>
<%@ page import="java.util.List" %>
<html>
<head>
    <meta charset="UTF-8">
</head>
<body>

<%
HttpSession currentsession = request.getSession(false);
if (currentsession == null || currentsession.getAttribute("user") == null) { 
    request.getRequestDispatcher("/login").include(request, response);
} else { 
    User currentuser = (User) currentsession.getAttribute("user");
    MessageDAO messagedao = new MessageDAO();
    List<Message> messages = messagedao.getMessages();
%>
    <%@ include file="header.jsp"%>
    <h1>Hello <%=currentuser.getName()%>, you're connected</h1>
    <h2>Here are your messages:</h2>
    <table border="1">
        <tr>
            <th>Subject</th>
            <th>Message</th>
        </tr>
        <% for (Message message : messages) { 
            String[] parts = message.getMessage().split("#", 2); // Split message content into subject and message parts
        %>
            <tr>
                <td><%=parts[0]%></td> <!-- Display the subject part -->
                <td><%=parts[1]%></td> <!-- Display the message part -->
            </tr>
        <% } %>
    </table>
<%
} // end else
%>

</body>
</html>
```

### `header.jsp`:

- La directive `<%@ page %>` est utilisée pour définir les paramètres de la page, tels que le langage de programmation, le type de contenu et l'encodage de la page.
- Le menu de navigation est encapsulé dans une balise `<nav>`, qui représente une section de navigation sur la page.
- À l'intérieur de la balise `<nav>`, il y a une liste à puces `<ul>` avec quatre éléments de liste `<li>`, chacun contenant un lien `<a>` vers une autre page ou une autre partie du site.
- Les liens pointent vers les destinations suivantes :
    - "/messagerie/" : probablement la page principale de la messagerie.
    - "inscription" : la page d'inscription.
    - "login" : la page de connexion.
    - "logout" : la page de déconnexion.
- Les styles CSS en ligne sont utilisés pour définir la mise en page du menu de navigation, tels que la largeur, l'espacement entre les éléments, la direction de flexion, l'alignement des éléments, etc.

```SQL
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<nav style="width: 100%;">
    <ul style="display: flex;gap:10%;flex-direction:row;align-items:center; width:100%;">
        <li><a href="/messagerie/">Sujet</a></li>
        <li><a href="inscription">Inscription</a></li>
        <li><a href="login">Identification</a></li>
        <li><a href="logout">Logout</a></li>
    </ul>
</nav>
```

### `inscription.jsp`

Ce code représente une page JSP pour l'inscription d'un nouvel utilisateur. Voici un résumé de son fonctionnement :

- Les directives `<%@ page %>` sont utilisées pour définir les paramètres de la page, tels que le langage de programmation, le type de contenu et l'encodage de la page.
- Les classes nécessaires sont importées à l'aide des directives `<%@ page import %>`.
- Les paramètres de la requête sont récupérés à l'aide de `request.getParameter()` pour obtenir les valeurs soumises par le formulaire d'inscription.
- Un objet `UserDAO` est créé pour interagir avec la base de données et vérifier si l'utilisateur existe déjà.
- Si tous les paramètres requis sont présents, la page vérifie d'abord si l'utilisateur existe déjà en appelant la méthode `userExists()` de `UserDAO`. Si l'utilisateur existe, un message d'erreur est affiché.
- Si l'utilisateur n'existe pas, un nouvel objet `User` est créé avec les informations fournies et enregistré dans la base de données à l'aide de la méthode `saveUser()` de `UserDAO`.
- Si l'enregistrement est réussi, un message de confirmation est affiché et l'utilisateur est redirigé vers la page principale de la messagerie.
- Si une exception SQLException se produit pendant le processus d'inscription, un message d'erreur est affiché.
- La partie HTML de la page contient un formulaire d'inscription avec des champs pour le nom d'utilisateur, le mot de passe, le prénom et le nom de famille.
- L'en-tête de la page est inclus à l'aide de la directive `<%@ include %>`, qui référence le fichier "header.jsp".

```SQL
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="com.messagerie.db.UserDAO" %>
<%@ page import="com.messagerie.models.User" %>
<%@ page import="java.sql.SQLException" %>
<%@ page import="java.io.PrintWriter" %>
<%
String username = request.getParameter("username"); // Assuming you have a field for username in your form
String password = request.getParameter("password");
String firstName = request.getParameter("name");
String lastName = request.getParameter("lastname");
UserDAO userDAO = new UserDAO();
if (username != null && password != null && firstName != null && lastName != null) {
    // Check if the user already exists                             
    boolean userExists = false;
    try {
        userExists = userDAO.userExists(firstName, lastName);
    } catch (SQLException e) {
        out.println("Error checking user existence: " + e.getMessage());
    }
    if (userExists) {
        out.println("<h1 style=\"color:red\">User already exists!</h1>");
    } else {
        User newUser = new User(firstName, lastName, password);
        try {
            userDAO.saveUser(newUser);
            out.println("User registered successfully!");
            HttpSession currentsession = request.getSession(false);
            currentsession.setAttribute("user", newUser);
            response.sendRedirect("/messagerie");
        } catch (SQLException e) {
            out.println("Error registering user: " + e.getMessage());
        }
    }
}
%>
<html>
<head>
    <meta charset="UTF-8">
    <title>User Registration</title>
</head>
<body>
<%@ include file="header.jsp"%>
    <h1>User Registration</h1>
    <form action="inscription" method="post">
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required><br>
        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required><br>
        <label for="name">First Name:</label>
        <input type="text" id="name" name="name" required><br>
        <label for="lastname">Last Name:</label>
        <input type="text" id="lastname" name="lastname" required><br>
        <input type="submit" value="Register">
    </form>
</body>
</html>
```

### `Login.jsp` :

Ce code représente une page JSP pour la connexion d'un utilisateur. Voici un résumé de son fonctionnement :

- Les directives `<%@ page %>` sont utilisées pour définir les paramètres de la page, tels que le langage de programmation, le type de contenu et l'encodage de la page.
- Les classes nécessaires sont importées à l'aide des directives `<%@ page import %>`.
- L'en-tête de la page est inclus à l'aide de la directive `<%@ include %>`, qui référence le fichier "header.jsp".
- La directive `<%@ page isErrorPage="true" %>` indique que cette page peut être utilisée comme page d'erreur personnalisée.
- Un formulaire de connexion est affiché, comprenant des champs pour le nom, le nom de famille et le mot de passe de l'utilisateur.
- Lorsque le formulaire est soumis, les paramètres de la requête sont récupérés à l'aide de `request.getParameter()`.
- Un objet `UserDAO` est créé pour interagir avec la base de données et récupérer l'utilisateur correspondant aux informations de connexion fournies.
- Si les informations de connexion sont valides et correspondent à un utilisateur enregistré, une session est créée pour cet utilisateur et il est redirigé vers la page principale de la messagerie.
- Si les informations de connexion sont invalides, un message d'erreur est affiché.
- Si une exception SQLException se produit pendant le processus de connexion, un message d'erreur est affiché.

```SQL
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="com.messagerie.db.UserDAO" %>
<%@ page import="com.messagerie.models.User" %>
<%@ page import="java.sql.SQLException" %>
<%@ page import="jakarta.servlet.http.HttpSession" %>
<%@ include file="header.jsp"%>
<%@ page isErrorPage="true" %>
<h1>Login</h1>
<form method="post" action="login">
    <label for="name">Name:</label><br>
    <input type="text" id="name" name="name"><br>
    <label for="lastname">Last Name:</label><br>
    <input type="text" id="lastname" name="lastname"><br>
    <label for="password">Password:</label><br>
    <input type="password" id="password" name="password"><br><br>
    <input type="submit" value="Login">
</form>
<%
    String name = request.getParameter("name");
    String lastname = request.getParameter("lastname");
    String password = request.getParameter("password");

        UserDAO userDAO1 = new UserDAO();
    if (name != null && lastname != null && password != null) {
        UserDAO userDAO = new UserDAO();
        try {
            User user = userDAO.getUserByNameAndLastname(name, lastname);
            if (user != null && user.getPassword().equals(password)) {
                HttpSession currentsession = request.getSession(false);
                currentsession.setAttribute("user", user);
                response.sendRedirect("/messagerie"); // Redirect to home page after successful login
            } else {
                out.println("<h2>Invalid credentials. Please try again.</h2>");
            }
        } catch (SQLException e) {
            out.println("<h2>An error occurred while processing your request. Please try again later.</h2>");
            e.printStackTrace();
        }
    }
%>
```

### `logout.jsp`:

Ce code représente une page JSP pour la déconnexion d'un utilisateur. Voici un résumé de son fonctionnement :

- Les directives `<%@ page %>` sont utilisées pour définir les paramètres de la page, tels que le langage de programmation, le type de contenu et l'encodage de la page.
- La classe nécessaire est importée à l'aide de la directive `<%@ page import %>`.
- La session actuelle est récupérée à l'aide de `request.getSession(false)` pour éviter de créer une nouvelle session si elle n'existe pas.
- Si une session existe, l'attribut "user" est supprimé de la session à l'aide de `currentsession.removeAttribute("user")`. Cela peut être utilisé pour déconnecter l'utilisateur en supprimant son attribut de session.
- Ensuite, l'utilisateur est redirigé vers la page de connexion à l'aide de `response.sendRedirect("/messagerie/login")`. Cela permet à l'utilisateur de revenir à la page de connexion après s'être déconnecté.

```SQL
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="jakarta.servlet.http.HttpSession" %>
<%
    HttpSession currentsession = request.getSession(false); // Don't create a new session if it doesn't exist
    if (currentsession != null) {
        currentsession.removeAttribute("user"); // Example: if you have a user attribute
    }
    response.sendRedirect("/messagerie/login");
%>
```

# Conclusion:

Ce projet est une application web de messagerie qui permet aux utilisateurs de s'inscrire, de se connecter pour consulter leurs messages et de se déconnecter. Il utilise une base de données MySQL pour stocker les informations des utilisateurs et des messages. Les interfaces utilisateur sont créées à l'aide de fichiers JSP, et les servlets sont utilisés pour gérer les requêtes HTTP. En résumé, c'est une application simple mais fonctionnelle qui offre une expérience de messagerie de base aux utilisateurs.