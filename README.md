# Configuração de Servidor Node.js com TypeScript e Express e prisma

Este guia fornece os comandos iniciais para configurar e executar um servidor básico usando Node.js, TypeScript e Express. Junto com Conexao prisma!

## Pré-requisitos

Certifique-se de que você tenha as seguintes ferramentas instaladas:

- [Node.js](https://nodejs.org/) (inclui npm)
- [Git](https://git-scm.com/)

## Passo a Passo

##1. **Crie um Novo Projeto**  
---------------------------------------
   Abra o terminal e execute os seguintes comandos:  
   bash
   mkdir meu-projeto
   cd meu-projeto
   npm init -y}
---------------------------------------

##2-Instale as Dependências 
---------------------------------------

npm install express
npm install typescript ts-node @types/node @types/express --save-dev

---------------------------------------

##3-Configure o TypeScript
---------------------------------------

npx tsc --init

---------------------------------------
##4-Crie a Estrutura de Diretórios
---------------------------------------

mkdir src
touch src/index.ts

---------------------------------------

##5-Escreva o Código do Servidor

---------------------------------------

import express from 'express';

const app = express();
const PORT = 3000;

// Middleware para analisar JSON
app.use(express.json());

// Rota de exemplo
app.get('/', (req, res) => {
  res.send('Olá, mundo!');
});

// Iniciando o servidor
app.listen(PORT, () => {
  console.log(`Servidor rodando na porta ${PORT}`);
});

---------------------------------------

##6-Adicione Scripts no package.json

---------------------------------------

"scripts": {
  "start": "node dist/index.js",
  "dev": "ts-node src/index.ts"
}

---------------------------------------

##7-Execute o Servidor
---------------------------------------

npm run dev

---------------------------------------

##8-instale o nodemon e o helmet
---------------------------------------

npm install nodemon --save-dev
npm install helmet

---------------------------------------

##9-configuraçao do nodemon
---------------------------------------
"scripts": {
  "start": "node dist/index.js",
  "dev": "nodemon src/index.ts"
}
---------------------------------------

##10-Usando Helmet

---------------------------------------

import helmet from 'helmet';

// Adicione este middleware antes de suas rotas
app.use(helmet());

---------------------------------------

#Configurando Banco com prisma##

##1-instale o prisma npm 

---------------------------------------

install prisma --save-dev
npm install @prisma/client

---------------------------------------

##2-Inicialize o Prisma

---------------------------------------
npx prisma init
---------------------------------------

##3-Configure o .env

---------------------------------------

DATABASE_URL="mysql://USERNAME:(nome)tPASSWORD@localhost:porta/nome-do-banco"

---------------------------------------

##4-Crie o Modelo no schema.prisma

---------------------------------------

datasource db {
  provider = "mysql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}

model User {
  id    Int    @id @default(autoincrement())
  name  String
  email String @unique
}

---------------------------------------
##5-Execute a Migração

---------------------------------------

npx prisma migrate dev --name init

---------------------------------------
