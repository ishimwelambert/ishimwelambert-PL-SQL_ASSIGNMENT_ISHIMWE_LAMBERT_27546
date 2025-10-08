# ishimwelambert-PL-SQL_ASSIGNMENT_ISHIMWE_LAMBERT_27546
# Oracle Database Assignment Report  
**Student Name:** Ishimwe Lambert  
**Student ID:** 27546  
**Course:** pl&sql
**Date:** October 8, 2025  

---

## Task 1: Create and Open a Pluggable Database (PDB)

### **Objective**
Create a new pluggable database (PDB) inside the Oracle 21c container database and configure it for access.

### **Steps Performed**
1. Logged in to Oracle SQL*Plus as SYSDBA:
   ```sql
   sqlplus / as sysdba
   ```

2. Created a new pluggable database:
   ```sql
   CREATE PLUGGABLE DATABASE LA_pdb_27546
   ADMIN USER LAMBERT_PLSQL_27546 IDENTIFIED BY "123"
   ROLES = (DBA)
   FILE_NAME_CONVERT = (
       'C:\app\ishim\product\21c\oradata\XE\PDBSEED\',
       'C:\app\ishim\product\21c\oradata\XE\LA_pdb_27546\'
   );
   ```
   #### screenshot:
   <img width="859" height="410" alt="creating pdb" src="https://github.com/user-attachments/assets/992e6711-09a6-404f-8f3e-94becc88b233" />


3. Opened the new PDB:
   ```sql
   ALTER SESSION SET CONTAINER = LA_pdb_27546;
   ALTER PLUGGABLE DATABASE OPEN READ WRITE;
   SHOW PDBS;
   ```

### **Result**
 Pluggable Database `LA_PDB_27546` created and opened successfully in **READ WRITE** mode.

---

## 🗂 Task 2: Create and Delete Another PDB

### **Objective**
Create and delete another PDB following the naming format:  
**FirstTwoLettersOfName_to_delete_pdb_StudentID**

Example: `la_to_delete_pdb_27546`

### **Steps Performed**
1. Created another pluggable database:
   ```sql
   CREATE PLUGGABLE DATABASE la_to_delete_pdb_27546
   ADMIN USER delete_admin IDENTIFIED BY "123"
   ROLES = (DBA)
   FILE_NAME_CONVERT = (
       'C:\app\ishim\product\21c\oradata\XE\PDBSEED\',
       'C:\app\ishim\product\21c\oradata\XE\la_to_delete_pdb_27546\'
   );
   ```

2. Verified creation:
   ```sql
   SHOW PDBS;
   ```
### screenshot:
<img width="886" height="511" alt="CREATE AND DELETE PDB" src="https://github.com/user-attachments/assets/8e6f2130-7e36-4f35-90df-f4cecd519bfd" />

3. Closed the PDB:
   ```sql
   ALTER PLUGGABLE DATABASE la_to_delete_pdb_27546 CLOSE IMMEDIATE;
   ```

4. Deleted it completely with datafiles:
   ```sql
   DROP PLUGGABLE DATABASE la_to_delete_pdb_27546 INCLUDING DATAFILES;
   ```
### screenshot:
<img width="817" height="418" alt="creat and delete pdb 2" src="https://github.com/user-attachments/assets/61cae486-3f7b-4f5e-88d9-187ad0933782" />

### **Result**
✅ PDB `la_to_delete_pdb_27546` successfully created and deleted.

---

## 🖥 Task 3: Configure Oracle Enterprise Manager (OEM)

### **Objective**
Configure and access **Oracle Enterprise Manager Database Express (OEM)** to monitor and manage the database.

### **Steps Performed**
1. Verified Oracle listener status:
   ```bash
   lsnrctl status
   ```
   - Listener **XE** active on port **1521**  
   - Service for `LA_PDB_27546` visible and READY  

2. Accessed Oracle Enterprise Manager:
   ```
   https://localhost:5500/em
   ```

3. Logged in with:
   - **Username:** `LAMBERT_PLSQL_27546`
   - **Password:** `123`
   - **Container Name:** `LA_PDB_27546`

4. Confirmed the dashboard loaded successfully, showing connection to the pluggable database.
### screenshot:
<img width="1353" height="618" alt="Oracle Enterprise Manager" src="https://github.com/user-attachments/assets/66189089-464d-469f-9aa6-45a13e3ad233" />


### **Result**
 Oracle Enterprise Manager configured successfully and connected to `LA_PDB_27546`.

---

##  Final Summary

All tasks — **PDB creation**, **deletion**, and **OEM configuration** — were completed successfully.  
This demonstrates strong understanding of **Oracle 21c multitenant architecture**, **container management**, and **database monitoring using OEM**.

---

### **Prepared by**
**Name:** Ishimwe Lambert  
**Date:** October 8, 2025  
**Subject:** pl&sql
