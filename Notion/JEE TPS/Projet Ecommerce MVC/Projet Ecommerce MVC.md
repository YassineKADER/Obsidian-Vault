# **Table des matières**

Table des matières

Reultat De ProJet

Structure de la base de données

Structure et code de projet

Models-JPA

Client

Product

Command

ClientDAO

ProductDAO

CommandDAO

Controllers-SERVLETS

Login

SignUp

Action

Cart

CommandServlet

Logout

Product

SaveProduct

UpdateProduct

Views-JSP/JSTL

Login

AddProduct

Cart

Commands

Product

Signup

Updateproduct

Les Fichiers De Configurations

Persistance.xml

Conclusion

# Reultat De ProJet

**Page d'inscription:**

![[Untitled 41.png|Untitled 41.png]]

Lorsque l'utilisateur est déjà créé dans la base de données, ce message apparaît à l'utilisateur

![[Untitled 1 20.png|Untitled 1 20.png]]

Si l'utilisateur se connecte en tant qu'administrateur, il peut simplement utiliser le site web comme un utilisateur normal

![[Untitled 2 18.png|Untitled 2 18.png]]

En tant que client, vous voyez ceci : vous pouvez simplement ajouter des produits à votre panier. Vous pouvez également les supprimer du panier ou les ajouter comme indiqué dans les images suivantes

![[Untitled 3 18.png|Untitled 3 18.png]]

![[Untitled 4 17.png|Untitled 4 17.png]]

Si vous êtes satisfait des produits dans votre panier, vous devriez passer commande pour ces produits.

![[Untitled 5 15.png|Untitled 5 15.png]]

Each user he can see ther commands and pervious commands also

![[Untitled 6 14.png|Untitled 6 14.png]]

Chaque utilisateur peut voir ses commandes en cours ainsi que ses commandes précédentes

![[Untitled 7 13.png|Untitled 7 13.png]]

L'administrateur peut également ajouter des produits et les supprimer comme le montrent les images suivantes

![[Untitled 8 11.png|Untitled 8 11.png]]

![[Untitled 9 8.png|Untitled 9 8.png]]

![[Untitled 10 7.png|Untitled 10 7.png]]

# Structure de la base de données

La structure de la base de données comprend les tables suivantes :

1. Table "clients" :
    
    - Champ "id" : de type entier (int), clé primaire (PRI), auto-incrémenté (auto_increment).
    - Champ "is_admin" : de type booléen (tinyint(1)), pouvant être NULL.
    - Champ "name" : de type chaîne de caractères (varchar(255)), pouvant être NULL.
    - Champ "password" : de type chaîne de caractères (varchar(255)), pouvant être NULL.
    
    ![[Untitled 11 5.png|Untitled 11 5.png]]
    
2. Table "products" :
    
    - Champ "id" : de type grand entier (bigint), clé primaire (PRI), auto-incrémenté (auto_increment).
    - Champ "name" : de type chaîne de caractères (varchar(255)), pouvant être NULL.
    - Champ "price" : de type nombre à virgule flottante (double), pouvant être NULL.
    
    ![[Untitled 12 4.png|Untitled 12 4.png]]
    
3. Table "orders" :
    
    - Champ "id" : de type grand entier (bigint), clé primaire (PRI), auto-incrémenté (auto_increment).
    - Champ "client_id" : de type entier (int), clé étrangère (MUL), ne peut pas être NULL.
    - Champ "total_price" : de type nombre à virgule flottante (double), ne peut pas être NULL.
    - Champ "product_ids" : de type texte (text), pouvant être NULL.
    
    ![[Untitled 13 3.png|Untitled 13 3.png]]
    

Ces tables définissent la structure de base de données pour stocker des informations sur les clients, les produits et les commandes.

# Structure et code de projet

L'architecture MVC (Modèle-Vue-Contrôleur) est un modèle de conception largement utilisé dans le développement web pour séparer la logique métier, la présentation et le contrôle des données. Dans ce modèle, les fichiers JSP (JavaServer Pages) agissent en tant que vues pour générer l'interface utilisateur, utilisant la bibliothèque JSTL (JavaServer Pages Standard Tag Library) pour simplifier les opérations logiques et d'affichage. JPA (Java Persistence API) est utilisé pour la persistance des données en fournissant une interface de haut niveau pour interagir avec la base de données de manière objet-relationnel. Cette approche favorise la modularité, la réutilisabilité du code et la séparation des préoccupations, améliorant ainsi la maintenabilité et la scalabilité des applications web.

La structure du projet suit une architecture MVC (Modèle-Vue-Contrôleur) classique pour organiser les différentes parties de l'application.

1. **Contrôleurs (Controllers)** :
    - `Action.java`, `Cart.java`, `CommandServlet.java`, `Login.java`, `Logout.java`, `Products.java`, `SaveProduct.java`, `Signup.java`, `UpdateProduct.java`: Ces classes Java agissent en tant que contrôleurs et gèrent les requêtes et les réponses HTTP. Chaque contrôleur est responsable d'une fonctionnalité spécifique de l'application.
2. **Modèles (Models)** :
    - `Client.java`, `ClientDAO.java`, `Command.java`, `CommandDAO.java`, `Main.java`, `Product.java`, `ProductDAO.java`: Ces classes Java représentent les entités métier de l'application et sont utilisées pour interagir avec la base de données. Les DAO (Data Access Objects) sont responsables de la persistance des données.
3. **Vues (Views)** :
    - `Addproduct.jsp`, `Cart.jsp`, `Commands.jsp`, `Login.jsp`, `Products.jsp`, `Signup.jsp`, `Updateproduct.jsp`: Ce sont des fichiers JSP (JavaServer Pages) qui contiennent le code HTML et les balises JSTL (JavaServer Pages Standard Tag Library) pour générer la présentation de l'interface utilisateur. Chaque vue correspond à une page ou une fonctionnalité de l'application.
4. **Ressources (Resources)** :
    - `context.xml`, `persistence.xml`, `web.xml`: Ces fichiers de configuration définissent les paramètres de contexte, la configuration de persistance pour l'ORM (Object-Relational Mapping) avec JPA (Java Persistence API) et la configuration du déploiement web de l'application.
5. **Autres fichiers** :
    - `pom.xml`: Ce fichier contient la configuration du projet Maven, y compris les dépendances et les plugins.
    - `index.jsp`: Page d'accueil de l'application.
    - `microprojet.war`: Fichier d'archive contenant l'application web prête à être déployée sur un serveur compatible.

Dans cette structure, le flux de contrôle est géré par les contrôleurs qui reçoivent les requêtes HTTP, interagissent avec les modèles pour accéder aux données, puis renvoient les résultats aux vues pour l'affichage.

**Structure de projet:**

