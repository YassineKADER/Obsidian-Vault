## Table Des Matières:

Table Des Matières:

Ex1:

Ex2:

Ex2.2:

Ex3:

Ex4:

Ex5:

Ex6:

Ex7:

Ex8:

Ex9:

# Ex1:

`index.jsp`

```Java
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Conversion Fahrenheit to Celsius</title>
</head>
<body>
    <h2>Convert Fahrenheit to Celsius</h2>
    <form method="get">
        Enter Fahrenheit temperature:
        <input type="text" name="temp">
        <input type="submit" value="Convert">
    </form>

    <%-- Check if request contains parameter "temp" --%>
    <% String tempF = request.getParameter("temp");
        if (tempF != null && !tempF.isEmpty()) {
            try {
                double fahrenheit = Double.parseDouble(tempF);
                double celsius = ((fahrenheit - 32) * 5) / 9.0;
    %>
                <table border="1">
                    <tr>
                        <th>Fahrenheit</th>
                        <th>Celsius</th>
                    </tr>
                    <tr>
                        <td align="center"><%= fahrenheit %></td>
                        <td align="center"><%= celsius %></td>
                    </tr>
                </table>
    <%      } catch (NumberFormatException e) { %>
                <p>Please enter a valid temperature.</p>
    <%      }
        }
    %>
</body>
</html>
```

Description du code :

1. Les directives JSP :
    - `<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>` : Cette directive définit la langue du code comme Java et le type de contenu comme du HTML avec l'encodage UTF-8.
    - `<!DOCTYPE html>` : La déclaration du type de document HTML utilisé dans la page.
2. La structure HTML :
    - `<html>`, `<head>`, `<title>`, `<body>` : Ces balises définissent la structure de base de la page HTML.
3. Le formulaire :
    - `<form method="get">` : Définit un formulaire HTML qui utilise la méthode GET pour soumettre les données.
    - `Enter Fahrenheit temperature:` : Label pour le champ de saisie de température Fahrenheit.
    - `<input type="text" name="temp">` : Champ de saisie où l'utilisateur peut entrer une température en Fahrenheit.
    - `<input type="submit" value="Convert">` : Bouton de soumission du formulaire pour effectuer la conversion.
4. Le code Java/JSP :
    - `<% String tempF = request.getParameter("temp");` : Récupère la valeur saisie dans le champ de température Fahrenheit.
    - `if (tempF != null && !tempF.isEmpty()) { ... }` : Vérifie si une valeur de température a été fournie.
    - `try { ... } catch (NumberFormatException e) { ... }` : Tente de convertir la température de Fahrenheit à Celsius, et gère les erreurs si la valeur saisie n'est pas un nombre valide.
    - `<%= fahrenheit %>` et `<%= celsius %>` : Affiche les valeurs de température Fahrenheit et Celsius dans la table HTML.
    - `<p>Please enter a valid temperature.</p>` : Affiche un message d'erreur si la valeur saisie n'est pas valide.

![[Untitled 37.png|Untitled 37.png]]

# Ex2:

`index.jsp`

```Java
<%@ page import="jakarta.servlet.http.HttpServletRequest" %>
<%@ page import="java.io.*" %>
<%@ page import="java.util.*" %>

<%
// Vérification si la requête est de type POST
if (request.getMethod().equals("POST")) {
    // Récupération de la couleur sélectionnée
    String couleur = request.getParameter("couleur");
%>
    <html>
    <head>
        <title>Selection de couleur</title>
    </head>
    <body>
        <h2>Vous avez choisi la couleur <%= couleur %></h2>
    </body>
    </html>
<%
} else {
%>
    <html>
    <head>
        <title>Selection de couleur</title>
    </head>
    <body>
        <h2>Selectionnez une couleur :</h2>
        <form method="post" action="">
            <select name="couleur">
                <option value="rouge">Rouge</option>
                <option value="vert">Vert</option>
                <option value="bleu">Bleu</option>
            </select>
            <input type="submit" value="Choisir">
        </form>
    </body>
    </html>
<%
}
%>
```

Description du code :

