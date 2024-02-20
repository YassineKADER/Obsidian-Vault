# DBA
## Class Notes
Shutdown:
Abort: shutdown sur place + possibility de recuperer les donnees
immediate: shutdown sur place
transactional: shutdown when validation/annulations de transaction
normal: quitter sur place
init.ora
dba_user //database has all informations of all users
```sql
--question 1
GRANT UPDATE (adresse) ON emp TO Ali;

GRANT INSERT (nemp, nom, prenom) ON emp TO Ali;

--question 2
GRANT CONNECT TO lila WITH ADMIN OPTION;
GRANT RESOURCE TO laila WITH ADMIN OPTION;

--question 3 
CREATE ROLE R;
GRANT ALL PRIVILEGES ON emp TO R;
GRANT CREATE SESSION, CREATE ANY TABLE TO R;

--question 4
GRANT R TO Khalid WITH ADMIN OPTION;
```
```sql
Connect sys / as sysdba
```
## Tp 1
### Gestion d’Instance et de Base de données ORACLE
1. **Startup Options:**
    - `startup`: Normal startup.
    - `startup nomount`: Starts the instance without mounting the database.
    - `startup mount`: Starts the instance and mounts the database.
    - `startup force`: Starts the database even if it's in an inconsistent state.
2. **Shutdown Options:**
    - `shutdown normal`: Waits for active transactions to complete.
    - `shutdown immediate`: Shuts down the database immediately.
    - `shutdown transactional`: Shuts down after active transactions complete.
    - `shutdown abort`: Shuts down the database abruptly.
3. **Connect as SYS and Stop the Database:**
    - `sqlplus sys as sysdba`
    - `shutdown;`
4. **Connect as SYS and Start Database with PFILE:**
    - `sqlplus sys as sysdba`
    - `startup pfile=init.ora;`
5. **Stop Database and Open in Read-Only Mode:**
    - `shutdown immediate;`
    - `startup mount;`
    - `alter database open read only;`
6. **Connect as HR, View Table Content:**
    - `sqlplus hr/hr`
    - `select * from regions;`
7. **Insert Row into REGIONS Table as HR User:**
    - `insert into regions values (...);`
8. **Switch Database to Read-Write Mode:**
    - `shutdown immediate;`
    - `startup;`
9. **Insert Row into REGIONS Table without Committing:**
    - Insert row without committing.
10. **Start SQL*Plus as SYSDBA and Perform Transactional Shutdown:**
    - `sqlplus sys as sysdba`
    - `shutdown transactional;`
11. **Undo HR Session Insertion, Then Exit:**
    - Rollback insertion in HR session.
    - Check impact in HR and SYS sessions.
12. **Connect as SYS and Start Database:**
    - `sqlplus sys as sysdba`
    - `startup;`
13. **Start Another Session as HR User.**
14. **Enable Restricted Session as SYS User.**
15. **Attempt Select Operation in HR Session.**
16. **Reconnect as HR User and Observe.**
17. **Disable Restricted Session as SYS User.**

### Gestion des utilisateurs, privilèges et rôles**
**1. Open SQL*Plus Session as user_isil and Display Username:**

- Command: `sqlplus user_isil/password`
- Response: `Connected to Oracle Database as USER_ISIL`

**2. In user_isil Session, Check Object Privileges Granted:**

- Command: `select * from user_tab_privs;`

**3. In user_isil Session, Check System Privileges Granted:**

- Command: `select * from user_sys_privs;`

**4. In user_isil Session, Check Roles Granted:**

- Command: `select * from user_role_privs;`

**5. Display Contents of emp_isil Table:**

- Command: `select * from emp_isil;`

**6. In Nom_isil Session, Create service Table:**

`create table service (     id number,     libelle varchar(15) );`

**7. In system Session, Remove 'CREATE TABLE' Privilege from R_isil Role:**

- Command: `revoke create table from R_isil;`

**8. View Updated Privileges of R_isil Role:**

- Command: `select * from dba_sys_privs where grantee = 'R_ISIL';`

**9. In Nom_isil Session, Create emp Table:**

`create table emp (     id_emp,     nom,     prenom,     salaire );`

**10. Revoke Role from Nom_isil User:** - Command: `revoke R_isil from Nom_isil;`

**11. In Nom_isil Session, Display Granted Roles:** - Command: `select * from session_roles;`

**12. Grant R_isil Role to All Database Users:** - Command: `grant R_isil to public;`

**13. View Updated Roles Granted to Nom_isil User:** - Command: `select * from user_role_privs where grantee = 'NOM_ISIL';`

**14. Revoke Role from Nom_isil User:** - Command: `revoke R_isil from Nom_isil;`

**15. From system Session, Grant Salary Modification Right to Nom_isil User:** - Command: `grant update (salaire) on emp_isil to Nom_isil;`

**16. In Nom_isil Session, Attempt Salary Modification:** - Command: `update emp_isil set salaire = salaire + 500 where ...;`

**17. Display Column-Level Privileges Granted to Nom_isil User:** - Command: `select table_name, column_name, privilege from user_tab_privs where grantee = 'NOM_ISIL';`

If a user needs to be defined, use the following command to create a user in Oracle 21c:

`CREATE USER username IDENTIFIED BY password;`

Replace `username` with the desired username and `password` with the desired password.