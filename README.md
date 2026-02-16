# oracle_pdb_ass_II_28797_salem

## 
Repository Link: 
Plugabble database PDB Name Created: [sa_pdb_28840]

--

## Overview

This assignment involved working with Oracle Database 21C Express Version using the multitenant architecture. The tasks included creating, configuring  and managing Pluggable Databases (PDBs), this was done by creating users inside the PDB, create and then delete a temporary PDB, and lastly accessing the Oracle Enterprise Manager (OEM) to monitor the database environment. The assignment was all about demonstrating practical skills in database administration and Pluggable Databas PDBS management.


## Oracle Environment Used

- Oracle Database Version: 21C XE
- Tool Used: SQL Developer , SQLPLUS
- OEM: Oracle Enterprise Manager Express


                               TASK 1
  
      Create a New Pluggable Database(PDBS)

A new Pluggable Database (PDB) was created following the required naming convention. The PDB was opened in READ WRITE mode.
This how the pdb was created; 

create PLUGGABLE DATABASE sa_pdb_28797
ADMIN USER pdbadmin IDENTIFIED BY auca
FILE_NAME_CONVERT = ('pdbseed','sa_pdb_28797');
                         
                         creating the user in our PDB
And afterwards a local user was then created inside that pdb with the necessary privileges for future coursework.
--
CREATE USER salem_plsqlauca_28797 IDENTIFIED BY auca;

This is how i verified if the recently created user was added to that pdb:
--
SELECT username FROM dba_users WHERE username = 'BENJAMIN_PLSQLAUCA_28840';

                          TASK 2
                          
  ## overview

A temporary PDB was created using the specified naming format as it was indicated . The next was to verify it's creation, then it was properly closed and then  deleted completely, including its data files. Then lastly the final verification was to confirm that the PDB no longer exists. 

At first we have to make our PDB open by thr root user cause is the one with the privilege to create and delete pdbs;
 --
ALTER SESSION SET CONTAINER= cdb$root;
 
 After we created that temporary PDB like shown below:
  --Create a temporary PDB
CREATE PLUGGABLE DATABASE sa_to_delete_pdb_28797 
ADMIN USER salem_plsqlauca_28797 IDENTIFIED BY auca
FILE_NAME_CONVERT = ('pdbseed', 'sa_to_delete_pdb_28797');
 
 Next was to dellete /drop the temp pbs,but before dropping it completely we have to close first that PDB we open before:

ALTER PLUGGABLE DATABASE sa_to_delete_pdb_28797 CLOSE IMMEDIATE;
then after we
-- Delete the created temporary pdb like follow:

 DROP PLUGGABLE DATABASE sa_to_delete_pdb_28797 INCLUDING DATAFILES;



                         TASK 3
Oracle Enterprise Manager Express was configured and accessed through the browser. The dashboard was used to verify the Oracle environment, confirm the created PDB, and display the user account created inside the PDB. as shown below in the image this is display out of that browser where you login from.


<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/6cbc69f0-266c-4ec2-a2a1-be1cb8b0942f" />



                         Conclusion

This tasks improve understanding of Oracle Multitenant Architecture, PDB lifecycle management, user administration, and Oracle Enterprise Manager monitoring.