```Plain
|
├── pom.xml
├── src
│   └── main
│       ├── java
│       │   ├── controllers
│       │   │   ├── Action.java
│       │   │   ├── Cart.java
│       │   │   ├── CommandServlet.java
│       │   │   ├── Login.java
│       │   │   ├── Lougout.java
│       │   │   ├── Products.java
│       │   │   ├── SaveProduct.java
│       │   │   ├── Signup.java
│       │   │   └── UpdateProduct.java
│       │   └── models
│       │       ├── Client.java
│       │       ├── ClientDAO.java
│       │       ├── Command.java
│       │       ├── CommandDAO.java
│       │       ├── Main.java
│       │       ├── Product.java
│       │       └── ProductDAO.java
│       ├── resources
│       │   └── META-INF
│       │       ├── context.xml
│       │       └── persistence.xml
│       └── webapp
│           ├── WEB-INF
│           │   ├── views
│           │   │   ├── Addproduct.jsp
│           │   │   ├── Cart.jsp
│           │   │   ├── Commands.jsp
│           │   │   ├── Login.jsp
│           │   │   ├── Products.jsp
│           │   │   ├── Signup.jsp
│           │   │   └── Updateproduct.jsp
│           │   └── web.xml
│           └── index.jsp
└── target
    ├── classes
    │   ├── META-INF
    │   │   ├── context.xml
    │   │   └── persistence.xml
    │   ├── controllers
    │   │   ├── Action.class
    │   │   ├── Cart.class
    │   │   ├── CommandServlet.class
    │   │   ├── Login.class
    │   │   ├── Lougout.class
    │   │   ├── Products.class
    │   │   ├── SaveProduct.class
    │   │   ├── Signup.class
    │   │   └── UpdateProduct.class
    │   └── models
    │       ├── Client.class
    │       ├── ClientDAO.class
    │       ├── Command.class
    │       ├── CommandDAO.class
    │       ├── Main.class
    │       ├── Product.class
    │       └── ProductDAO.class
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
    ├── microprojet
    │   ├── META-INF
    │   ├── WEB-INF
    │   │   ├── classes
    │   │   │   ├── META-INF
    │   │   │   │   ├── context.xml
    │   │   │   │   └── persistence.xml
    │   │   │   ├── controllers
    │   │   │   │   ├── Action.class
    │   │   │   │   ├── Cart.class
    │   │   │   │   ├── CommandServlet.class
    │   │   │   │   ├── Login.class
    │   │   │   │   ├── Lougout.class
    │   │   │   │   ├── Products.class
    │   │   │   │   ├── SaveProduct.class
    │   │   │   │   ├── Signup.class
    │   │   │   │   └── UpdateProduct.class
    │   │   │   └── models
    │   │   │       ├── Client.class
    │   │   │       ├── ClientDAO.class
    │   │   │       ├── Command.class
    │   │   │       ├── CommandDAO.class
    │   │   │       ├── Main.class
    │   │   │       ├── Product.class
    │   │   │       └── ProductDAO.class
    │   │   ├── lib
    │   │   │   ├── angus-activation-2.0.0.jar
    │   │   │   ├── antlr4-runtime-4.13.0.jar
    │   │   │   ├── byte-buddy-1.14.11.jar
    │   │   │   ├── classmate-1.5.1.jar
    │   │   │   ├── glassfish-jstl-11.0.20.jar
    │   │   │   ├── hibernate-commons-annotations-6.0.6.Final.jar
    │   │   │   ├── hibernate-core-6.4.4.Final.jar
    │   │   │   ├── istack-commons-runtime-4.1.1.jar
    │   │   │   ├── jakarta.activation-api-2.1.0.jar
    │   │   │   ├── jakarta.el-api-5.0.1.jar
    │   │   │   ├── jakarta.inject-api-2.0.1.jar
    │   │   │   ├── jakarta.persistence-api-3.2.0-M2.jar
    │   │   │   ├── jakarta.servlet.jsp.jstl-3.0.0.jar
    │   │   │   ├── jakarta.servlet.jsp.jstl-api-3.0.0.jar
    │   │   │   ├── jakarta.transaction-api-2.0.1.jar
    │   │   │   ├── jakarta.xml.bind-api-4.0.0.jar
    │   │   │   ├── jandex-3.1.2.jar
    │   │   │   ├── jaxb-core-4.0.2.jar
    │   │   │   ├── jaxb-runtime-4.0.2.jar
    │   │   │   ├── jboss-logging-3.5.0.Final.jar
    │   │   │   ├── mysql-connector-j-8.3.0.jar
    │   │   │   ├── protobuf-java-3.25.1.jar
    │   │   │   └── txw2-4.0.2.jar
    │   │   ├── views
    │   │   │   ├── Addproduct.jsp
    │   │   │   ├── Cart.jsp
    │   │   │   ├── Commands.jsp
    │   │   │   ├── Login.jsp
    │   │   │   ├── Products.jsp
    │   │   │   ├── Signup.jsp
    │   │   │   └── Updateproduct.jsp
    │   │   └── web.xml
    │   └── index.jsp
    └── microprojet.war
```

## Models-JPA

### Client

Ce code représente une classe Java nommée Client qui est annotée avec des annotations JPA pour la persistance des données dans une base de données relationnelle. Voici une explication des principaux éléments de cette classe :

- `@Entity` : Cette annotation indique que la classe Client est une entité persistante, ce qui signifie qu'elle est associée à une table dans la base de données.
- `@Table(name = "clients")` : Spécifie le nom de la table dans la base de données avec laquelle cette entité est associée.
- `@Id` : Indique que le champ `id` est la clé primaire de l'entité.
- `@GeneratedValue(strategy = GenerationType.IDENTITY)` : Spécifie que la génération de la valeur de la clé primaire se fait de manière automatique à l'aide de la stratégie d'identité de la base de données.
- `@Column(name = "name")`, `@Column(name = "is_admin")`, `@Column(name = "password")` : Ces annotations définissent les colonnes correspondantes dans la table de la base de données et spécifient les noms des colonnes.

La classe Client contient également des méthodes pour accéder et modifier les attributs de l'entité, ainsi qu'une méthode `toString()` pour obtenir une représentation textuelle de l'objet Client.

```Java
package models;

import jakarta.persistence.*; 

@Entity
@Table(name = "clients")
public class Client {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "name")
    private String name;

    @Column(name = "is_admin")
    private boolean isAdmin;

    @Column(name = "password")
    private String password;

    public Client(String name, boolean isAdmin, String password) {
        this.name = name;
        this.isAdmin = isAdmin;
        this.password = password;
    }

    public Client() {
    }

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public boolean isAdmin() {
        return isAdmin;
    }

    public void setAdmin(boolean admin) {
        isAdmin = admin;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    public String getPassword() {
        return password;
    }

    @Override
    public String toString() {
        return "Client [id=" + id + ", name=" + name + ", isAdmin=" + isAdmin + ", password=" + password + "]";
    }
}
```

### Product

Ce code représente une classe Java nommée Product, qui est également annotée avec des annotations JPA pour la persistance des données dans une base de données relationnelle. Voici une explication des principaux éléments de cette classe :

- `@Entity` : Cette annotation indique que la classe Product est une entité persistante, ce qui signifie qu'elle est associée à une table dans la base de données.
- `@Table(name = "products")` : Spécifie le nom de la table dans la base de données avec laquelle cette entité est associée.
- `@Id` : Indique que le champ `id` est la clé primaire de l'entité.
- `@GeneratedValue(strategy = GenerationType.IDENTITY)` : Spécifie que la génération de la valeur de la clé primaire se fait de manière automatique à l'aide de la stratégie d'identité de la base de données.
- `@Column(name = "name")`, `@Column(name = "price")` : Ces annotations définissent les colonnes correspondantes dans la table de la base de données et spécifient les noms des colonnes.

La classe Product contient également des méthodes pour accéder et modifier les attributs de l'entité, ainsi qu'une méthode `toString()` pour obtenir une représentation textuelle de l'objet Product.

```Java
package models; 
import jakarta.persistence.*;
@Entity
@Table(name = "products")
public class Product {
    @Override
    public String toString() {
        return "Product [id=" + id + ", name=" + name + ", price=" + price + "]";
    }

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public Product() {
    }

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "name")
    private String name;

    @Column(name = "price")
    private double price;

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }
}
```

### Command

Ce code représente une classe Java nommée Command, utilisée pour représenter une commande dans un système de gestion de commandes. Voici une explication des principaux éléments de cette classe :

- `@Entity` : Cette annotation indique que la classe Command est une entité persistante, ce qui signifie qu'elle est associée à une table dans la base de données.
- `@Table(name = "commande")` : Spécifie le nom de la table dans la base de données avec laquelle cette entité est associée.
- `@Id` : Indique que le champ `id` est la clé primaire de l'entité.
- `@GeneratedValue(strategy = GenerationType.IDENTITY)` : Spécifie que la génération de la valeur de la clé primaire se fait de manière automatique à l'aide de la stratégie d'identité de la base de données.
- `@ManyToOne` et `@JoinColumn(name = "client_id")` : Ces annotations définissent la relation Many-to-One entre la commande et le client, avec la colonne `client_id` dans la table des commandes.
- `@Column(name = "total_price")` : Cette annotation spécifie la colonne correspondant au prix total de la commande dans la table.
- `@Column(name = "product_ids")` : Cette annotation spécifie la colonne contenant les identifiants des produits associés à la commande.
- `@Transient` : Cette annotation indique que le champ `productsNames` ne sera pas persisté dans la base de données.

La classe Command contient également des méthodes pour accéder et modifier les attributs de l'entité, ainsi qu'une méthode `toString()` pour obtenir une représentation textuelle de l'objet Command.

```Java
package models;
import jakarta.persistence.*;
@Entity
@Table(name = "commande")
public class Command {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    @ManyToOne
    @JoinColumn(name = "client_id")
    private Client client;
    @Column(name = "total_price")
    private double totalPrice;
    @Column(name = "product_ids") 
    private String productIds; 

    @Transient
    private String productsNames;
    public Command() {
    }

    public Command(Client client, double totalPrice, String productIds) {
        this.client = client;
        this.totalPrice = totalPrice;
        this.productIds = productIds;
    }

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public Client getClient() {
        return client;
    }

    public void setClient(Client client) {
        this.client = client;
    }

    public double getTotalPrice() {
        return totalPrice;
    }

    public void setTotalPrice(double totalPrice) {
        this.totalPrice = totalPrice;
    }

    public String getProductIds() {
        return productIds;
    }

    public void setProductIds(String productIds) {
        this.productIds = productIds;
    }

    public void addProductId(Long productId) {
        if (productIds == null) {
            productIds = productId.toString();
        } else {
            productIds += productId+",";
        }
    }

    public void removeProductId(Long productId) {
        if (productIds != null) {
            productIds = productIds.replace(productId+",", "");
            return;
        }
    }
    @Override
    public String toString() {
        return "Order{" +
                "id=" + id +
                ", client=" + client +
                ", totalPrice=" + totalPrice +
                ", productIds='" + productIds + '\'' +"productsNames='"+productsNames+"'"+
                '}';
    }

    public String getProductsNames() {
        return productsNames;
    }

    public void setProductsNames(String productsNames) {
        this.productsNames = productsNames;
    }    
}
```

### ClientDAO

