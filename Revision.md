- QCM
	- Composent de serveur oracle
		Les modes de demarrage d'instance
		Les interaction entre eux
- Gestion des utilisateurs
	Les priviliges
	Les Tables spaces(ajouter maximiser etc...)
	les Vues, les types de vues(statique, dynamique)
- DW
	type de modelisation(ETL, MDX,OLAP, DATAMART)
	Tables deimension et fait

les operation de trie execute sur les tables space temporaire(example: Order BY)
alter databse archivelog;/ alter database no archivelog;
les fichier neccessaire pour le fonctionnement de bd:
	1 fichier de donner
	1 fichier de controle
	2 fichier de jornalisation au moins, au cas ou une fichier saturer, le db switch a l'autre fichier

Procedure d'execution d'un request d'interogation et la transaction comment le serveur interagit ?;
parsing, analyse, fitch
lberary cash: plan d'exucution d'un request
pga se utiliser dans les request d'interogation, il ne utilse pas dans les transaction.