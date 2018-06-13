---
layout: post
title: PostgreSQL
---

Deployment PostgreSQL in RaspberryPi3.

mariadb100-server is marked broken in FreeBSD arm 12.0
Both mysql and mariadb are **sucks**, so go into PostgreSQL
The difference between these 3 systems is the path.
As example of FreeBSD

```shell
su root
ports install postgresql10-server
pw user add postgres
chown postgres:postgres /var/db/postgres/data

su - postgres
initdb -D /var/db/postgres/data
postgres -D /var/db/postgres/data &
vi /var/db/postgres/data/pg_hba.conf
```
> host    all             all              0.0.0.0/0              md5

```shell
vi /var/db/postgres/data96/postgresql.conf
```
> listen_addresses = '\*'

Export and import database like below
```shell
pg_dump -U USERNAME DBNAME > dbexport.pgsql
#pg_dump -U USERNAME DBNAME -N topology -T spatial_ref_sys > dbexport.pgsql  # If with restricted access permissions
psql -U USERNAME DBNAME < dbexport.pgsql
```