Ce code représente une classe Java nommée ClientDAO, utilisée pour interagir avec la base de données pour la gestion des clients. Voici une explication des principales méthodes de cette classe :

- `saveClient(Client client)` : Cette méthode permet de sauvegarder un client dans la base de données en utilisant l'EntityManager pour persister l'objet Client.
- `updateClient(Client client)` : Cette méthode permet de mettre à jour les informations d'un client existant dans la base de données.
- `getClientById(int id)` : Cette méthode récupère un client à partir de son identifiant dans la base de données.
- `getAllClients()` : Cette méthode récupère tous les clients enregistrés dans la base de données.
- `deleteClient(Long id)` : Cette méthode supprime un client de la base de données en fonction de son identifiant.
- `closeEntityManager()` : Cette méthode permet de fermer l'EntityManager après avoir terminé les opérations sur la base de données.
- `isValidClient(String name, String password)` : Cette méthode vérifie si un client avec le nom d'utilisateur et le mot de passe fournis existent dans la base de données. Elle retourne le client s'il est valide, sinon elle retourne null.

La classe ClientDAO utilise l'EntityManager pour interagir avec la base de données en utilisant des requêtes JPQL (Java Persistence Query Language) pour effectuer des opérations de lecture, écriture et suppression sur l'entité Client.

```Java
package models;

import jakarta.persistence.EntityManager;
import jakarta.persistence.EntityManagerFactory;
import jakarta.persistence.Persistence;
import java.util.List;

public class ClientDAO {
    private EntityManager entityManager;

    public ClientDAO() {
        EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myPersistenceUnit");
        entityManager = entityManagerFactory.createEntityManager();
    }

    public void saveClient(Client client) {
        entityManager.persist(client);
    }

    public void updateClient(Client client) {
        entityManager.getTransaction().begin();
        entityManager.merge(client);
        entityManager.getTransaction().commit();
    }

    public Client getClientById(int id) {
        return entityManager.find(Client.class, id);
    }

    public List<Client> getAllClients() {
        return entityManager.createQuery("SELECT c FROM Client c", Client.class).getResultList();
    }

    public void deleteClient(Long id) {
        Client client = entityManager.find(Client.class, id);
        if (client != null) {
            entityManager.getTransaction().begin();
            entityManager.remove(client);
            entityManager.getTransaction().commit();
        }
    }

    public void closeEntityManager() {
        entityManager.close();
    }

    public Client isValidClient(String name, String password) {
        List<Client> clients = entityManager
                .createQuery("SELECT c FROM Client c WHERE c.name = :name AND c.password = :password", Client.class)
                .setParameter("name", name)
                .setParameter("password", password)
                .getResultList();
        return clients.size() == 1 ? clients.get(0) : null;
    }
}
```

### ProductDAO

Ce code représente une classe Java nommée ProductDAO, utilisée pour interagir avec la base de données pour la gestion des produits. Voici une explication des principales méthodes de cette classe :

- `saveProduct(Product product)` : Cette méthode permet de sauvegarder un produit dans la base de données en utilisant l'EntityManager pour persister l'objet Product.
- `updateProduct(Product product)` : Cette méthode permet de mettre à jour les informations d'un produit existant dans la base de données.
- `getProductById(int id)` : Cette méthode récupère un produit à partir de son identifiant dans la base de données.
- `getAllProducts()` : Cette méthode récupère tous les produits enregistrés dans la base de données.
- `deleteProduct(Long id)` : Cette méthode supprime un produit de la base de données en fonction de son identifiant.
- `closeEntityManager()` : Cette méthode permet de fermer l'EntityManager après avoir terminé les opérations sur la base de données.

La classe ProductDAO utilise l'EntityManager pour interagir avec la base de données en utilisant des requêtes JPQL (Java Persistence Query Language) pour effectuer des opérations de lecture, écriture et suppression sur l'entité Product.

```Java
package models;

import java.util.List;

import jakarta.persistence.EntityManager;
import jakarta.persistence.EntityManagerFactory;
import jakarta.persistence.Persistence;

public class ProductDAO {
    private EntityManager entityManager;

    public ProductDAO() {
        EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("myPersistenceUnit");
        entityManager = entityManagerFactory.createEntityManager();
    }

    public void saveProduct(Product product) {
        entityManager.getTransaction().begin();
        entityManager.persist(product);
        entityManager.getTransaction().commit();
    }

    public void updateProduct(Product product) {
        entityManager.getTransaction().begin();
        entityManager.merge(product);
        entityManager.getTransaction().commit();
    }

    public Product getProductById(int id) {
        return entityManager.find(Product.class, id);
    }

    public List<Product> getAllProducts() {
        return entityManager.createQuery("SELECT p FROM Product p", Product.class).getResultList();
    }

    public void deleteProduct(Long id) {
        Product product = entityManager.find(Product.class, id);
        if (product != null) {
            entityManager.getTransaction().begin();
            entityManager.remove(product);
            entityManager.getTransaction().commit();
        }
    }

    public void closeEntityManager() {
        entityManager.close();
    } 
}
```

### CommandDAO

Ce code représente une classe Java nommée CommandDAO, utilisée pour interagir avec la base de données pour la gestion des commandes. Voici une explication des principales méthodes de cette classe :

- `saveCommand(Command command)` : Cette méthode permet de sauvegarder une commande dans la base de données en utilisant l'EntityManager pour persister l'objet Command.
- `updateCommand(Command command)` : Cette méthode permet de mettre à jour les informations d'une commande existante dans la base de données.
- `deleteCommand(Command command)` : Cette méthode permet de supprimer une commande de la base de données en fonction de l'objet Command fourni.
- `getAllCommands()` : Cette méthode récupère toutes les commandes enregistrées dans la base de données. Elle utilise également la méthode `getAllProducts` pour récupérer les produits associés à chaque commande.
- `getAllProducts(Command command)` : Cette méthode récupère tous les produits associés à une commande spécifique en fonction des identifiants de produits stockés dans la commande.
- `getAllCommandsForClient(Client client)` : Cette méthode récupère toutes les commandes d'un client spécifique en fonction de l'objet Client fourni. Elle utilise également la méthode `getAllProducts` pour récupérer les produits associés à chaque commande.
- `closeEntityManager()` : Cette méthode permet de fermer l'EntityManager après avoir terminé les opérations sur la base de données.

La classe CommandDAO utilise l'EntityManager pour interagir avec la base de données en utilisant des requêtes JPQL (Java Persistence Query Language) pour effectuer des opérations de lecture, écriture et suppression sur l'entité Command. Elle utilise également la classe ProductDAO pour récupérer les produits associés aux commandes.

```Java
package models;

import java.util.List;

import java.util.ArrayList;
import jakarta.persistence.EntityManager;
import jakarta.persistence.EntityManagerFactory;
import jakarta.persistence.Persistence;
import jakarta.persistence.criteria.CriteriaBuilder.In;

public class CommandDAO {
   EntityManager em;
   
   public CommandDAO(){
    EntityManagerFactory emf = Persistence.createEntityManagerFactory("myPersistenceUnit");
    em = emf.createEntityManager();
   }

   public void saveCommand(Command command){
    em.getTransaction().begin();
    em.persist(command);
    em.getTransaction().commit();
   }

   public void updateCommand(Command command){
    em.getTransaction().begin();
    em.merge(command);
    em.getTransaction().commit();
   }

   public void deleteCommand(Command command){
    em.getTransaction().begin();
    em.remove(command);
    em.getTransaction().commit();
   }

   public List<Command> getAllCommands(){
        List<Command> commands =  em.createQuery("SELECT c FROM Command c", Command.class)
                .getResultList();
        for (Command i : commands) {
            String products = "";
            List<Product> test = getAllProducts(i);
            for(Product j : test){
                products += j.getName() + ",";
            }
            i.setProductsNames(products.substring(0, products.length() - 2));
        }
        return commands;
   }

   public List<Product> getAllProducts(Command command){
    List<Product> products = new ArrayList<Product>();
    ProductDAO productDAO = new ProductDAO();
    for(String i : command.getProductIds().split(",")){
        int id  = Integer.parseInt(i);
        products.add(productDAO.getProductById(id));
    }
    return products;
   }
   public List<Command> getAllCommandsForClient(Client client) {
        List<Command> commands =  em.createQuery("SELECT c FROM Command c WHERE c.client = :client", Command.class)
                .setParameter("client", client)
                .getResultList();
        for (Command i : commands) {
            String products = "";
            List<Product> test = getAllProducts(i);
            for(Product j : test){
                products += j.getName() + ",";
            }
            i.setProductsNames(products.substring(0, products.length() - 2));
        }
        return commands;
    }

   public void closeEntityManager(){
    em.close();
   }
}
```

## Controllers-SERVLETS

### Login

Ce code représente un servlet Java nommé Login qui gère le processus de connexion des utilisateurs à votre application. Voici une explication des principales fonctionnalités de ce servlet :

