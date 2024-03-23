Un commutateur de transfert basé sur l'interface d'entrée et l'adresse MAC de destination.

Un commutateur utilise sa table d'adresses MAC pour prendre des décisions de transmission.

> [!important]  
> Un commutateur ne permettra jamais de transférer le trafic sur l'interface où il a reçu letrafic  

==**La méthode d'apprentissage et de transmission du commutateur:**==

> [!important]  
> ETAPE1: Apprendre Examiner l'adresse source (LEARN)-Ajoute le MAC source si ce n'est pas dans la table-Réinitialise le réglage du délai d'arrêt à 5 minutes si la source est dans le tableau  
  
> [!important]  
> ETAPE2:Transfert Examiner l'adresse de destination (FORWOARD)-Si le MAC de destination se trouve dans la table d'adresses MAC, il est transféré hors duport spécifié.-Si un MAC de destination n'est pas dans la table, il est inondé de toutes les interfacessauf celle qu'il a reçue.  

**Les méthodes de transmission du commutateur:**

`Commutation de stockage et de transfert`

Reçoit la trame entière et assure la validité de la trame. La commutation par stockage et retransmission est la méthode de commutation LAN principale de Cisco.

`Commutation par coupure (cut through)`

Transfère la trame immédiatement après avoir déterminé l'adresse MAC de destination d'une trame entrante et le port de sortie.

**Domaines de collision:**

Les commutateurs éliminent les domaines de collision et réduisent la congestion.

> [!important]  
> -Lorsqu'il y a duplex intégral (FULL DUPLEX) sur le lien, les domaines de collision sont éliminés.-Lorsqu'il y a un ou plusieurs périphériques en semi-duplex (HALF DUPLEX), il y aura désormais un domaine de collision.La plupart des appareils, y compris Cisco et Microsoft, utilisent l'auto-négociation commeparamètre par défaut pour le duplex et la vitesse.  

### Domaines de diffusion:

==**Un domaine de diffusion s'étend sur tous les périphériques de couche 1 ou 2 d'un réseau local.**==

- Seul un périphérique de couche 3 (routeur) brisera `(brisera=break)` le domaine de diffusion, également appelé `domaine de diffusion MAC`.
- Le domaine de diffusion MAC ==est constitué de tous les périphériques du réseau local qui reçoivent les trames de diffusion provenant d'un hôte.==
- Lorsque le commutateur ==de couche 2 reçoit la diffusion, il l'inondera toutes les interfaces à l'exception de l'interface d'entrée==.
- Trop de diffusions peuvent causer de ==la congestion et des performances== réseau médiocres.
- L'augmentation des périphériques au niveau de la couche 1 ou de la couche 2 entraîne (entraine = `leads` ) le développement du domaine de diffusion.

# Resume:

## **Transfert de trame:**

- **==Ingress==** **est le port d'entrée,** **==egress==** **est le port de sortie.**
- **Le commutateur** **==construit une table d'adresses MAC==** **pour transférer les trames sur le réseau local.**
- **Le commutateur peut utiliser soit la méthode du** **==stockage et de la retransmission==****, soit la méthode de la retransmission par coupure.**

## **Domaines de commutation:**

- **Les ports Ethernet en** ==**semi-duplex font partie d'un domaine de collision**==**.**
- **Le duplex** ==**intégral éliminera**== **les domaines de collision.**
- **Un** ==**commutateur va inonder toutes les interfaces sauf le port d'entrée si la trame est une diffusion ou si le MAC de destination monodiffusion est inconnu**==**.**
- **Les domaines de diffusion peuvent être** ==**fragmentés par un périphérique de couche 3, comme un routeur**==**.**
- **Les commutateurs étendent les domaines de diffusion,** ==**mais peuvent éliminer les domaines de collision et soulager la congestion**==**.**