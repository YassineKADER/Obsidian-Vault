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

**Gestion des utilisateurs, privilèges et rôles**

1. **Connect as SYS and Create emp_isil Table:**
    
    - `sqlplus sys as sysdba`
    - `create table emp_isil (id_emp, nom, prenom, salaire);`
2. **Insert Rows into emp_isil Table.**
    
3. **Create user_isil User with Password Policy:**
    
    - `create user user_isil identified by password quota 100M on users;`
4. **Create R_isil Role:**
    
    - `create role R_isil;`
5. **Grant Privileges to R_isil Role:**
    
    - `grant create session, create table, select on emp_isil to R_isil;`
6. **Grant R_isil Role to user_isil:**
    
    - `grant R_isil to user_isil;`
7. **View Roles Granted to user_isil:**
    
    - `select * from dba_role_privs where grantee = 'USER_ISIL';`