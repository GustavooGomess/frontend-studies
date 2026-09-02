# Aula 05 — Criando APIs para o Front-end

**Disciplina:** Frameworks Front-end
**Professor:** Prof. Me. Deivison S. Takatu

---

## 📌 Sumário

- API (Application Programming Interface)
- Protocolo HTTP
- EndPoint
- JSON (JavaScript Object Notation)
- Servidor Backend e Web Service
- Criando uma API REST com Express
- Documentando uma API (Postman)
- Atividades 01 e 02

---

## 1. Métodos HTTP

| Método | Finalidade | Características |
|---|---|---|
| **GET** | Recuperar informações do servidor | Seguro (não altera dados), idempotente |
| **POST** | Criar novos recursos | Não idempotente (chamadas repetidas criam múltiplos recursos) |
| **PUT/PATCH** | Atualizar recursos | PUT substitui por completo; PATCH atualiza parcialmente |
| **DELETE** | Remover um recurso específico | Idempotente (apagar algo já apagado não gera erro) |

---

## 2. EndPoint

Uma URL específica que dá acesso a um recurso ou funcionalidade de uma API, representando o ponto de comunicação entre cliente e servidor.

**Exemplo:** `GET` lista usuários, `POST` adiciona um novo usuário.

---

## 3. JSON (JavaScript Object Notation)

Formato leve de troca de dados, fácil de ler/escrever para humanos e de parsear/gerar para máquinas. Baseado em:
- Coleções de pares nome/valor (objetos)
- Listas ordenadas de valores (arrays)

---

## 4. Servidor Backend e Web Service

- **Servidor Backend:** processa requisições, gerencia dados e responde a clientes (apps, navegadores). Suas funções principais são armazenar/recuperar dados, executar regras de negócio e fornecer APIs.
- **Web Service:** serviço acessível via web (HTTP/HTTPS) que permite a comunicação padronizada entre sistemas heterogêneos.

---

## 5. Framework Express.js

Framework para Node.js que simplifica a criação de servidores web e APIs — minimalista, flexível e muito usado no ecossistema JavaScript.

**Vantagens sobre o Node.js puro:**
- Roteamento facilitado (`/users`, `/products`)
- Middlewares para autenticação, logs, etc.
- Leve e rápido para criar APIs

**Quando usar:**
- ✅ APIs REST, integração com bancos de dados, backends escaláveis
- ✅ Servir páginas com templates e middlewares
- ❌ Evitar em apps em tempo real (prefira WebSockets) ou processamento pesado (prefira Workers)

### Exemplo básico (`api.js`)
```javascript
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

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Servidor rodando na porta ${PORT}`);
});
```

> **CORS** é um mecanismo de segurança que controla o acesso entre domínios diferentes no navegador.

---

## 6. Criando uma API REST com CRUD

**Passo a passo:**
1. Instalar `express` e `body-parser`
2. Criar `server.js`
3. Implementar as rotas CRUD lendo/gravando em `data.json`
4. Rodar com `node server.js`

### Rotas CRUD
| Rota | Método | Ação |
|---|---|---|
| `/api/notes` | GET | Lista todas as notas |
| `/api/notes` | POST | Cria uma nova nota (exige `titulo` e `texto`) |
| `/api/notes/:id` | GET | Retorna uma nota específica |
| `/api/notes/:id` | PUT | Atualiza uma nota existente |
| `/api/notes/:id` | DELETE | Remove uma nota (retorna status 204) |

### Estrutura do código (`server.js`)
```javascript
const express = require('express');
const bodyParser = require('body-parser');
const fs = require('fs');

const app = express();
const PORT = 3000;
const FILE = 'data.json';

app.use(bodyParser.json());
app.use((req, res, next) => {
  res.header('Access-Control-Allow-Origin', '*');
  next();
});

function readNotes() {
  try {
    return JSON.parse(fs.readFileSync(FILE));
  } catch {
    return [];
  }
}

function saveNotes(notes) {
  fs.writeFileSync(FILE, JSON.stringify(notes, null, 2));
}

app.get('/api/notes', (req, res) => res.json(readNotes()));

app.post('/api/notes', (req, res) => {
  const notes = readNotes();
  const novaNota = { id: Date.now().toString(), titulo: req.body.titulo, texto: req.body.texto };
  notes.push(novaNota);
  saveNotes(notes);
  res.json(novaNota);
});

app.put('/api/notes/:id', (req, res) => {
  const notes = readNotes();
  const index = notes.findIndex(n => n.id === req.params.id);
  if (index >= 0) {
    notes[index].titulo = req.body.titulo;
    notes[index].texto = req.body.texto;
    saveNotes(notes);
    res.json(notes[index]);
  } else {
    res.status(404).json({ erro: 'Nota não encontrada' });
  }
});

app.delete('/api/notes/:id', (req, res) => {
  const notes = readNotes().filter(n => n.id !== req.params.id);
  saveNotes(notes);
  res.json({ mensagem: 'Nota removida' });
});

app.listen(PORT, () => console.log('Servidor rodando em http://localhost:3000'));
```

---

## 7. Deploy: Render + Vercel

| Etapa | Detalhe |
|---|---|
| Back-end no Render | Commit no GitHub → criar conta no Render → New Web Service → conectar repositório → definir Start Command (`node api.js`) → deploy |
| Conectar Front-end | Substituir `http://localhost:3000/api/notes` pela URL gerada no Render |
| Front-end na Vercel | Criar interface React consumindo a API → subir para o GitHub → deploy na Vercel |

**Render** é uma plataforma de hospedagem em nuvem com deploy contínuo automático, certificado SSL gratuito e integração fácil com Git — ideal para APIs e microsserviços.

---

## 8. Documentando uma API — Postman

- Ferramenta colaborativa para criar, testar, documentar e monitorar requisições HTTP (GET, POST, PUT, DELETE, etc.)
- Permite organizar **coleções de requisições**, usar variáveis de ambiente, scripts pré-request e testes automatizados
- Recursos avançados: Mock Servers, Monitoramento, suporte a GraphQL, WebSockets e OAuth 2.0
- Pode gerar documentação automática e integrar a pipelines de CI/CD via **Newman** (CLI do Postman)

---

## ✅ Atividade 01

Atualizar o repositório da disciplina com todos os arquivos da aula e enviar o link atualizado pelo formulário indicado.

## ✅ Atividade 02

1. Fazer o deploy do back-end (Express) no **Render**
2. Construir um Front-End que consuma as rotas CRUD da API
3. Criar uma **coleção no Postman** documentando as 4 operações CRUD, com parâmetros e códigos de resposta
4. Entregar um documento com prints do código, da aplicação funcionando, link do repositório GitHub, link do deploy na Vercel e link da coleção do Postman

---

## 🤔 Questões para Refletir

- Quais são os riscos de segurança desse projeto e como mitigá-los?
- Usar um arquivo JSON (`data.json`) para armazenar dados é uma boa prática em produção? Vantagens e desvantagens?
- Que limitações um servidor baseado em arquivo JSON teria com 10.000 registros?
- Por que concentrar todo o código em `server.js` é problemático, e como melhorar a organização da lógica?

---

## 📝 Síntese

```
API → HTTP → EndPoint → JSON → Servidor Backend → Express (CRUD) → Deploy (Render/Vercel) → Documentação (Postman)
```

---

**Referência:** Material da disciplina Frameworks Front-end — Criando APIs para o Front-end, Prof. Me. Deivison S. Takatu.