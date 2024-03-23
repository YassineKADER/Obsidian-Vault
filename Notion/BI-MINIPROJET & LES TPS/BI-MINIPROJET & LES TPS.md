# **Table des matières**

Table des matières

Cahier de Charges - Analyse de Marché avec Données Massives

Objectif:

Étapes du projet:

Livrables Attendus:

Contraintes Techniques:

Calendrier et Échéances:

Notes Supplémentaires:

Collecting & Cleaning:

Data Collecting:

Cleaning And Formatting:

Slicing et creation des tables fait et des tables des tables de dimensions:

Model Mixte:

Data Slicing:

Reporting & Visualization:

Visualization:

OLAP

# Cahier de Charges - Analyse de Marché avec Données Massives

## Objectif:

Le projet vise à analyser le marché en utilisant une grande quantité de données sur les ventes. Les données comprennent les colonnes suivantes: ['Order_ID','Order_Date','Ship_Date','Ship_Mode','Customer_ID','Customer_Name','Segment','Country','City','State','Postal_Code','Region','Product_ID','Category','Sub-Category','Product_Name','Sales','Quantity','Discount','Profit']

## Étapes du projet:

1. **Collecte de Données:**
    - Les données sont stockées dans des fichiers CSV distincts pour chaque table:
        - customers.csv (clients)
        - orders.csv (commandes)
        - dates.csv (dates)
        - products.csv (produits)
        - categories.csv (catégories)
        - subcategories.csv (sous-catégories)
        - locations.csv (emplacements)
2. **Prétraitement des Données:**
    - Charger les fichiers CSV dans des DataFrames (par exemple, pandas en Python, Pentaho DI).
    - Vérifier la qualité des données (valeurs manquantes, erreurs, duplications, etc.).
    - Nettoyer et transformer les données au besoin (formatage des dates, suppression des doublons, etc.).
3. **Création d'un Modèle de Données:**
    - Concevoir un schéma de base de données mixte pour le data warehouse.
    - Identifier les entités, les attributs et les relations entre les tables.
    - Utiliser des clés primaires et étrangères pour lier les tables entre elles.
4. **Chargement des Données dans le Data Warehouse:**
    - Créer une base de données relationnelle (par exemple, MySQL, PostgreSQL).
    - Concevoir des scripts SQL pour créer les tables selon le modèle défini.
    - Charger les données des fichiers CSV dans les tables correspondantes.
5. **Analyse de Marché:**
    - Réaliser des requêtes SQL pour extraire des informations pertinentes:
        - Analyser les ventes par segment de client, par pays, par ville, etc.
        - Examiner les tendances temporelles des ventes (mensuelles, annuelles).
        - Identifier les produits les plus vendus, les catégories les plus lucratives, etc.
        - Évaluer la rentabilité des ventes en fonction des discounts appliqués.
6. **Visualisation des Données:**
    - Utiliser des outils de visualisation (comme matplotlib, seaborn, Tableau, Power BI) pour créer des graphiques et des tableaux de bord.
    - Présenter les résultats de manière claire et concise pour faciliter la compréhension et la prise de décision.

## Livrables Attendus:

1. Schéma du Data Warehouse:
    - Diagramme entité-relation (ER) montrant la structure des tables et leurs relations.
2. Code Source:
    - Scripts Python pour le prétraitement des données et le chargement dans la base de données.
    - Scripts SQL pour la création des tables et l'analyse des données.
3. Rapport d'Analyse:
    - Rapport détaillé sur les résultats de l'analyse de marché.
    - Graphiques, tableaux et conclusions sur les tendances et les insights découverts.
4. Tableau de Bord Interactif (en option):
    - Si nécessaire, créer un tableau de bord interactif pour visualiser les données clés.

## Contraintes Techniques:

- Utiliser des technologies open source et largement utilisées (Python, pandas, SQL).
- Assurer la sécurité et la confidentialité des données pendant tout le processus.

## Calendrier et Échéances:

- **Date de début:** [Date de début du projet]
- **Date de fin:** [Date de fin du projet]
- **Échéances intermédiaires:** Définir des dates limites pour chaque étape du projet.

## Notes Supplémentaires:

