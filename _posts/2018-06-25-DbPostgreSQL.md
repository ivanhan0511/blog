---
layout: post
title: PostgreSQL
---

Some tips about  PostgreSQL in three different systems and the differences are `path`.

## Install and init
---
### Install
- Manjaro OS
  ```shell
  sudo yaourt -S postgres
  ```

- macOSX
  ```shell
  #有postgres8.x已经安装了，所以产生了一个opt版本
  brew install postgresql@96
  echo 'export PATH="/usr/local/opt/postgresql@9.6/bin:$PATH"' >> ~/.zshrc
  ```

- FreeBSD
  ```shell
  su - root
  ports install postgresql10-server
  ```

### Create user
- Manjaro OS

- macOSX
  ```shell
  createuser -d -P postgres
  mkdir -p /usr/local/var/db/postgresql96/defaultdb
  sudo chown postgres:postgres /usr/local/var/db/postgresql96/defaultdb
  sudo passwd postgres
  ```

- FreeBSD
  ```shell
  pw user add postgres
  chown postgres:postgres /var/db/postgres/data
  ```


### init
- Manjaro OS
  ```shell
  sudo su - postgres -c 'pg_ctl -D /var/lib/postgres/data -l /var/lib/postgres/data/postgres.log start'  # Manjaro
  ```

- macOSX
  ```shell
  sudo su postgres -c 'pg_ctl init -D /usr/local/var/db/postgresql96/defaultdb'
  sudo su postgres -c 'pg_ctl -D /usr/local/var/db/postgresql96/defaultdb -l /usr/local/var/db/postgresql96/postgres.log start'
  ```

- FreeBSD
  ```shell
  su - postgres
  initdb -D /var/db/postgres/data
  postgres -D /var/db/postgres/data &
  ```


### access remotely
- step 1
  ```sh  ell
  vi /var/db/postgres/data/pg_hba.conf
  ```
  > host  all   all 0.0.0.0/0   md5
- step 2
  ```shell
  vi /var/db/postgres/data96/postgresql.conf
  ```
  > listen_addresses = '\*'


## Client
```shell
psql -U postgres
```




## Export and import database like below
---
### Export
```shell
pg_dump -U USERNAME DBNAME > dbexport.pgsql
# If with restricted access permissions
pg_dump -U USERNAME DBNAME -N topology -T spatial_ref_sys > dbexport.pgsql  
```

### Import
```shell
psql -U USERNAME DBNAME < dbexport.pgsql
```


