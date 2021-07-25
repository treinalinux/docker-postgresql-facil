# Docker Postgresql Fácil

Não quer ser DBA e somente desenvolver, mas tem problemas com o banco de dados?

Escolheu o repositório certo, até porque se tiver problemas é só apagar o container e criar de novo, vamos lá:


## Passo 1 - Criando o banco de dados PostegreSQL

```bash
docker run --name postgres -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres
```

## Passo 2 - Criando o pgadmin4 para administração

```bash
docker run --name my_pgadmin4 -p 5050:5050 -d fenglc/pgadmin4
```

## Passo 3 - Logar no pgadmin4

Acesso o seu navegador no endereço http://SeuIP:porta, exemplo:

```
http://192.168.0.120:5050
```

Segue o usuário e senha do pgadmin4:

- user: pgadmin4@pgadmin.org
- password: admin


## Deu ruim no banco, e agora?

É simples, remove os containers criados:

```bash
docker rm postgres                                                               
```

```bash
docker rm my_pgadmin4
```

---
## Docker Hub
- fenglc/pgadmin4](https://hub.docker.com/r/fenglc/pgadmin4)


---
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
         Some psql features might not work.
You are now connected to database "treinalinux" as user "postgres".
```

## Create Table

For create new tables you need you know [DATATYPES](https://www.postgresql.org/docs/12/datatype.html)

See data types much used:

-   integer -> signed four-byte integer
-   real -> single precision floating-point number (4 bytes)
-   serial -> autoincrementing four-byte integer
-   numeric -> exact numeric of selectable precision
-   char (n) -> fixed-length character string
-   varchar (n) -> variable-length character string
-   text -> variable-length character string
-   boolean -> logical Boolean (true/false)
-   date -> calendar date (year, month, day)
-   timestamp -> date and time (no time zone)

```postgres
CREATE TABLE aluno (
	id SERIAL,
	nome VARCHAR(255),
	cpf CHAR(11),
	observacao TEXT,
	idade INTEGER,
	dinheiro NUMERIC(10,2),
	altura REAL,
	ativo BOOLEAN,
	hora_aula TIME,
	matriculado_em TIMESTAMP
);
```

## Select table

```postgres
treinalinux=# SELECT * FROM aluno;
 id | nome | cpf | observacao | idade | dinheiro | altura | ativo | hora_aula | matriculado_em
----+------+-----+------------+-------+----------+--------+-------+-----------+----------------
(0 rows)

```
