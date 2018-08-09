# postgresql

## Manual initialization db

```console
$ /usr/pgsql-10/bin/postgresql-10-setup initdb
$ systemctl start postgresql-10
```

## Create database, user

```console
# CREATE DATABASE dbname;
# CREATE USER username WITH ENCRYPTED PASSWORD 'password';
# GRANT ALL PRIVILEGES ON DATABASE dbname TO username;
```

## Add permission (FOR STAGING ONLY)

*Set in file /var/lib/pgsql/10/data/postgresql.conf*
```code
listen_addresses = '*'
```

*Set in /var/lib/pgsql/10/data/pg_hba.conf*
```code
host  all all 0.0.0.0/0 trust
```

## Backup

```code
$ pg_dump -h localhost -U username -d dbname > `date +%Y-%m-%d_%H:%M`-backup.sql
```
