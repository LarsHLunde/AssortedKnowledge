# APEX install guide

This guide is made for running on Oracle Linux 7

## Packages needed
Oracle Database XE  
https://www.oracle.com/uk/database/technologies/xe-downloads.html  
  
Oracle APEX  
https://www.oracle.com/tools/downloads/apex-downloads.html  
  
Oracle JDK 11   
https://www.oracle.com/java/technologies/javase/jdk11-archive-downloads.html  
  
Add ORDS repo to config:  
https://yum.oracle.com/repo/OracleLinux/OL7/oracle/software/x86_64/  
  
  
## Installing pre-requisites
### Installing the ORDS repo
To install the yum repo for ORDS, just run the following commands  
```
echo "[ol7_software]" > /etc/yum.repos.d/oracle-software-ol7.repo
echo "name=Oracle Linux Software" >> /etc/yum.repos.d/oracle-software-ol7.repo
echo "baseurl=https://yum.oracle.com/repo/OracleLinux/OL7/oracle/software/x86_64/" >> /etc/yum.repos.d/oracle-software-ol7.repo
echo "gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle" >> /etc/yum.repos.d/oracle-software-ol7.repo
echo "gpgcheck=1" >> /etc/yum.repos.d/oracle-software-ol7.repo
echo "enabled=1" >> /etc/yum.repos.d/oracle-software-ol7.repo
```

### Install Oracle Database prerequisites
First we need to install the prerequisites package with:
```
yum install -y oracle-database-preinstall-21c
``` 
The script isn't great, so we need to run some manual code to make the user work correctly:  
(all done as root)  
```
cd
mkdir /home/oracle
cp -f .bashrc .bash_profile /home/oracle
chown oracle:oinstall -R /home/oracle
```

## Installing Database
As root, install the Oracle Database XE rpm file you downloaded from the link above:  
```
yum install -y ./oracle-database-xe-21c-1.0-1.ol7.x86_64.rpm
```

Change user to oracle  
```
su - oracle
```
The rest of this section is to be done entirely as the oracle user:  
  
Run the following commands:
```
export ORACLE_HOME=/opt/oracle/product/21c/dbhomeXE/
export PATH=$ORACLE_HOME/bin:$PATH
dbca
```

Install the Database in the normal way, in this example I'm calling  
the Container Database APEXCDB and the PDB APEXPDB

I would strongly advice adding this line to your Oracle users .bashrc file:  
```
export ORACLE_SID=APEXCDB
```  

Then we need to add the PDB to our TNSNAMES:  
/opt/oracle/homes/OraDBHome21cXE/network/admin/tnsnames.ora  
```
APEXPDB =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = localhost)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = APEXPDB)
    )
  )
```
set your enivonment with oraenv and try to log in to your PDB:

```
[oracle@apex ~]$ . oraenv
ORACLE_SID = [APEXCDB] ?
The Oracle base remains unchanged with value /opt/oracle
[oracle@apex ~]$ sqlplus sys/syspass@APEXPDB as sysdba

SQL*Plus: Release 21.0.0.0.0 - Production on Tue Aug 2 18:37:43 2022
Version 21.3.0.0.0

Copyright (c) 1982, 2021, Oracle.  All rights reserved.


Connected to:
Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0

SQL> exit
Disconnected from Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0
[oracle@apex ~]$
```

We now have a working database, unfortunatley,  
the database will not survive a reboot, and even after it restarts,  
the PDB we created will not autostart, so those are the 2 next steps.

### Adding a restart service

First step of adding a restart service is to add autostart to **/etc/oratab**.  
Swith this line:  
```
APEXCDB:/opt/oracle/product/21c/dbhomeXE:N
```
for this line:  
```
APEXCDB:/opt/oracle/product/21c/dbhomeXE:Y
```  
Then we add the following to the file **/etc/systemd/system/oracle-database.service** :   
```
[Unit]
Description=Oracle Database Service
After=syslog.target network.target

[Service]
RemainAfterExit=yes
User=oracle
Restart=no
ExecStart=/opt/oracle/product/21c/dbhomeXE/bin/dbstart /opt/oracle/product/21c/dbhomeXE
ExecStop=/opt/oracle/product/21c/dbhomeXE/bin/dbshut /opt/oracle/product/21c/dbhomeXE

[Install]
WantedBy=multi-user.target
```  
  
And enable the service with systemd:

