# Aula 03 — Projetos com Frameworks Front-end

**Disciplina:** Frameworks Front-end
**Foco:** Diferenças entre frameworks, construção de projetos com React, Angular, Vue e Next.js, e reaproveitamento de projetos existentes.
**Professor:** Prof. Me. Deivison S. Takatu

---

## 📌 Sumário

- Introdução aos Frameworks Front-end
- Framework × Biblioteca
- React, Vue, Angular e Next.js
- Comparativo entre Frameworks
- Criação e estrutura de projetos
- Git e versionamento
- Atividade prática

---

## 1. Introdução aos Frameworks Front-end

Um framework front-end reúne ferramentas, bibliotecas e convenções que padronizam a construção de interfaces web, oferecendo uma base pré-estruturada que agiliza o desenvolvimento de aplicações mais elaboradas.

**Sem framework (Vanilla JS):** código escrito manualmente, manutenção mais trabalhosa, muita repetição.
**Com framework:** componentes reaproveitáveis, estado controlado, atualizações otimizadas.

---

## 2. Framework x Biblioteca

| Framework | Biblioteca |
|---|---|
| Comanda o fluxo de execução (inversão de controle) | Você decide quando acioná-la |
| Impõe uma estrutura própria | Oferece flexibilidade, sem regras rígidas |
| Exemplos: Angular, Vue | Exemplos: React, jQuery |

**Exemplo prático:**
- **Biblioteca:** você mesmo decide o momento de chamar `ReactDOM.render()`.
- **Framework:** é o Angular quem determina quando os componentes serão renderizados.

---

## 3. Por que Utilizar um Framework?

- **Ganho de produtividade** — funcionalidades prontas para roteamento, estado e renderização
- **Boas práticas incorporadas** — código dividido em componentes
- **Manutenção mais simples** — Virtual DOM (React), Change Detection (Angular)
- **Apoio da comunidade** — ampla documentação, plugins e soluções já testadas

---

## 4. Exemplos de Frameworks

- **React** — lançado pelo Facebook em 2013; do ponto de vista técnico é uma **biblioteca**, e não um framework, embora costume ser tratada como tal
- **Angular** — mantido pelo Google; framework robusto voltado para SPAs
- **Vue.js** — framework de adoção progressiva, que se ajusta conforme a aplicação cresce

