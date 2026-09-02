# ⚛️ React

## O que é

Biblioteca JavaScript lançada pelo Facebook em 2013, uma das ferramentas mais usadas para construção de Web Apps atualmente. Tecnicamente é uma **biblioteca**, e não um framework — embora costume ser tratada como tal — já que quem controla o fluxo de execução é o próprio desenvolvedor (você decide quando chamar `ReactDOM.render()`).

Requer familiaridade prévia com **HTML** e **JavaScript**.

---

## Por que usar

- Arquitetura orientada a **componentes** reutilizáveis
- **Virtual DOM**, que garante aplicações rápidas e escaláveis
- Grande comunidade, documentação extensa e ecossistema maduro

---

## Conceitos Fundamentais

### Hooks
- **`useState`** → gerencia o estado do componente
- **`useEffect`** → lida com efeitos colaterais, como chamadas a APIs

### JSX
- Usa `{}` para inserir expressões JavaScript dentro do markup
- Atributos escritos em **camelCase** (ex: `className`)
- Tags sempre autofechadas quando vazias (ex: `<img />`)

### Gerenciamento de Estado
- **Context API** → indicada para estados simples
- **Redux** → indicada para estados mais complexos ou globais

---

## DOM x Virtual DOM

O **DOM** é a representação em árvore de uma página web. O **Virtual DOM**, usado pelo React, é uma cópia mais leve dessa árvore: o React primeiro atualiza a cópia, compara com o DOM real e aplica apenas as diferenças encontradas — otimizando o desempenho da aplicação.

---

## Criando um Projeto React

```bash
npx create-react-app meu-projeto-react
cd meu-projeto-react
code .
npm start
```

> O `npx` executa pacotes sem exigir instalação global. O `create-react-app` monta automaticamente toda a estrutura inicial (build, Babel, servidor de desenvolvimento, scripts, etc.).

---

## Estrutura do Projeto

| Item | Função |
|---|---|
| `node_modules/` | Pacotes e dependências instaladas |
| `public/` | Arquivos públicos (HTML, JSON, imagens) |
| `src/` | Código JavaScript e React da aplicação |
| `.gitignore` | Define o que o Git deve ignorar |
| `package.json` | Dependências e informações do projeto |
| `package-lock.json` | Registro exato das dependências instaladas |

### Principais arquivos
- **`index.js`** → ponto de entrada; renderiza o `App` no DOM
- **`App.js`** → componente raiz da aplicação
- **`App.css`** → estilos do componente App
- **`index.css`** → estilos globais

---

## Comparativo Node.js Puro x Express (para contexto de API)

```javascript
// Node.js puro
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

---

## Deploy

Projetos React são tipicamente publicados na **Vercel**, com integração direta ao GitHub e deploy automático a cada push.