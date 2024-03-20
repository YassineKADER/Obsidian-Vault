# Domaine vs Groupe de travail
- **Groupe de travail** n'est pas égal à **Domaine**.
- **Domaine** implique **Matériel + Serveur (gestion centralisée)**.

## Active Directory (AD)
- AD est un service d'annuaire qui permet une gestion centralisée des données.
- **Contrôleur de domaine (CD)** : C'est un serveur qui exécute Active Directory.
- **DNS** : Nécessaire pour localiser les ressources.

## Objets dans AD
- Utilisateurs, groupes d'utilisateurs, réseaux IP, Sites, Serveurs, etc.

## Unité d'organisation (OU)
- Un conteneur (Dossier) qui permet d'ajouter des utilisateurs, des groupes, des comptes d'ordinateurs, et d'appliquer des droits d'accès (Objet de stratégie de groupe : GPO).

## Groupe
- C'est un groupe d'utilisateurs, ayant les mêmes droits, sur lequel on applique des politiques de groupe.
- Types de groupes :
  - **Groupe de sécurité** : Un groupe normal qui contient des utilisateurs que nous pouvons créer.
  - **Groupe de distribution** : Un groupe de messagerie.
- Niveaux de portée des groupes :
  - Local
  - Global au sein d'un arbre ou d'une forêt
  - Universel au sein d'une forêt ou de plusieurs forêts

## Site
- Un ensemble de contrôleurs connectés entre eux.

## Réplication
- Une copie de données d'un serveur ou DC.

## Relation de confiance
- Les relations qui lient les domaines et les forêts entre eux (automatique au sein de la même forêt entre un domaine et un domaine enfant, (manuel) non automatique entre les forêts).

# DC Promo
- **Niveau fonctionnel de la forêt** : Ancien ou nouveau mais dans une nouvelle installation, nous devons choisir le plus récent ou en fonction de ce dont nous aurons besoin sur le DC.
- **NTDS** : C'est le fichier qui contient toutes les informations liées aux objets, etc.

# Rôles et Fonctionnalités
- Rôles : DHCP, IIS, DNS, etc.
- Fonctionnalités : Ajouter des fonctionnalités comme le téléchargement, etc.
- Pourquoi avons-nous besoin de migrer vers l'utilisation de domaine ? Pour la gestion centralisée.

# Étapes pour joindre un PC à un domaine
1. Il doit être connecté au réseau.
2. Il a besoin d'une adresse IP.
3. Il a besoin d'une adresse DNS (si le serveur est loin).
4. Il a besoin d'une passerelle.
5. Migration du groupe de travail vers le domaine.
- Nous créons des groupes pour appliquer des droits communs aux membres du groupe.

# Bureau à distance
- Démarrer > Outil d'administration > Gestion du serveur > Bureau à distance
- Création de dossiers partagés + sécurisés seul l'utilisateur peut y accéder.

# Lecteur réseau
- Il permet d'accéder à un dossier via un lecteur.
- Utilisateurs/profil/connecter/<chemin du dossier partagé/%username%>
- Profil : Environnement d'un utilisateur (documents, images, etc...)
  - Mobile | Itinérant
  - Local
  - Obligatoire : Mobile mais obligatoire lorsque nous changeons dans le profil lors de la déconnexion, le profil revient à l'état initial

# Différence entre GPO Appliqué sur Utilisateur ou Ordinateur
- Utilisateur : Juste sur le profil de l'utilisateur.
- Ordinateur : Sur tous les comptes connectés.
- Forcer la mise à jour : gpupdate /force
