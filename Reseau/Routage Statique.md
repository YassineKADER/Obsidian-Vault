Supposons que nous avons deux réseaux :

    Réseau A : 192.168.1.0/24 (par exemple, une interface FastEthernet0/0 est configurée avec l'adresse IP 192.168.1.1)
    Réseau B : 10.0.0.0/24 (par exemple, une interface FastEthernet0/1 est configurée avec l'adresse IP 10.0.0.1)

Nous allons configurer des routes statiques sur le routeur pour permettre au réseau A d'accéder au réseau B et vice versa.

Voici comment cela peut être configuré :

```zsh
Router> enable
Router# configure terminal
Router(config)# ip route 10.0.0.0 255.255.255.0 192.168.1.2
```

Dans cet exemple :

    ip route indique que nous ajoutons une route statique.
    10.0.0.0 255.255.255.0 est la destination de la route (le réseau B).
    192.168.1.2 est la passerelle par défaut pour atteindre le réseau B à partir du réseau A. Assurez-vous que cette adresse IP correspond à l'interface connectée au réseau B sur le routeur voisin.

De même, vous devrez configurer une route statique sur le routeur connecté au réseau B pour permettre à ses périphériques d'accéder au réseau A. Voici comment cela peut être configuré sur ce routeur :

Router> enable
Router# configure terminal
Router(config)# ip route 192.168.1.0 255.255.255.0 10.0.0.2

Dans cet exemple :

    ip route indique que nous ajoutons une route statique.
    192.168.1.0 255.255.255.0 est la destination de la route (le réseau A).
    10.0.0.2 est la passerelle par défaut pour atteindre le réseau A à partir du réseau B. Assurez-vous que cette adresse IP correspond à l'interface connectée au réseau A sur le routeur voisin.

N'oubliez pas de sauvegarder la configuration après avoir ajouté les routes statiques pour vous assurer qu'elles seront persistantes après un redémarrage :

Router(config)# end
Router# copy running-config startup-config

Cela configure le routage statique de base pour permettre la communication entre les deux réseaux. Assurez-vous d'adapter ces exemples à votre configuration réseau réelle en remplaçant les adresses IP et les masques de sous-réseau par ceux de votre propre réseau.