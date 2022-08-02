# APEX install guide

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

TODO: 
Oracle restart service
Oracle autostart PDB

## Installing APEX

## Installing ORDS
Before installing ORDS, we need to install JDK11  
```
yum install -y ./jdk-11*rpm
```  
