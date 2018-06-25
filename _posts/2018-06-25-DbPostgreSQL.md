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
  ```shell
  createuser -d -P postgres
  sudo chown postgres:postgres /var/lib/postgres/data
  sudo mkdir /run/postgresql
  sudo chown postgres:postgres /run/postgresql
  ```

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
  sudo su - postgres -c 'pg_ctl init -D /var/lib/postgres/data -l /var/lib/postgres/data/postgres.log'
  sudo su - postgres -c 'pg_ctl -D /var/lib/postgres/data -l /var/lib/postgres/data/postgres.log start'
  ```

- macOSX
  ```shell
  sudo su postgres -c 'pg_ctl init -D /usr/local/var/db/postgresql96/defaultdb -l /usr/local/var/db/postgresql96/postgres.log'
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


## Operations
---
### Preparation
- Login
  ```shell
  psql -U postgres
  ```
- Setup password for user `postgres`
  ```shell
    \password postgres
  ```
- Create a DB user
  ```shell
  CREATE USER dbuser WITH PASSWORD 'password';
  ```
- Create DB which is owned by `postgres`
  ```shell
  CREATE DATABASE mqtt_api OWNER postgres;
  ```
- Grant privilege
  ```shell
  GRANT ALL PRIVILEGES ON DATABASE mqtt_api to postgres;
  ```

### Login example
```shell
psql -U postgres -d mqtt_api -h 127.0.0.1 -p 5432
```

### Operations in DB
- Create a new table
  ```sql
  CREATE TABLE user_tbl(name VARCHAR(20), signup_date DATE);
  ```

- Insert data
  ```sql
  INSERT INTO user_tbl(name, signup_date) VALUES('Tom', '2018-06-25');
  ```

- Query
  ```sql
  SELECT * FROM user_tbl;
  ```

- Update
  ```shell
  UPDATE user_tbl set name = 'Tom' WHERE name = 'Kaden';
  ```

- Delete
  ```shell
  DELETE FROM user_tbl WHERE name = '李四' ;
  ```

- Add column
  ```shell
  ALTER TABLE user_tbl ADD email VARCHAR(40);
  ```

- Insert column after a colum
  ```shell
  ALTER TABLE user_tbl ALTER COLUMN signup_date SET NOT NULL;
  ```

- Alter column name
  ```shell
  ALTER TABLE user_tbl RENAME COLUMN signup_date TO signup;
  ```

- Delete column
  ```shell
  ALTER TABLE user_tbl DROP COLUMN email;
  ```

- Update table name
  ```shell
  ALTER TABLE user_tbl RENAME TO backup_tbl;
  ```

- Delete table
  ```shell
  DROP TABLE IF EXISTS backup_tbl;
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


