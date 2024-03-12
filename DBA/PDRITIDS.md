## Procédure d'exécution d'une requête d'interrogation et d'une transaction et interaction du serveur :

**Requête d'interrogation:**

**1. Parsing (Analyse syntaxique):**

- Le serveur reçoit la requête du client et vérifie sa syntaxe.
- Il s'agit de s'assurer que la requête est correctement formulée et qu'elle respecte les règles du langage SQL.
- En cas d'erreur de syntaxe, le serveur renvoie un message d'erreur au client.

**2. Analyse:**

- Le serveur analyse la requête pour déterminer son sens et son objectif.
- Il identifie les tables, les colonnes et les fonctions impliquées dans la requête.
- Le serveur détermine également l'ordre d'exécution des opérations de la requête.

**3. Exécution:**

- Le serveur accède aux données des tables et des colonnes spécifiées dans la requête.
- Il calcule les résultats des fonctions et des expressions.
- Le serveur génère un ensemble de résultats qui contient les données demandées.

**4. Retour des résultats:**

- Le serveur envoie l'ensemble de résultats au client.
- Le client peut ensuite afficher, traiter ou stocker les résultats.

**Transaction:**

**1. Début de la transaction:**

- Le client envoie une demande au serveur pour démarrer une transaction.
- La transaction est un ensemble d'opérations qui doivent être exécutées de manière atomique, c'est-à-dire que toutes les opérations doivent réussir ou échouer ensemble.

**2. Exécution des opérations:**

- Le serveur exécute les opérations de la transaction, comme l'insertion, la mise à jour ou la suppression de données.
- Il peut y avoir plusieurs opérations dans une transaction.

**3. Validation ou annulation:**

- Si toutes les opérations de la transaction se déroulent correctement, la transaction est validée et les modifications sont permanentes.
- Si une erreur survient pendant l'exécution d'une opération, la transaction est annulée et toutes les modifications apportées aux données sont annulées.

**Interaction du serveur:**

- Le serveur agit comme un intermédiaire entre le client et la base de données.
- Il reçoit les requêtes du client, les traite et renvoie les résultats ou les confirmations de transaction.
- Le serveur gère également l'accès aux données et garantit la cohérence et l'intégrité de la base de données.

**Points importants:**

- Les requêtes d'interrogation et les transactions peuvent être exécutées simultanément par plusieurs utilisateurs.
- Le serveur utilise des mécanismes de verrouillage pour garantir l'intégrité des données pendant les transactions.
- Les transactions peuvent être imbriquées les unes dans les autres.

**Exemple:**

Un utilisateur souhaite transférer 100 € de son compte courant vers son compte d'épargne. Il envoie une requête au serveur pour démarrer une transaction. La transaction effectue deux opérations :

1. Débiter 100 € du compte courant.
2. Créditer 100 € sur le compte d'épargne.

Si les deux opérations réussissent, la transaction est validée et les modifications sont permanentes. Si une erreur survient pendant l'une des opérations, la transaction est annulée et aucune modification n'est apportée aux comptes.

**Diagramme:**

Diagramme d'interaction requête/transaction/serveur: [https://www.linguee.fr/francais-anglais/traduction/non+valide.html](https://www.linguee.fr/francais-anglais/traduction/non+valide.html)

**En résumé:**

Le serveur joue un rôle crucial dans l'exécution des requêtes d'interrogation et des transactions. Il assure la communication entre le client et la base de données, gère l'accès aux données et garantit l'intégrité et la cohérence de la base de données.

**Parsing, analyse et fetch:**

- Le parsing et l'analyse font partie du processus d'exécution d'une requête d'interrogation.
- Le parsing vérifie la syntaxe de la requête, tandis que l'analyse détermine son sens et son objectif.
- Le fetch est l'étape suivante après l'exécution de la requête.
- Le serveur récupère les données des tables et des colonnes spécifiées dans la requête et les envoie au client.