1. Importation des classes :
    - `<%@ page import="jakarta.servlet.http.HttpServletRequest" %>` : Importe la classe HttpServletRequest pour permettre l'utilisation de la requête HTTP.
    - `<%@ page import="java.io.*" %>` : Importe des classes d'entrée/sortie pour gérer les flux.
    - `<%@ page import="java.util.*" %>` : Importe des classes utilitaires Java.
2. Bloc de script JSP :
    - `<% ... %>` : Ce bloc contient du code Java à exécuter côté serveur.
3. Vérification de la méthode de requête :
    - `if (request.getMethod().equals("POST")) { ... }` : Vérifie si la méthode de requête est POST.
4. Traitement pour la méthode POST :
    - `String couleur = request.getParameter("couleur");` : Récupère la couleur sélectionnée à partir des paramètres de la requête POST.
    - Affichage de la page HTML avec la couleur sélectionnée.
5. Traitement pour la méthode GET :
    - Sinon, affiche un formulaire pour permettre à l'utilisateur de sélectionner une couleur.
    - `<form method="post" action="">` : Formulaire avec la méthode POST pour envoyer les données à la même page.
    - `<select name="couleur"> ... </select>` : Liste déroulante pour sélectionner une couleur.
    - `<input type="submit" value="Choisir">` : Bouton pour soumettre le formulaire.

![[Untitled 1 16.png|Untitled 1 16.png]]

![[Untitled 2 14.png|Untitled 2 14.png]]

# Ex2.2:

`Index.jsp`

```Java
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Exercice 2</title>
</head>
<body>

<%
// Récupération des valeurs du formulaire
String nom = request.getParameter("nom");
String[] langages = request.getParameterValues("langages");
%>

<h2>Récapitulatif des informations :</h2>
<p>Nom : <%= nom %></p>
<p>Langages de programmation connus :</p>
<ul>
    <% 
    if (langages != null) {
        for (String langage : langages) {
    %>
    <li><%= langage %></li>
    <% 
        }
    } else {
    %>
    <li>Aucun langage sélectionné</li>
    <% 
    }
    %>
</ul>

<form method="post" action="">
    <label for="nom">Nom :</label>
    <input type="text" id="nom" name="nom" required><br><br>
    <label for="langages">Langages de programmation connus :</label><br>
    <input type="checkbox" id="java" name="langages" value="Java">
    <label for="java">Java</label><br>
    <input type="checkbox" id="c" name="langages" value="C">
    <label for="c">C</label><br>
    <input type="checkbox" id="cplusplus" name="langages" value="C++">
    <label for="cplusplus">C++</label><br>
    <input type="checkbox" id="visualbasic" name="langages" value="VisualBasic">
    <label for="visualbasic">VisualBasic</label><br>
    <input type="checkbox" id="lisp" name="langages" value="Lisp">
    <label for="lisp">Lisp</label><br>
    <input type="checkbox" id="prolog" name="langages" value="Prolog">
    <label for="prolog">Prolog</label><br>
    <input type="checkbox" id="autres" name="langages" value="Autres">
    <label for="autres">Autres</label><br><br>
    <input type="submit" value="Soumettre">
</form>

</body>
</html>
```

Description du code :

1. Directives JSP :
    - `<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>` : Définit la langue du code comme Java et spécifie l'encodage des caractères pour la page HTML.
2. Structure HTML :
    - `<!DOCTYPE html>`, `<html>`, `<head>`, `<title>`, `<meta charset="UTF-8">` : Définit la structure de base de la page HTML.
3. Bloc de script JSP :
    - `<% ... %>` : Contient du code Java à exécuter côté serveur.
4. Récupération des valeurs du formulaire :
    - `String nom = request.getParameter("nom");` : Récupère la valeur saisie dans le champ "nom" du formulaire.
    - `String[] langages = request.getParameterValues("langages");` : Récupère les valeurs sélectionnées dans les cases à cocher des langages de programmation.
5. Affichage des informations saisies :
    - Affiche le nom saisi par l'utilisateur.
    - Parcourt la liste des langages de programmation sélectionnés et les affiche sous forme de liste à puces.
    - Si aucun langage n'est sélectionné, affiche "Aucun langage sélectionné".
6. Formulaire :
    - `method="post" action=""` : Utilise la méthode POST pour envoyer les données à la même page.
    - Champ de saisie pour le nom et cases à cocher pour les langages de programmation.
    - Bouton de soumission du formulaire.

