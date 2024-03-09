## Tablespaces Cheat Sheet

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
DATAFILE 'chemin_vers_fichier' TAILLE taille;

CREATE TEMPORARY TABLESPACE nom_tablespace
TEMPFILE 'chemin_vers_fichier' TAILLE taille;

--Création de Tablespace d'Annulation :
CREATE UNDO TABLESPACE nom_tablespace_annulation
DATAFILE 'chemin_vers_fichier' TAILLE taille;

--Attribution des Tablespaces

--Attribution de Tablespace Permanent :
ALTER USER nom_utilisateur DEFAULT TABLESPACE nom_tablespace;

--Attribution de Tablespace Temporaire :
ALTER USER nom_utilisateur TABLESPACE TEMPORAIRE nom_tablespace;

--Gestion des Tablespaces

--Modification des Tablespaces :
ALTER TABLESPACE nom_tablespace {AJOUTER|SUPPRIMER} DATAFILE 'chemin_vers_fichier';

--Suppression des Tablespaces :

DROP TABLESPACE nom_tablespace;

Surveillance des Tablespaces :

sql

    SELECT * FROM DBA_TABLESPACES;

Opérations supplémentaires

    Ajout de Fichiers de Données :

    sql

ALTER TABLESPACE nom_tablespace AJOUTER DATAFILE 'chemin_vers_fichier' TAILLE taille;

Redimensionnement des Fichiers de Données :

sql

    ALTER DATABASE DATAFILE 'chemin_vers_fichier' REDIMENSIONNER taille;

Tablespace par Défaut

Pour afficher les tablespaces par défaut existants :

sql

SELECT PROPERTY_NAME, PROPERTY_VALUE
FROM DATABASE_PROPERTIES
WHERE PROPERTY_NAME LIKE '%DEFAULT%';
```