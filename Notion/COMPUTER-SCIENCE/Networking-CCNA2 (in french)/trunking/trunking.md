Sans VLAN, tous les périphériques connectés aux commutateurs recevront tout le trafic de monodiffusion, de multidiffusion et de diffusion.

![[Untitled 50.png|Untitled 50.png]]

Avec les VLAN, le trafic de monodiffusion, de multidiffusion et de diffusion est limité à un VLAN. Sans un périphérique de couche 3 permettant de connecter les VLAN, les périphériques de différents VLAN ne peuvent pas communiquer.

![[Untitled 1 26.png|Untitled 1 26.png]]

  

==**Le but du port "trunked" est de faire passer le trafic pour plusieurs VLAN.**==

**protocole 802.1q : (ajouter tags a trame ) La principale fonction de la norme est de transporter les Vlans sur le réseau, pour permettre à deux machines d'un même Vlan de communiquer au travers un nombre non définit d'équipement réseau.**

```Bash
switch\#configure terminal
switch(config)# interface name_interface0/1
switch(config)# switchport mode trunk
switch(config)# switchport trunk native vlan vlan-id //priciser le vlna natif (ne sont pas necessaire)
switch(config-if)# switchport trunk  allowed vlan 1-99// les vlans qui autoriser pourconnecter avec autre vlan ou pour passer dans le trunck
switch(config)# no switchport trunk native vlan vlan-id //supprimer le vlna natif est le trunk mode
```

> [!important]  
> Les trunks sont de couche 2 et transportent le trafic pour tous les VLAN.  

# Identification du VLAN avec une étiquette

![[Untitled 2 24.png|Untitled 2 24.png]]

L'en tête IEEE 802.1Q est de 4 octets Lorsque l'étiquette est créée, le FCS doit être recalculé. Lorsqu'elle est envoyée aux périphériques terminaux, cette étiquette doit être supprimée et le FCS doit être recalculé pour retourner à son numéro d'origine

![[Untitled 3 24.png|Untitled 3 24.png]]

> [!important]  
> trunk de base 802.1Q:  

- Étiquetage est généralement effectué sur tous les VLAN.
- L'utilisation d'un VLAN natif a été conçue pour une utilisation ancienne, comme le concentrateur dans l'exemple.
- Moins qu'il ne soit modifié, VLAN1 est le VLAN natif.
- Les deux extrémités d’une liaison trunk doit être configurées avec le même VLAN natif.
- Chaque trunk est configuré séparément, il est donc possible d'avoir un VLAN natif différent sur des trunks séparés.

![[Untitled 4 23.png|Untitled 4 23.png]]

la commande pour modifier ou pour assurer le mode trunk pour un port:

```Bash
Switch(config)# interface FastEthernet0/3
Switch(config-if)#
Switch(config-if)# switchport mode trunk
```

**==VLAN NATIF : (Vlan par defaut)==** pour assurer la compatibilité descendante avec le traffic non tager. lorsqu'un switch reçoit une trame sans tag.

```Bash
switch\#configure terminal
switch(config)# interface name_interface0/1
switch(config-if)# switchport trunk  native vlan id_vlan
switch(config-if)# switchport trunk  allowed vlan 1-99    // les vlans qui autoriser pour connecter avec autre vlan ou pour passer dans le trunck
```

# DTP:

Le **Dynamic Trunk Protocol** ou **DTP** est un [protocole réseau](https://fr.wikipedia.org/wiki/Protocole_r%C3%A9seau) propriétaire de [Cisco Systems](https://fr.wikipedia.org/wiki/Cisco_Systems), permettant de ==gérer dynamiquement l'activation/désactivation du mode trunk d'un port sur un== ==[commutateur réseau](https://fr.wikipedia.org/wiki/Commutateur_r%C3%A9seau)==.

Le DTP gère la négociation d’agrégation (mode trunk d'un port) uniquement si le port de l’autre commutateur est configuré dans un mode d’agrégation qui prend en charge ce protocole.

les caractéristiques de protocole DTP sont les suivantes:

- Activé par défaut sur les commutateurs Catalyst 2960 et 2950
- Dynamic auto est par défaut sur les commutateurs 2960 et 2950
- Peut être désactivé avec la commande `nonegotiate`
- Peut être réactivé en réglant l'interface sur `dynamic auto`
- La définition d'un commutateur sur un trunk statique ou un accès statique évitera les problèmes de négociation avec la commande `switchport mode trunk` ou `switchport mode access`.

![[Untitled 5 21.png|Untitled 5 21.png]]

- _**Access**_ — Puts the [Ethernet](https://en.wikipedia.org/wiki/Ethernet) port into permanent nontrunking mode and negotiates to convert the link into a nontrunk link. The Ethernet port becomes a nontrunk port even if the neighboring port does not agree to the change.
- _**Trunk**_ — Puts the Ethernet port into permanent trunking mode and negotiates to convert the link into a trunk link. The port becomes a trunk port even if the neighboring port does not agree to the change.
- _**Dynamic Auto**_ — Makes the Ethernet port willing to convert the link to a trunk link. The port becomes a trunk port if the neighboring port is set to trunk or _dynamic desirable_ mode. This is the default mode for some switchports.
- _**Dynamic**_ _**Desirable**_ — Makes the port actively attempt to convert the link to a trunk link. The port becomes a trunk port if the neighboring Ethernet port is set to trunk, _dynamic desirable_ or _dynamic auto_ mode.
- _**No**__**negotiate**_ — Disables DTP. The port will not send out DTP frames or be affected by any incoming DTP frames. If you want to set a trunk between two switches when DTP is disabled, you must manually configure trunking using the (switchport mode trunk) command on both sides.

![[Untitled 6 18.png|Untitled 6 18.png]]

## Vérifier le mode du protocole DTP:

![[Untitled 7 16.png|Untitled 7 16.png]]

**we can’t remove DTP from an interface when we enable dynamic auto or dynamic desraible to an interface. in this issue we need to to affect an mode trunk or access to an interface to disable DTP.**

![[Untitled 8 13.png|Untitled 8 13.png]]

![[Untitled 9 10.png|Untitled 9 10.png]]

![[Untitled 10 9.png|Untitled 10 9.png]]

```Bash
show dtp interface //display the mode of dtp
(config-if) switchport nenonegotiate //desactivate dtp from an interface 
```