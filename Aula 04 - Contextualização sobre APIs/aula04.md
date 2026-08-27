# Resumo da Aula: Consumindo APIs no Front-end

**Disciplina:** Frameworks Front-end
**Professor:** Me. Deivison S. Takatu (deivison.takatu@edu.senai.br)

---

## 1. API (Application Programming Interface)

Uma API é um conjunto de protocolos, rotinas e ferramentas para construção de software. Ela define como diferentes componentes de software devem interagir, permitindo que sistemas distintos se comuniquem entre si.

**REST (Representational State Transfer)** é o estilo arquitetural mais usado para APIs web, com os seguintes princípios:
- Comunicação cliente-servidor **sem estado** (stateless)
- Uso padronizado de métodos HTTP
- Recursos identificados por URIs
- Representações de dados (geralmente em JSON)

---

## 2. Protocolo HTTP

HTTP (Hypertext Transfer Protocol) é o protocolo que permite a comunicação na Web, estabelecendo as regras de troca de informações entre clientes (navegadores) e servidores.

**Conceitos principais:**
- **Modelo cliente-servidor:** o navegador (cliente) faz requisições a servidores web.
- **Stateless:** cada requisição é independente; o servidor não "lembra" requisições anteriores.
- **Baseado em texto:** as mensagens são legíveis por humanos.

### Métodos HTTP

| Método | Finalidade | Características |
|---|---|---|
| **GET** | Recuperar informações do servidor | Seguro (não altera dados), idempotente |
| **POST** | Criar novos recursos no servidor | Não idempotente (chamadas repetidas criam múltiplos recursos) |
| **PUT** | Substituir completamente um recurso existente | Serve para atualizar informações |
| **PATCH** | Atualizar parcialmente um recurso | Serve para atualizar informações |
| **DELETE** | Remover um recurso específico | Idempotente (apagar algo já apagado não gera erro) |

### Como funciona uma requisição na prática

1. **Navegador/Front-end:** o usuário acessa a página ou clica em um botão.
2. **Requisição HTTP:** o navegador envia uma requisição ao servidor (GET, POST, PUT, DELETE).
3. **Servidor Express.js:** o backend recebe a requisição, identifica a rota e executa a lógica necessária.
4. **Banco de Dados/API Externa:** o servidor busca, grava ou atualiza informações.
5. **Resposta JSON:** o servidor retorna os dados processados em formato JSON.
6. **Atualização da Tela:** o front-end recebe a resposta e exibe os dados ao usuário.

---

## 3. EndPoint

Um **endpoint** é uma URL específica que fornece acesso a um recurso ou funcionalidade de uma API — o ponto de comunicação entre cliente e servidor.