![[Untitled 3 14.png|Untitled 3 14.png]]

![[Untitled 4 14.png|Untitled 4 14.png]]

# Ex3:

`index.jsp`

```Java
<%@ page import="jakarta.servlet.http.HttpServletRequest" %>
<%@ page import="java.io.*" %>
<%@ page import="java.util.*" %>
<%@ page errorPage="Error.jsp" %>
<%
// Vérification si la requête est de type POST
if (request.getMethod().equals("POST")) {
    // Récupération de la couleur sélectionnée
    String couleur = request.getParameter("couleur");
    if (couleur.equals("orange")) {
        throw new Exception("Cette couleur n'est pas belle");
    }
%>
    <html>
    <head>
        <title>Selection de couleur</title>
    </head>
    <body>
        <h2>Vous avez choisi la couleur <%= couleur %></h2>
    </body>
    </html>
<%
} else {
%>
    <html>
    <head>
        <title>Selection de couleur</title>
    </head>
    <body>
        <h2>Sélectionnez une couleur :</h2>
        <form method="post" action="">
            <select name="couleur">
                <option value="rouge">Rouge</option>
                <option value="vert">Vert</option>
                <option value="bleu">Bleu</option>
                <option value="orange">Orange</option> <!-- Ajout de l'option "Orange" -->
            </select>
            <input type="submit" value="Choisir">
        </form>
    </body>
    </html>
<%
}
%>
```

```Java
<%@ page import="java.io.*" %>
<%@ page import="java.util.*" %>
<%@ page import="java.lang.Exception" %>

<%@ page isErrorPage="true" %>
<html>
<head>
    <title>Erreur</title>
</head>
<body>
    <h2>Une erreur s'est produite :</h2>
    <p><%= exception.getMessage() %></p>
</body>
</html>
```

Description du code :

1. Importation des classes :
    - Les directives `<%@ page import="..." %>` sont utilisées pour importer les classes nécessaires.
2. Définition de la page d'erreur :
    - `<%@ page errorPage="Error.jsp" %>` : Spécifie la page JSP à afficher en cas d'erreur.
3. Bloc de script JSP :
    - `<% ... %>` : Contient du code Java à exécuter côté serveur.
4. Vérification de la méthode de requête :
    - `if (request.getMethod().equals("POST")) { ... }` : Vérifie si la méthode de requête est POST.
5. Traitement pour la méthode POST :
    - Récupération de la couleur sélectionnée à partir des paramètres de la requête POST.
    - Vérification si la couleur sélectionnée est "orange". Si c'est le cas, une exception est déclenchée avec un message d'erreur.
6. Affichage de la couleur sélectionnée :
    - Si la requête n'est pas de type POST, affiche un formulaire permettant à l'utilisateur de sélectionner une couleur parmi une liste.

![[Untitled 5 12.png|Untitled 5 12.png]]

![[Untitled 6 11.png|Untitled 6 11.png]]

# Ex4:

`Compteur.java`

```Java
public class Compteur {
    private int nombre;

    public Compteur() {
        this.nombre = 0;
    }

    public void incrementer() {
        this.nombre++;
    }

    public int getNombre() {
        return nombre;
    }

    public void setNombre(int nombre) {
        this.nombre = nombre;
    }
}
```

```Java
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="com.example.Compteur" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Compteur</title>
</head>
<body>

<%
// Counter avec portée "application"
Compteur compteurApplication = (Compteur) application.getAttribute("compteurApplication");
if (compteurApplication == null) {
    compteurApplication = new Compteur();
    application.setAttribute("compteurApplication", compteurApplication);
}

compteurApplication.incrementer();
int nombreApplication = compteurApplication.getNombre();
%>

<h2>Counter avec portée "application" : <%= nombreApplication %></h2>

<%
// Counter avec portée "session"
Compteur compteurSession = (Compteur) session.getAttribute("compteurSession");
if (compteurSession == null) {
    compteurSession = new Compteur();
    session.setAttribute("compteurSession", compteurSession);
}

compteurSession.incrementer();
int nombreSession = compteurSession.getNombre();
%>

<h2>Counter avec portée "session" : <%= nombreSession %></h2>

<%
// Counter avec portée "request"
Compteur compteurRequest = (Compteur) request.getAttribute("compteurRequest");
if (compteurRequest == null) {
    compteurRequest = new Compteur();
    request.setAttribute("compteurRequest", compteurRequest);
}

compteurRequest.incrementer();
int nombreRequest = compteurRequest.getNombre();
%>

<h2>Counter avec portée "request" : <%= nombreRequest %></h2>

</body>
</html>
```

