![[Untitled 48.png|Untitled 48.png]]

`**Sécurité:**` les groupes contenant des données sensibles sont séparés du reste du réseau, ce qui diminue les risques de violation de confidentialité. Comme l'illustre la figure, les ordinateurs du personnel enseignant se trouvent sur le VLAN 10 et sont complètement séparés du trafic des données des étudiants et des invités.

`**Réduction des coûts**``:` des économies sont réalisées grâce à une diminution des mises à niveau onéreuses du réseau et à l'utilisation plus efficace de la bande passante et des liaisons montantes existantes.

`**Meilleures performances:**`

le fait de diviser des réseaux linéaires de couche 2 en plusieurs groupes de travail logiques (domaines de diffusion) réduit la quantité de trafic inutile sur le réseau et augmente les performances.

`**Réduction des domaines de diffusion:**`- la division d'un réseau en VLAN réduit le nombre de périphériques dans le domaine de diffusion.  
Comme l'illustre la figure, il y a six ordinateurs dans ce réseau, mais seulement trois domaines de diffusion : Personnel, Étudiant et Invité.  

`**Efficacité accrue du personnel informatique:**` les VLAN facilitent la gestion du réseau, car les utilisateurs ayant des besoins réseau similaires partagent le même VLAN. Lorsque vous configurez un nouveau commutateur, toutes les stratégies et procédures déjà configurées pour le VLAN correspondant sont implémentées lorsque les ports sont affectés. Le personnel informatique peut aussi identifier facilement la fonction d'un VLAN en lui donnant un nom approprié. Dans la figure, pour qu'ils puissent être facilement identifiables, le VLAN 10 a été nommé « Personnel », le VLAN 20, « Étudiant » et le VLAN 30, « Invité ».

`**Gestion simplifiée de projets et d'applications**``:` les VLAN rassemblent des utilisateurs et des périphériques réseau pour prendre en charge des impératifs commerciaux ou géographiques. La séparation des fonctions facilite la gestion d'un projet ou l'utilisation d'une application spécialisée. Une plate-forme de développement d'e-learning  
pour le personnel enseignant est un exemple de ce type d'application.