- Le respect des bonnes pratiques en matière de gestion de projet et d'analyse de données est crucial.
- La collaboration étroite entre les équipes technique, analytique et de gestion est recommandée pour garantir le succès du projet.

# Collecting & Cleaning:

Voici les détails sur les colonnes et un exemple de données fourni :

- **Order_ID** : Identifiant unique pour chaque commande.
- **Order_Date** : Date à laquelle la commande a été passée.
- **Ship_Date** : Date à laquelle la commande a été expédiée.
- **Ship_Mode** : Mode d'expédition de la commande (par exemple, Standard, Express, etc.).
- **Customer_ID** : Identifiant unique pour chaque client.
- **Customer_Name** : Nom du client.
- **Segment** : Segment de marché auquel le client appartient (par exemple, Entreprise, Consommateur, etc.).
- **Country** : Pays où la commande a été passée.
- **City** : Ville où la commande a été passée.
- **State** : État ou province où la commande a été passée.
- **Postal_Code** : Code postal de l'endroit où la commande a été passée.
- **Region** : Région géographique (par exemple, Ouest, Sud, etc.).
- **Product_ID** : Identifiant unique pour chaque produit.
- **Category** : Catégorie du produit (par exemple, Fournitures de bureau, Meubles, etc.).
- **Sub-Category** : Sous-catégorie du produit (par exemple, Étiquettes, Tables, etc.).
- **Product_Name** : Nom du produit.
- **Sales** : Montant total des ventes pour la commande.
- **Quantity** : Quantité du produit commandé.
- **Discount** : Rabais appliqué à la commande.
- **Profit** : Bénéfice généré par la commande.

> Il est important de noter que ces données contenir des erreurs et des données incorrectes qui nécessiteront un nettoyage et une correction avant de pouvoir être analysées de manière fiable 💡

**Example:**

|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|Order_ID|Order_Date|Ship_Date|Ship_Mode|Customer_ID|Customer_Name|Segment|Country|City|State|Postal_Code|Region|Product_ID|Category|Sub-Category|Product_Name|Sales|Quantity|Discount|Profit|
|CA-2016-138688|06/12/2016|06/16/2016|Deuxième Classe|DV-13045|Darrin Van Huff|Entreprise|États-Unis|Los Angeles|Californie|90036.0|Ouest|OFF-LA-10000240|Fournitures de bureau|Étiquettes|Étiquettes auto-adhésives pour machines à écrire|14,62 $|2|0%|6,87 $|
|US-2015-108966|10/11/2015|10/18/2015|Standard|SO-20335|Sean O'Donnell|Consommateur|États-Unis|Fort Lauderdale|Floride|33311.0|Sud|FUR-TA-10000577|Meubles|Tables|Table rectangulaire mince de la série Bretford CR4500|957,58 $|5|45%|-383,03 $|

## Data Collecting:

La source de données que nous avons comprend 4 bases de données MySQL, un fichier CSV, un fichier texte (TXT) et un fichier JSON. J'ai besoin de collecter ces données et de les formater à partir des 4 sources, donc j'utilise Pentaho Data Integration (PDI) à cet effet.

![[Untitled.jpeg]]

Pentaho DI

> [!important]  
> Pentaho Data Integration (PDI) est une plateforme open source pour l'intégration de données, le nettoyage, la transformation et le chargement de données provenant de diverses sources. Elle offre une interface graphique conviviale pour créer des flux de données et est largement utilisée pour l'analyse et le reporting dans les entreprises.  

Voila les fichier que j’ai utliser:

![[Untitled 11.png|Untitled 11.png]]

Datasources files

Pour tableu de db:

![[Untitled 1 3.png|Untitled 1 3.png]]

Tables in Mysql db

Alors j’ajoute tous les sources dans pentaho :

![[Untitled 2 3.png|Untitled 2 3.png]]

Reading Data From Mysql, txt, csv,json files

## Cleaning And Formatting:

Pour formater les données, j'utilise Pentaho. L'idée principale qui m'est venue d'abord est de nettoyer les données et de les combiner dans une seule table ou un seul ensemble de données volumineux pour ensuite les découper en petites dimensions et tables de faits. Pour cela, j'utilise diverses techniques telles que les colonnes ordonnées (Orsecolumns) en utilisant les valeurs de sélection dans Pentaho, l'ajout de flux (append stream), des scripts JS pour vérifier d'autres éléments comme le format des dates et les enregistrements non valides.

