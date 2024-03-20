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
- C'est un groupe d'utilisateurs, ayant les mêmes droits, sur lequel on applique des politiques de groupe (Objet de stratégie de groupe : GPO).
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


**Contrôleurs de domaines** : Dans un domaine, tous les contrôleurs de domaine participent à la réplication et contiennent une copie complète de toutes les informations d’annuaire liées à leur domaine1. Toute modification des données d’annuaire est répliquée sur tous les contrôleurs de domaine inclus dans le domaine1.

**Liaisons entre sites** : Pour configurer un déploiement multisite, plusieurs étapes sont nécessaires pour modifier les paramètres d’infrastructure réseau, notamment : configuration de sites Active Directory et de contrôleurs de domaine supplémentaires, configuration de groupes de sécurité supplémentaires et configuration d’objets de groupe stratégie de groupe (GPO) si vous n’utilisez pas d’objets de stratégie de groupe configurés automatiquement

# GPO
**Un Objet de stratégie de groupe (GPO)** est un ensemble de paramètres créés à l’aide de l’éditeur de stratégie de groupe de la console de gestion Microsoft (MMC). Les GPO peuvent être associés à un ou plusieurs conteneurs Active Directory, y compris des sites, des domaines ou des unités organisationnelles (OU).
**Les GPO** vous permettent d’appliquer les mêmes paramètres à tous les utilisateurs et ordinateurs dans un domaine Active Directory en fournissant un ensemble de règles et de paramètres pour l’environnement Windows.Cela vous permet de gérer et de configurer de manière centralisée les systèmes d’exploitation, les utilisateurs et les applications.
# Les types des profiles:
**Profil local** : Un profil local est créé la première fois qu’un utilisateur se connecte à un ordinateur. Le profil est stocké sur le disque dur local de l’ordinateur. [Les modifications apportées au profil local sont spécifiques à l’utilisateur et à l’ordinateur sur lequel les modifications sont effectuées]

**Profil itinérant (mobile)** : Un profil utilisateur itinérant est une copie du profil local qui est copiée et stockée sur un partage de serveur. Ce profil est téléchargé sur n’importe quel ordinateur sur lequel un utilisateur se connecte sur un réseau. Les modifications apportées à un profil utilisateur itinérant sont synchronisées avec la copie du serveur du profil lorsque l’utilisateur se déconnecte. [L’avantage des profils utilisateurs itinérants est que les utilisateurs n’ont pas besoin de créer un profil sur chaque ordinateur qu’ils utilisent sur un réseau]

**Profil obligatoire** : Un profil utilisateur obligatoire est un type de profil que les administrateurs peuvent utiliser pour spécifier des paramètres pour les utilisateurs. Seuls les administrateurs système peuvent apporter des modifications aux profils utilisateurs obligatoires. [Les modifications apportées par les utilisateurs aux paramètres du bureau sont perdues lorsque l’utilisateur se déconnecte]

## Other Things:

- **Domaine** : Un domaine est une limite administrative dans laquelle un serveur qui exécute Microsoft Active Directory fournit des services d'annuaire. Les domaines sont généralement configurés en fonction des besoins de gestion de votre organisation.

- **Sous-domaine** : Un sous-domaine est un domaine qui fait partie d'un domaine plus grand dans le système de noms de domaine (DNS) hiérarchique. Par exemple, "sales.example.com" est un sous-domaine du domaine "example.com".

- **Forêt** : Une forêt est une collection de domaines qui partagent un catalogue global, une configuration de schéma et une configuration de domaine. Les forêts permettent aux organisations de regrouper et d'administrer plusieurs domaines.

- **Arborescence** : Une arborescence est une hiérarchie de domaines dans Active Directory. Chaque arborescence partage un seul schéma de domaine, qui définit les objets et les attributs qui peuvent être créés dans Active Directory.

- **Contrôleur de domaine (DC)** : Un contrôleur de domaine est un serveur qui exécute une version du système d'exploitation Windows Server et a Active Directory Domain Services installé. Lorsqu'un serveur devient un contrôleur de domaine, il contient une copie complète de tous les objets du domaine et contrôle les modifications apportées à ces objets.

- **Active Directory (AD)** : Active Directory est un service d'annuaire qui identifie tous les éléments d'un réseau. Il permet aux administrateurs de gérer les éléments du réseau et les utilisateurs de se connecter à des ressources réseau.