# **Table des matières**

Table des matières

Introduction:

Structure De Projet:

Structure De BD:

# Introduction:

Ce rapport présente un projet d'e-commerce développé en utilisant des servlets Java. L'objectif principal de ce projet est de créer une plateforme en ligne permettant aux utilisateurs de naviguer à travers une sélection de produits, de les ajouter à leur panier d'achat et de passer des commandes. Le projet est structuré en utilisant le modèle MVC (Model-View-Controller), où les servlets agissent en tant que contrôleurs pour gérer les requêtes HTTP, accéder à la base de données et coordonner l'affichage des pages web dynamiques.

La structure du projet comprend plusieurs classes servlets telles que Achat, Commande, Confirmation, Login et Register, chacune responsable d'une fonctionnalité spécifique de l'application. En plus des servlets, une classe Connectiondb est utilisée pour établir une connexion à la base de données, tandis que des classes utilitaires sont présentes dans le package "outils" pour effectuer des opérations communes telles que le calcul de la taille du panier.

La base de données sous-jacente stocke des informations sur les produits disponibles à l'achat, les utilisateurs enregistrés, les commandes passées et d'autres données pertinentes pour le fonctionnement de l'application. Le projet utilise également un fichier de configuration web.xml pour mapper les URL aux servlets correspondants et pour d'autres configurations servlet.

Ce rapport examinera en détail l'architecture du projet, la mise en œuvre des fonctionnalités clés, les défis rencontrés et les solutions apportées, ainsi que les perspectives d'amélioration et les recommandations pour l'avenir du projet.

# Structure De Projet:

La structure du projet est organisée de manière conventionnelle pour une application web Java utilisant Maven comme gestionnaire de dépendances. Voici une explication de la structure du projet :

1. `**pom.xml**` : Le fichier de configuration Maven pour le projet, qui spécifie les dépendances, les plugins et d'autres configurations du projet.
2. `**src/main/java**` : Le répertoire contenant le code source Java principal de l'application. Les servlets, les classes utilitaires et d'autres classes Java nécessaires pour l'application sont généralement placés ici.
3. `**src/main/java/Achat.java**`**,** `**Commande.java**`**,** `**Confirmation.java**`**,** `**Connectiondb.java**`**,** `**Login.java**`**,** `**Register.java**`**,** `**outils/cartsize.java**` : Ces fichiers Java représentent les différentes fonctionnalités de l'application. Par exemple, "`Achat.java`" peut gérer l'affichage des produits disponibles à l'achat, "Commande.java" peut gérer le traitement des commandes, etc.
4. `**src/main/webapp/WEB-INF**` : Le répertoire contenant les fichiers de configuration de l'application web, tels que "web.xml". Ce fichier de configuration est utilisé pour mapper les URL aux servlets correspondants, définir des filtres, des écouteurs et d'autres configurations spécifiques à la servlet.
5. `**src/test/java**` : Le répertoire contenant les tests unitaires Java pour l'application. Bien qu'il semble vide dans votre structure actuelle, il est recommandé d'écrire des tests unitaires pour garantir le bon fonctionnement de l'application.
6. `**target**` : Le répertoire de sortie Maven où sont générés les fichiers compilés, les fichiers JAR, WAR et d'autres artefacts de construction. Les sous-répertoires tels que "classes", "maven-archiver", "maven-status", etc., contiennent des fichiers générés lors de la compilation et de la construction du projet.
7. `**servlet-1.0-SNAPSHOT.war**` : L'archive Web AR (Web Application ARchive) générée par Maven à partir du projet. Ce fichier WAR peut être déployé sur un serveur d'applications compatible Java EE, tel que Apache Tomcat, pour exécuter l'application web.

La structure du projet est bien organisée, avec les fichiers sources Java et les ressources web placés dans les répertoires appropriés selon les conventions de Maven et de Java EE. Cela facilite le développement, la gestion et le déploiement de l'application web.

