### Types de Tablespaces
- **Tablespaces permanents :**
  - Stockent des données persistantes.
  - Exemples : `(DATA)`, `(USERS)`.
- **Tablespaces temporaires :**
  - Stockage de données temporaire.
  - Exemples : `(TEMP)`.
- **Tablespaces d'annulation :**
  - Stockent les informations d'annulation des transactions.
  - Exemples : `(UNDOTBS)`.
### Création des Tablespaces
- **Création de Tablespace Permanent :**
  ```sql
  CREATE TABLESPACE nom_tablespace
  DATAFILE 'chemin_vers_fichier' TAILLE taille;```
- Création de Tablespace Temporaire :
```SQL
CREATE TEMPORARY TABLESPACE nom_tablespace
TEMPFILE 'chemin_vers_fichier' SIZE taille;
```
- Création de Tablespace d'Annulation :
```SQL
CREATE UNDO TABLESPACE nom_tablespace_annulation
DATAFILE 'chemin_vers_fichier' SIZE taille;
```

### Attribution des Tablespaces
- Attribution de Tablespace Permanent :
```SQL
ALTER USER nom_utilisateur DEFAULT TABLESPACE nom_tablespace;
```
- Attribution de Tablespace Temporaire :
```SQL
ALTER USER nom_utilisateur TEMPORARY TABLESPACE nom_tablespace;
```
- Attribution de Tablespace Undo:
```sql
ALTER SYSTEM SET UNDO_TABLESPACE = undo_tablespace_name;
```
### Gestion des Tablespaces
- Modification des Tablespaces :
```SQL
ALTER DATABASE DATAFILE '/path/to/datafile.dbf' RESIZE 100M;
ALTER DATABASE DATAFILE '/path/to/datafile.dbf' AUTOEXTEND ON MAXSIZE 200M;
ALTER TABLESPACE nom_tablespace RENAME TO new_name;
ALTER TABLESPACE nom_tablespace {ADD|DELETE} DATAFILE 'chemin_vers_fichier' SIZE 100M;
```
- Suppression des Tablespaces :
```SQL
DROP TABLESPACE nom_tablespace;
DROP TABLESPACE <tablespace_name> INCLUDING CONTENTS AND DATAFILES;
```
- Surveillance des Tablespaces :
```SQL
SELECT * FROM DBA_TABLESPACES;
```
### Opérations supplémentaires
- Ajout de Fichiers de Données :
```SQL
ALTER TABLESPACE nom_tablespace ADD DATAFILE 'chemin_vers_fichier' TAILLE taille;
```
- Redimensionnement des Fichiers de Données :
```SQL
ALTER DATABASE DATAFILE 'chemin_vers_fichier' RESIZE taille;
```
- Tablespace par Défaut

```SQL
SELECT PROPERTY_NAME, PROPERTY_VALUE
FROM DATABASE_PROPERTIES
WHERE PROPERTY_NAME LIKE '%DEFAULT%';
```