**Exemplo citado:** [awesomeapi-cep](https://github.com/awesomeapibrasil/awesomeapi-cep)
- Método **GET**: lista todos os usuários.
- Método **POST**: adiciona um novo usuário.

### Repositórios de APIs Públicas

Catálogos de APIs públicas são úteis para estudar e desenvolver aplicações reais, reunindo APIs de diversos projetos e serviços.
**Exemplo citado:** [freepublicapis.com](https://www.freepublicapis.com/)

---

## 4. JSON (JavaScript Object Notation)

Formato leve de troca de dados que:
- É fácil para humanos lerem e escreverem.
- É fácil para máquinas parsearem e gerarem.

Baseado em duas estruturas:
- **Objetos:** coleções de pares nome/valor.
- **Arrays:** listas ordenadas de valores.

---

## 5. Servidor Backend e Web Service

**Servidor Backend:** sistema que processa requisições, gerencia dados e fornece respostas para clientes (apps, navegadores). Funções principais:
- Armazenar/recuperar dados (banco de dados)
- Executar regras de negócio
- Fornecer APIs para comunicação

**Web Service:** serviço acessível via web que permite comunicação entre sistemas usando HTTP/HTTPS, possibilitando que sistemas heterogêneos (diferentes linguagens, plataformas ou tecnologias) se comuniquem de forma padronizada.

---

## 6. Criando uma API REST com Express

### Framework Express.js
- Framework para Node.js que facilita a criação de servidores web e APIs.
- Minimalista, flexível e muito popular no ecossistema JavaScript.
- **Simplifica o Node.js:** o módulo `http` puro exige mais código para rotas e middlewares — o Express torna isso mais fácil.
- **Roteamento:** facilita a definição de rotas (ex.: `/users`, `/products`).
- **Middlewares:** funções que processam requisições/respostas (ex.: autenticação, logs).
- **Velocidade:** leve e rápido para criar APIs ou servidores web.

**Quando usar Express.js:**
1. Para APIs REST eficientes, integração com bancos de dados e backends escaláveis (web e mobile).
2. Para servir páginas com templates e middlewares que simplificam autenticação, logs e tratamento de erros.
3. **Evitar** para aplicações em tempo real (preferir WebSockets) ou processamento pesado (usar Workers) — Express é melhor para prototipagem rápida.

### Node.js puro vs. Express.js

**Node.js puro:**
```js
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.url === '/') {
    res.end('Olá, mundo!');
  } else {
    res.end('Rota não encontrada!');
  }
});

server.listen(3000);
```

**Express.js:**
```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Olá, mundo!');
});

app.listen(3000);
```

### Passo a passo prático (criando a API)

1. **Inicializar o projeto:** criar uma nova pasta e abrir no VS Code.
2. **Instalar o Express.js:** `npm install express`
3. **Instalar o Cors:** `npm install cors express`
   > CORS é um mecanismo de segurança que controla o acesso entre domínios diferentes no navegador.
4. **Criar o arquivo `api.js`:**
   ```js
   import express from 'express';
   import cors from 'cors';

   const app = express();

   app.use(cors());

   app.get('/', (req, res) => {
     res.json({
       date: new Date().toLocaleString('pt-BR'),
       status: 'API no Render funcionando!'
     });
   });

   // Porta dinâmica para o Render
   const PORT = process.env.PORT || 3000;
   app.listen(PORT, () => {
     console.log(`Servidor rodando na porta ${PORT}`);
   });
   ```
5. **Executar o servidor:** `node api.js`

---

## 7. Render para Simular Web Services

O **Render** é uma plataforma de hospedagem em nuvem moderna, usada na aula para publicar a API criada.

**Características:**
- Suporta Node.js, Python e outras linguagens.
- Integração fácil com repositórios Git.
- Deploy contínuo automático, com planos gratuitos para projetos pequenos.
- Interface simples e intuitiva para iniciantes.
- Escalável para aplicações profissionais, com certificado SSL gratuito — ideal para APIs e microsserviços.

**Benefícios destacados:**
- Deploy rápido em poucos cliques, sem terminal, com atualizações automáticas via GitHub.
- Ambiente de produção profissional, com escalabilidade automática e monitoramento de desempenho.
- Suporte técnico eficiente e infraestrutura confiável — indicado também para projetos acadêmicos.

### Passo a passo do deploy no Render

1. **Commit do projeto no GitHub:** deixar o projeto disponível em um repositório.
2. **Criar conta no Render:** acessar `dashboard.render.com`.
3. **Criar novo "Web Service":** clicar em *New* e conectar o repositório do GitHub.
4. **Definir comando de start:** Build Command: `node` / Start Command: `node api.js`
5. **Deploy do Web Service:** após o deploy, a API fica acessível em `seu-projeto.onrender.com`.

---

## 8. Atividades propostas na aula

**Atividade 01:** Pesquisar 10 projetos no GitHub que utilizem algum tipo de API, cloná-los, analisar o framework utilizado e as APIs consumidas, e criar um arquivo Markdown com uma tabela detalhando os projetos e suas informações.

**Atividade 02:**
1. Criar uma API usando Express, com uma rota de consulta de data e hora, fazer o deploy no Render conectado a um repositório, e depois desenvolver um front-end que consuma essa API e exiba a data e hora na tela.
2. Usar um repositório separado para a API e para o Front. Organizar tudo em um documento com prints do código, da aplicação em funcionamento, dos painéis do Render e da Vercel, além dos links dos repositórios no GitHub, e enviar a atividade na plataforma Canva.

---

## Referências

> As referências abaixo são as indicadas pelo **Prof. Me. Deivison S. Takatu** no material original da aula (slide "Referências"), e não fontes levantadas por esta análise.

1. SOUZA, Natan. **Bootstrap 4: conheça a biblioteca front-end mais utilizada no mundo.** São Paulo: Casa do Código, 2018. E-book. Disponível em: https://plataforma.bvirtual.com.br.
2. MACHADO, Kheronn Khennedy. **Angular 11 e Firebase: construindo uma aplicação integrada com a plataforma do Google.** São Paulo: Casa do Código, 2021. E-book. Disponível em: https://plataforma.bvirtual.com.br. Acesso em: 13 maio 2025.
3. EIS, Diego. **Guia Front-end: o caminho das pedras para ser um dev front-end.** São Paulo: Casa do Código, 2015. E-book. Disponível em: https://plataforma.bvirtual.com.br.
4. GONÇALVES, Edson. **Desenvolvendo aplicações Web com JSP, Servlets, JavaServer Faces, Hibernate, EJB 3 Persistence e Ajax.** Rio de Janeiro: Ciência Moderna, c2007.
5. HARTCOPP, Patrícia Ferreira. **Métrica Web.** São Paulo: Contentus, 2020. E-book (94 p.). Disponível em: https://plataforma.bvirtual.com.br/Acervo/Publicacao/185191. Acesso em: 30 abr. 2024.
6. NIEDERAUER, Juliano. **Desenvolvendo Websites com PHP: aprenda a criar Websites dinâmicos e interativos com PHP e banco de dados.** 3. ed. São Paulo: Novatec, 2017.
7. PREECE, J.; ROGERS, Y.; SHARP, H. **Design de Interação: além da interação Homem-Computador.** 3. ed. Porto Alegre: Bookman, 2013.
8. SOUSA, Roque Fernando Marcos. **Canvas HTML 5: composição gráfica e interatividade na Web.** Rio de Janeiro: Brasport, 2014. E-book (194 p.). Disponível em: https://plataforma.bvirtual.com.br/Acervo/Publicacao/160686. Acesso em: 22 jun. 2024.