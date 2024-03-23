**Le routage inter-VLAN est un processus qui permet de transférer du trafic réseau d'un VLAN  
à un autre à l'aide d'un périphérique de couche 3 comme un routeur  
**.**. Il existe 3 options de routage inter-VLAN:**

- ==**Routage inter-VLAN hérité**== **- Il s'agit d'une solution héritée. Il n'est pas bien dimensionné.**
- ==**Router-on-a-Stick**== **- C'est une solution acceptable pour un réseau de petite à moyenne taille.**
- ==**Commutateur de couche 3 utilisant des interfaces virtuelles commutées (SVIS)**== **- Il s'agit de la solution la plus évolutive pour les moyennes et grandes entreprises.**

  

### ==**Router-on-a-stick**==

**is a type of router configuration in which you are able to use a single physical interface to route traffic between multiple VLANs.**

![[Untitled 51.png|Untitled 51.png]]

**The router interface is configured as a trunk link and is connected to a trunk switch port. il faut :**

**-cree des interfaces virtual pour chaque vlan. par exemple G0/0/1.10 (VLAN10) et G0/0/1.20 (VLAN20).  
-chaque  
**==**vlan**== **doit prendre un virtual interface.**

![[Untitled 1 27.png|Untitled 1 27.png]]

```Bash
// CONFIGURATION DES INTERFACES VIRTUAL

R1(config)# interface G0/0/1.10
R1(config-subif)# encapsulation dot1Q 10 //read trames of VLAN 10 (10 represente the vlan number)
R1(config-subif)# ip add 192.168.10.1 255.255.255.0 //assign an ip^to the interface (the subnet must be identical to vlan10 connected devices and also give this ip to default gateway for each connected device on the same vlan)
R1(config-subif)# no shutdown
R1(config-subif)# exit
R1(config)#
R1(config)# interface G0/0/1.20
R1(config-subif)# encapsulation dot1Q 20
R1(config-subif)# ip add 192.168.20.1 255.255255.0
R1(config-subif)# no shutdown
R1(config-subif)# exit
R1(config)#

// CONFIGURATION DES PORTS TRUNK OF THE SWITCHE

S1(config)# interface fa0/1
S1(config-if)# switchport mode trunk
S1(config-if)# no shut
S1(config-if)# exit
S1(config)# interface fa0/5
S1(config-if)# switchport mode trunk
S1(config-if)# no shut
S1(config-if)# end

// CONFIGURATION DES PORTS EN MOD ACCESS FOR DEVICES

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
R1(config-if)# no shut
R1(config-if)# end
R1\#10
```

### ==**Routage interVLAN sur un commutateur de couche 3**==

**Layer 3 switches for inter-VLAN routing: They are much faster than router-on-a-stick  
because everything is hardware switched and routed. There is no need  
for external links from the switch to the router for routing  
**

dans cette partie on utilise :

**-des commutateurs de couche 3.  
-des interfaces virtuelles commutées (SVI).  
-chaque  
**==**vlan**== **doit prendre un SVI.**

### **Les Avnetages :**

- ==**Ils sont beaucoup plus rapides que les routeurs sur bâton car tout est commuté et acheminé par le matériel.**==
- **Il n'est pas nécessaire d'utiliser des liaisons externes entre le commutateur et le routeur pour le routage.**
- **Ils ne sont pas limités à une liaison, car les canaux EtherChannels de couche 2 peuvent être utilisés comme liaisons de trunk entre les commutateurs pour augmenter la bande passante.**
- **La latence est bien plus faible, car les données n'ont pas besoin de quitter le commutateur pour être acheminées vers un autre réseau.**
- **Le seul inconvénient est que les commutateurs de couche 3 sont plus chers.**
- **Ils sont plus souvent déployés dans un réseau local de campus que les routeurs.**

![[Untitled 2 25.png|Untitled 2 25.png]]

pour la configuration:

![[Untitled 3 25.png|Untitled 3 25.png]]

une autre exemple:

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

### ==**Legacy inter-VLAN routing**==

**multiple router interfaces are used, each connecting to a switch port in different VLANs.**

![[Untitled 4 24.png|Untitled 4 24.png]]

- **==La première solution de routage inter-VLAN reposait sur l'utilisation d'un routeur avec plusieurs interfaces Ethernet.Chaque interface de routeur était connectée à un port de commutateur dans différents VLANs==**. Les interfaces de routeur ont servi de passerelles par défaut vers les hôtes locaux du sous-réseau VLAN.
- L'ancien routage inter-VLAN utilisant des interfaces physiques fonctionne, mais il présente une limitation importante. Il n'est pas raisonnablement évolutif car les routeurs ont un nombre limité d'interfaces physiques. Lanécessité de posséder une interface de routeur physique par VLAN épuise rapidement la capacité du routeur.
- Remarque:Cette méthode de routage inter-VLAN n'est plus implémentée dans les réseaux commutés et est incluse à des fins d'explication uniquement.