## **MODULE 1**

IOS image files **contain the system code that your router uses to function**

**Flash memory**  
 stores fully functional Cisco IOS images and is the default location where the switch gets its Cisco IOS at boot time. Flash memory also can be used to store other files, including backup copies of configuration files.  

**`Switch Boot Sequence`**  
After a Cisco switch is powered on, it goes through the following five-step boot  
sequence:  

**==POST==** :**program stored in ROM** **This tests the hardware of the computer before loading the OS.**

==**A boot loader**== : **is a critical piece of software running on any system. Whenever a computing system is initially powered on, the first piece of code to be loaded and run is the boot loader.**

A boot loader, also called a boot manager, is **a small program that places the operating system (OS) of a computer into memory**

The core function of Cisco IOS is **to enable data communications between network nodes**  
.IOS images are stored   
**in a device called the flash (lowercase)**  
.  
.  

> **First, the switch loads a power-on self-test (POST) program stored in ROM. POST checks the CPU subsystem. It tests the CPU, DRAM, and the portion of the flash device that makes up the flash file system.**

> **Next, the switch loads the boot loader software. The boot loader is a small program stored in ROM and is run immediately after POST successfully completes.**

> **The boot loader performs low-level CPU initialization. It initializes the CPU registers, which control where physical memory is mapped, the quantity of memory, and its speed.**

> **The boot loader initializes the flash file system on the system board.**

> **Finally, the boot loader locates and loads a default IOS operating system software image into memory and hands control of the switch over to the IOS.**

  

### ==les commandes :==

  

**switch>****`enable`**

**switch#** **`configure terminal`**

**switch(config)#**

**switch(config)#** `**hostname**` **name-de-switch**

**switch (config)#** `**enable password**` **123**

**switch (config)#** `**enable secret**` **123**

  

### **==pour sécurise accès par console :==**

  

**switch (config)#** `**line console 0**` **// un seul line console in switch**

**switch (config-line)#**`**password**` **321**

**switch (config-line)#**`**login**` **// activer l’utilisation de mot de pass.**

**switch (config-line)#**`**loggin synchronous**` **// désactiver les messages no soliciter**

**switch (config-line)#** `**exec-timeout**` **10 // time veuille de switch.**

  

### ==accès par telnet :==

accès a distance :

**switch (config)#** `**line VTY**` **0 4 // nombre de ligne qui autoriser pour accès switch a distance**

**switch (config-line)#**`**password**` **3214 // mot de passe line VTY**

**switch (config-line)#**`**login**`

  

==**SVI : SWITCH VIRTUAL INTERFACE :**==

crée un SVI :

**switch(config)#** `**int vlan 1**` **// crée virtual interface vlan**

**switch(config)#** `**no sh**`

**switch(config)#** `**ip addresse 10.0.0.1 255.0.0.0**` **// crée ip addresse de interface vlan**

with this svi we can acces a distance.

==**SSH:**==

  

  

  

==**configuration des ports :**== ==**( speed / duplex / off-on)**==

  

`**half duplex :**`

**pour envoyer et recieve des informations mais pas en meme temps.**

`**full duplex :**`

**pour envoyer et recieve des informations en meme temps.**

`**auto mdix :**`

**exicte auto dans les interfaces ca rolle est recpgnize type of cable.**

**adapter avec type de cable.**

  
  
**Passez en mode de configuration globale. S1#** `**configure terminal**`**  
Passez en mode de configuration d’interface S1(config)#  
**`**interface FastEthernet 0/1**`**  
Configurez le mode bidirectionnel d'interface. S1(config-if)#  
**`**duplex full**`**  
Configurez la vitesse d'interface S1(config-if)#  
**`**speed 100**`**  
Repassez en mode d'exécution privilégié S1(config-if)#  
**`**end**`**  
Enregistrez la configuration en cours dans la configuration  
de démarrage. S1#  
**`**copy running-config startup-config**`

  

### ==**Types of Vlans :**==

  

==**Data Vlan:**==

**configurated to carry user-generated traffic**

**are used to sperate the network into groups of users or devices.**

  

  

  

