# Configuração de Servidor Node.js com TypeScript e Express

Este guia fornece os comandos iniciais para configurar e executar um servidor básico usando Node.js, TypeScript e Express.

## Pré-requisitos

Certifique-se de que você tenha as seguintes ferramentas instaladas:

- [Node.js](https://nodejs.org/) (inclui npm)
- [Git](https://git-scm.com/)

## Passo a Passo

1. **Crie um Novo Projeto**  
   Abra o terminal e execute os seguintes comandos:  
   ```bash
   mkdir meu-projeto
   cd meu-projeto
   npm init -y

2-instale dependencias 

npm install express
npm install typescript ts-node @types/node @types/express --save-dev

3-instale o tsc

npx tsc --init

4-crie a estrutura de diretorios

mkdir src
touch src/index.ts

5-escreva o codigo no servidor
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

6-Adicione Scripts no package.json

---------------------------------------

"scripts": {
  "start": "node dist/index.js",
  "dev": "ts-node src/index.ts"
}

---------------------------------------

7-executar o servidor

npm run dev