```
sudo systemctl enable oracle-database
```

### Autostart PDB
By default, the PDB will not start on database startup.  
To remedy this you need to log in to the CDB and save the current running state.  
  
As oracle, set the oracle environment, log in to the cdb and run:  
```
alter pluggable database APEXPDB save state;
```  
Like so:  
```
[oracle@apex ~]$ . oraenv
ORACLE_SID = [APEXCDB] ?
The Oracle base remains unchanged with value /opt/oracle
[oracle@apex ~]$ sqlplus / as sysdba

SQL*Plus: Release 21.0.0.0.0 - Production on Wed Aug 3 07:01:13 2022
Version 21.3.0.0.0

Copyright (c) 1982, 2021, Oracle.  All rights reserved.


Connected to:
Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0

SQL> alter pluggable database APEXPDB save state;

Pluggable database altered.

SQL> exit
Disconnected from Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0
[oracle@apex ~]$
```  

## Installing APEX
### Preparations
For neatness sake we will put apex under **/opt/oracle/product/apex/**  
as oracle create the new apex directory and copy the APEX zip in to the new folder:  
```
mv apex_22.1_en.zip /opt/oracle/product
cd /opt/oracle/product
unzip apex_22.1_en.zip
```  

Before installing APEX on to the database we need to set up the pre-requisites for APEX:  
First we need to set db_create_file_dest, and create tablespaces for APEX.  
Set the oracle environment with . oraenv, log in to the PDB as sys,  
change db_create_file_dest to /opt/oracle/oradata/APEXCDB,
and create the a tablespace with these commands:  
```
alter system set db_create_file_dest='/opt/oracle/oradata/APEXCDB' scope=both;
CREATE TABLESPACE apex DATAFILE SIZE 100M AUTOEXTEND ON NEXT 1M;
```  
Example output:  
```
[oracle@apex product]$ . oraenv
ORACLE_SID = [APEXCDB] ?
The Oracle base remains unchanged with value /opt/oracle
[oracle@apex product]$ sqlplus sys/syspass@APEXPDB as sysdba

SQL*Plus: Release 21.0.0.0.0 - Production on Wed Aug 3 07:28:38 2022
Version 21.3.0.0.0

Copyright (c) 1982, 2021, Oracle.  All rights reserved.


Connected to:
Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0

SQL> alter system set db_create_file_dest='/opt/oracle/oradata/APEXCDB' scope=both;

System altered.

SQL> CREATE TABLESPACE apex DATAFILE SIZE 100M AUTOEXTEND ON NEXT 1M;

Tablespace created.

SQL> exit
Disconnected from Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0
[oracle@apex product]$
```  

### Installing APEX
The next step is to run the apex installer script in the database.  
As oracle, with the right oracle environment go to /opt/oracle/product/apex/,  
and log in as sys in to the PDB, from there run the apexins.sql script with:
```
@apexins.sql APEX APEX TEMP /i/
```  
Example output:  
```
[oracle@apex ~]$ . oraenv
ORACLE_SID = [APEXCDB] ?
The Oracle base remains unchanged with value /opt/oracle
[oracle@apex ~]$ cd /opt/oracle/product/apex/
[oracle@apex apex]$ sqlplus sys/syspass@APEXPDB as sysdba

SQL*Plus: Release 21.0.0.0.0 - Production on Wed Aug 3 07:36:01 2022
Version 21.3.0.0.0

Copyright (c) 1982, 2021, Oracle.  All rights reserved.


Connected to:
Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0

SQL> @apexins.sql APEX APEX TEMP /i/
...set_appun.sql

PL/SQL procedure successfully completed.
etc...
```    
This is will take a while, but once it's done, it is fully installed.  
  
The last piece of this section is changing the APEX passwords password,  
this can be done whenever and also unlocks the admin account if it locks.  

Log in to the PDB as previously in the same directory and run @apxchpwd.sql for admin:  
```
[oracle@apex apex]$ sqlplus sys/syspass@APEXPDB as sysdba

SQL*Plus: Release 21.0.0.0.0 - Production on Wed Aug 3 07:43:50 2022
Version 21.3.0.0.0

Copyright (c) 1982, 2021, Oracle.  All rights reserved.


Connected to:
Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0

SQL> @apxchpwd.sql
...set_appun.sql
================================================================================
This script can be used to change the password of an Oracle APEX
instance administrator. If the user does not yet exist, a user record will be
created.
================================================================================
Enter the administrator's username [ADMIN]
User "ADMIN" does not yet exist and will be created.
Enter ADMIN's email [ADMIN] admin@oracle.com
Enter ADMIN's password []
Created instance administrator ADMIN.

SQL> exit
Disconnected from Oracle Database 21c Express Edition Release 21.0.0.0.0 - Production
Version 21.3.0.0.0
[oracle@apex apex]$
```

and @apex_rest_config.sql for the REST users used by ORDS.  
  
Final thing is that the APEX users are locked by default, so log in to the PDB as SYS and run the following:  
```
ALTER USER APEX_220100 ACCOUNT UNLOCK;
ALTER USER APEX_PUBLIC_USER ACCOUNT UNLOCK;
```

## Installing ORDS
This section is done exclusively as root.  
Before installing ORDS, we need to install JDK11 which we downloaded in the first section  
```
yum install -y ./jdk-11*rpm
```  
  
Last part is the ORDS install, which hosts the frontend for APEX.  
First just install ORDS from the repo we set up in pre-requisites:  
```
yum install -y ords
```  

and run the configuration script with:  
```
ords --config /etc/ords/config install
```
I will just supply my install, and write the significant points that I needed to edit:
 - Enter the database service name [orcl]: APEXPDB
 - Enter the database password for SYS AS SYSDBA: 
 - Enter the APEX static resources location: /opt/oracle/product/apex/images
The rest can be left as defaults

```
[root@apex ~]# ords --config /etc/ords/config install

ORDS: Release 22.2 Production on Wed Aug 03 11:51:36 2022

Copyright (c) 2010, 2022, Oracle.

Configuration:
  /etc/ords/config/

The configuration folder /etc/ords/config does not contain any configuration files.

Oracle REST Data Services - Interactive Install

  Enter a number to select the type of installation
    [1] Install or upgrade ORDS in the database only
    [2] Create or update a database pool and install/upgrade ORDS in the database
    [3] Create or update a database pool only
  Choose [2]:
  Enter a number to select the database connection type to use
    [1] Basic (host name, port, service name)
    [2] TNS (TNS alias, TNS directory)
    [3] Custom database URL
  Choose [1]:
  Enter the database host name [localhost]:
  Enter the database listen port [1521]:
  Enter the database service name [orcl]: APEXPDB
  Provide database user name with administrator privileges.
    Enter the administrator username: sys
  Enter the database password for SYS AS SYSDBA:
Connecting to database user: SYS AS SYSDBA url: jdbc:oracle:thin:@//localhost:1521/APEXPDB

Retrieving information.
  Enter the default tablespace for ORDS_METADATA and ORDS_PUBLIC_USER [SYSAUX]:
  Enter the temporary tablespace for ORDS_METADATA and ORDS_PUBLIC_USER [TEMP]:
  Enter a number to select additional feature(s) to enable:
    [1] Database Actions  (Enables all features)
    [2] REST Enabled SQL and Database API
    [3] REST Enabled SQL
    [4] Database API
    [5] None
  Choose [1]:
  Enter a number to configure and start ORDS in standalone mode
    [1] Configure and start ORDS in standalone mode
    [2] Skip
  Choose [1]:
  Enter a number to use HTTP or HTTPS protocol
    [1] HTTP
    [2] HTTPS
  Choose [1]:
  Enter the HTTP port [8080]:
  Enter the APEX static resources location: /opt/oracle/product/apex/images
```

At some stage the output will stop with:  
```
2022-08-03T11:54:28.758Z INFO        Oracle REST Data Services initialized
Oracle REST Data Services version : 22.2.1.r2021302
Oracle REST Data Services server info: jetty/9.4.48.v20220622
Oracle REST Data Services java info: Java HotSpot(TM) 64-Bit Server VM 11.0.15.1+2-LTS-10
```
Which means it's running in the foreground, Ctrl+C out of there, and run it from systemd instead:  
```
[root@apex ~]# systemctl enable ords --now
Created symlink from /etc/systemd/system/multi-user.target.wants/ords.service to /etc/systemd/system/ords.service.
Created symlink from /etc/systemd/system/graphical.target.wants/ords.service to /etc/systemd/system/ords.service.
[root@apex ~]#
```

The frontend should now be running on the server on port 8080.
The first time you log in, you need to log in as admin on the internal workspace:  