Les transformations se sont déroulées comme suit :

![[Untitled 3 3.png|Untitled 3 3.png]]

Cleaning and formatting PDI

Ouput :

![[Untitled 4 3.png|Untitled 4 3.png]]

Output file

**Results Metrics:**

Nous avons commencé avec 30 000 lignes de données et actuellement nous en avons seulement 25 000 après le formatage et le nettoyage.

![[Untitled 5 3.png|Untitled 5 3.png]]

## Slicing et creation des tables fait et des tables des tables de dimensions:

### Model Mixte:

![[BI.png]]

Basé sur le schéma de base de données que vous avez fourni, qui comprend des tables telles que `orders` (commandes), `products` (produits), `subcategories` (sous-catégories), `categories` (catégories), `customers` (clients), `locations` (emplacements) et `dates` (dates), vous semblez travailler dans un contexte de data warehousing ou de business intelligence où vous avez probablement un mélange de tables de faits et de dimensions.

Identifions les tables de faits et de dimensions en fonction de votre schéma :

1. **Table de Faits :**
    - La table `orders` peut être considérée comme une table de faits car elle contient des valeurs numériques mesurables et additives telles que `Sales` (ventes), `Quantity` (quantité), `Discount` (remise) et `Profit` (profit). Les tables de faits stockent généralement des données transactionnelles et sont liées à plusieurs tables de dimensions.
2. **Tables de Dimensions :**
    - Les tables `products` (produits), `subcategories` (sous-catégories) et `categories` (catégories) peuvent être considérées comme des tables de dimensions. Elles fournissent un contexte et des attributs descriptifs liés aux produits et à leur catégorisation. Les tables de dimensions sont généralement de taille plus petite et sont utilisées pour filtrer, regrouper et analyser les données de la table de faits.
    - Les tables `customers` (clients) et `locations` (emplacements) sont également des tables de dimensions car elles fournissent des informations sur les clients et leurs emplacements, qui peuvent être utilisées pour la segmentation et l'analyse.
    - La table `dates` (dates) peut être une table de dimension temporelle qui fournit des attributs liés à la date tels que `Date`, `DayOfWeek` (jour de la semaine), `Week` (semaine), `Month` (mois), `Quarter` (trimestre) et `Year` (année). Les tables de dimension temporelle sont cruciales pour l'analyse et le reporting basés sur le temps.

### Data Slicing:

Pour cette étape, j'utilise Python et Pandas pour la création de sous-tables, car j'ai rencontré quelques difficultés avec l'utilisation de Pentaho DI. Dans ce processus, j'adopte un modèle mixte où je crée plusieurs tables à partir du grand dataframe. La table de dimension principale est celle des commandes (order), tandis que les autres tables sont des tables de faits (fact tables).

![[Untitled 6 3.png|Untitled 6 3.png]]

> [!important]  
> Pandas is a Python library used for data manipulation and analysis. It provides data structures and tools for working with structured data, such as data frames, which are similar to tables in a database.  

**Slicing Script Example:**

![[Untitled 7 3.png|Untitled 7 3.png]]

Après le découpage et la mise en forme des tables, voici le résultat final qui sera exporté vers des fichiers CSV pour alimenter le data warehouse avec ces tables.

![[Untitled 8 2.png|Untitled 8 2.png]]

J'utilise Pentaho DI pour l'alimentation de chaque table comme suit :

![[Untitled 9 2.png|Untitled 9 2.png]]

Notre Base de donnees apres l’alimentation:

![[Untitled 10 2.png|Untitled 10 2.png]]

## Reporting & Visualization:

Bien sûr, pour cette étape, nous pouvons utiliser des logiciels tels que Power BI et Pentaho Analytics. Cependant, j'ai rencontré des problèmes de compatibilité avec mon appareil, c'est pourquoi j'ai décidé d'utiliser Matplotlib, et d'autres analyses avec pandas et le connecteur MySQL pour se connecter à la base de données et l'utiliser avec pandas.

![[Untitled 1.jpeg]]

  

![[Untitled 11 2.png|Untitled 11 2.png]]