```Shell
.
├── pom.xml
├── src
│   ├── main
│   │   ├── java
│   │   │   ├── Achat.java
│   │   │   ├── Commande.java
│   │   │   ├── Confirmation.java
│   │   │   ├── Connectiondb.java
│   │   │   ├── Login.java
│   │   │   ├── Register.java
│   │   │   └── outils
│   │   │       └── cartsize.java
│   │   └── webapp
│   │       └── WEB-INF
│   │           └── web.xml
│   └── test
│       └── java
└── target
    ├── classes
    │   ├── Achat.class
    │   ├── Commande.class
    │   ├── Confirmation.class
    │   ├── Connectiondb.class
    │   ├── Login.class
    │   ├── Register.class
    │   └── outils
    │       └── cartsize.class
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
    │       │   ├── Achat.class
    │       │   ├── Commande.class
    │       │   ├── Confirmation.class
    │       │   ├── Connectiondb.class
    │       │   ├── Login.class
    │       │   ├── Register.class
    │       │   └── outils
    │       │       └── cartsize.class
    │       ├── lib
    │       │   ├── mysql-connector-j-8.3.0.jar
    │       │   └── protobuf-java-3.25.1.jar
    │       └── web.xml
    └── servlet-1.0-SNAPSHOT.war
```

# Structure De BD:

Dans ce projet d'e-commerce utilisant MySQL comme système de gestion de base de données, nous utilisons plusieurs tables pour stocker les données relatives aux produits, aux commandes et éventuellement aux utilisateurs. Voici une description des tables utilisées :

1. **Table** **`Disque`** :
    
    - Cette table stocke les informations sur les disques disponibles à l'achat.
    - Colonnes :
        - `id` : Un identifiant unique auto-incrémenté pour chaque disque.
        - `nom` : Le nom du disque.
        - `prix` : Le prix du disque.
    
    ![[Untitled 36.png|Untitled 36.png]]
    