- La méthode `doGet` est appelée lorsque le client envoie une requête GET au servlet, généralement lorsqu'il accède à la page de connexion. Elle initialise un attribut "errorMessage" vide pour afficher les messages d'erreur et redirige vers la page de connexion (Login.jsp).
- La méthode `doPost` est appelée lorsque le client soumet le formulaire de connexion avec la méthode POST. Elle récupère les paramètres "name" et "password" du formulaire, puis utilise la classe ClientDAO pour vérifier si les informations d'identification fournies sont valides.
- Si les informations d'identification sont valides (client différent de null), le client est ajouté à la session et une redirection est effectuée vers la page des produits ("/microprojet/products").
- Si les informations d'identification ne sont pas valides, un message d'erreur est défini dans l'attribut "errorMessage" et le client est redirigé vers la page de connexion pour réessayer.

Ce servlet utilise les annotations `@WebServlet` pour définir son nom et le chemin d'accès URL ("/login"). Il utilise également les classes HttpServletRequest et HttpServletResponse pour gérer les requêtes et les réponses HTTP, ainsi que la classe ClientDAO pour interagir avec la base de données et vérifier les informations d'identification de l'utilisateur.

```Java
package controllers;

import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletResponse;
import models.Client;
import models.ClientDAO;

import java.io.IOException;
import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServletRequest;

@WebServlet(name = "Login", urlPatterns = "/login")
public class Login extends HttpServlet{
    public void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException {
        request.setAttribute("errorMessage", "");
        request.getRequestDispatcher("WEB-INF/views/Login.jsp").forward(request, response);
    }
    public void doPost(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException {
        String name = request.getParameter("name");
        String password = request.getParameter("password");
        ClientDAO cdao = new ClientDAO();
        Client client = cdao.isValidClient(name, password);
        if (client != null){
            request.getSession().setAttribute("client", client);
            request.setAttribute("admin", client.isAdmin());
            response.sendRedirect("/microprojet/products");
        } else {
            request.setAttribute("errorMessage", "Invalid name or password");
            request.getRequestDispatcher("WEB-INF/views/Login.jsp").forward(request, response);
        }
    } 
}
```

### SignUp

Ce code représente un servlet Java nommé Signup, qui gère le processus d'inscription des utilisateurs à votre application. Voici une explication des principales fonctionnalités de ce servlet :

- La méthode `doGet` est appelée lorsque le client envoie une requête GET au servlet, généralement lorsqu'il accède à la page d'inscription. Elle initialise un attribut "errorMessage" vide pour afficher les messages d'erreur et redirige vers la page d'inscription (Signup.jsp).
- La méthode `doPost` est appelée lorsque le client soumet le formulaire d'inscription avec la méthode POST. Elle récupère les paramètres "name" et "password" du formulaire, puis utilise la classe ClientDAO pour vérifier si un utilisateur avec le même nom existe déjà dans la base de données.
- Si aucun utilisateur avec le même nom n'existe (client est null), un nouveau client est créé avec les informations d'inscription fournies. Ce client est ensuite enregistré dans la base de données à l'aide de ClientDAO. Ensuite, le client est ajouté à la session, l'attribut "admin" est défini, et une redirection est effectuée vers la page des produits ("/microprojet/products").
- Si un utilisateur avec le même nom existe déjà, un message d'erreur est défini dans l'attribut "errorMessage" et le client est redirigé vers la page d'inscription pour réessayer.

Ce servlet utilise les annotations `@WebServlet` pour définir son nom et le chemin d'accès URL ("/signup"). Il utilise également les classes HttpServletRequest et HttpServletResponse pour gérer les requêtes et les réponses HTTP, ainsi que la classe ClientDAO pour interagir avec la base de données et vérifier l'existence des utilisateurs.

```Java
package controllers;

import java.io.IOException;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import models.Client;
import models.ClientDAO;

@WebServlet(name = "Signup", urlPatterns = "/signup")
public class Signup extends HttpServlet{
    public void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException {
        request.setAttribute("errorMessage", "");
        request.getRequestDispatcher("WEB-INF/views/Signup.jsp").forward(request, response);
    }
    
    public void doPost(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException {
        String name = request.getParameter("name");
        String password = request.getParameter("password");
        ClientDAO cdao = new ClientDAO();
        Client client = cdao.isValidClient(name, password);
        if (client == null){
            client = new Client();
            client.setName(name);
            client.setPassword(password);
            cdao.saveClient(client);
            Client sessionclient = cdao.isValidClient(name, password);
            request.getSession().setAttribute("client", sessionclient);
            request.setAttribute("admin", client.isAdmin());
            response.sendRedirect("/microprojet/products");
        } else {
            request.setAttribute("errorMessage", "User already exists");
            request.getRequestDispatcher("WEB-INF/views/Signup.jsp").forward(request, response);
        }
    } 
}
```

### Action

Ce code représente un servlet Java nommé Action qui gère différentes actions liées aux produits dans votre application. Voici un résumé des fonctionnalités de ce servlet :

- La méthode `init` est utilisée pour initialiser le servlet et créer une instance de ProductDAO pour interagir avec la base de données.
- La méthode `doPost` est appelée lorsqu'une requête POST est envoyée au servlet. Elle vérifie le paramètre "action" pour déterminer quelle action doit être effectuée. Les actions possibles sont : "addtocart", "saveproduct", "removeproduct" et "updateproduct".
    - Si l'action est "addtocart", le produit est ajouté au panier de l'utilisateur. Les produits ajoutés sont stockés dans une liste dans la session de l'utilisateur.
    - Si l'action est "saveproduct", un nouveau produit est créé avec les informations fournies dans les paramètres de la requête. Ce produit est ensuite enregistré dans la base de données à l'aide de ProductDAO.
    - Si l'action est "removeproduct", le produit spécifié est supprimé de la base de données à l'aide de ProductDAO.
    - Si l'action est "updateproduct", les informations du produit spécifié sont récupérées de la base de données à l'aide de ProductDAO. Ces informations sont ensuite transmises à la page de mise à jour des produits (Updateproduct.jsp) pour permettre à l'utilisateur de les modifier.

Ce servlet utilise les annotations `@WebServlet` pour définir son nom et le chemin d'accès URL ("/action"). Il utilise également les classes HttpServletRequest et HttpServletResponse pour gérer les requêtes et les réponses HTTP, ainsi que la classe ProductDAO pour interagir avec la base de données et gérer les produits.

```Java
package controllers;

import java.io.IOException;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import jakarta.servlet.http.HttpSession;
import models.Product;
import models.ProductDAO;

import java.util.List;
import java.util.ArrayList;

@WebServlet(name = "Action", urlPatterns = "/action")
public class Action extends HttpServlet{
    ProductDAO productDAO;    
    public void init() {
        productDAO = new ProductDAO();
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        String action = req.getParameter("action");
        if (action.equals("addtocart")) {
            HttpSession session = req.getSession();
            List<String> cart = (List<String>) session.getAttribute("cart");
            if (cart == null) {
                cart = new ArrayList<>();
            }
            cart.add(req.getParameter("productId"));
            session.setAttribute("cart", cart);
            res.sendRedirect("/microprojet/products");
        }else if (action.equals("saveproduct")) {
            Product product = new Product();
            product.setName(req.getParameter("name"));
            product.setPrice(Double.parseDouble(req.getParameter("price")));
            productDAO.saveProduct(product);
            res.sendRedirect("/microprojet/products");
        }else if(action.equals("removeproduct")){
            productDAO.deleteProduct(Long.parseLong(req.getParameter("productId")));
            res.sendRedirect("/microprojet/products");
        }else if(action.equals("updateproduct")){
            Product product = productDAO.getProductById(Integer.parseInt(req.getParameter("productId")));
            req.setAttribute("name", product.getName());
            req.setAttribute("price", product.getPrice());
            req.setAttribute("productId", product.getId());
            req.getRequestDispatcher("WEB-INF/views/Updateproduct.jsp").forward(req, res);
        }
    }
}
```

### Cart

Ce code représente un servlet Java nommé Cart qui gère les opérations liées au panier dans votre application. Voici un résumé des fonctionnalités de ce servlet :

- La méthode `init` est utilisée pour initialiser le servlet et créer une instance de ProductDAO pour interagir avec la base de données.
- La méthode `doGet` est appelée lorsqu'une requête GET est envoyée au servlet. Elle récupère les identifiants des produits stockés dans le panier de l'utilisateur depuis la session. Ensuite, elle utilise ProductDAO pour récupérer les informations des produits à partir de ces identifiants. Enfin, elle transmet ces informations à la page Cart.jsp pour afficher le contenu du panier à l'utilisateur.
- La méthode `doPost` est appelée lorsqu'une requête POST est envoyée au servlet, généralement lorsqu'un utilisateur souhaite supprimer un produit de son panier. Si l'action est "delete", le produit correspondant est supprimé de la liste des produits du panier dans la session de l'utilisateur, puis l'utilisateur est redirigé vers la page du panier pour afficher le panier mis à jour.

Ce servlet utilise les annotations `@WebServlet` pour définir son nom et le chemin d'accès URL ("/cart"). Il utilise également les classes HttpServletRequest et HttpServletResponse pour gérer les requêtes et les réponses HTTP, ainsi que la classe ProductDAO pour interagir avec la base de données et gérer les produits.