Description du code :

1. Directive JSP :
    - `<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>` : Définit la langue du code comme Java et spécifie l'encodage des caractères pour la page HTML.
2. Importation de la classe Compteur :
    - `<%@ page import="com.example.Compteur" %>` : Importe la classe `Compteur` pour pouvoir l'utiliser dans le code.
3. Structure HTML :
    - `<!DOCTYPE html>`, `<html>`, `<head>`, `<title>`, `<meta charset="UTF-8">` : Définit la structure de base de la page HTML.
4. Bloc de script JSP :
    - `<% ... %>` : Contient du code Java à exécuter côté serveur.
5. Utilisation des compteurs :
    - `Compteur compteurApplication = (Compteur) application.getAttribute("compteurApplication");` : Récupère le compteur avec portée "application" à partir des attributs de l'application.
    - Si le compteur n'existe pas, il est créé et stocké dans les attributs de l'application.
    - Le même processus est répété pour les compteurs avec portée "session" et "request".
    - Chaque compteur est ensuite incrémenté et le nombre actuel est récupéré à des fins d'affichage.

![[Untitled 7 11.png|Untitled 7 11.png]]

# Ex5:

`PodsIdealBean.java`

```Java
public class PoidsIdealBean {
    private char sexe;
    private double taille;
    private double poidsIdeal;

    public char getSexe() {
        return sexe;
    }

    public void setSexe(char sexe) {
        this.sexe = sexe;
    }

    public double getTaille() {
        return taille;
    }

    public void setTaille(double taille) {
        this.taille = taille;
    }

    public double getPoidsIdeal() {
        if (sexe == 'F') {
            poidsIdeal = (72.7 * taille) - 58;
        } else if (sexe == 'H') {
            poidsIdeal = (62.1 * taille) - 44.7;
        }
        return poidsIdeal;
    }

    public void setPoidsIdeal(double poidsIdeal) {
        this.poidsIdeal = poidsIdeal;
    }
}
```

b) Vous pouvez mettre le code du bean dans le répertoire `WEB-INF/classes` de votre environnement de développement local.

c) Voici le code de la page JSP `poidsIdeal.jsp` :

```Java
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="com.example.PoidsIdealBean" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Calcul du poids idéal</title>
</head>
<body>

<form method="post" action="">
    <label for="sexe">Sexe (F ou H) :</label>
    <input type="text" id="sexe" name="sexe" required><br><br>
    
    <label for="taille">Taille (en mètres) :</label>
    <input type="text" id="taille" name="taille" required><br><br>
    
    <input type="submit" value="Calculer">
</form>

<%
// Création et initialisation du bean correspondant aux paramètres de la requête
if (request.getMethod().equals("POST")) {
    PoidsIdealBean poidsIdealBean = new PoidsIdealBean();
    poidsIdealBean.setSexe(request.getParameter("sexe").charAt(0));
    poidsIdealBean.setTaille(Double.parseDouble(request.getParameter("taille")));
%>

<h2>Le poids idéal est : <%= poidsIdealBean.getPoidsIdeal() %> kg</h2>

<%
}
%>
</body>
</html>
```

Description du code :

1. Directives JSP :
    - `<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>` : Définit la langue du code comme Java et spécifie l'encodage des caractères pour la page HTML.
2. Importation de la classe PoidsIdealBean :
    - `<%@ page import="com.example.PoidsIdealBean" %>` : Importe la classe PoidsIdealBean nécessaire pour effectuer le calcul du poids idéal.
3. Structure HTML :
    - `<!DOCTYPE html>`, `<html>`, `<head>`, `<title>`, `<meta charset="UTF-8">` : Définit la structure de base de la page HTML.
4. Formulaire :
    - `<form method="post" action="">` : Utilise la méthode POST pour envoyer les données à la même page.
    - Champ de saisie pour le sexe et la taille.
    - Bouton de soumission du formulaire.
