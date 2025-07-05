# Data-Driven-Store
Projeto final da disciplina: Banco de Dados Relacional e Não Relacional

Este projeto contém um conjunto de serviços em containers Docker: Redis, PostgreSQL, MongoDB, ClickHouse e Neo4j.  
Este README orienta como instalar, configurar e executar esses containers usando Docker Compose.

---

## Pré-requisitos

- Docker instalado na sua máquina  
- Docker Compose instalado na sua máquina

---

## Passos para rodar os containers

1. **Clone este repositório**

```bash
git clone <URL_DO_REPOSITORIO>
cd <NOME_DA_PASTA>
```

2. **Verifique o arquivo `docker-compose.yml`**

Certifique-se que o arquivo `docker-compose.yml` está na raiz do projeto. Ele define os serviços e volumes utilizados:

- Redis na porta 6379  
- PostgreSQL na porta 5432  
- MongoDB na porta 27017  
- ClickHouse nas portas 8123 (HTTP) e 9000 (TCP)  
- Neo4j nas portas 7474 (HTTP) e 7687 (Bolt)  

3. **Inicie os containers**

Rode o comando para subir os containers em segundo plano:

```bash
docker-compose up -d
```

4. **Verifique se os containers estão rodando**

```bash
docker ps
```

Deve aparecer os containers: `redis-server`, `postgres-db`, `mongodb`, `clickhouse-server` e `neo4j`.

---

## Configurações dos serviços

### Redis

- Container: `redis-server`  
- Porta: `6379`  
- Volume persistente: `redis_data`

### PostgreSQL

- Container: `postgres-db`  
- Porta: `5432`  
- Usuário: `admin`  
- Senha: `admin`  
- Banco de dados: `mydatabase`  
- Volume persistente: `postgres_data`

### MongoDB

- Container: `mongodb`  
- Porta: `27017`  
- Usuário root: `admin`  
- Senha root: `admin`  
- Volume persistente: `mongodb_data`

### ClickHouse

- Container: `clickhouse-server`  
- Portas: `8123` (HTTP), `9000` (TCP)
- Usuário root: `admin`  
- Senha root: `admin123`  
- Volume persistente: `clickhouse_data`  
- Arquivo de configuração customizado: `./config/users.xml` mapeado para `/etc/clickhouse-server/users.d/custom-user.xml`

### Neo4j

- Container: `neo4j`  
- Portas: `7474` (HTTP), `7687` (Bolt)  
- Usuário/senha: `neo4j` / `adminegm2025`  
- Plugins ativados: `apoc`  
- Volume persistente: `neo4j_data`

---

## Parar os containers

Para parar todos os containers, rode:

```bash
docker-compose down
```

---

## Observações

- Os dados de cada serviço são armazenados em volumes Docker locais para garantir persistência.  
- O serviço ClickHouse utiliza um arquivo de configuração personalizado, que deve estar presente na pasta `./config` ao lado do `docker-compose.yml`.  
- Para acessar os serviços externamente, utilize as portas mapeadas informadas acima.

---

Se precisar de ajuda, abra uma issue ou entre em contato!