```Java
package controllers;

import java.util.List;
import java.io.IOException;
import java.util.ArrayList;
import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import models.Product;
import models.ProductDAO;

@WebServlet(name = "Cart", value = "/cart")
public class Cart extends HttpServlet {
    ProductDAO productDAO;

    public void init() {
        productDAO = new ProductDAO();
    }

    public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        List<String> productsIds = (List<String>) request.getSession().getAttribute("cart");
        if (productsIds == null) {
            response.sendRedirect("/microprojet/products");
            return;
        }
        List<Product> products = new ArrayList<Product>();
        for (String i : productsIds) {
            int id = Integer.parseInt(i);
            products.add(productDAO.getProductById(id));
        }
        request.setAttribute("products", products);
        request.getRequestDispatcher("WEB-INF/views/Cart.jsp").forward(request, response);
    }

    public void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String action = request.getParameter("action");
        if (action.equals("delete")) {
            List<String> productsIds = (List<String>) request.getSession().getAttribute("cart");
            productsIds.remove(request.getParameter("productId"));
            request.getSession().setAttribute("cart", productsIds);
            response.sendRedirect(request.getContextPath() + "/cart");
        }
    }
}
```

### CommandServlet

Ce code représente un servlet Java nommé CommandServlet qui gère les commandes des utilisateurs dans votre application. Voici un résumé des fonctionnalités de ce servlet :

- La méthode `init` est utilisée pour initialiser le servlet et créer des instances de ProductDAO et CommandDAO pour interagir avec la base de données.
- La méthode `doGet` est appelée lorsqu'une requête GET est envoyée au servlet. Elle récupère le client à partir de la session et vérifie s'il s'agit d'un administrateur ou d'un client normal. En fonction de cela, elle utilise CommandDAO pour récupérer les commandes correspondantes et les transmet à la page Commands.jsp pour affichage.
- La méthode `doPost` est appelée lorsqu'une requête POST est envoyée au servlet, généralement lorsqu'un utilisateur finalise sa commande. Elle récupère les identifiants des produits dans le panier de l'utilisateur depuis la session, calcule le prix total de la commande en utilisant ProductDAO pour récupérer les prix des produits, puis crée une nouvelle commande avec ces informations et l'ajoute à la base de données via CommandDAO. Enfin, l'utilisateur est redirigé vers la page des produits après avoir passé sa commande avec succès.

Ce servlet utilise les annotations `@WebServlet` pour définir son nom et le chemin d'accès URL ("/command"). Il utilise également les classes HttpServletRequest et HttpServletResponse pour gérer les requêtes et les réponses HTTP, ainsi que les classes Client, Command, ProductDAO et CommandDAO pour interagir avec la base de données et gérer les commandes et les produits.

```Java
package controllers;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import models.CommandDAO;
import models.ProductDAO;
import java.io.IOException;
import models.Command;

import java.util.List;

import models.Client;

@WebServlet(name = "CommandServlet", value = "/command")
public class CommandServlet extends HttpServlet{
    private ProductDAO productDAO;
    private CommandDAO commandDAO;
    public void init() {
        productDAO = new ProductDAO();
        commandDAO = new CommandDAO();
    }

    public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        Client client = (Client) request.getSession().getAttribute("client");
        if(client.isAdmin()){
        List<Command> commands = commandDAO.getAllCommands();
        request.setAttribute("commands", commands);
        request.getRequestDispatcher("/WEB-INF/views/Commands.jsp").forward(request, response);
        }else{
        List<Command> commands = commandDAO.getAllCommandsForClient(client);
        request.setAttribute("commands", commands);
        request.getRequestDispatcher("/WEB-INF/views/Commands.jsp").forward(request, response);
        }
    }

    public void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        List<String> productsids =  (List<String>) request.getSession().getAttribute("cart");
        String products_ids = "";
        double total_price = 0;
        for (String id : productsids) {
            total_price += productDAO.getProductById(Integer.parseInt(id)).getPrice();
            products_ids += id + ",";
        }
         Command command = new Command();
        command.setProductIds(products_ids);
        command.setTotalPrice(total_price);
        command.setClient((Client) request.getSession().getAttribute("client"));
        commandDAO.saveCommand(command);
        response.sendRedirect("/microprojet/products");
    }
}
```

### Logout

Ce code représente un servlet Java nommé Lougout (il semble y avoir une erreur de frappe dans le nom, il devrait être Logout) qui gère la déconnexion des utilisateurs de votre application. Voici un résumé de son fonctionnement :

- Le servlet est configuré avec l'annotation `@WebServlet` pour définir son nom et le chemin d'accès URL ("/logout").
- La méthode `doGet` est appelée lorsqu'une requête GET est envoyée au servlet, généralement lorsqu'un utilisateur clique sur un lien de déconnexion. Elle invalide la session de l'utilisateur en appelant `req.getSession().invalidate()` pour supprimer toutes les données de session associées à cet utilisateur. Ensuite, elle redirige l'utilisateur vers la page des produits en utilisant `resp.sendRedirect("/microprojet/products")`.

Ce servlet est utilisé pour gérer la déconnexion des utilisateurs de manière sécurisée en invalidant leur session et en les redirigeant vers une page appropriée après la déconnexion, dans ce cas-ci, la page des produits de l'application.

```Java
package controllers;

import java.io.IOException;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

@WebServlet(name = "Lougout", urlPatterns = "/logout")
public class Lougout extends HttpServlet{
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.getSession().invalidate();
        resp.sendRedirect("/microprojet/products");
    }
}
```

### Product

Ce code représente un servlet Java nommé Products qui gère l'affichage des produits sur la page principale de votre application. Voici un résumé de son fonctionnement :

- Le servlet est configuré avec l'annotation `@WebServlet` pour définir son nom et le chemin d'accès URL ("/products").
- La méthode `doGet` est appelée lorsqu'une requête GET est envoyée au servlet, généralement lorsqu'un utilisateur accède à la page des produits. Elle commence par vérifier si l'utilisateur est connecté en récupérant le client à partir de la session. Si l'utilisateur n'est pas connecté (client est null), il est redirigé vers la page de connexion ("/microprojet/login").
- Si l'utilisateur est connecté, le servlet récupère la liste de tous les produits à l'aide de la méthode `getAllProducts` du `ProductDAO` et les place dans un attribut "products" de la requête. Il récupère également d'autres informations sur le client comme son statut d'administrateur et son nom, et les place dans des attributs appropriés de la requête.
- Les en-têtes de réponse sont configurés pour éviter la mise en cache des données de la page.
- Enfin, le servlet transfère le contrôle à la vue "Products.jsp" située dans le dossier "WEB-INF/views".

Ce servlet assure donc que seuls les utilisateurs connectés peuvent accéder à la liste des produits et fournit les données nécessaires à l'affichage de cette liste dans la vue associée.

```Java
package controllers;

import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import models.*;
import java.io.IOException;
import jakarta.servlet.http.HttpServletResponse;

@WebServlet(name = "Products", urlPatterns = "/products")
public class Products extends HttpServlet{
    private ProductDAO productDAO = new ProductDAO();
    public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        Client client = (Client) request.getSession().getAttribute("client");
        if (client == null) {
            response.sendRedirect("/microprojet/login");
            return;
        }
        request.setAttribute("admin", client.isAdmin());
        request.setAttribute("name", client.getName());
        request.setAttribute("products", productDAO.getAllProducts());
        response.setHeader("Cache-Control","no-cache, no-store, must-revalidate");
        response.setHeader("Pragma","no-cache");
        response.setHeader("Expires","0");
        request.getRequestDispatcher("WEB-INF/views/Products.jsp").forward(request, response);
    }
}
```

### SaveProduct

Ce servlet Java nommé `SaveProduct` est configuré pour gérer les requêtes GET sur l'URL "/saveproduct" à l'aide de l'annotation `@WebServlet`. Voici un résumé de son fonctionnement :

- Lorsqu'une requête GET est reçue sur l'URL "/saveproduct", la méthode `doGet` du servlet est appelée.
- À l'intérieur de la méthode `doGet`, le servlet utilise `req.getRequestDispatcher` pour transférer le contrôle à la vue "Addproduct.jsp" située dans le dossier "WEB-INF/views".
- Cette redirection permet d'afficher le formulaire d'ajout de produit à l'utilisateur. La logique de traitement du formulaire (par exemple, la validation des données et l'ajout effectif du produit dans la base de données) serait généralement gérée dans une autre méthode du servlet (par exemple, `doPost`).

En résumé, ce servlet sert principalement à afficher le formulaire d'ajout de produit à l'utilisateur lorsqu'il accède à l'URL "/saveproduct" via une requête GET.

```Java
package controllers;

import java.io.IOException;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

@WebServlet(name = "SaveProduct", urlPatterns = "/saveproduct")
public class SaveProduct extends HttpServlet{
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.getRequestDispatcher("WEB-INF/views/Addproduct.jsp").forward(req, resp);
    }
}
```

### UpdateProduct