[![](https://www.clemanet.com/images/topologie_vlan.png)](https://www.clemanet.com/images/topologie_vlan.png)

### ==Ajout de vlan :==

  

**2960-RG(config)#**`**vlan**`

**22960-RG(config-vlan)#**`**name**` **administration**

**2960-RG(config-vlan)#**`**ex**`

**2960-RG(config)#**`**vlan**` **3,4,5**

**2960-RG(config-vlan)\#ex**

**2960-RG(config)#**

  

**==_To assign an Ethernet interface to a VLAN 15 :_==**

switch#`**configure**` **terminal**

switch(config)# `**interface**` **name_interface0/1**

switch(config-if)# `**switchport access**` **vlan 15**

  

==**mode trunk :**==

**Le but du port "trunked" est de faire passer le trafic pour plusieurs VLAN.**

**protocole 802.1q : (ajouter tags a trame ) La principale fonction de la norme est de transporter les Vlans sur le réseau, pour permettre à deux machines d'un même Vlan de communiquer au travers un nombre non définit d'équipement réseau.**

switch#`**configure**` **terminal**

switch(config)# `**interface**` **name_interface0/1**

switch(config-if)# `**switchport trunk**` **allowed vlan 1-99 // les vlans qui autoriser pour connecter avec autre vlan ou pour passer dans le trunck**

  

==**VLAN NATIF : Vlan par defaut**==

**pour assurer la compatibilité descendante avec le traffic non tager.**

**lorsqu'un switch reçoit une trame sans tag.**

switch#`**configure**` **terminal**

switch(config)# `**interface**` **name_interface0/1**

switch(config-if)# `**switchport trunk native**` **name_vlan**

switch(config-if)# `**switchport trunk**` **allowed vlan 1-99 // les vlans qui autoriser pour connecter avec autre vlan ou pour passer dans le trunck**

  

**PROTOCOLE DTP:**

**DTP, le protocole Dynamic Trunking, est utilisé sur les commutateurs LAN Cisco comme outil pour négocier une liaison entre deux appareils compatibles DTP sans configuration manuelle.**

![[My_project.png]]

  

![[Untitled 52.png|Untitled 52.png]]

![[Untitled 1 28.png|Untitled 1 28.png]]

  

**we can’t remove DTP from an interface when we enable dynamic auto or dynamic desraible to an interface. in this issue we need to to affect an mode trunk or access to an interface to disable DTP.**

  

![[Untitled 8 13.png|Untitled 8 13.png]]

![[Untitled 9 10.png|Untitled 9 10.png]]

![[Untitled 10 9.png|Untitled 10 9.png]]

  

### ==**LES INTER-VLANS:**==

  

**Le routage inter-VLAN est un processus qui permet de transférer du trafic réseau d'un VLAN  
à un autre à l'aide d'un périphérique de couche 3 comme un routeur  
**.**. Il existe 3 options de routage inter-VLAN:**

- ==**Routage inter-VLAN hérité**== **- Il s'agit d'une solution héritée. Il n'est pas bien dimensionné.**
- ==**Router-on-a-Stick**== **- C'est une solution acceptable pour un réseau de petite à moyenne taille.**
- ==**Commutateur de couche 3 utilisant des interfaces virtuelles commutées (SVIS)**== **- Il s'agit de la solution la plus évolutive pour les moyennes et grandes entreprises.**

  

### ==**“Router-on-a-stick”**==

**is a type of router configuration in which you are able to use a single physical interface to route traffic between multiple VLANs. The router interface is configured as a trunk link and is connected to a trunk switch port.**

**il faut :**

**-cree des interfaces virtual pour chaque vlan. par exemple G0/0/1.10 (VLAN10) et G0/0/1.20 (VLAN20).**

**-chaque** ==**vlan**== **doit prendre un virtual interface.**

![[Untitled 1 27.png|Untitled 1 27.png]]

```Plain

// CONFIGURATION DES INTERFACES VIRTUAL

R1(config)# interface G0/0/1.10
R1(config-subif)# description Default Gateway for VLAN 10
R1(config-subif)# encapsulation dot1Q 10
R1(config-subif)# ip add 192.168.10.1 255.255.255.0
R1(config-subif)# exit
R1(config)#
R1(config)# interface G0/0/1.20
R1(config-subif)# description Default Gateway for VLAN 20
R1(config-subif)# encapsulation dot1Q 20
R1(config-subif)# ip add 192.168.20.1 255.255255.0
R1(config-subif)# exit
R1(config)#

// CONFIGURATION DES PORTS TRUNK

S1(config)# interface fa0/1
S1(config-if)# switchport mode trunk
S1(config-if)# no shut
S1(config-if)# exit
S1(config)# interface fa0/5
S1(config-if)# switchport mode trunk
S1(config-if)# no shut
S1(config-if)# end

// CONFIGURATION DES PORTS EN MOD ACCESS

S1(config)# interface fa0/6
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 10
S1(config-if)# no shut
S1(config-if)# exit

S1(config)# interface fa0/18
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 10
S1(config-if)# no shut
S1(config-if)# exit

// CONFIGURATION DES PORT ROUTER MOD TRUNK:

R1(config)# interface G0/0/1
R1(config-if)# description Trunk link to S1
R1(config-if)# no shut
R1(config-if)# end
R1#
```

  

### ==**“Routage interVLAN sur un commutateur de couche 3”**==

  

**Layer 3 switches for inter-VLAN routing: They are much faster than router-on-a-stick  
because everything is hardware switched and routed. There is no need  
for external links from the switch to the router for routing  
**

dans cette partie on utilise :

**-des commutateurs de couche 3.**

**-des interfaces virtuelles commutées (SVI).**

**-chaque** ==**vlan**== **doit prendre un SVI.**

![[Untitled 2 26.png|Untitled 2 26.png]]

```Plain
// CREATION DES VALNS :

D1(config)\#vlan 10
D1(config-vlan)\#name LAN10
D1(config-vlan)\#vlan 20
D1(config-vlan)\#name LAN20
D1(config-vlan)\#exit
D1(config)#

// CREATION DES INTERFACES VLAN :

D1(config)# interface vlan 10
D1(config-if)# description Default Gateway SVI for 192.168.10.0/24
D1(config-if)# ip add 10.1.10.1 255.255.255.0
D1(config-if)# no shut
D1(config-if)# exit
D1(config)#
D1(config)# interface vlan 20
D1(config-if)# description Default Gateway SVI for 192.168.20.0/24
D1(config-if)# ip add 10.1.20.1 255.255.255.0
D1(config-if)# no shut
D1(config-if)# exit
D1(config)#

// CONFIGURE ACCESS PORTS :

D1(config)# interface fa0/0
D1(config-if)# description Access port to PC1
D1(config-if)# switchport mode access
D1(config-if)# switchport access vlan 10
D1(config-if)# exit
D1(config)#
D1(config)# interface fa0/8
D1(config-if)# description Access port to PC2
D1(config-if)# switchport mode access
D1(config-if)# switchport access vlan 20
D1(config-if)# exit
```

  

```Plain
 // ENABLE IP ROUTING:

Finally, enable IPv4 routing with the ip routing global configuration 
command to allow traffic to be exchanged between VLANs 10 and 20.

D1(config)\#ip routing
D1(config)#
```

  

### ==“====**Legacy inter-VLAN routing”**==

**multiple router interfaces are used, each connecting to a switch port in different VLANs**

.

![[Untitled 3 26.png|Untitled 3 26.png]]

- **La première solution de routage inter-VLAN reposait sur l'utilisation d'un routeur avec plusieurs interfaces Ethernet.Chaque interface de routeur était connectée à un port de commutateur dans différents VLANs. Les interfaces de routeur ont servi de passerelles par défaut vers les hôtes locaux du sous-réseau VLAN.**
- **L'ancien routage inter-VLAN utilisant des interfaces physiques fonctionne, mais il présente une limitation importante. Il n'est pas raisonnablement évolutif car les routeurs ont un nombre limité d'interfaces physiques. Lanécessité de posséder une interface de routeur physique par VLAN épuise rapidement la capacité du routeur.**
- **Remarque:Cette méthode de routage inter-VLAN n'est plus implémentée dans les réseaux commutés et est incluse à des fins d'explication uniquement.**

  

### ==“====**STP spanning tree protocol” :**==

**Spanning Tree Protocol (STP) is a Layer 2 network protocol used to prevent looping within a network topology. STP was created to avoid the problems that arise when computers exchange data on a local area network (LAN) that contains redundant paths.**

- **Le protocole STP est un protocole réseau de prévention des boucles qui permet la redondance tout en créant une topologie de couche 2 sans boucle.**
- **STP bloque logiquement les boucles physiques dans un réseau de couche 2, empêchant les trames d'encercler le réseau pour toujours.**

  

==**Étapes vers une topologie sans boucle :**==

==**1**==**. Choisir le pont racine**

==**2**==**. Choisir les ports racine.**

==**3**==**. Choisir les ports désignés.**

==**4**==**. Choisir des ports alternatifs (bloqués)**

  

- **Pendant le fonctionnement de STA et de STP, les commutateurs utilisent des BPDU (Bridge Protocol Data Units) pour partager des informations sur eux-mêmes et sur leurs connexions. Les BPDU permettent de choisir le pont racine, les ports racine, les ports désignés et les ports alternatifs.**
- **Chaque trame BPDU contient un ID de pont (bridge ID) qui identifie le commutateur ayant envoyé la trame BPDU. La BID participe à la prise de nombreuses décisions STA, y compris les rôles de pont racine et de port.**
- **L'ID de pont contient une valeur de priorité, l'adresse MAC du commutateur et un ID système étendu. La valeur d'ID de pont la plus basse est déterminée par une combinaison de ces trois champs.**

==**Priorité de Pont:**== **Une priorité de pont inférieure est préférable. Une priorité de pont de 0 a préséance sur toutes les autres priorités de pont.**

==**L'ID système étendu:**== **identifier le VLAN de cette BPDU.**

==**Adresse MAC:**== **le commutateur dont l'adresse MAC de valeur est la plus faible, exprimée au format hexadécimal, aura le BID le plus bas.**

### ==**1.**== _**Choisir le pont racine :**_