Work groue != Domain
Domain
	Materiel + Serveur (gestion cnetraliser)
	Active directory(AD): ;une service qui permit de gestion centraliser des donnees
	Controleur de domain(CD): c'est serveur qui execute active directory
		DNS: (Permet de localiser les resources)Necessaite un DNS
	Object de AD:
		Users, group of users, reseux IP, Site, Serveur ....
	Uniter d'organisation(UO):
		Conteneur (Dossier) qui permet de mettre des utilisateurs, des groupes, compte des ordinateurs, et permet d'appliquer les droits d'access (Strategies de groupe GPO: Group Policy Object)
	Groupe: C'est un groupe des utilisateur, ayant les memes droits, sur le quelle on applique les strategies des groups.
		Type de groupes:
			groupe de security: groupe normal quion peut creer
			groupe de distrubution: groupe de messagerie
		Type de niveux des groupes(on parle sur ou cette goup est connue):
			Local
			Global
			Universie
		Une site: ensemble des controleurs connecter entre eux
		Replication: une copie de donner dun serveur ou dcP
		Relation d'aprobation: les relation qui liee les domain et les foret enter eux(automatique au sein de meme foret, (manuelle) non automatique entre foret)