# 🅰️ Angular

## O que é

Framework completo mantido pelo **Google**, voltado para a construção de SPAs (Single Page Applications). Diferente do React, o Angular é um **framework** de verdade: é ele quem comanda o fluxo de execução e decide quando renderizar os componentes.

---

## Requisitos

- Node.js instalado
- Conhecimento em **Programação Orientada a Objetos (POO)**

---

## Destaques

- Framework completo (roteamento, cliente HTTP, injeção de dependências)
- **TypeScript** nativo
- Segue a arquitetura **MVC**
- CLI robusta (`@angular/cli`)
- **Change Detection** eficiente

---

## Conceitos Fundamentais

| Conceito | Descrição |
|---|---|
| **Componentes** | `@Component` — junta HTML, CSS e TypeScript |
| **Módulos** | `@NgModule` |
| **Serviços** | `@Injectable` |
| **Data Binding** | `[(ngModel)]` (bidirecional) e `{{ }}` (interpolação) |
| **Injeção de dependência** | Provida pelo próprio Angular |
| **Roteamento** | `RouterModule` |

---

## Criando um Projeto Angular

```bash
npm install -g @angular/cli
ng new meu-app-angular
cd meu-app-angular
code .
ng serve
```

---

## Estrutura do Projeto

| Item | Função |
|---|---|
| `node_modules/` | Dependências instaladas |
| `public/` | Arquivos estáticos públicos |
| `src/app/` | Componentes, módulos e serviços |
| `index.html` | Ponto de entrada; renderiza `<app-root>` |
| `main.ts` | Inicializa o módulo raiz e renderiza no DOM |
| `main.server.ts` / `server.ts` | Angular Universal (SSR) |
| `angular.json` | Configuração principal (build, testes, estilos) |
| `tsconfig*.json` | Configurações do TypeScript |

---

## Framework x Biblioteca (Angular como exemplo)

| Framework | Biblioteca |
|---|---|
| Comanda o fluxo de execução (inversão de controle) | Você decide quando acioná-la |
| Impõe uma estrutura própria | Oferece flexibilidade, sem regras rígidas |
| **Exemplo: Angular** | Exemplo: React |

**Exemplo prático:** é o Angular quem determina quando os componentes serão renderizados — diferente do React, onde você mesmo chama `ReactDOM.render()`.

---

## Deploy

Assim como os demais projetos front-end da disciplina, aplicações Angular podem ser publicadas na **Vercel** ou em outra plataforma de hospedagem em nuvem, com integração via GitHub.