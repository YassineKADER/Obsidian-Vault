Exercice 1: CIDR (Classless Inter-Domain Routing)

Annonce de l’exercice : Vous avez reçu le bloc CIDR 192.168.0.0/24. Vous devez diviser ce bloc en sous-réseaux, chacun pouvant accueillir au moins 50 hôtes. Quels sont les sous-réseaux ?

Solution : Pour accueillir au moins 50 hôtes, nous avons besoin de 6 bits (2^6 = 64). Donc, nous utilisons 26 bits pour le réseau. Le masque de sous-réseau est donc /26.

Les sous-réseaux sont :

    192.168.0.0/26
    192.168.0.64/26
    192.168.0.128/26
    192.168.0.192/26

Exercice 2: VLSM (Variable Length Subnet Mask)

Annonce de l’exercice : Vous avez reçu le bloc 192.168.1.0/24. Vous devez créer 3 sous-réseaux avec respectivement 100, 50 et 25 hôtes. Comment répartiriez-vous les sous-réseaux en utilisant VLSM pour une utilisation optimale de l’adresse IP ?

Solution : Commencez par le sous-réseau avec le plus grand nombre d’hôtes. Pour 100 hôtes, nous avons besoin de 7 bits (2^7 = 128), donc nous utilisons 25 bits pour le réseau. Le premier sous-réseau est donc 192.168.1.0/25.

Ensuite, pour 50 hôtes, nous avons besoin de 6 bits (2^6 = 64), donc nous utilisons 26 bits pour le réseau. Le deuxième sous-réseau est donc 192.168.1.128/26.

Enfin, pour 25 hôtes, nous avons besoin de 5 bits (2^5 = 32), donc nous utilisons 27 bits pour le réseau. Le troisième sous-réseau est donc 192.168.1.192/27.