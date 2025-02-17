## Descrição

Este projeto consiste em uma API RESTful desenvolvida utilizando o framework NestJS para gerenciar contas bancárias, pagamentos e relatórios de transações, além de implementar funcionalidades de autenticação baseada em JWT e upload de imagens para Amazon S3.

## Tecnologias Utilizadas
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white)
![NestJS](https://img.shields.io/badge/nestjs-%23E0234E.svg?style=for-the-badge&logo=nestjs&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-3982CE?style=for-the-badge&logo=Prisma&logoColor=white)
![Jest](https://img.shields.io/badge/-jest-%23C21325?style=for-the-badge&logo=jest&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Amazon S3](https://img.shields.io/badge/AMAZON%20S3-%23FF9900.svg?style=for-the-badge&logo=aws&logoColor=white)

## Instalação e configuração do projeto

## Pré-requisitos

- Docker instalado na máquina local.
- Docker Compose instalado na máquina local.

## 1. Configuração do arquivo `.env`

- Crie o arquivo .env na raiz do projeto as seguintes informações:

```properties
DATABASE_URL="postgresql://postgres:myP$W@localhost:5432/eabankdb?schema=public"

POSTGRES_DB=eabankdb
POSTGRES_USER=postgres
POSTGRES_PASSWORD=eabankP$W
```

- Estas variáveis serão utilizadas pelo Docker Compose para configurar o banco de dados.

## 2. Suba o banco de dados PostgreSQL com o Docker Compose

- Execute o seguinte comando para construir e iniciar os serviços definidos no docker-compose.yml:

```bash
$ docker-compose up -d --build
```

- verifique se os container subiram corretamente:

```bash
$ docker-compose ps
```

- Você deverá ver algo semelhante a isso:

```bash
   Name              Command                State           Ports
--------------------------------------------------------------------
pgadmin       /entrypoint.sh                  Up       0.0.0.0:80->80/tcp
postgresdb    docker-entrypoint.sh postgres   Up       0.0.0.0:5432->5432/tcp
```

## Acessar o pgAdmin

- Se necessário, você pode acessar o pgAdmin para gerenciar o banco de dados PostgreSQL. Abra um navegador e vá para http://localhost:80.

- Use as credenciais configuradas no docker-compose.yml (PGADMIN_DEFAULT_EMAIL e PGADMIN_DEFAULT_PASSWORD).

## Variáveis do Amazon S3

- Adicione ao final do arquivo .env as seguintes variáveis para conexão do módulo de upload de arquivos

```properties
AWS_S3_REGION=us-east-2
AWS_ACCESS_KEY_ID=AAAABBBBCCCCDDDDEEEE
AWS_SECRET_ACCESS_KEY=abcdefghij1234567890abcdefghij123/456789
```
- Criar um ```bucket``` no S3 com o nome ```ea-bank-payment-voucher``` (desabilitar o bloqueio do acesso público)

## Instalação

```bash
$ npm install
```

## Aplicando as migrações do banco de dados:

```bash
# Ambiente de desenvolvimento
$ npx prisma migrate dev

# Ambiente de produção
$ npx prisma migrate deploy
```

## Iniciando o App

```bash
# desenvolvimento
$ npm run start

# desenvolvimento com modo de observação (watch mode)
$ npm run start:dev

# produçao
$ npm run start:prod
```

## Testes

```bash
# testes unitários
$ npm run test
```
