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

-   user: pgadmin4@pgadmin.org
-   password: admin

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

-   fenglc/pgadmin4](https://hub.docker.com/r/fenglc/pgadmin4)