matplotlib

  

Cette example d’analyse fournit des informations clés pour l'entreprise en matière de ventes et de rentabilité. En comprenant les ventes par catégorie, le bénéfice par segment, le mode d'expédition le plus souvent associé à des remises avantageuses, les ventes moyennes par catégorie, le bénéfice maximum par sous-catégorie, les bénéfices totaux par région et les meilleurs clients, l'entreprise peut prendre des décisions stratégiques. Ces données permettent d'identifier les domaines à fort potentiel de croissance, d'optimiser les stratégies de tarification et de promotion, de cibler les segments de clients les plus rentables, et de maximiser la rentabilité globale de l'entreprise:

**Sales Per Category**

|   |   |   |
|---|---|---|
|index|Category|Sales|
|0|Furniture|1775353.5462|
|1|Office Supplies|1889360.964|
|2|Technology|2462358.425|

**Profit By Segment**

|   |   |   |
|---|---|---|
|index|Segment|Profit|
|0|Consumer|491099.35762|
|1|Corporate|299361.86303|
|2|Home Office|196626.02552|

Avg Discount By Ship Mode

|   |   |   |
|---|---|---|
|index|Ship_Mode|Discount|
|0|First Class|0.15815313056757443|
|1|Same Day|0.1485964935064935|
|2|Second Class|0.1439079817629179|
|3|Standard Class|0.1548402805453592|

Svg Sales By Category

|   |   |   |
|---|---|---|
|index|Category|Sales|
|0|Furniture|369.48044665972947|
|1|Office Supplies|122.77347222041718|
|2|Technology|463.54639024849394|

  

Max Profit By Subcategory

|   |   |   |
|---|---|---|
|index|Sub-Category|Profit|
|0|Accessories|829.3754|
|1|Appliances|793.716|
|2|Art|111.824|
|3|Binders|4946.37|
|4|Bookcases|374.6286|
|5|Chairs|770.352|
|6|Copiers|8399.976|
|7|Envelopes|204.0714|
|8|Fasteners|99.39215|
|9|Furnishings|272.792|
|10|Labels|126.3942|
|11|Machines|2799.984|
|12|Paper|352.296|
|13|Phones|1228.1787|
|14|Storage|792.2691|
|15|Supplies|327.506|
|16|Tables|610.8624|

Total Profit By Region

|   |   |   |
|---|---|---|
|index|Region|Profit|
|0|Central|188171.17452|
|1|East|298574.54086|
|2|South|155389.68965|
|3|West|344951.84114|

Top 10 Customers

|   |   |   |
|---|---|---|
|index|Customer_Name|Sales|
|708|Sean Miller|73558.302|
|753|Tamara Chand|57087.914000000004|
|638|Raymond Buch|45352.017|
|80|Becky Martin|45117.373999999996|
|780|Tom Ashbrook|43786.86|
|449|Ken Lonsdale|42056.663|
|693|Sanjit Chand|41545.682|
|6|Adrian Barton|41371.465000000004|
|340|Hunter Lopez|38473.114|
|694|Sanjit Engle|36040.694|

## Visualization:

![[Untitled 12.png]]

![[Untitled 13.png]]

![[Untitled 14.png]]

![[Untitled 15.png]]

![[Untitled 16.png]]

![[Untitled 17.png]]

![[Untitled 18.png]]

Ce graphique en nuage de points montre la relation entre les ventes et les bénéfices, permettant de visualiser la corrélation entre ces deux variables dans les données.

![[Untitled 19.png]]

Ce boxplot montre la répartition des ventes selon les segments de clients, offrant une vue des variations et tendances des ventes par segment.

![[Untitled 20.png]]

Ce graphique linéaire représente l'évolution des ventes au fil du temps, en utilisant la date des commandes comme variable temporelle, offrant ainsi une perspective temporelle sur les ventes.

![[Untitled 21.png]]

Ce violonplot illustre la distribution des bénéfices selon le mode de livraison, mettant en évidence la variation des bénéfices en fonction du mode de livraison utilisé.

## OLAP

Pour utiliser un cube OLAP avec votre modèle de données Mixte dans Pentaho Schema Workbench, suivez ces étapes :

