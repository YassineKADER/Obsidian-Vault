  

**VLAN de données:**

==Un VLAN de données est un réseau local virtuel configuré pour transmettre le trafic généré par l'utilisateur==. Un VLAN acheminant du trafic de voix ou de gestion ne peut pas faire partie d'un VLAN de données. Il est d'usage de séparer le trafic de voix et de gestion du trafic de données. Un VLAN de données est parfois appelé un VLAN utilisateur. Les VLAN de données sont utilisés pour diviser un réseau en groupes d'utilisateurs ou de périphériques.

**VLAN par défaut:**

==Tous les ports de commutateur font partie du VLAN par défaut après le démarrage initial d'un commutateur chargeant la configuration par défaut==. Les ports de commutateur qui participent au VLAN par défaut appartiennent au même domaine de diffusion. Cela permet à n'importe quel périphérique connecté à n'importe quel port du commutateur de communiquer avec d'autres périphériques sur d'autres ports du commutateur. Le VLAN par défaut pour les commutateurs Cisco est VLAN 1.  
Dans la figure, la commande  
**show vlan brief** a été émise sur un commutateur utilisant la configuration par défaut.  
Notez que tous les ports sont assignés au VLAN 1 par défaut.  
  

![[Untitled 47.png|Untitled 47.png]]

Le VLAN 1 dispose de toutes les fonctions de n'importe quel VLAN, à l'exception du fait qu'il ne peut pas être renommé ni supprimé. Par défaut, tout le trafic de contrôle de couche 2 est associé au VLAN 1.

**VLAN natif:**  
Un réseau local virtuel natif est affecté à un port trunk 802.1Q.  
==Les ports trunk sont les liaisons entre les commutateurs qui prennent en charge la transmission du trafic associée à plusieurs VLAN==. Un port trunk 802.1Q prend en charge le trafic provenant de nombreux VLAN (trafic étiqueté ou « tagged traffic »), ainsi que le trafic qui ne provient pas d'un VLAN (trafic non étiqueté ou « untagged traffic »). Le trafic étiqueté est appelé ainsi en référence à l'étiquette de 4 octets  
ajoutée dans l'en-tête de trame Ethernet originale et spécifiant le VLAN auquel la trame appartient. Le port trunk 802.1Q place le trafic non étiqueté sur le VLAN natif, qui par défaut est le VLAN 1.  

==Les VLAN natifs sont définis dans la spécification IEEE 802.1Q pour assurer la compatibilité descendante avec le trafic non étiqueté qui est commun aux scénarios LAN existants. Un VLAN natif sert d'identificateur commun aux extrémités d'une liaison trunk.==

Il est généralement recommandé de configurer le VLAN natif en tant que VLAN inutilisé, distinct du VLAN 1 et des autres VLAN. En fait, il n'est pas rare de dédier un VLAN fixe jouant le rôle de VLAN natif pour tous les ports trunk du domaine commuté.

**VLAN de gestion:**

Un VLAN de gestion est ==un réseau local virtuel configuré pour accéder aux fonctionnalités de gestion d'un commutateur==. Le VLAN 1 est le VLAN de gestion par défaut. Pour créer le VLAN de gestion, l'interface virtuelle du commutateur (SVI) de ce VLAN se voit attribuer une adresse IP et un masque de sous-réseau, ce qui permet de gérer le commutateur via HTTP, Telnet, SSH ou SNMP. Sachant que la configuration initiale d'un commutateur Cisco utilise le VLAN 1 par défaut, il n'est pas judicieux de le choisir comme VLAN de gestion.

**VLAN de voix:**

==Un VLAN distinct est requis car le trafic de voix nécessite:==

-La bande passante consolidée.

-La priorité de QOS élevée.

-La capacité d'éviter la congestion.

-Le délai inférieur à 150 ms de la source à la destination.

-L'ensemble du réseau doit être conçu pour prendre en charge la voix.