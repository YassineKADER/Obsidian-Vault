PL-SQL bloc:

```SQL
DECLARE
--declaration
	BEGIN
	--program
	Exception
	--exceptions handeling
END ;
--just begin and end are necessary
```

Variables:

```SQL
Vname type;--declaration of a variable
Vname := value;--initialization
Vname type := value; --declaration and initianlization
Vname [CONSTANT] datatype [NOT NULL] [:= | DEFAULT expression];
--Exemple:
name VARCHAR2(30);
name VARCHAR2(30) := ‘toto’;
```

Comments:

```SQL
--single comment
/* multi line comment */
```

Affectation from a table:

```SQL
Begin
	v_name varvhar2(30);
	SELECT ename INTO v_name FROM emp --where ....;
	--if we have multiple values
	SELECT ename, sal INTO v_ename, v_sal FROM emp WHERE ROWNUM = 1;
End;
```

Variables typées dynamiquement:

`Types composites adaptés à la récupération des colonnes et lignes des tables SQL :`

```SQL
%TYPE
%ROWTYPE
```

On peut déclarer qu’une variable est du même type qu’une colonne d’une table ou d’une vue (ou qu’une autre variable) :

```SQL
nom emp.name%TYPE;
```

Exemple:

![[Untitled 31.png|Untitled 31.png]]

Une variable peut contenir toutes les colonnes d’une ligne d’une table:

```SQL
employe emp%ROWTYPE;
```

déclare que la variable employe contiendra une ligne de la table emp.

![[Untitled 1 10.png|Untitled 1 10.png]]

Plusieurs façons de donner une valeur à une  
variable:  
  
`:=`  
  
`par la directive INTO de la requête SELECT`

![[Untitled 2 8.png|Untitled 2 8.png]]

![[Untitled 3 8.png|Untitled 3 8.png]]

Les corseurs:

Toutes les requêtes SQL sont associées à un curseur:  
 Ce curseur représente la zone mémoire utilisée pour analyser et exécuter la requête.  
 Le curseur peut être implicite (pas déclaré par l’utilisateur) ou explicite.  
 Les curseurs explicites servent à retourner plusieurs lignes avec un select.  

![[Untitled 4 8.png|Untitled 4 8.png]]

![[Untitled 5 6.png|Untitled 5 6.png]]

![[Untitled 6 5.png|Untitled 6 5.png]]

```SQL
CURSOR / nomcurseur / IS / requete / ;
--Example:
CURSOR emp_cur IS SELECT * FROM EMP ;
--Ouvrir un cursor
Open nimcurseur;
/*Lors de l'ouverture d'un curseur, la requête du curseur est
évaluée, et le curseur contient toutes les données retournées par la
requête. On ouvre un curseur dans une section BEGIN :*/
```

Read the rows of a cursor:

```SQL
FETCH / nom curseur / INTO / listevariables/;
--Example:
DECLARE
CURSOR emp_cur IS
SELECT * FROM emp ;
ligne emp_cur%rowtype ;
BEGIN
OPEN emp_cur ;
LOOP
FETCH emp_cur INTO ligne ;
EXIT WHEN emp_cur%NOTFOUND ;
DBMS_OUTPUT . PUT_LINE ( ligne . ename ) ;
END LOOP ;
/.../
END
```

to close a cursor after using it:

```SQL
close nom curseur;
```

Iterate a cursoe with `foor loop`

```SQL
ligne emp_cur%ROWTYPE;
FOR ligne IN emp_cur LOOP
/* Traitement */
END LOOP ;
```

curseur parametrer:

```SQL
CURSOR / nom / (/ liste des parametres /) IS / requete /
--Example:
CURSOR enfants (numparent NUMBER) IS
SELECT *
FROM personne
WHERE pere = numparent
OR mere = numparent ;

OPEN enfants ( 1 ) ;

FOR e IN enfants ( 1 ) LOOP
DBMS_OUTPUT.PUT_LINE(e.nompers ||" "|| e.prenompers) ;
END LOOP ;
```

Les procedeurs:

![[Untitled 7 5.png|Untitled 7 5.png]]

![[Untitled 8 4.png|Untitled 8 4.png]]

les fonctions:

![[Untitled 9 3.png|Untitled 9 3.png]]

![[Untitled 10 3.png|Untitled 10 3.png]]

Compilation et suppression:

![[Untitled 11 3.png|Untitled 11 3.png]]

Triggers:

```SQL
CREATE OR REPLACE TRIGGER myFirstTrigger
BEFORE UPDATE OF ename ON emp
FOR EACH ROW
WHEN(:old.ename = ‘Mabrouk’)
BEGIN
DBMS_OUTPUT.ENABLE(20000);
DBMS_OUTPUT.PUT_LINE(:OLD.ENAME||’ ‘||:NEW.ENAME);
EXCEPTION
WHEN OTHERS THEN
DBMS_OUTPUT.PUT_LINE(SQLERRM);
END;
SQL> UPDATE emp
SET ename = 'Durand'
WHERE empno = 7839;
SQL> Sami Durand
```

Triggers with multi events:

```SQL
CREATE OR REPLACE TRIGGER myFirstTrigger
AFTER UPDATE OR INSERT ON emp
FOR EACH ROW
BEGIN
DBMS_OUTPUT.ENABLE(20000);
IF INSERTING THEN
DBMS_OUTPUT.PUT_LINE(' INSERT ');
END IF;
IF UPDATING('ENAME') THEN
DBMS_OUTPUT.PUT_LINE(' UPDATED ' || :NEW.ENAME);
END IF;
END;
```

![[Untitled 12 2.png|Untitled 12 2.png]]