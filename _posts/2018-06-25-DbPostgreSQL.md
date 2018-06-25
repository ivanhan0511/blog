---
layout: post
title: PostgreSQL
---

Some tips about  PostgreSQL

mariadb100-server is marked broken in FreeBSD arm 12.0
Both mysql and mariadb are **sucks**, so go into PostgreSQL
The difference between these 3 systems is the path.

```shell
su - root
ports install postgresql10-server
pw user add postgres
chown postgres:postgres /var/db/postgres/data

su - postgres
initdb -D /var/db/postgres/data
postgres -D /var/db/postgres/data &
vi /var/db/postgres/data/pg_hba.conf
```
> host    all             all              0.0.0.0/0              md5

- To access into this DB remotely
  ```shell
  vi /var/db/postgres/data96/postgresql.conf
  ```
  > listen_addresses = '\*'

## Export and import database like below
```shell
pg_dump -U USERNAME DBNAME > dbexport.pgsql
#pg_dump -U USERNAME DBNAME -N topology -T spatial_ref_sys > dbexport.pgsql  # If with restricted access permissions
psql -U USERNAME DBNAME < dbexport.pgsql
```


### Installation
brew install postgresql@96
# 有postgres8.x已经安装了，所以产生了一个opt版本
echo 'export PATH="/usr/local/opt/postgresql@9.6/bin:$PATH"' >> ~/.zshrc
createuser -d -P postgres
mkdir -p /usr/local/var/db/postgresql96/defaultdb
sudo chown postgres:postgres /usr/local/var/db/postgresql96/defaultdb
sudo su postgres -c 'initdb -D /usr/local/var/db/postgresql96/defaultdb'
#sudo su postgres -c 'pg_ctl init -D /usr/local/var/db/postgresql96/defaultdb' # Use pg_ctl cli
#sudo su postgres -c 'initdb -D /var/lib/postgres/data' # In Manjaro system
sudo passwd postgres
sudo su postgres -c 'pg_ctl -D /usr/local/var/db/postgresql96/defaultdb start'
#sudo su postgres -c 'pg_ctl -D /usr/local/var/db/postgresql96/defaultdb -l /usr/local/var/db/postgresql96/postgres.log start'
#sudo su - postgres -c 'pg_ctl -D /var/lib/postgres/data -l /var/lib/postgres/data/postgres.log start'  # Manjaro
psql -U postgres

