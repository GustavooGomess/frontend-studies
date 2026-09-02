# 🟩 Vue.js

## O que é

Framework **progressivo**, ou seja, pode ser adotado aos poucos — de trechos pequenos de uma página até aplicações completas em formato SPA. Ajusta-se conforme a aplicação cresce em complexidade.

---

## Requisitos

- Node.js instalado
- Conhecimento em JavaScript/TypeScript
- Familiaridade com programação reativa e orientada a componentes

---

## Destaques

- **Progressivo** — adoção gradual
- **Reatividade eficiente**
- **Single-File Components (SFC)** — HTML, CSS e JS reunidos em um único arquivo `.vue`
- **Curva de aprendizado tranquila**
- **Desempenho otimizado**

---

## Criando um Projeto Vue

```bash
npm create vue@latest
cd meu-projeto-vue
npm install
code .
npm run dev
```

---

## Estrutura do Projeto

| Item | Função |
|---|---|
| `node_modules/` | Dependências instaladas |
| `public/` | Arquivos estáticos que não passam pelo build do Vite |
| `src/assets/` | Imagens, fontes e CSS global, processados pelo Vite |
| `src/components/` | Componentes reutilizáveis |
| `App.vue` | Componente raiz |
| `main.js` | Ponto de entrada; monta o app no DOM |
| `index.html` | Único HTML da SPA (`div #app`) |
| `vite.config.js` | Configurações do Vite (build, plugins, proxies) |

---

## Por que o Vue se destaca

Diferente do Angular (framework "impositivo") e do React (biblioteca flexível mas sem estrutura própria), o Vue busca um meio-termo: fornece uma estrutura organizada via **Single-File Components**, mas permite adoção incremental — dá pra começar só adicionando o Vue a uma página existente, sem precisar reescrever tudo como SPA.

---

## Deploy

Como os demais projetos da disciplina, aplicações Vue podem ser publicadas via **Vercel** ou hospedagem equivalente, com deploy automático a partir do repositório no GitHub.