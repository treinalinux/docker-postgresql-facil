# Commands psql

## logon on postgres with psql

```bash
psql -h 192.168.0.120 -p 5432 -U postgres -d postgres
```

## Create DATABASE

```postgres
postgres=# CREATE DATABASE treinalinux;
```

or

```postgres
CREATE DATABASE treinalinux2
    WITH
    OWNER = postgres
    ENCODING = 'UTF8'
    CONNECTION LIMIT = -1;
```

## List DATABASES

```postgres
postgres=# \l
```

## Delete DATABASE

```postgres
postgres=# DROP DATABASE treinalinux2;
```

## DATABASE current?

```postgres
postgres=# SELECT CURRENT_DATABASE();
```

## Conect in other DATABASE

```postgres
postgres=# \c treinalinux
Password:
psql (12.7 (Ubuntu 12.7-0ubuntu0.20.04.1), server 13.2 (Debian 13.2-1.pgdg100+1))
WARNING: psql major version 12, server major version 13.
```
