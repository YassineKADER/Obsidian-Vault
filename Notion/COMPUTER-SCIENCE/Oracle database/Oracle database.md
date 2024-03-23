- ==**R**==_==**esources:**==_
    
    [https://docs.oracle.com/cd/E17781_01/server.112/e18804/memory.htm#ADMQS181](https://docs.oracle.com/cd/E17781_01/server.112/e18804/memory.htm#ADMQS181)
    
    [https://indico.cern.ch/event/36804/attachments/731758/1003980/oracleArchitecture.pdf](https://indico.cern.ch/event/36804/attachments/731758/1003980/oracleArchitecture.pdf)
    
    [https://docs.oracle.com/database/121/ADMQS/GUID-78E9CAFD-D0AD-4E2E-9B73-D2AA1CF22772.htm](https://docs.oracle.com/database/121/ADMQS/GUID-78E9CAFD-D0AD-4E2E-9B73-D2AA1CF22772.htm)
    
      
    

Oracle Database is a multi-model database management system produced and marketed by Oracle Corporation. It is a database commonly used for running online transaction processing, data warehousing and mixed database workloads.

## Oracle data base components :

![[Untitled 23.png|Untitled 23.png]]

## _The oracle database:_

•An Oracle Database consists of at least one database instance and one database. The database instance handles memory and processes. The database consists of physical files called data files, and can be a non-container database or a multitenant container database. An Oracle Database also uses several database system files during its operation.

**_==The Oracle Real Application Clusters==_**_==:==_

Oracle Real Application Clusters (RAC) allow customers to run a single Oracle Database across multiple servers in order to maximize availability and enable horizontal scalability, while accessing shared storage.

## The listener:

The listener is a database server process. It receives client requests, establishes a connection to the database instance, and then hands over the client connection to the server process. The listener can run locally on the database server or run remotely. Typical Oracle RAC environments are run remotely

L'écouteur est un processus de serveur de base de données. Il reçoit les demandes des clients, établit une connexion à l'instance de base de données, puis transmet la connexion client au processus serveur.

## The Oracle Instance:

a set of memory and process structures, running on a specific computer.

This is the point of access for clients, and the instance is responsible for translating the SQL calls given by the client, to actual data transfers to and from the database stored in the operating system files.

- ==An Oracle instance is normally associated with an Oracle database.two together make up the Oracle Server.==
- ==An Oracle instance may exist without being associated with an Oracle database eg:==
    
    ==_the case before the database is created or as an intermediate step during the startup of the Oracle server._==
    
- ==An instance cannot be associated with more than one database.==
- ==But one database (on a set of physical disks), can be associated with multiple instances (each on a separate computer),==
    
    if the actual hardware configuration allow multiple computers to concurrently access a single set of disks.
    
    > [!important]  
    > Oracle Database XE uses Automatic Memory Management which usually provides the best memory configuration based on your resources and workload. Do not set any memory-related parameters unless you fully understand the consequences.  
      
    > [!important]  
    > There are two types of memory that the Oracle instance allocates:  
    
    ## **SGA Components:**
    
    - System global area (SGA) A shared memory area that contains data buffers and control information for the instance. The SGA is divided into separate buffer areas and data pools.
        
        ![[Untitled 1 4.png|Untitled 1 4.png]]
        
    
    |Component|Description|
    |---|---|
    |Buffer cache|The buffer cache is the component of the SGA that acts as the buffer to store any data being queried or modified. All clients connected to the database share access to the buffer cache. The buffer cache helps avoid repeated access from the physical disk, a time-consuming operation.|
    |Shared pool|The shared pool caches operational information and code that can be shared among users. For example:  <br>  <br>-  <br>_SQL statements are cached so that they can be reused._  <br>  <br>  <br>-  <br>_Information from the data dictionary, such as user account data, table and index descriptions, and privileges, is cached for quick access and reusability._  <br>  <br>-  <br>_Stored procedures are cached for faster access._|
    |Redo log buffer|The redo log buffer improves performance by caching redo information (used for instance recovery) until it can be written at once and at a more opportune time to the physical redo log files that are stored on disk.|
    |Large pool|The large pool is an optional area that is used for buffering large I/O requests for various server processes.|
    
    - La zone de programme global (PGA) est une région mémoire qui contient des données et des informations de contrôle pour un processus serveur. C'est une mémoire non partagée créée par la base de données Oracle lorsqu'un processus serveur est démarré. L'accès à la PGA est exclusif au processus serveur. Il y a une PGA pour chaque processus serveur. Les processus en arrière-plan allouent également leur propre PGA. La mémoire PGA totalement allouée pour tous les processus serveur et en arrière-plan attachés à une instance de base de données Oracle est appelée mémoire PGA totale de l'instance, et l'ensemble de toutes les PGA individuelles est appelé PGA totale de l'instance, ou simplement PGA de l'instance.
        
        -The PGA is used to process SQL statements and to hold logon and other session information. A large part of the PGA is dedicated to SQL work areas, which are working memory areas for sorts and other SQL operations.
        
        -The amount of PGA memory used and the contents of the PGA depend on whether the instance is running in dedicated server or shared server mode.
        
    
    [![](https://docs.oracle.com/cd/E17781_01/server.112/e18804/img/xedba002.gif)](https://docs.oracle.com/cd/E17781_01/server.112/e18804/img/xedba002.gif)
    
    Memory Allocation in Oracle Database
    
    ## Table spaces and data files:
    
      
    

![[Untitled 2 4.png|Untitled 2 4.png]]

### wath is tablespace ?

Un _tablespace_ est un espace logique qui contient les objets stockés dans la base de données comme les tables ou les index.

![[Untitled 3 4.png|Untitled 3 4.png]]

  

![[Untitled 4 4.png|Untitled 4 4.png]]

## **La connexion client/****serveur**

- **Mode dédié** : une processus **serveur** pour un processus client.
- **Mode partagé** : les clients partagent un groupe de processus **serveurs**. Evite les processus **serveurs** inactifs.

L'optimiseur compare les plans et choisit le plan avec le coût le plus bas. La sortie de l'optimiseur est un plan d'exécution qui décrit la méthode d'exécution optimale. Les plans montrent la combinaison des étapes qu'Oracle Database utilise pour exécuter une instruction SQL.

SOME ROLES:

- **The CONNECT role was originally intended to allow users to log in to the database**. In versions of Oracle before version 6, the CONNECT privilege enabled a user to create a session in a database and allowed little else.
- The RESOURCE role **grants a user the privileges necessary to create procedures, triggers and, in Oracle8, types within the user's own schema area**. Granting a user RESOURCE without CONNECT, while possible, does not allow the user to log in to the database.

# DATA UNITES

Un _tablespace_ est un espace logique qui contient les objets stockés dans la base de données comme les tables ou les index.

Un tablespace est composé d'au moins un datafile, c'est-à-dire un fichier de données qui est physiquement présent sur le serveur à l'endroit stipulé lors de sa création.

Chaque datafile est constitué de segments d'au moins un extent (ou page) lui-même constitué d'au moins 3 blocs : l'élément le plus petit d'une base de données.

L'extent n'a aucune signification particulière, c'est juste un groupe de blocs contigus pouvant accueillir des données, nous verrons néanmoins que cette notion d'extent peut poser des problèmes de gestion d'espace disque.

# Voici la hiérarchie des unités de stockage dans le système de gestion de base de données Oracle (DMS), de la plus grande à la plus petite :

1. Tablespace : un tablespace est une unité de stockage logique qui contient un ou plusieurs fichiers de données. Un tablespace est utilisé pour regrouper des objets liés, tels que des tables et des indexes, afin de faciliter leur gestion.
2. Fichier de données : un fichier de données est un fichier physique sur le disque dur du serveur qui stocke les données pour un tablespace. Un tablespace peut contenir plusieurs fichiers de données.
3. Segment : un segment est une unité de stockage logique utilisée pour stocker un type de données spécifique, comme une table, un index ou un lob (objet large). Un segment est composé d'un ou plusieurs extents, qui sont à leur tour composés de blocks.
4. Extent : Un extent est une unité de stockage physique qui contient plusieurs blocs de données.
5. Block : un block est la plus petite unité de stockage dans un DMS Oracle. C'est l'unité de base de stockage et de récupération de données. Un block est généralement composé de plusieurs lignes de données.

En résumé, les unités de stockage dans un DMS Oracle sont organisées en une hiérarchie allant de la plus grande unité (tablespace) à la plus petite (block). Un tablespace contient un ou plusieurs fichiers de données, qui contiennent à leur tour des extents, qui sont composés de blocks. Un segment est une unité de stockage logique utilisée pour stocker un type de données spécifique et est composé d'un ou plusieurs extents.