5. Bloc de script JSP :
    - `<% ... %>` : Contient du code Java à exécuter côté serveur.
6. Traitement du formulaire :
    - Si la méthode de requête est POST, crée un objet PoidsIdealBean et initialise ses propriétés avec les valeurs saisies par l'utilisateur.
    - Affiche le poids idéal calculé en appelant la méthode getPoidsIdeal() de l'objet PoidsIdealBean.

![[Untitled 8 10.png|Untitled 8 10.png]]

# Ex6:

a) Dans la page `exercice4a.jsp`, la variable `nombreAleatoireClasse` est déclarée en tant que variable de classe statique (`static`), ce qui signifie qu'elle conserve sa valeur entre les requêtes et que la même valeur aléatoire sera affichée pour toutes les requêtes jusqu'à ce que le conteneur soit arrêté. Cela est dû au fait que les variables de classe statiques sont partagées entre toutes les instances de la classe et persistent pendant toute la durée de vie de l'application.

b) Dans la page `exercice4b.jsp`, la variable `nombreAleatoireClasse` est déclarée localement à l'intérieur de la page JSP, ce qui signifie qu'elle est recréée et réinitialisée à chaque requête. Par conséquent, une nouvelle valeur aléatoire sera générée à chaque fois que la page est chargée, et cette valeur sera différente à chaque requête jusqu'à ce que le conteneur soit arrêté.

c) La différence entre les pages `exercice4a.jsp` et `exercice4b.jsp` réside dans la portée de la variable `nombreAleatoireClasse`. Dans `exercice4a.jsp`, la variable est déclarée en tant que variable de classe statique, ce qui la rend partagée entre toutes les instances de la classe JSP et conserve sa valeur entre les requêtes. Dans `exercice4b.jsp`, la variable est déclarée localement à l'intérieur de la page JSP, ce qui la rend spécifique à chaque requête et génère une nouvelle valeur aléatoire à chaque chargement de la page.

# Ex7:

```SQL
-- Table des médecins
CREATE TABLE Medecins (
    IDMedecin INT PRIMARY KEY,
    Nom VARCHAR(100),
    Specialite VARCHAR(100)
);

-- Table des patients
CREATE TABLE Patients (
    IDPatient INT PRIMARY KEY,
    Nom VARCHAR(100),
    NumeroTelephone VARCHAR(20)
);

-- Table des rendez-vous
CREATE TABLE RendezVous (
    IDRendezVous INT PRIMARY KEY,
    IDPatient INT,
    IDMedecin INT,
    DateHeure DATETIME,
    FOREIGN KEY (IDPatient) REFERENCES Patients(IDPatient),
    FOREIGN KEY (IDMedecin) REFERENCES Medecins(IDMedecin)
);
```

# Ex8:

`index.jsp`

```SQL
<%@ page import="java.sql.*" %>
<%@ page import="bd.inc.jsp" %>
<%@ page language="java" %>
<%@ page contentType="text/html; charset=UTF-8" %>
<html>
<head>
    <title>Liste des rendez-vous</title>
</head>
<body>
    <h1>Liste des rendez-vous par médecin</h1>
    <table border="1">
        <thead>
            <tr>
                <th>Médecin</th>
                <th>Patient</th>
                <th>Date de rendez-vous</th>
            </tr>
        </thead>
        <tbody>
            <% 
            String url = "jdbc:mysql://localhost:3306/test";
            String username = "root";
            String password = "root";
            try {
                bd.inc.jsp.setDriver("com.mysql.jdbc.Driver");
                Connection conn = bd.inc.jsp.getConnection(url, username, password);
                String sql = "SELECT m.Nom AS Medecin, p.Nom AS Patient, r.DateHeure AS DateRendezVous " +
                             "FROM Medecins m " +
                             "INNER JOIN RendezVous r ON m.IDMedecin = r.IDMedecin " +
                             "INNER JOIN Patients p ON r.IDPatient = p.IDPatient " +
                             "ORDER BY m.Nom";
                Statement stmt = conn.createStatement();
                ResultSet rs = stmt.executeQuery(sql);
                while (rs.next()) {
                    String medecin = rs.getString("Medecin");
                    String patient = rs.getString("Patient");
                    Timestamp dateRdv = rs.getTimestamp("DateRendezVous");
                    %>
                    <tr>
                        <td><%= medecin %></td>
                        <td><%= patient %></td>
                        <td><%= dateRdv %></td>
                    </tr>
                    <%
                }
                rs.close();
                stmt.close();
                conn.close();
            } catch (Exception e) {
                out.println("Error: " + e.getMessage());
            }
            %>
        </tbody>
    </table>
</body>
</html>
```

