Work groue != Domain
Domain
	Materiel + Serveur (gestion cnetraliser)
	Active directory(AD): une service d'annuaire qui permit de gestion centraliser des donnees
	Controleur de domain(CD): c'est serveur qui execute active directory
		DNS: (Permet de localiser les resources)Necessaite un DNS
	Object de AD:
		Users, group of users, reseux IP, Site, Serveur ....
	Uniter d'organisation(UO):
		Conteneur (Dossier) qui permet de mettre des utilisateurs, des groupes, compte des ordinateurs, et permet d'appliquer les droits d'access (Strategies de groupe GPO: Group Policy Object)
	Groupe: C'est un groupe des utilisateur, ayant les memes droits, sur le quelle on applique les strategies des groups.
		Type de groupes:
			groupe de security: groupe normal qui contient des utlisateurs qu'on peut creer
			groupe de distrubution: groupe de messagerie
		Type de niveux des groupes(on parle sur ou cette goup est connue):
			Local
			Global au seins d'un aroborissant ou foret
			Universire au seins d'un foret ou pleusierus foret
		Une site: ensemble des controleurs connecter entre eux
		Replication: une copie de donner dun serveur ou dcP
		Relation d'aprobation: les relation qui liee les domain et les foret enter eux(automatique au sein de meme foret entre un domain et domain fille, (manuelle) non automatique entre foret)


search about dc promo
Niveu fonctionnel de la foret: old or new but in new installaition we need to choose the latest one  or depending or wath things that we will need on the dc
NTDS: c'est le fichier aui contient tous les information liee soit au objest ou etc.....

Role:DHCP, IIS, DNS etc...
Fonctionality:ajou des fonctionalities comme telechargement etc....
pourquoi ona besoin de migrer vers l'utilisation de domain?: pour la gestion centraliser

**Les etapes pour joindre un pc a domain:**
	1- il faut quil soit brancher au reseau
	2- il a besoin d'un adress ip
	3 - il a besoin d'adress de dns(si serveur loin)
	4- il a besoin de gateway
	5- migration de groupe de travail vers domain
on creer des groupe pour appliquer des droit commun a les membres de groupe

Remote desktop
start>outil administration> gestion serveur> bereu a distence
creation des dossier parteger+securiser seule utilisateur peut l'acceder

\\ipadress
lecteur reseau:
	il ne permet d'acceder a un dossier via une lecteur
	users/profile/connecter/<chemainde dossier partager/\%username\%>
	