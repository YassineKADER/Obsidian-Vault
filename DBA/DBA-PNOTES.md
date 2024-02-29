## Architecture Oracle :

### Serveur Oracle :

Un serveur Oracle est composé d'une instance Oracle et d'une base de données Oracle.

**Instance Oracle :** La combinaison des processus d'arrière-plan et des structures mémoire. Il est nécessaire de démarrer l'instance pour accéder aux données de la base.

**Base de données Oracle :** Constituée de fichiers système, appelés fichiers de base de données, qui stockent physiquement les données de la base.

### Processus Utilisateur :

- Processus Serveur
- Processus d'Arrière-plan (DBWn, LGWR, PMON, CKPT, SMON)
- Processus d'Écoute

### Structure Mémoire :

**SGA (System Global Area) :** Stocke les informations partagées par les processus de la base de données.

- Shared Pool
- Database Buffer Cache (Cache de données)
- Redo Log Buffer (Cache de reprise)
- Large Pool
- Zone de Mémoire Java

**PGA (Program Global Area) :** Mémoire réservée à chaque processus utilisateur.

### Gestion des Utilisateurs :

- Création d'Utilisateurs
- Modification de Mot de Passe
- Activation/Verrouillage de Compte
- Assignation de Profils

### Gestion des Privilèges :

- Privilèges Système
- Privilèges d'Objet
- Création de Rôles
- Attribution de Privilèges et de Rôles
- Révocation de Privilèges et de Rôles

### Base de Données Oracle :

- Démarrage :
    - Nomount
    - Mount
    - Open
- Arrêt :
    - Shutdown Immediate
    - Shutdown Transactional
    - Shutdown Normal
    - Shutdown Abort

### SQL Queries :

- Accord de Permissions
- Création de Rôles
- Attribution de Privilèges aux Rôles
- Attribution de Rôles aux Utilisateurs
- Gestion de la Privatisation de Colonnes

### Options de Démarrage :

- Démarrage Normal
- Démarrage sans Montage
- Montage de la Base de Données
- Démarrage Forcé

### Gestion de la Mémoire :

- Paramètres dans `init.ora`
- SGA (Vue d'ensemble et commandes)
- PGA (Vue d'ensemble et commandes)
- **Shutdown Options**:
    - Abort: `SHUTDOWN ABORT;`
    - Immediate: `SHUTDOWN IMMEDIATE;`
    - Transactional: `SHUTDOWN TRANSACTIONAL;`
    - Normal: `SHUTDOWN NORMAL;`
- **SQL Queries**:
    - Granting Permissions:
        - `GRANT UPDATE (column_name) ON table_name TO user_name;`
        - `GRANT INSERT (column1, column2) ON table_name TO user_name;`
    - Creating Roles: `CREATE ROLE role_name;`
    - Granting Privileges to Roles: `GRANT privilege_name ON object_name TO role_name;`
    - Granting Roles to Users: `GRANT role_name TO user_name;`
- **Startup Options**:
    - Normal startup: `STARTUP;`
    - Startup without mounting: `STARTUP NOMOUNT;`
    - Mount the database: `STARTUP MOUNT;`
    - Forceful startup: `STARTUP FORCE;`
- **User Management**:
    - Creating Users: `CREATE USER username IDENTIFIED BY password;`
    - Revoking Privileges: `REVOKE privilege_name ON object_name FROM user_name;`
    - Revoking Roles from Users: `REVOKE role_name FROM user_name;`
    - Granting Column-level Privileges: `GRANT privilege_name (column_name) ON table_name TO user_name;`
- **PGA and SGA**:
    - Setting Parameters in `init.ora`:
        - `SGA_TARGET=500M;`
        - `PGA_AGGREGATE_TARGET=200M;`
- **Oracle Architecture**:
    - Viewing Memory Structures:
        - `SELECT * FROM V$SGA;`
        - `SELECT * FROM V$PGA;`
    - Viewing Background Processes:
        - `SELECT * FROM V$PROCESS;`
        - `SELECT * FROM V$SESSION;`