Ce servlet Java nommé `UpdateProduct` est configuré pour gérer les requêtes POST sur l'URL "/updateproduct" à l'aide de l'annotation `@WebServlet`. Voici un résumé de son fonctionnement :

- Le servlet utilise la méthode `init` pour initialiser une instance de `ProductDAO`.
- Lorsqu'une requête POST est reçue sur l'URL "/updateproduct", la méthode `doPost` du servlet est appelée.
- À l'intérieur de la méthode `doPost`, le servlet récupère les paramètres de la requête POST, notamment le nom, le prix et l'identifiant du produit à mettre à jour.
- En utilisant ces paramètres, le servlet crée un nouvel objet `Product` avec les informations mises à jour.
- Le servlet utilise ensuite le `ProductDAO` pour effectuer la mise à jour du produit dans la base de données en appelant la méthode `updateProduct`.
- Après la mise à jour réussie, le servlet redirige l'utilisateur vers la page des produits ("/microprojet/products") en utilisant `response.sendRedirect`.

En résumé, ce servlet sert à gérer les requêtes POST d'actualisation de produits, en mettant à jour les informations du produit dans la base de données et en redirigeant l'utilisateur vers la page des produits après la mise à jour.

```Java
package controllers;

import java.io.IOException;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import models.Product;
import models.ProductDAO;

@WebServlet(name = "UpdateProduct", urlPatterns = "/updateproduct")
public class UpdateProduct extends HttpServlet{
    ProductDAO productDAO;
    public void init(){
        productDAO = new ProductDAO();
    }
    public void doPost(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException {
        String name = request.getParameter("name");
        String price = request.getParameter("price");
        String id = request.getParameter("productId");
        Product product = new Product( name, Double.parseDouble(price));
        product.setId(Long.parseLong(id));
        productDAO.updateProduct(product);
        long timestamp = System.currentTimeMillis(); // Get current timestamp
        String redirectUrl = "/microprojet/products";
        response.sendRedirect(redirectUrl);
    }
}
```

## Views-JSP/JSTL

### Login

Ce code représente une page HTML pour la connexion (login) d'un utilisateur. Voici un résumé des éléments clés de cette page :

- La page utilise la balise `<%@ page %>` pour spécifier le langage Java et le codage de caractères.
- Le code HTML est structuré avec les balises `<html>`, `<head>`, et `<body>`, contenant les éléments de contenu.
- Dans la balise `<style>` du `<head>`, des règles CSS sont définies pour le style visuel de la page, comme la mise en page, les couleurs et les polices.
- À l'intérieur du `<body>`, il y a un conteneur de connexion `<div>` avec un formulaire de connexion. Le formulaire utilise la méthode POST pour envoyer les données au serveur.
- Le formulaire comporte des champs de saisie pour le nom d'utilisateur (Name) et le mot de passe (Password), avec des balises `<input>` de type "text" et "password".
- Un bouton de connexion est inclus dans le formulaire, qui sera activé lorsque l'utilisateur soumettra le formulaire.
- Un message d'erreur `<div>` est prévu pour afficher les messages d'erreur, qui peuvent être définis à partir de la demande servlet.
- Enfin, un lien vers la page de création de compte (SignUp) est également inclus pour permettre aux utilisateurs de s'inscrire s'ils n'ont pas encore de compte.

Cette page est conçue pour fournir une interface conviviale pour que les utilisateurs saisissent leurs informations de connexion et se connectent à l'application. Elle suit les bonnes pratiques en matière de sécurité en utilisant le cryptage de mot de passe (type "password") et en exigeant des champs obligatoires (attribut "required" dans les balises `<input>`).

```Java
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Page</title>
</head>
<style>

body {
    font-family: Arial, sans-serif;
    background-color: \#f2f2f2;
}

.login-container {
    max-width: 400px;
    margin: 100px auto;
    padding: 20px;
    border: 1px solid \#ccc;
    border-radius: 5px;
    background-color: \#fff;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
}

h2 {
    text-align: center;
    margin-bottom: 20px;
}

.input-group {
    margin-bottom: 15px;
}

.input-group label {
    display: block;
    margin-bottom: 5px;
}

input[type="text"],
input[type="password"] {
    width: 100%;
    padding: 8px;
    border-radius: 3px;
    border: 1px solid \#ccc;
}

button {
    width: 100%;
    padding: 10px;
    border: none;
    border-radius: 3px;
    background-color: \#007bff;
    color: \#fff;
    cursor: pointer;
}

.error-msg {
    color: red;
    margin-top: 10px;
    text-align: center;
}
</style>
<body>
    <div class="login-container">
        <h2>Login</h2>
        <form action="" method="post">
            <div class="input-group">
                <label for="username">Name</label>
                <input type="text" id="username" name="name" required>
            </div>
            <div class="input-group">
                <label for="password">Password</label>
                <input type="password" id="password" name="password" required>
            </div>
            <button type="submit">Login</button>
            <div id="error-msg" class="error-msg">
                <%= request.getAttribute("errorMessage") %>
            </div>
        </form>
        <a href="signup">SignUp</a>
    </div>
</body>
</html>
```

### AddProduct

Ce code représente une page HTML pour ajouter un produit à l'application. Voici un résumé des éléments clés de cette page :

- La page utilise la balise `<%@ page %>` pour spécifier le langage Java et le codage de caractères.
- Le code HTML est structuré avec les balises `<html>`, `<head>`, et `<body>`, contenant les éléments de contenu.
- Dans la balise `<style>` du `<head>`, des règles CSS sont définies pour le style visuel de la page, comme la mise en page, les couleurs et les polices.
- Le corps de la page contient un conteneur `<div>` avec une classe "container", qui contient le formulaire pour ajouter un produit.
- Le formulaire utilise la méthode POST pour envoyer les données au serveur, avec l'action "action" spécifiée dans l'attribut `action`.
- Le formulaire comporte des champs de saisie pour le nom du produit (Name) et le prix (Price), avec des balises `<input>` de type "text" et "number".
- Le bouton "Add Product" est un bouton de soumission de formulaire, qui déclenchera l'action de sauvegarde du produit sur le serveur.
- Les balises `<label>` sont utilisées pour identifier les champs de saisie et améliorer l'accessibilité.
- Des règles CSS sont appliquées pour le style des éléments du formulaire, comme la largeur des champs de saisie, le rembourrage, les couleurs de fond et de texte, etc.

Cette page est conçue pour fournir une interface conviviale permettant aux utilisateurs d'ajouter un nouveau produit à l'application. Les champs requis sont marqués comme tels (attribut "required" dans les balises `<input>`), et des contraintes sont appliquées au champ de prix (minimum 0 et étape de 0.01) pour garantir des données valides lors de la soumission du formulaire.

```Java
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Add Product</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: \#f7f7f7;
            margin: 0;
            padding: 0;
        }

        .container {
            max-width: 600px;
            margin: 20px auto;
            padding: 20px;
            background-color: \#fff;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            margin-bottom: 20px;
        }

        form {
            width: 100%;
            max-width: 400px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        input[type="text"], input[type="number"] {
            width: 100%;
            padding: 8px;
            border-radius: 3px;
            border: 1px solid \#ccc;
            box-sizing: border-box;
        }

        input[type="submit"] {
            padding: 10px 20px;
            background-color: \#007bff;
            color: \#fff;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: \#0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Add Product</h2>
        <form action="action" method="post">
        <input type="hidden" name="action" value="saveproduct">
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" id="name" name="name" required>
            </div>
            <div class="form-group">
                <label for="price">Price:</label>
                <input type="number" id="price" name="price" min="0" step="0.01" required>
            </div>
            <input type="submit" value="Add Product">
        </form>
    </div>
</body>
</html>
```

### Cart

Ce code représente une page HTML utilisant JSTL (JavaServer Pages Standard Tag Library) pour afficher un panier d'achats. Voici un aperçu des éléments principaux de cette page :

- La directive `<%@ taglib %>` est utilisée pour importer la bibliothèque de balises JSTL Core.
- La page utilise JSTL pour une boucle `c:forEach` qui itère sur une liste de produits `${products}`.
- Chaque produit est affiché dans un tableau avec les colonnes ID, Name et Price.
- Pour chaque produit, un formulaire est créé avec un bouton "Remove" qui permet de supprimer le produit du panier.
- L'action de suppression est envoyée au servlet "/microprojet/cart" avec les paramètres nécessaires (ID du produit et action "delete").
- En bas de la page, un formulaire est utilisé pour permettre à l'utilisateur de passer une commande en cliquant sur le bouton "Commander".

Ce code HTML/JSTL est conçu pour une interface utilisateur simple et fonctionnelle permettant de visualiser les produits dans le panier, de les supprimer individuellement et de passer une commande globale. Les styles CSS sont utilisés pour rendre l'interface plus attrayante et conviviale.

