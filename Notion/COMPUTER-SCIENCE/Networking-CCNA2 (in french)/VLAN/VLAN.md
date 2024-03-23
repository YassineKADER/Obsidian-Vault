---

[[Networking-CCNA2 (in french)]]

[[Networking-CCNA2 (in french)]][Layer 2](https://www.techtarget.com/searchnetworking/definition/Data-Link-layer)) broadcast domain, which is the set of network devices an [Ethernet](https://www.techtarget.com/searchnetworking/definition/Ethernet) broadcast packet can reach.  
A VLAN, like the LAN it sits atop, operates at Layer 2 of the network, the Ethernet level. VLANs partition a single switched network into a set of overlaid  
[virtual networks](https://www.techtarget.com/searchnetworking/definition/virtual-networking) that can meet different functional and security requirements. This partitioning avoids the need to have multiple, distinct physical networks for different use cases.

==Les VLAN sont des connexions logiques avec d'autres périphériques similaires,== `qui regroupe un sous-ensemble de périphériques partageant un réseau local physique, isolant le trafic pour chaque groupe.`

### L**es caractéristiques des VLANS:**

-Fournir la segmentation ==des différents groupes de périphériques sur les mêmes commutateurs==

-Fournir une organisation plus facile à gérer

-Les diffusions, les multidiffusions et les monodiffusions sont isolées dans le VLAN individuel

-Chaque VLAN aura sa propre plage d'adressage IP unique

-Domaines de Diffusion Plus Petits

### Les Aventages des VLAN sont les suivants:

|   |   |
|---|---|
|**Domaines de Diffusion Plus Petits**|La division du réseau local réduit le nombre de domaines de diffusion|
|**Sécurité optimisée**|Seuls les utilisateurs du même VLAN peuvent communiquer ensemble|
|**Efficacité accrue des IT**|Les VLAN peuvent regrouper des appareils ayant des exigences  <br>similaires, par exemple professeurs contre étudiants|
|**Réduction des coûts**|Un commutateur peut prendre en charge plusieurs groupes ou VLAN|
|**Meilleures performances**|Les domaines de diffusion plus petits réduisent le trafic et améliorent la  <br>bande passante|
|**Gestion simplifiée**|Des groupes similaires auront besoin d'applications similaires et d'autres  <br>ressources réseau|

### **Réseaux sans VLAN:**

Sans VLAN, tous les périphériques connectés aux commutateurs recevront tout le trafic de monodiffusion, de multidiffusion et de diffusion.

![[/Untitled 46.png|Untitled 46.png]]

Avec les VLAN, le trafic de monodiffusion, de multidiffusion et de diffusion est limité à un VLAN. Sans un périphérique de couche 3 permettant de connecter les VLAN, les périphériques de différents VLAN ne peuvent pas communiquer.

![[/Untitled 1 24.png|Untitled 1 24.png]]

# Identification du VLAN avec une étiquette

**-L'entête IEEE 802.1Q est de 4 octets**

**-Lorsque l'étiquette est créée, le FCS doit être recalculé.**

**-Lorsqu'elle est envoyée aux périphériques terminaux, cette étiquette doit être supprimée et le FCS doit être recalculé pour retourner à son numéro d'origine.**

**-Étiquetage est généralement effectué sur tous les VLAN.**

**-L'utilisation d'un VLAN natif a été conçue pour une utilisation ancienne, comme le concentrateur dans l'exemple.**

**-Moins qu'il ne soit modifié, VLAN1 est le VLAN natif.**

**-Les deux extrémités d’une liaison trunk doit être configurées avec le même VLAN natif.**

**-Chaque trunk est configuré séparément, il est donc possible d'avoir un VLAN natif différent**

**sur des trunks séparés.**

> [!important]  
> [[Networking-CCNA2 (in french)]][[Networking-CCNA2 (in french)]][[Networking-CCNA2 (in french)]][[Networking-CCNA2 (in french)]]  

[[Networking-CCNA2 (in french)]]

```Bash
show vlan | show vlan brief

\#output

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/5, Fa0/6, Fa0/7, Fa0/8
                                                Fa0/9, Fa0/10, Fa0/11, Fa0/12
                                                Fa0/13, Fa0/14, Fa0/15, Fa0/16
                                                Fa0/17, Fa0/18, Fa0/19, Fa0/20
                                                Fa0/21, Fa0/22, Fa0/23, Fa0/24
                                                Gig0/1, Gig0/2
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
1    enet  100001     1500  -      -      -        -    -        0      0
1002 fddi  101002     1500  -      -      -        -    -        0      0   
1003 tr    101003     1500  -      -      -        -    -        0      0   
1004 fdnet 101004     1500  -      -      -        ieee -        0      0   
1005 trnet 101005     1500  -      -      -        ibm  -        0      0   

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------

Remote SPAN VLANs
------------------------------------------------------------------------------

Primary Secondary Type              Ports
------- --------- ----------------- ------------------------------------------
```

[[Networking-CCNA2 (in french)]]:

```Bash
Switch(config)\#vlan 20
Switch(config-vlan)\#name test2
Switch(config-vlan)\#exit
Switch(config)\#exit
Switch#
%SYS-5-CONFIG_I: Configured from console by console

Switch\#show vlan

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/5, Fa0/6, Fa0/7, Fa0/8
                                                Fa0/9, Fa0/10, Fa0/11, Fa0/12
                                                Fa0/13, Fa0/14, Fa0/15, Fa0/16
                                                Fa0/17, Fa0/18, Fa0/19, Fa0/20
                                                Fa0/21, Fa0/22, Fa0/23, Fa0/24
                                                Gig0/1, Gig0/2
10   test                             active    
20   test2                            active    
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
1    enet  100001     1500  -      -      -        -    -        0      0
10   enet  100010     1500  -      -      -        -    -        0      0
20   enet  100020     1500  -      -      -        -    -        0      0
1002 fddi  101002     1500  -      -      -        -    -        0      0   
1003 tr    101003     1500  -      -      -        -    -        0      0   
1004 fdnet 101004     1500  -      -      -        ieee -        0      0   
1005 trnet 101005     1500  -      -      -        ibm  -        0      0   

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------

Remote SPAN VLANs
------------------------------------------------------------------------------

Primary Secondary Type              Ports
------- --------- ----------------- ------------------------------------------
Switch#
```

[[Networking-CCNA2 (in french)]]`[[Networking-CCNA2 (in french)]]`:

[[Networking-CCNA2 (in french)]]:

```Bash
int f0/1 //if you wanna select one port
int range f0/1-10 //if you wanna to select multiple ports
```

[[Networking-CCNA2 (in french)]]`[[Networking-CCNA2 (in french)]]`[[Networking-CCNA2 (in french)]]

[[Networking-CCNA2 (in french)]][[Networking-CCNA2 (in french)]]

```Bash
Switch(config-if-range)\#switchport mode access
Switch(config-if-range)\#switchport access vlan 10
```

![[Untitled 2 22.png|Untitled 2 22.png]]

![[Untitled 3 22.png|Untitled 3 22.png]]

# Vérifier les informations sur les VLAN

![[Untitled 4 21.png|Untitled 4 21.png]]

> [!important]  
> Afficher une ligne pour chaque VLAN comportant le nom du VLAN son état et ses ports. briefAfficher des informations sur un VLAN identifié par un ID de VLAN.id vlan-idAfficher des informations sur un VLAN identifié par un nom de VLAN.name vlan-nameAfficher les informations récapitulatives sur le VLAN. summary  

pour supprimer l’affectation d’un vlan a une interface

![[Untitled 5 19.png|Untitled 5 19.png]]

Utilisez les commandes ==show vlan brief== ou ==show interface fa0/18 switchport== pour vérifier l'association correcte de VLAN

> [!important]  
> Supprimez tous les VLAN avec les commandes delete flash:vlan.dat ou delete vlan.dat  

> ✨ le nombre maximale de vlan gu’on peut le creer est: `4094`

> [!important]  
> Les vlan standard de 1 to 1005 (les plages normale)  
  
> [!important]  
> Les vlan qu’il ne sont pas standard de 1006 to 4094 (les plages étendue)  
  
> [!important]  
> Show tranks interfaces: show interfaces switchportor show interfaces trunk  
  
> [!important]  
> Trunk Port permet de supprimer l’id de vlan avant de sortir de l’interface  
  
> [!important]  
> les vlans stocké dans un fichier : VLAN.DAT  
  
> [!important]  
> default name for a vlan for example a vlan 10 the default name will be vlan0010