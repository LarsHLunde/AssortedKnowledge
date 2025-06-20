# Postgres on OEL9
## Intro
I'm writing this mostly for myself.  
So it's gonna be quick and dirty.  
  
## Code
dnf install https://download.postgresql.org/pub/repos/yum/reporpms/EL-9-x86_64/pgdg-redhat-repo-latest.noarch.rpm -y  
dnf -qy module disable postgresql  
dnf install postgresql16-server -y  
/usr/pgsql-16/bin/postgresql-16-setup initdb  
systemctl enable postgresql-16 --now   
systemctl status postgresql-16  
  
## Backup manager  
yum install \*epel\* -y  
yum install pgbackrest -y  

mkdir -p /backup/pgbackrest/{archive,backup,conf}  
chown -R postgres:postgres /backup/pgbackrest  
chmod 750 /backup/pgbackrest  
touch /etc/pgbackrest.conf  
chown postgres:postgres /etc/pgbackrest.conf  
chmod 640 /etc/pgbackrest.conf  

## Random data table
yum install python3-pip -y  
pip3 install psycopg  
su - postgres  
psql  
```
CREATE DATABASE random_string_db;

\c random_string_db

CREATE TABLE random_strings (
    id SERIAL PRIMARY KEY,
    content TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

\q
```  

vi random-strings.py  
  
```
#!/usr/bin/env python3
import psycopg
import random
import string

def random_string(length=10):
    return ''.join(random.choices(string.ascii_letters + string.digits, k=length))

try:
    conn = psycopg.connect(dbname="random_string_db", user="postgres")
    cur = conn.cursor()
    cur.execute("INSERT INTO random_strings (content) VALUES (%s)", (random_string(),))
    conn.commit()
    cur.close()
    conn.close()
except Exception as e:
    print("Error:", e)
```  
  
python3 random-strings.py  
crontab -e  
```
* * * * * python3 random-strings.py
``` 