1. Directives JSP :
    - `<%@ page import="java.sql.*" %>` : Importe les classes nécessaires pour travailler avec JDBC.
    - `<%@ page import="bd.inc.jsp" %>` : Importe la classe `bd.inc.jsp` (probablement un fichier de configuration JDBC).
    - `<%@ page language="java" %>` : Spécifie que le code Java sera utilisé dans cette page JSP.
    - `<%@ page contentType="text/html; charset=UTF-8" %>` : Définit le type de contenu de la page comme HTML avec l'encodage UTF-8.
2. Balises HTML :
    - `<html>`, `<head>`, `<title>` : Balises HTML pour la structure de base de la page.
    - `<body>` : Début du corps de la page HTML.
3. Titre et en-tête de la page :
    - `<h1>Liste des rendez-vous par médecin</h1>` : Titre de la page.
4. Récupération et affichage des données de la base de données :
    - Les informations de connexion à la base de données (URL, nom d'utilisateur et mot de passe) sont définies.
    - Une connexion à la base de données est établie en utilisant les informations de connexion.
    - Une requête SQL est exécutée pour récupérer les rendez-vous de la base de données.
    - Les résultats de la requête sont parcourus à l'aide d'une boucle while.
    - Pour chaque rendez-vous, les données du médecin, du patient et la date du rendez-vous sont extraites et affichées dans une ligne du tableau HTML.
5. Gestion des erreurs :
    - Une gestion basique des erreurs est effectuée avec un bloc try-catch. En cas d'erreur lors de l'exécution de la requête SQL ou lors de la récupération des données, un message d'erreur est affiché à l'utilisateur.
6. Fermeture des ressources :
    - Les ressources JDBC (ResultSet, Statement et Connection) sont correctement fermées dans des blocs finally pour libérer les ressources et éviter les fuites de mémoire.

![[Untitled 9 7.png|Untitled 9 7.png]]

# Ex9:

![[Untitled 10 6.png|Untitled 10 6.png]]

a) Lorsque nous appelons la page tout de suite après le démarrage du conteneur JSP à 10h00, voici les valeurs affichées :

- `Time1` affiche l'heure actuelle (10h00) et les minutes actuelles (00).
- `Time2`, `Time3`, et `Time4` affichent également l'heure actuelle (10h00) et les minutes actuelles (00), car les instances de `TimeBean` ont été créées à ce moment-là et sont associées aux différentes portées (`request`, `session`, `application`) mais partagent les mêmes valeurs car elles ont été créées simultanément.

b) Lorsque nous rafraîchissons la page 5 minutes après le démarrage du conteneur JSP dans le même navigateur, les valeurs affichées seront mises à jour pour toutes les instances de `TimeBean` :

- `Time1` affiche toujours l'heure actuelle (10h05) et les minutes actuelles (05).
- `Time2`, `Time3`, et `Time4` affichent également l'heure actuelle (10h05) et les minutes actuelles (05), car toutes les instances ont été mises à jour lors du rafraîchissement de la page.

c) Lorsque nous appelons la page 15 minutes après le démarrage du conteneur JSP dans un autre navigateur, les valeurs affichées dépendront de la portée des instances de `TimeBean` :

- `Time1` affiche l'heure actuelle (10h15) et les minutes actuelles (15), car la portée `page` est spécifique à cette instance de la page et n'est pas partagée entre les navigateurs.
- `Time2` affiche également l'heure actuelle (10h15) et les minutes actuelles (15), car la portée `request` est spécifique à chaque requête et n'est pas partagée entre les navigateurs.
- `Time3` et `Time4` affichent l'heure actuelle (10h05) et les minutes actuelles (05), car elles ont été créées au moment du premier appel à la page dans le premier navigateur et partagent la même portée (`session` et `application`).