1. **Création du Modèle de Données :**
    - j;ai utilise Pentaho Schema Workbench pour créer un schéma.
2. **Définition des Faits et des Mesures :**
3. **Création du Cube OLAP :**
    - À l'aide de Pentaho Schema Workbench, vous avez créé un cube OLAP en définissant les dimensions nécessaires et en les reliant aux tables correspondantes de votre schéma.
4. **Configuration des Hiérarchies :**
    - Pour chaque dimension, vous avez configuré des hiérarchies afin d'organiser les données de manière logique pour l'analyse (par exemple, hiérarchie de Date avec Année > Trimestre > Mois > Jour).
5. **Paramétrage des Propriétés du Cube :**
    
    configuré les propriétés du cube telles que les agrégations, les formats de mesure, etc., pour optimiser les performances et la convivialité de l'analyse.
    
    ### Requets MDX:
    
    **Total des Ventes par Année :**
    
    - `SELECT [Measures].[Sales] ON COLUMNS, [Date].[Year].MEMBERS ON ROWS FROM [orders]`
    - **Total des Ventes par Catégorie de Produit :**
    - `SELECT [Measures].[Sales] ON COLUMNS, [Category].[Category].MEMBERS ON ROWS FROM [orders]`
    - **Total des Ventes par Client et par Année :**
    
    `SELECT [Measures].[Sales] ON COLUMNS, [Customer].[Customer].MEMBERS ON ROWS, [Date].[Year].MEMBERS ON PAGES FROM [orders]`
    
    ## Resources:
    
    [https://www.kaggle.com/code/bahadir23/inventory-optimization-and-sustainability-analysis](https://www.kaggle.com/code/bahadir23/inventory-optimization-and-sustainability-analysis)
    
    [https://www.kaggle.com/datasets/winston56/fortune-500-data-2021](https://www.kaggle.com/datasets/winston56/fortune-500-data-2021)
    
    [https://www.kaggle.com/code/bahadir23/inventory-optimization-and-sustainability-analysis](https://www.kaggle.com/code/bahadir23/inventory-optimization-and-sustainability-analysis)
    
    ## Conclusion
    
    En conclusion, malgré les difficultés rencontrées avec certains outils de BI en raison de problèmes de compatibilité, j'ai réussi à mener à bien le processus de nettoyage, de formatage et de création de tables à l'aide de Pentaho DI, Python avec Pandas, et Matplotlib pour la visualisation. Ces étapes ont permis de réduire les données initiales de 30 000 à 25 000 lignes, et les tables résultantes ont été exportées avec succès vers des fichiers CSV pour alimenter le data warehouse, et de fait visualization et reporting.
    
    # TP01
    
    **1-**
    
    - **Startup:** Démarrage normal de la base de données.
    - **Startup nomount:** Démarrage de la base de données sans monter les fichiers de données.
    - **Startup mount:** Démarrage de la base de données et montage des fichiers de données, mais sans ouvrir la base.
    - **Startup force:** Démarrage forcé de la base de données, même si elle est en mode incompatible.
    
    **2-**
    
    - **Shutdown normal:** Arrêt normal de la base de données, avec fermeture propre des fichiers et transactions.
    - **Shutdown immediate:** Arrêt immédiat de la base de données, sans attendre la fin des transactions en cours.
    - **Shutdown transactional:** Arrêt de la base de données après la fin des transactions en cours.
    - **Shutdown abort:** Arrêt brutal de la base de données, avec perte des données non validées.
    
    **3-**
    
    ```Plain
    CONNECT / AS SYSDBA;
    SHUTDOWN NORMAL;
    ```
    
    4-
    
    ![[Untitled 2.jpeg]]
    
    5-
    
    ![[Untitled 3.jpeg]]
    
    6-
    
    ![[Untitled 4.jpeg]]
    
    7-
    
    ![[Untitled 5.jpeg]]
    
    10-
    
    ![[Untitled 6.jpeg]]
    
    11-
    
    ![[Untitled 7.jpeg]]
    
    12-
    
    ![[Untitled 8.jpeg]]
    
    13-
    
    ![[Untitled 9.jpeg]]
    
    ![[Untitled 22.png]]
    
    14-
    
    ![[Untitled 10.jpeg]]
    
    15-
    
    ![[Untitled 11.jpeg]]
    
    16-
    
    ![[Untitled 12.jpeg]]
    
    17-
    
    ![[Untitled 13.jpeg]]
    
    1-
    
    ![[Untitled 14.jpeg]]
    
    2-
    
    ![[Untitled 15.jpeg]]
    
    3-
    
    ![[Untitled 16.jpeg]]
    
    4-
    
    ![[Untitled 17.jpeg]]
    
    5-
    
    ![[Untitled 18.jpeg]]
    
    6-
    
    ![[Untitled 19.jpeg]]
    
    7-
    
    ![[Untitled 20.jpeg]]
    
    8-
    
    ![[Untitled 21.jpeg]]
    
    9-
    
    ![[Untitled 22.jpeg]]
    
    10-
    
    ![[Untitled 23.jpeg]]
    
    11-
    
    ![[Untitled 24.jpeg]]
    
    12-
    
    ![[Untitled 25.jpeg]]
    
    13-
    
    ![[Untitled 26.jpeg]]
    
    14-
    
    ![[Untitled 27.jpeg]]
    
    15-
    
    ![[Untitled 28.jpeg]]
    
    16-
    
    ![[Untitled 29.jpeg]]
    
    17-
    
    ![[Untitled 30.jpeg]]
    
    18-
    
    ![[Untitled 31.jpeg]]
    
    19-
    
    ![[Untitled 32.jpeg]]
    
    20-
    
    ![[Untitled 33.jpeg]]
    
    21-
    
    ![[Untitled 34.jpeg]]
    
    22-
    
    ![[Untitled 35.jpeg]]
    
    23-
    
    ![[Untitled 36.jpeg]]
    
    24-
    
    ![[Untitled 37.jpeg]]
    
    # TP2
    
    1-
    
    ![[Untitled 38.jpeg]]
    
    2-
    
    ![[Untitled 39.jpeg]]
    
    3-
    
    ![[Untitled 40.jpeg]]
    
    4-
    
    ![[Untitled 41.jpeg]]
    
    5-
    
    ![[Untitled 42.jpeg]]
    
    6-
    
    ![[Untitled 43.jpeg]]
    
    7-
    
    ![[Untitled 44.jpeg]]
    
    ![[Untitled 45.jpeg]]
    
    ![[Untitled 46.jpeg]]
    
    ![[Untitled 47.jpeg]]
    
    ![[Untitled 48.jpeg]]
    
    ![[Untitled 49.jpeg]]
    
    ![[Untitled 50.jpeg]]
    
    ![[Untitled 51.jpeg]]
    
    ![[Untitled 52.jpeg]]
    
    ![[Untitled 53.jpeg]]
    
    ![[Untitled 54.jpeg]]
    
    ![[Untitled 55.jpeg]]
    
    ![[Untitled 56.jpeg]]
    
    ![[Untitled 57.jpeg]]
    
    ![[Untitled 58.jpeg]]
    
    ![[Untitled 59.jpeg]]
    
    ![[Untitled 60.jpeg]]
    
    ![[Untitled 61.jpeg]]
    
    ![[Untitled 62.jpeg]]
    
    ![[Untitled 63.jpeg]]
    
    ![[Untitled 64.jpeg]]
    
    ![[Untitled 65.jpeg]]
    
    ![[Untitled 66.jpeg]]
    
    ![[Untitled 67.jpeg]]
    
    ![[Untitled 68.jpeg]]
    
    ![[Untitled 69.jpeg]]
    
    ![[Untitled 70.jpeg]]
    
    ![[Untitled 71.jpeg]]
    
    ![[Untitled 72.jpeg]]
    
    ![[Untitled 73.jpeg]]
    
    ![[Untitled 74.jpeg]]
    
    ![[Untitled 75.jpeg]]
    
    ![[Untitled 76.jpeg]]
    
    ![[Untitled 77.jpeg]]
    
    ![[Untitled 78.jpeg]]
    
    ![[Untitled 79.jpeg]]
    
    ![[Untitled 80.jpeg]]
    
    ![[Untitled 81.jpeg]]
    
    ![[Untitled 82.jpeg]]
    
    ![[Untitled 83.jpeg]]