```Java
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html lang="en">
<%@ page isELIgnored="false" %>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shopping Cart</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: \#f7f7f7;
            margin: 0;
            padding: 0;
        }

        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background-color: \#fff;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            margin-bottom: 20px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            padding: 10px;
            border: 1px solid \#ddd;
        }

        th {
            background-color: \#f0f0f0;
        }

        tr:nth-child(even) {
            background-color: \#f9f9f9;
        }

        form {
            display: inline;
        }

        input[type="submit"] {
            padding: 8px 16px;
            background-color: \#007bff;
            color: \#fff;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: \#0056b3;
        }

        .remove-btn {
            background-color: \#dc3545;
        }

        .remove-btn:hover {
            background-color: \#c82333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Shopping Cart</h2>
        
        <table>
            <tr>
                <th>ID</th>
                <th>Name</th>
                <th>Price</th>
                <th>Action</th>
            </tr>
            <c:forEach var="product" items="${products}">
                <tr>
                    <td>${product.id}</td>
                    <td>${product.name}</td>
                    <td>${product.price}</td>
                    <td>
                        <form action="/microprojet/cart" method="post">
                            <input type="hidden" name="productId" value="${product.id}" />
                            <input type="hidden" name="action" value="delete">
                            <input type="submit" value="Remove" class="remove-btn" />
                        </form>
                    </td>
                </tr>
            </c:forEach>
        </table>
        <form action="/microprojet/command" method="post">
            <input type="submit" value="Commander" />
        </form>
    </div>
</body>
</html>
```

### Commands

Ce code représente une page HTML utilisant JSTL pour afficher une liste de commandes. Voici un aperçu des éléments principaux de cette page :

- La directive `<%@ taglib prefix="c" uri="<http://java.sun.com/jsp/jstl/core>"%>` est utilisée pour importer la bibliothèque de balises JSTL Core.
- La page utilise JSTL pour une boucle `c:forEach` qui itère sur une liste de commandes `${commands}`.
- Chaque commande est affichée dans un tableau avec les colonnes ID, TotalPrice et ProductsNames.
- Un lien est fourni pour permettre à l'utilisateur de revenir au panier ou d'accéder à la liste des commandes.

Les styles CSS sont utilisés pour rendre l'interface plus attrayante et conviviale. La page est conçue pour afficher les détails de chaque commande dans un tableau organisé et permettre à l'utilisateur de naviguer facilement entre différentes parties de l'application.

```Java
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
<!DOCTYPE html>
<%@ page isELIgnored="false" %>
<Context cachingAllowed="false">
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Commandes List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: \#f7f7f7;
            margin: 0;
            padding: 0;
        }

        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background-color: \#fff;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            margin-bottom: 20px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            padding: 10px;
            border: 1px solid \#ddd;
        }

        th {
            background-color: \#f0f0f0;
        }

        tr:nth-child(even) {
            background-color: \#f9f9f9;
        }

        form {
            display: inline;
        }

        input[type="submit"] {
            padding: 8px 16px;
            background-color: \#007bff;
            color: \#fff;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: \#0056b3;
        }

        a {
            color: \#007bff;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        a:hover {
            color: \#0056b3;
        }

        a:visited {
            color: \#6610f2;
        }

        a:active {
            color: \#dc3545;
        }

        a:disabled {
            color: \#6c757d;
            pointer-events: none;
        }
    </style>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="Cache-Control" content="no-cache, no-store, must-revalidate">
    <meta http-equiv="Pragma" content="no-cache">
    <meta http-equiv="Expires" content="0">
</head>
<body>
    <div class="container">

        <c:if test="${error != null}">
            <p style="color: red;">${error}</p>
        </c:if>
        <h1><c:out value="${name}" /></h1>
        <h2>Commands List</h2>
        
        <table>
            <tr>
                <th>ID</th>
                <th>TotalPrice</th>
                <th>ProductsNames</th>
            </tr>
            <c:forEach var="command" items="${commands}">
                <tr>
                    <td>${command.id}</td>
                    <td>${command.totalPrice}</td>
                    <td>${command.productsNames}</td>
                </tr>
            </c:forEach>
        </table>
        <a href="/microprojet/cart">Go To Cart </a>
        <a href="/microprojet/commandes">Commandes</a>
    </div>
</html>
```

### Product

Ce code représente une page HTML utilisant JSTL pour afficher une liste de produits. Voici un aperçu des éléments principaux de cette page :

- La directive `<%@ taglib prefix="c" uri="<http://java.sun.com/jsp/jstl/core>"%>` est utilisée pour importer la bibliothèque de balises JSTL Core.
- La page utilise JSTL pour une boucle `c:forEach` qui itère sur une liste de produits `${products}`.
- Chaque produit est affiché dans un tableau avec les colonnes ID, Name, Price et des boutons d'action.
- Les boutons d'action permettent d'ajouter un produit au panier, de mettre à jour un produit (pour les administrateurs), ou de supprimer un produit (pour les administrateurs).
- Des liens sont fournis pour permettre à l'utilisateur de naviguer vers d'autres parties de l'application, comme le panier, les commandes, ou pour se déconnecter.
- Certains éléments sont conditionnellement affichés en fonction du rôle de l'utilisateur, par exemple, l'ajout de produit n'est visible que pour les administrateurs.

Les styles CSS sont utilisés pour rendre l'interface plus attrayante et conviviale. La page est conçue pour afficher les détails de chaque produit dans un tableau organisé et permettre à l'utilisateur d'effectuer des actions spécifiques en fonction de son rôle dans l'application.

```Java
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
<!DOCTYPE html>
<%@ page isELIgnored="false" %>
<Context cachingAllowed="false">
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: \#f7f7f7;
            margin: 0;
            padding: 0;
        }

        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background-color: \#fff;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            margin-bottom: 20px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            padding: 10px;
            border: 1px solid \#ddd;
        }

        th {
            background-color: \#f0f0f0;
        }

        tr:nth-child(even) {
            background-color: \#f9f9f9;
        }

        form {
            display: inline;
        }

        input[type="submit"] {
            padding: 8px 16px;
            background-color: \#007bff;
            color: \#fff;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: \#0056b3;
        }

        a {
            color: \#007bff;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        a:hover {
            color: \#0056b3;
        }

        a:visited {
            color: \#6610f2;
        }

        a:active {
            color: \#dc3545;
        }

        a:disabled {
            color: \#6c757d;
            pointer-events: none;
        }
    </style>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="Cache-Control" content="no-cache, no-store, must-revalidate">
    <meta http-equiv="Pragma" content="no-cache">
    <meta http-equiv="Expires" content="0">
</head>
<body>
    <div class="container">

        <c:if test="${error != null}">
            <p style="color: red;">${error}</p>
        </c:if>
        <h1>Hi, <c:out value="${name}" /></h1>
        <h2>Product List</h2>
        
        <table>
            <tr>
                <th>ID</th>
                <th>Name</th>
                <th>Price</th>
                <th>Action</th>
            </tr>
            <c:forEach var="product" items="${products}">
                <tr>
                    <td>${product.id}</td>
                    <td>${product.name}</td>
                    <td>${product.price}</td>
                   <td style="/*! align-content: center; */justify-content: center;/*! align-self: center; */display: flex;gap: 15px;">
                        <form action="/microprojet/action" method="post">
                            <input type="hidden" name="productId" value="${product.id}" />
                            <input type="hidden" name="action" value="addtocart" />
                            <input type="submit" value="Add to Cart" />
                        </form>
                        <c:if test="${admin}">
                            <form action="/microprojet/action" method="post">
                                <input type="hidden" name="productId" value="${product.id}" />
                                <input type="hidden" name="action" value="updateproduct" />
                                <input type="submit" value="Update" />
                            </form>
                            <form action="/microprojet/action" method="post">
                                <input type="hidden" name="productId" value="${product.id}" />
                                <input type="hidden" name="action" value="removeproduct" />
                                <input type="submit" value="Remove" style="color:red;"/>
                            </form>
                        </c:if>
                    </td>
                </tr>
            </c:forEach>
        </table>
        <a href="/microprojet/cart">Go To Cart </a>
        <a href="/microprojet/command">Commandes</a>
        <a href="/microprojet/logout">Logout</a>
        <c:if test="${admin}">
            <a href="/microprojet/saveproduct">Add Product</a>
        </c:if>
    </div>
</html>
```

### Signup

Ce code représente une page HTML pour un formulaire d'inscription (SignUp). Voici un aperçu des éléments principaux de cette page :

- La directive `<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>` définit la langue, le type de contenu et l'encodage de la page.
- La balise `<!DOCTYPE html>` spécifie le type de document HTML.
- La section `<head>` contient les métadonnées de la page telles que l'encodage, le titre et les styles CSS.
- Dans la section `<style>`, des règles CSS sont définies pour styliser les éléments de la page, tels que le conteneur principal, les champs de saisie, les boutons, etc.
- La section `<body>` contient le contenu principal de la page, y compris le formulaire d'inscription.
- Le formulaire utilise la méthode POST pour envoyer les données au serveur. Il contient des champs pour le nom (name) et le mot de passe (password) de l'utilisateur.
- Un bouton "SignUp" est inclus pour soumettre le formulaire.
- Un message d'erreur `<div id="error-msg">` est utilisé pour afficher les éventuelles erreurs de validation du formulaire.
- Un lien `<a href="login">Login</a>` est fourni pour rediriger vers la page de connexion si l'utilisateur a déjà un compte.