2. **Table** **`commande`** :
    
    - Cette table pourrait être utilisée pour enregistrer les détails des commandes passées par les utilisateurs.
    - Colonnes :
        - `description` : Une description de la commande.
    
    ![[Untitled 1 15.png|Untitled 1 15.png]]
    
    # Présentation des classes du projet:
    
    ## Class `Connectiondb`:
    
    La classe `Connectiondb` utilise le pattern Singleton pour assurer qu'une seule instance de connexion à la base de données est créée et partagée dans toute l'application. Voici une explication de la mise en œuvre du Singleton dans cette classe :
    
    - Le constructeur de la classe est privé, empêchant ainsi l'instanciation directe de la classe depuis l'extérieur.
    - La méthode statique `getConnection()` est utilisée pour récupérer l'instance unique de la connexion à la base de données. Si aucune connexion n'existe déjà, une nouvelle connexion est créée et retournée.
    - La variable statique `connection` stocke l'instance unique de la connexion, garantissant qu'elle est partagée entre toutes les parties de l'application qui ont besoin d'accéder à la base de données.
    - Les méthodes `getConnection()` et `closeConnection()` sont déclarées comme statiques pour qu'elles puissent être appelées sans avoir besoin d'instancier la classe `Connectiondb`.
    
    ![[Untitled 2 13.png|Untitled 2 13.png]]
    
    # Class `Register` (Servlet):
    
    La classe `Register` est un servlet responsable de la gestion de l'enregistrement des utilisateurs sur le site web. Voici un aperçu de ses fonctionnalités :
    
    1. **doGet()** : Cette méthode est appelée lorsqu'une requête GET est envoyée au servlet Register. Elle génère et affiche un formulaire HTML permettant aux utilisateurs de saisir leur nom, prénom et mot de passe.
    2. **doPost()** : Cette méthode est appelée lorsqu'une requête POST est envoyée au servlet Register. Elle récupère les paramètres de la requête (nom, prénom et mot de passe), crée des cookies pour stocker ces informations, puis redirige l'utilisateur vers la page de connexion (Login) avec les informations d'identification nouvellement enregistrées.
    
    ![[Untitled 3 13.png|Untitled 3 13.png]]
    
    **Preview:**
    
    ![[Untitled 4 13.png|Untitled 4 13.png]]
    
    ## Class `Login` (Servlet):
    
    Cette classe servlet `Login` est responsable de la gestion de l'authentification des utilisateurs sur le site web. Voici une description détaillée de ses fonctionnalités :
    
    1. **doGet()** : Cette méthode est appelée lorsqu'une requête GET est envoyée au servlet Login. Elle génère et affiche un formulaire HTML pour que les utilisateurs saisissent leur nom d'utilisateur et leur mot de passe.
    2. **doPost()** : Cette méthode est appelée lorsqu'une requête POST est envoyée au servlet Login. Elle récupère les paramètres de la requête (nom d'utilisateur et mot de passe), vérifie ces informations à partir des cookies de la requête, puis affiche le résultat de l'authentification. Si les informations d'identification sont valides, l'utilisateur est redirigé vers la page Achat. Sinon, un message d'erreur est affiché et l'utilisateur est redirigé vers le formulaire de connexion pour réessayer.
    
    ```Java
    @WebServlet("/Login")
    public class Login extends HttpServlet {
        protected void doGet(HttpServletRequest request, HttpServletResponse response)
                throws ServletException, IOException {
            String nom = request.getParameter("nom");
            String password = request.getParameter("password");
            response.setContentType("text/html");
            PrintWriter out = response.getWriter();
            out.println("<html>");
            out.println("<head><Title>Login:</Title></head>");
            out.println("<body>");
            out.println("<h3>Authentification</h3>");
            out.println("<span>Name: " + nom +" "+"Password: "+password+ "</span>");
            out.println("<form action=\"Login\" method=\"POST\">");
            out.println("    <label for=\"nom\">Nom:</label>");
            out.println("    <input type=\"text\" name=\"nom\" required><br>");
            out.println("    <label for=\"password\">mot de pass:</label>");
            out.println("    <input type=\"password\" name=\"password\" required><br>");
            out.println("    <input type=\"submit\" value=\"Login\">");
            out.println("</form>");
            out.println("<body>");
            out.println("</html>");
            out.close();
        }
        protected void doPost(HttpServletRequest request, HttpServletResponse response)
                throws ServletException, IOException {
            String nom = request.getParameter("nom");
            String password = request.getParameter("password");
            Cookie[] cookies = request.getCookies();
            boolean userNom = false;
            boolean userPassword = false;
    
            if (cookies != null) {
                for (Cookie cookie : cookies) {
                    if (cookie.getName().equals("nom") && cookie.getValue().equals(nom)) {
                        userNom = true;
                    }
                    if (cookie.getName().equals("password") && cookie.getValue().equals(password)) {
                        userPassword = true;
                    }
                }
            }
            response.setContentType("text/html");
            PrintWriter out = response.getWriter();
    
            out.println("<html>");
            out.println("<head><title>Authentication Result</title></head>");
            out.println("<body>");
            out.println("<h3>Authentication Result</h3>");
    
            if (userNom && userPassword) {
                out.println("<p>Welcome, " + nom + "!</p>");
                            response.sendRedirect("Achat");
            } else {
                out.println("<script>");
                out.println("alert('Invalid credentials. Please try again.');");
                out.println("window.location.href='Login';");
                out.println("</script>");
            }
    
            out.println("</body>");
            out.println("</html>");
            out.close();
        }
    
    }
    ```
    
    **Preview:**
    
    ![[Untitled 5 11.png|Untitled 5 11.png]]
    
    ## Class `Achat` (Servlet):
    
    La classe `Achat` est un servlet responsable de l'affichage des disques disponibles à l'achat sur le site web. Voici un aperçu de ses fonctionnalités :
    
    1. **doGet()** : Cette méthode est appelée lorsqu'une requête GET est envoyée au servlet Achat. Elle configure le type de contenu de la réponse HTTP et récupère la session utilisateur pour gérer le panier d'achats. Ensuite, elle récupère le nom d'utilisateur à partir des cookies de la requête, puis génère une page HTML affichant les disques disponibles à l'achat en appelant la méthode `ShowAllDisques()`.
    2. **ShowAllDisques()** : Cette méthode privée est utilisée pour afficher tous les disques disponibles à l'achat. Elle se connecte à la base de données, exécute une requête SQL pour récupérer les informations sur les disques, puis génère une table HTML affichant le nom, le prix et un lien pour ajouter chaque disque au panier.
    
    Après avoir généré la page HTML, le servlet envoie la réponse HTTP au client et termine le traitement de la requête.
    
    La classe `Achat` contribue ainsi à fournir une interface conviviale pour les utilisateurs afin de parcourir et d'ajouter des disques à leur panier d'achats sur le site web.
    
    ```Java
    @WebServlet("/Achat")
    public class Achat extends HttpServlet {
        protected void doGet(HttpServletRequest request, HttpServletResponse response)
                throws ServletException, IOException, UnsupportedEncodingException {
            response.setContentType("text/html");
            HttpSession session = request.getSession(true);
            List<String> cart = (List<String>) session.getAttribute("cart");
            if (cart == null) {
                cart = new ArrayList<>();
                session.setAttribute("cart", cart);
            }
            Cookie[] cookies = request.getCookies();
            String nomValue = null;
            if (cookies != null) {
                for (Cookie cookie : cookies) {
                    if (cookie.getName().equals("nom")) {
                        nomValue = cookie.getValue();
                    }
                }
            }
            PrintWriter out = response.getWriter();
            out.println("<html>");
            out.println("<head><title>Buy Disques</title></head>");
            out.println("<body>");
            out.println("<div style=\"margin-bottom:15px;\">");
            out.println("<h1 style=\"text-align: center;\">Welcome" + nomValue + "</h1>");
            out.println("</div>");
            out.println("<h3 style=\"text-align: center;margin-bottom:10px;\">(Disaues lists)</h3>");
            try {
                ShowAllDisques(out);
            } catch (SQLException e) {
                throw (new IOException(e.getStackTrace().toString()));
            }
        }
        private void ShowAllDisques(PrintWriter out) throws UnsupportedEncodingException, SQLException {
            Connection connection = null;
            Statement statement = null;
            ResultSet resultSet = null;
            connection = Connectiondb.getConnection();
            statement = connection.createStatement();
            resultSet = statement.executeQuery("SELECT * FROM Disque");
            out.println("<table border=\"1\" style=\"margin: auto;\">");
            out.println("<tr><th>Name</th><th>Add to cart</th></tr>");
            while (resultSet.next()) {
                String nomDisque = resultSet.getString("nom");
                String prix = resultSet.getString("prix");
                String code = resultSet.getString("id");
                out.println("<tr>");
                out.println("<td>" + nomDisque + " " + prix + " EUROS" + "</td>");
                if (nomDisque != null || nomDisque != "null") {
                    out.println("<td> <a href=\"Commande?nom=" + URLEncoder.encode(nomDisque, "UTF-8") + "&prix="
                            + URLEncoder.encode(prix, "UTF-8") + "&code=" + URLEncoder.encode(code, "UTF-8") +"\">Add to cart</a> </td>");
    
                }
                out.println("</tr>");
            }
            out.println("</table>");
            out.println("<body>");
            out.println("</html>");
            out.close();
        }
    }
    ```
    
    **Preview:**
    
    ![[Untitled 6 10.png|Untitled 6 10.png]]
    
    ## Class `Commande` (Servlet):
    
    La classe `Commande` est un servlet responsable de la gestion du panier d'achats sur le site web. Voici un aperçu de ses fonctionnalités :
    
    1. **doGet()** : Cette méthode est appelée lorsqu'une requête GET est envoyée au servlet Commande. Elle récupère les informations sur un disque spécifique à partir des paramètres de la requête (nom et prix), ainsi que le nom d'utilisateur à partir des cookies de la requête. Ensuite, elle ajoute le disque au panier d'achats de l'utilisateur en utilisant une session. Elle affiche ensuite le contenu du panier d'achats sous forme de tableau HTML, avec des liens pour supprimer des éléments du panier ou vider complètement le panier. Elle affiche également le nombre total d'articles dans le panier.
    
    Cette classe permet aux utilisateurs de consulter le contenu de leur panier d'achats, d'ajouter ou de supprimer des articles, et de procéder à la confirmation de leur commande. Elle offre une interface conviviale pour gérer les achats sur le site web.
    
    ```Java
    @WebServlet("/Commande")
    public class Commande extends HttpServlet {
        protected void doGet(HttpServletRequest request, HttpServletResponse response)
                throws ServletException, IOException {
            String itemName = request.getParameter("nom");
            String itemPrice = request.getParameter("prix");
            Cookie[] cookies = request.getCookies();
            String nomValue = null;
            if (cookies != null) {
                for (Cookie cookie : cookies) {
                    if (cookie.getName().equals("nom")) {
                        nomValue = cookie.getValue();
                    }
                }
            }
            String action = request.getParameter("action");
            HttpSession session = request.getSession(true);
            List<String> cart = (List<String>) session.getAttribute("cart");
            cart.add(itemName + " - " + itemPrice + " EUROS");
            session.setAttribute("cart", cart);
            response.setContentType("text/html");
            PrintWriter out = response.getWriter();
            out.println("<html>");
            out.println("<head><title>Shopping Cart</title></head>");
            out.println("<body>");
            out.println("<h1 style=\"text-align: center;\">Welcome" + nomValue + "</h1>");
            synchronized (session) {
                if (session.getAttribute("cart") != null) {
                    cart = (List<String>) session.getAttribute("cart");
                } else {
                    cart = new ArrayList<>();
                    session.setAttribute("cart", cart);
                }
    
                if ("remove".equals(action)) {
                    String itemToRemove = request.getParameter("item");
                    cart.remove(itemToRemove);
                } else if ("clear".equals(action)) {
                    cart.clear();
                }
                if (cart != null && !cart.isEmpty()) {
                    out.println("<table border=\"1\" style=\"margin: auto;\">");
                    out.println("<tr><th>Name</th><th>Actions</th></tr>");
                    for (String cartItem : cart) {
                        if(!cartItem.contains("null")){out.println("<tr>");
                        out.println("<td>" + cartItem + "</td>");
                        out.println("<td>");
                        out.println("<a href=\"Commande?action=remove&item=" + URLEncoder.encode(cartItem, "UTF-8")
                                + "\">Remove</a> | ");
                        out.println("</td>");
                        out.println("</tr>");}
                    }
                    out.println("</table>");
                    out.println("<p style=\"text-align: center;\">Cart Items:  " + cartsize.calcsize(cart)
                            + " disque (s) </p>");
                } else {
                    out.println("<table border=\"1\" style=\"margin: auto;\">");
                    out.println("<tr><th>Name</th></tr>");
                    out.println("<tr>");
                    out.println("<td>Cart Empty</td>");
                    out.println("</tr>");
                    out.println("</table>");
                }
                out.println("<p style=\"text-align: center;\">");
                out.println("<a href=\"Commande?action=clear\">clear cart</a>");
                out.println("</p>");
                out.println("<p style=\"text-align: center;\"><a href=\"Achat\">Add another disque</a></p>");
                out.println("<p style=\"text-align: center;\"><a href=\"Confirmation?action=confirm\">Confirm</a></p>");
                out.println("</body>");
                out.println("</html>");
            }
    
        }
    }
    ```
    
    **Preview**:
    
    ![[Untitled 7 10.png|Untitled 7 10.png]]
    
    ## Class `Confirmation` (Servlet):
    
    La classe `Confirmation` est un servlet responsable de la confirmation des commandes sur le site web. Voici un aperçu de ses fonctionnalités :
    
    1. **doGet()** : Cette méthode est appelée lorsqu'une requête GET est envoyée au servlet Confirmation. Elle récupère le nom d'utilisateur à partir des cookies de la requête, ainsi que le contenu du panier d'achats à partir de la session utilisateur. Ensuite, elle affiche le contenu du panier d'achats, offre la possibilité de confirmer la commande et affiche également une liste des commandes déjà confirmées.
    2. **confirmOrder()** : Cette méthode privée est utilisée pour confirmer la commande en insérant les articles du panier dans la base de données. Elle exécute une requête SQL d'insertion pour chaque article du panier dans la table "commande". Si l'insertion est réussie pour tous les articles, la méthode retourne true, sinon elle retourne false.
    
    La classe `Confirmation` offre ainsi une interface conviviale pour confirmer les commandes des utilisateurs sur le site web, tout en fournissant une liste des commandes déjà confirmées.
    
    ```Java
    @WebServlet("/Confirmation")
    public class Confirmation extends HttpServlet {
        protected void doGet(HttpServletRequest request, HttpServletResponse response)
                throws ServletException, IOException {
            Cookie[] cookies = request.getCookies();
            String nomValue = null;
            if (cookies != null) {
                for (Cookie cookie : cookies) {
                    if (cookie.getName().equals("nom")) {
                        nomValue = cookie.getValue();
                    }
                }
            }
            String action = request.getParameter("action");
            HttpSession session = request.getSession(true);
            List<String> cart = (List<String>) session.getAttribute("cart");
            response.setContentType("text/html");
            PrintWriter out = response.getWriter();
            out.println("<html>");
            out.println("<head><title>Shopping Cart</title></head>");
            out.println("<body>");
            out.println("<h1 style=\"text-align: center;\">Welcome" + nomValue + "</h1>");
            synchronized (session) {
                if (session.getAttribute("cart") != null) {
                    cart = (List<String>) session.getAttribute("cart");
                } else {
                    cart = new ArrayList<>();
                    session.setAttribute("cart", cart);
                }
                 if ("confirm".equals(action)) {
                try {
                boolean isOrderConfirmed = confirmOrder(cart);
                cart.clear();
                if (isOrderConfirmed) {
                out.println("<p style=\"text-align: center;\">Commandes Confirmed!</p>");
                } else {
                out.println("<p style=\"text-align: center;\">Error</p>");
                }
                } catch (Exception e) {
                e.printStackTrace();
                out.println("<p style=\"text-align: center;\">Confirmation Error</p>");
                }
                }
                if (cart != null && !cart.isEmpty()) {
                    out.println("<table border=\"1\" style=\"margin: auto;\">");
                    out.println("<tr><th>Name</th></tr>");
                    for (String cartItem : cart) {
                        if(!cartItem.contains("null")){out.println("<tr>");
                        out.println("<td>" + cartItem + "</td>");
                        out.println("</tr>");}
                    }
                    out.println("</table>");
                } else {
                    out.println("<table border=\"1\" style=\"margin: auto;\">");
                    out.println("<tr><th>Name</th></tr>");
                    out.println("<tr>");
                    out.println("<td>Your card is empty</td>");
                    out.println("</tr>");
                    out.println("</table>");
                }
                out.println("<p style=\"text-align: center;\">");
                out.println("</p>");
                out.println("<p style=\"text-align: center;\"><a href=\"Achat\">add another disque</a></p>");
               out.println("<>");
               out.println("<h1 style=\"text-align: center;\">Commandes List</h1>");
               out.println("<table border=\"1\" style=\"margin: auto;\">");
               out.println("<tr><th>description</th></tr>");
               try {
                   Connection connection = null;
                   Statement statement = null;
                   ResultSet resultSet = null;
                   connection = Connectiondb.getConnection();
                   statement = connection.createStatement();
                   resultSet = statement.executeQuery("SELECT * FROM commande");
                   while (resultSet.next()) {
                       String description = resultSet.getString("description");
                       out.println("<tr>");
                       out.println("<td>" + description + "</td>");
                       out.println("</tr>");
                    }
                } catch (SQLException e) {
                    e.printStackTrace();
                }
                out.println("</table>");
                out.println("</body>");
                out.println("</html>");
            }
    
        }
        private boolean confirmOrder(List<String> cart) {
            Connection connection = null;
            PreparedStatement preparedStatement = null;
    
            try {
                connection = Connectiondb.getConnection();
                preparedStatement = connection.prepareStatement("INSERT INTO commande (description) VALUES (?)");
                Iterator<String> iterator = cart.iterator();
                while (iterator.hasNext()) {
                    String cartItem = iterator.next();
                    preparedStatement.setString(1, cartItem);
                    preparedStatement.executeUpdate();
                }
                return true;
            } catch (SQLException e) {
                    e.printStackTrace();
            return false;
            }     }
    }
    ```
    
    **Preview**:
    
    ![[Untitled 8 9.png|Untitled 8 9.png]]
    
    # Conclusion:
    
    En conclusion, ce projet de site web d'e-commerce réalisé avec des servlets Java offre une interface conviviale pour les utilisateurs afin de parcourir, sélectionner et commander des disques musicaux. Les servlets, telles que `Login`, `Register`, `Achat`, `Commande`, et `Confirmation`, permettent aux utilisateurs de s'authentifier, de consulter et de gérer leur panier d'achats, ainsi que de confirmer leurs commandes.
    
    L'utilisation de servlets Java et de concepts tels que les sessions utilisateur, les cookies et la communication avec une base de données MySQL via JDBC permet de créer une application web robuste et fonctionnelle pour gérer les transactions d'achat en ligne. Ce projet illustre l'utilisation pratique des servlets Java pour développer des fonctionnalités avancées dans un environnement web.