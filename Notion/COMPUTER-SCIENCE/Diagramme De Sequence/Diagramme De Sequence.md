## Comment ?

- Les diagrammes de cas d’utilisation modélisent à QUOI sert le  
    système, en organisant les interactions possibles avec les acteurs.  
    
- Les diagrammes de classes permettent de spécifier la structure et les liens entre les objets dont le système est composé : ils spécifie  
    QUI sera à l’oeuvre dans le système pour réaliser les fonctionnalités  
    décrites par les diagrammes de cas d’utilisation.  
    
- Les diagrammes de séquences permettent de décrire COMMENT les éléments du système interagissent entre eux et avec les acteurs :
    - Les objets au coeur d’un système interagissent en s’échangent des messages.
    - Les acteurs interagissent avec le système au moyen d’IHM (Interfaces Homme-Machine).

![[Untitled 32.png|Untitled 32.png]]

  

### Ligne de vie:

Une ligne de vie représente un participant à une interaction (objet ou acteur). La syntaxe de son libellé est : `nomLigneDeVie {[selecteur]}: NomClasseOuActeur`

Une ligne de vie est une instance, donc il y a nécessairement les _deux points_ (_:_) dans son libellé.

Dans le cas d’une collection de participants, un sélecteur permet de choisir un objet parmi n (par exemple `objets[2]`).

![[Untitled 1 11.png|Untitled 1 11.png]]

### **Messages:**

Les principales informations contenues dans un diagramme de séquence sont les messages échangés entre les lignes de vie :

- Ils sont représentés par des flèches
- Ils sont présentés du haut vers le bas le long des lignes de vie, dans un ordre chronologique

Un message définit une communication particulière entre des lignes de vie (objets ou acteurs).

Plusieurs types de messages existent, dont les plus courants :

- l’envoi d’un signal ;
- l’invocation d’une opération (appel de méthode) ;
- la création ou la destruction d’un objet.

La réception des messages provoque une période d’activité (rectangle  
vertical sur la ligne de vie) marquant le traitement du message  
(spécification d’exécution dans le cas d’un appel de méthode).  

## Messages synchrones et asynchrones

Un message _synchrone_ bloque l’expéditeur jusqu’à la réponse du destinataire. Le flot de contrôle passe de l’émetteur au récepteur.

- Si un objet A envoie un message synchrone à un objet B, A reste bloqué tant que B n’a pas terminé.
- On peut associer aux messages d’appel de méthode un message de  
    retour (en pointillés) marquant la reprise du contrôle par l’objet  
    émetteur du message synchrone.  
    

Un message _asynchrone_ n’est pas bloquant pour l’expéditeur. Le message envoyé peut être pris en compte par le récepteur à tout moment ou ignoré.

![[Untitled 2 9.png|Untitled 2 9.png]]

### Creation Ou Destruction D’un Objet:

![[Untitled 3 9.png|Untitled 3 9.png]]

### Message Réflexif:

![[Untitled 4 9.png|Untitled 4 9.png]]

### Message Alternatif:

![[Untitled 5 7.png|Untitled 5 7.png]]

![[Untitled 6 6.png|Untitled 6 6.png]]

### Boucle:

![[Untitled 7 6.png|Untitled 7 6.png]]

### **Référence à un autre diagramme:**

![[Untitled 8 5.png|Untitled 8 5.png]]

![[Untitled 9 4.png|Untitled 9 4.png]]

![[Untitled 10 4.png|Untitled 10 4.png]]

![[Untitled 11 4.png|Untitled 11 4.png]]

![[Untitled 12 3.png|Untitled 12 3.png]]

![[Untitled 13 2.png|Untitled 13 2.png]]