Cette page est conçue pour permettre aux utilisateurs de s'inscrire en fournissant leur nom et leur mot de passe, avec des fonctionnalités de validation et de présentation visuelle grâce aux styles CSS.

```Java
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SignUp Page</title>
</head>
<style>

body {
    font-family: Arial, sans-serif;
    background-color: \#f2f2f2;
}

.login-container {
    max-width: 400px;
    margin: 100px auto;
    padding: 20px;
    border: 1px solid \#ccc;
    border-radius: 5px;
    background-color: \#fff;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
}

h2 {
    text-align: center;
    margin-bottom: 20px;
}

.input-group {
    margin-bottom: 15px;
}

.input-group label {
    display: block;
    margin-bottom: 5px;
}

input[type="text"],
input[type="password"] {
    width: 100%;
    padding: 8px;
    border-radius: 3px;
    border: 1px solid \#ccc;
}

button {
    width: 100%;
    padding: 10px;
    border: none;
    border-radius: 3px;
    background-color: \#007bff;
    color: \#fff;
    cursor: pointer;
}

.error-msg {
    color: red;
    margin-top: 10px;
    text-align: center;
}
</style>
<body>
    <div class="login-container">
        <h2>SignUp</h2>
        <form action="" method="post">
            <div class="input-group">
                <label for="username">Name</label>
                <input type="text" id="username" name="name" required>
            </div>
            <div class="input-group">
                <label for="password">Password</label>
                <input type="password" id="password" name="password" required>
            </div>
            <button type="submit">SignUp</button>
            <div id="error-msg" class="error-msg">
                <%= request.getAttribute("errorMessage") %>
            </div>
        </form>
        <a href="login">Login</a>
    </div>
</body>
</html>

```

### Updateproduct

Ce code représente une page HTML pour mettre à jour les informations d'un produit. Voici un aperçu des éléments principaux de cette page :

- La directive `<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>` définit la langue, le type de contenu et l'encodage de la page.
- La directive `<%@ taglib prefix="c" uri="<http://java.sun.com/jsp/jstl/core>"%>` importe la bibliothèque JSTL Core pour l'utilisation des expressions EL (Expression Language).
- La balise `<!DOCTYPE html>` spécifie le type de document HTML.
- La section `<head>` contient les métadonnées de la page telles que l'encodage, le titre et les styles CSS.
- Dans la section `<style>`, des règles CSS sont définies pour styliser les éléments de la page, tels que le conteneur principal, les champs de saisie, les boutons, etc.
- La section `<body>` contient le contenu principal de la page, y compris le formulaire de mise à jour du produit.
- Le formulaire utilise la méthode POST pour envoyer les données au serveur. Il contient des champs pour le nom (name) et le prix (price) du produit, ainsi qu'un champ caché pour l'identifiant du produit (productId) et l'action de mise à jour (action).
- Les valeurs par défaut du nom et du prix du produit sont obtenues à partir des variables EL `${name}` et `${price}`.
- Un bouton "Update Product" est inclus pour soumettre le formulaire de mise à jour.

Cette page est conçue pour permettre aux utilisateurs de modifier le nom et le prix d'un produit existant en utilisant un formulaire convivial et stylisé. Les valeurs actuelles du produit sont pré-remplies dans le formulaire pour faciliter la mise à jour.

```Java

<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
<!DOCTYPE html>
<%@ page isELIgnored="false" %>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Update</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: \#f7f7f7;
            margin: 0;
            padding: 0;
        }

        .container {
            max-width: 600px;
            margin: 20px auto;
            padding: 20px;
            background-color: \#fff;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            margin-bottom: 20px;
        }

        form {
            width: 100%;
            max-width: 400px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        input[type="text"], input[type="number"] {
            width: 100%;
            padding: 8px;
            border-radius: 3px;
            border: 1px solid \#ccc;
            box-sizing: border-box;
        }

        input[type="submit"] {
            padding: 10px 20px;
            background-color: \#007bff;
            color: \#fff;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: \#0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Update Product</h2>
        <form action="updateproduct" method="post">
        <input type="hidden" name="action" value="saveproduct">
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" id="name" name="name" value="${name}">
            </div>
            <div class="form-group">
                <label for="price">Price:</label>
                <input type="number" id="price" name="price" min="0" step="0.01" value="${price}" required>
            </div>
            <input type="hidden" name="productId" value="${productId}">
            <input type="submit" value="Update Product">
        </form>
    </div>
</body>
</html>
```

# Les Fichiers De Configurations

## Persistance.xml

Le fichier que vous avez fourni est un fichier de configuration XML pour la persistence des entités dans une application Java EE utilisant JPA (Java Persistence API) avec Hibernate comme fournisseur de persistance. Voici une explication de chaque partie du fichier :

1. `<?xml version="1.0" encoding="UTF-8"?>`: Cette déclaration indique que le fichier est au format XML et qu'il est encodé en UTF-8.
2. `<persistence>`: C'est la balise racine du fichier de configuration de la persistance.
3. `xmlns="<http://xmlns.jcp.org/xml/ns/persistence>"`: Cela définit l'espace de noms par défaut pour les éléments XML dans le fichier de configuration de la persistance.
4. `xmlns:xsi="<http://www.w3.org/2001/XMLSchema-instance>"` et `xsi:schemaLocation="<http://xmlns.jcp.org/xml/ns/persistence> <http://xmlns.jcp.org/xml/ns/persistence/persistence_2_2.xsd>"`: Ces attributs définissent l'espace de noms XSI et l'emplacement du schéma XSD utilisé pour valider la structure du fichier XML.
5. `version="2.2"`: Indique la version de la spécification de la persistance utilisée dans ce fichier.
6. `<persistence-unit name="myPersistenceUnit" transaction-type="RESOURCE_LOCAL">`: Cette balise définit une unité de persistance nommée "myPersistenceUnit" avec un type de transaction "RESOURCE_LOCAL", ce qui signifie que les transactions sont gérées localement par l'application.
7. `<provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>`: Spécifie le fournisseur de persistance à utiliser, qui est Hibernate dans ce cas.
8. `<class>models.Client</class>`, `<class>models.Product</class>`, `<class>models.Command</class>`: Ces balises déclarent les classes d'entité que JPA doit gérer pour la persistance. Dans cet exemple, les classes `Client`, `Product`, et `Command` sont déclarées comme des entités persistantes.
9. `<properties>`: C'est la section où vous pouvez spécifier les propriétés de configuration pour la connexion à la base de données. Dans cet exemple, les propriétés spécifient le pilote JDBC, l'URL de la base de données, le nom d'utilisateur et le mot de passe pour se connecter à la base de données MySQL.

- `<property name="jakarta.persistence.jdbc.driver" value="com.mysql.cj.jdbc.Driver" />`: Spécifie le pilote JDBC à utiliser.
- `<property name="jakarta.persistence.jdbc.url" value="jdbc:mysql://172.19.0.2:3306/test" />`: Spécifie l'URL de la base de données MySQL.
- `<property name="jakarta.persistence.jdbc.user" value="root" />`: Spécifie le nom d'utilisateur pour la connexion à la base de données.
- `<property name="jakarta.persistence.jdbc.password" value="root" />`: Spécifie le mot de passe pour la connexion à la base de données.

Assurez-vous d'adapter ces configurations à votre environnement et à votre base de données spécifiques avant de les utiliser dans votre application Java EE avec JPA et Hibernate.

```Java
<?xml version="1.0" encoding="UTF-8"?>
<persistence xmlns="http://xmlns.jcp.org/xml/ns/persistence"
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence http://xmlns.jcp.org/xml/ns/persistence/persistence_2_2.xsd"
             version="2.2">

    <persistence-unit name="myPersistenceUnit" transaction-type="RESOURCE_LOCAL">
        <provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>
        <class>models.Client</class>
        <class>models.Product</class>
        <class>models.Command</class>
        <properties>
            <property name="jakarta.persistence.jdbc.driver" value="com.mysql.cj.jdbc.Driver" />
            <property name="jakarta.persistence.jdbc.url" value="jdbc:mysql://172.19.0.2:3306/test" />
            <property name="jakarta.persistence.jdbc.user" value="root" />
            <property name="jakarta.persistence.jdbc.password" value="root" />
        </properties>
    </persistence-unit>
</persistence>
```

# Conclusion

Le projet présente une application Web Java EE robuste conçue pour le commerce électronique. En utilisant des Servlets, des JSP et JSTL, il gère l'authentification des utilisateurs, la liste des produits, la fonctionnalité du panier d'achat et le traitement des commandes. Le backend utilise JPA avec Hibernate pour l'interaction avec la base de données, garantissant une persistance et une récupération efficaces des données. Avec une architecture MVC claire, il sépare les préoccupations pour une maintenance et une évolutivité faciles. Dans l'ensemble, le projet illustre une approche complète pour développer une plateforme de shopping en ligne fonctionnelle et conviviale.