- Something
    
    # Séquence de démarrage du commutateur:
    
    1. Execute le programme **POST (Power-On Self Test)** le but et de tester le **CPU, ROM, RAM** et d’autre periphirique.
    2. Le commutateur exécute le bootloader. Le bootloader est un petit programme stocké dans le mémoire morte et exécuté immédiatement après le réeussite de **POST.**
    3. Initialiser les registeres du processeur qui controlent l’emplacement auquel le mémoire phisique est mappée.
    4. Le bootloader initialise le sysème de fichiers flash sur la carte système.
    5. Enfin, il localise et charge une image de logiciel du **OS IOS** par défaut dans le mémoire et transfère le controle du commutateur a l’ios.
    
    ## Duplex Mode:
    
    **Half-duplex:**
    
    - est un flux de données unidirectionnel, ce qui signifie que les données ne peuvent fonctionner que dans une seule direction à la fois.
        
        > L’envoi et la réception de données ne se font pas en même temps.
        
        **C’est similaire à une communication avec des talkiewalkies**, ou seule une personne peut parler à la fois.
        
        Étant donné que les données peuvent circuler que dans un seul sens, chaque périphérique dans un système **half-duplex** doit constamment attendre son tour pour transmettre des données. **Ce qui provoque des problèmes de performance.**
        
        > Ce sont plutôt les anciens matériels comme les hubs qui fonctionnent en half-duplex.
        
        > Dans ce mode, si un périphérie transmet en même temps qu’un autre, alors une collision se produit.
        
        Pour palier à ce problème, il existe une fonctionnalité qui s’appelle : **|CSMA /CD.** En français ça se traduit par : **circuit de détection de collision.**
        
        Ça permet de réduire les risques de collisions, car il va bloquer les PC’s qui posent problème pendant une période aléatoire avant qu’ils puissent retransmettre.
        
    
    [![](https://w3p6c7f9.rocketcdn.me/wp-content/uploads/2019/09/full-duplex-half-duplex-3.png)](https://w3p6c7f9.rocketcdn.me/wp-content/uploads/2019/09/full-duplex-half-duplex-3.png)
    
    ![[Untitled 24.png|Untitled 24.png]]
    
    **FULL-duplex:**
    
    - **C’est comme une communication téléphonique,** car chaque personne peut parler et entendre ce que l’autre personne dit simultanément.Le flux de données est donc bidirectionnel.
        
        Les données peuvent être envoyées et reçues en même temps. La plupart des cartes réseau qui sont vendues aujourd’hui sont en **full-duplex.**
        
        Si deux périphériques à chaque extrémité sont en full duplex, **|**alors , la méthode qui permettait de limiter les collisions, le CSMA/CD, sera désactivée.  
        Voyons maintenant sa configuration.  
          
        
        ![[Untitled 1 5.png|Untitled 1 5.png]]
        
        **La commande « duplex** » permet de configurer soit en half duplex / en full duplex ou en Auto.
        
        > L’option Auto définit une autonégociation entre les deux extrémités.
        
        L’image montre l’ exemple d’une configuration duplex et de vitesse, sur les interfaces Fast Ethernet des deux switchs.
        
        Pour éviter les problèmes d’incompatibilité, chaque extrémité doit être configurée à l’identique.
        
        **|Dans cet exemple, les ports Fast Ethernet 0/5 et 0/3,** ceux qui sont connectés directement à un PC, sont configurés en full duplex avec une vitesse de **100 mégas.**
        
        **|Et les ports entre les 2 switchs** sont en mode auto, pour le duplex et la vitesse, de cette manière les switchs négocieront automatiquement ces deux paramètres.
        
        ![[Untitled 2 5.png|Untitled 2 5.png]]
        
        **Et pour finir, la commande show interfaces,** en mode privilège, permet de vérifier les paramètres de duplex sur chaque switch.
        
        Cette commande affiche des stats et des états sur les interfaces du switch.
        
    
    ![[Untitled 3 5.png|Untitled 3 5.png]]
    
    # Les modes de configuration d’un commutateur:
    
    `switch>` | mode utilisateur
    
    `switch#` | mode préviligié
    
    `switch(config)#` | mode de configuration globale
    
    `switch(config-if)#` | mode de configuration d’interface
    
    `switch(config-vlan)#` | mode de configuration de **vlan**
    
    `switch(config-line)#` | mode de configuration des lignes
    
    # configuration de base d’un commutateur:
    
    ![[Untitled 4 5.png|Untitled 4 5.png]]
    
    ![[Untitled 5 4.png|Untitled 5 4.png]]
    
      
    
    # **La commande boot system:**
    
    Le commutateur tente de démarrer automatiquement en utilisant les informations de la variable d'environnement BOOT. Si cette variable n'est pas définie, le commutateur tente de charger et d'exécuter le premier fichier exécutable qu'il peut trouver.
    
    Le système d'exploitation IOS initialise ensuite les interfaces à l'aide des commandes Cisco IOS figurant dans le fichier de configuration initiale. Le fichier startup-config est appelé config.text et se trouve en flash
    
    boot example:
    
    ```Shell
    S1(config)# boot system flash:/c2960-lanbasek9-mz.150-2.SE/C2960-Lanbasek-MZ-2-se.bin
    ```
    
    |   |   |
    |---|---|
    |boot system|la commande principale|
    |flash:|mean storage device (périphérique de stockage)|
    |/c2960-la……|location to the ios (chemain d’accés a le fichier ios)|
    

[[VLAN]]

[[Les types de vlan]]

[[les types de niveau de vlan]]

[[les Aventages de vlans]]

[[STP]]

[[trunking]]

[[Routage Inter-VLAN]]

[[Resume]]

[[concept de commutation]]