> Fonte de popularidade: [Google Trends](https://trends.google.com.br/)

---

## 5. Características dos Frameworks Front-end

- **Organização clara do código** — separação bem definida entre HTML, CSS e JS
- **Componentização** — peças independentes e reutilizáveis
- **Programação reativa** — a interface se atualiza sozinha conforme o estado muda
- **Ferramentas de build e empacotamento** — minificação, transpilação e compatibilidade entre navegadores
- **Sistema de rotas** — navegação fluida em SPAs, sem recarregar a página inteira
- **Integração com APIs** — requisições assíncronas e sincronização de dados
- **Documentação e comunidade ativas**
- **Padrões de design e acessibilidade**
- **Suporte a testes** — unitários e de integração

---

## 6. Comparativo entre Frameworks

Escolher o framework adequado influencia diretamente o desempenho, a escalabilidade, a facilidade de manutenção e a experiência de quem usa a aplicação. Vale considerar: complexidade do projeto, curva de aprendizado, desempenho e apoio da comunidade.

> Fonte: [StackShare](https://stackshare.io/stackups)

---

## 7. React

Lançada pelo Facebook em 2013, a biblioteca React é uma das ferramentas mais usadas para Web Apps atualmente. Requer familiaridade prévia com HTML e JavaScript. Sua arquitetura orientada a componentes, aliada ao Virtual DOM, resulta em aplicações rápidas e escaláveis.

### Conceitos fundamentais
- **Hooks:** `useState` (controla o estado) e `useEffect` (lida com efeitos colaterais, como requisições a APIs)
- **JSX:** utiliza `{}` para expressões JS; atributos escritos em camelCase (`className`); tags sempre autofechadas quando vazias (`<img />`)
- **Gerenciamento de estado:** Context API (para casos simples) ou Redux (para estados mais complexos ou globais)

### DOM x Virtual DOM
O DOM é a representação em forma de árvore de uma página web. O Virtual DOM, adotado pelo React, é uma cópia mais leve dessa árvore: o React atualiza primeiro a cópia, compara com o DOM real e aplica somente as diferenças encontradas, otimizando o desempenho.

---

## 8. Angular

### Requisitos
- Node.js já instalado
- Familiaridade com Programação Orientada a Objetos (POO)

### Destaques
- Framework completo (roteamento, cliente HTTP, injeção de dependências)
- TypeScript já integrado
- Segue arquitetura MVC
- CLI robusta
- Change Detection eficiente

### Conceitos fundamentais
- **Componentes** — `@Component` (junta HTML, CSS e TypeScript)
- **Módulos** — `@NgModule`
- **Serviços** — `@Injectable`
- **Data Binding** — `[(ngModel)]` (bidirecional) e `{{ }}` (interpolação)
- **Injeção de dependência** e **roteamento** — `RouterModule`

### Criando um projeto
```bash
npm install -g @angular/cli
ng new meu-app-angular
cd meu-app-angular
code .
ng serve
```

### Estrutura principal
| Item | Função |
|---|---|
| `node_modules/` | Dependências instaladas |
| `public/` | Arquivos estáticos públicos |
| `src/app/` | Componentes, módulos e serviços |
| `index.html` | Ponto de entrada; renderiza `<app-root>` |
| `main.ts` | Inicializa o módulo raiz e renderiza no DOM |
| `main.server.ts` / `server.ts` | Angular Universal (SSR) |
| `angular.json` | Configuração geral (build, testes, estilos) |
| `tsconfig*.json` | Configurações do TypeScript |

---

## 9. Vue

### Requisitos
- Node.js já instalado
- Conhecimento em JavaScript/TypeScript
- Familiaridade com programação reativa e orientada a componentes

### Destaques
- **Progressivo** — pode ser adotado aos poucos, de trechos pequenos até SPAs completas
- **Reatividade eficiente**
- **Single-File Components (SFC)** — HTML, CSS e JS reunidos em um único arquivo `.vue`
- **Curva de aprendizado tranquila**
- **Desempenho otimizado**

### Criando um projeto
```bash
npm create vue@latest
cd meu-projeto-vue
npm install
code .
npm run dev
```

### Estrutura principal
| Item | Função |
|---|---|
| `node_modules/` | Dependências instaladas |
| `public/` | Arquivos estáticos que não passam pelo processo de build do Vite |
| `src/assets/` | Imagens, fontes e CSS global, processados pelo Vite |
| `src/components/` | Componentes reutilizáveis |
| `App.vue` | Componente raiz |
| `main.js` | Ponto de entrada; monta a aplicação no DOM |
| `index.html` | Único arquivo HTML da SPA (`div #app`) |
| `vite.config.js` | Configurações do Vite (build, plugins, proxies) |

---

## 10. Next.js

Framework construído sobre o React, voltado para aplicações Web modernas e full-stack. Acrescenta recursos que o React sozinho não oferece:

- Roteamento baseado em arquivos
- Renderização no lado do servidor (SSR)
- Server Components
- Otimização automática de imagens e fontes
- Gerenciamento de páginas e layouts
- APIs e funcionalidades de backend
- Otimizações voltadas a desempenho e SEO

### Criando um projeto
```bash
npx create-next-app@latest meu-projeto
cd meu-projeto
code .
npm run dev
```

### Estrutura principal
| Item | Função |
|---|---|
| `node_modules/` | Dependências instaladas |
| `public/` | Arquivos estáticos (não passam pelo build) |
| `app/` | Diretório principal (App Router) — páginas, layouts, estilos |

> Os arquivos `page.js` definem as páginas da aplicação; a organização das pastas é o que determina as rotas.

---

## 11. Importando Projetos

Partir de projetos-modelo já prontos pode agilizar bastante o trabalho — a comunidade open source disponibiliza centenas de opções gratuitas e adaptáveis.

**Ferramentas para buscar projetos:**
- **GitHub** — [Repository Search](https://github.com/search) *(usa-se `git clone <url>`)*
- **Vercel** — Busca por Templates *(permite baixar apenas parte do repositório)*
- **CodeSandbox** — Template Search

> Fonte: [CodeSandbox](https://codesandbox.io/)

---

## ✅ Atividade

Desenvolver, **em grupo**, quatro projetos Web sobre o mesmo tema, empregando **React, Vue, Angular e Next.js**. Cada projeto precisa ter ao menos uma página funcional, responsiva e bem organizada, utilizando componentes e os recursos básicos da tecnologia escolhida.

Ao longo do desenvolvimento, os projetos devem:
- Ser versionados com **Git** e publicados no **GitHub**, com um histórico de commits que mostre a evolução da aplicação
- Ficar organizados cada um em seu próprio repositório
- Vir acompanhados de uma **breve comparação** entre as quatro tecnologias, apontando as principais diferenças percebidas

### Entregas
| # | Projeto |
|---|---------|
| 01 | React |
| 02 | Vue |
| 03 | Angular |
| 04 | Next.js |
| 05 | Cópia de um projeto a partir de um repositório |

---

## 📝 Resumo

```
Frameworks × Bibliotecas → React, Angular, Vue, Next.js → Criação de projetos → Git/GitHub → Comparativo técnico
```

Esta aula aprofundou a construção prática de projetos nos principais frameworks/bibliotecas do mercado, reforçando conceitos de estrutura de pastas, ferramentas de CLI e boas práticas de versionamento aplicadas a cada tecnologia.

---

**Referência do material:** Frameworks Front-end — Projetos com Frameworks Front-end, Prof. Me. Deivison S. Takatu.