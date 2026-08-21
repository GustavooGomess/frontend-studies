# Aula 02 — Configuração do Ambiente de Desenvolvimento

Anotações da disciplina de **Frameworks Front-end**, abordando a preparação do ambiente de trabalho, controle de versão com Git, Node.js, React e publicação de aplicações em produção.

**Professor:** Prof. Me. Deivison S. Takatu

---

## 📌 Tópicos Abordados

- Fundamentos de Controle de Versão
- Versionamento Semântico (SemVer)
- Git e Gerenciamento de Histórico
- Tags, Branches e Boas Práticas
- Ambiente de Desenvolvimento (VS Code)
- Node.js e Gerenciador de Pacotes NPM
- Criação de um Projeto em React
- Publicação e Hospedagem via Vercel
- Atividade Prática

---

## 1. Controle de Versão

É a prática de atribuir uma identificação exclusiva a cada estado de um projeto, mantendo o registro de **quais** mudanças ocorreram, **quem** as realizou, **em que momento**, e possibilitando o retorno a estados anteriores quando necessário.

### Controle de Versão x Backup

| Controle de Versão | Backup |
|---|---|
| Preserva o histórico completo de mudanças | Guarda apenas uma cópia do estado atual |
| Rastreia autoria, data e motivo da alteração | Não oferece esse nível de rastreabilidade |
| Viabiliza colaboração em paralelo | Costuma trabalhar com cópias isoladas |
| Possibilita reverter mudanças específicas | Geralmente restaura tudo de uma vez |

### Vantagens
- Permite que vários desenvolvedores trabalhem ao mesmo tempo
- Diminui retrabalho e conflitos de código
- Garante rastreabilidade, auditoria e possibilidade de recuperação
- Eleva o controle de qualidade do software

---

## 2. SemVer (Versionamento Semântico)

Formato padrão: **MAJOR.MINOR.PATCH**

```
2.1.3
```

- **MAJOR** → alteração que quebra compatibilidade (ex: `2.0.0`)
- **MINOR** → adição de funcionalidade sem quebrar compatibilidade (ex: `1.1.0`)
- **PATCH** → correção de defeito (ex: `1.0.1`)

**Exemplo de progressão:**
```
1.0.0 → Lançamento estável inicial
1.1.0 → Funcionalidade nova, compatível
1.1.1 → Ajuste de bug
2.0.0 → Alteração que quebra compatibilidade
```

**Categorias de mudança:** correção de bug, nova funcionalidade, aprimoramento de recurso, refatoração, melhoria de performance, correção de segurança, atualização de dependência, inclusão de testes.

---

## 3. Git

Ferramenta de controle de versão usada para acompanhar e administrar as alterações feitas nos arquivos do projeto.

**Checar se está instalado:**
```bash
git --version
```

**Configuração inicial do usuário:**
```bash
git config --global user.name "<Nome>"
git config --global user.email "<Email>"
```

---

## 4. Tags no Git

Servem para sinalizar pontos importantes no histórico do projeto, normalmente associados a versões lançadas (ex: `v1.0.0`).

- **Lightweight** → aponta apenas para um commit
- **Annotated** → guarda informações extras como autor, data e mensagem

**Comandos úteis:**
```bash
git tag                # exibir tags existentes
git tag 1.0.0           # criar uma nova tag
git push origin 1.0.0   # enviar a tag para o repositório remoto
```

---

## 5. Boas Práticas no Uso do Git

- Fazer commits **pequenos e regulares**
- Escrever mensagens **objetivas**, explicando o que mudou e o motivo
- Utilizar **branches** para desenvolver funcionalidades sem interferir na branch principal
- **Testar** o código antes de integrar (merge)

---

## 6. VS Code

Editor de código (IDE) que concentra recursos para escrever, testar, rodar e depurar software, com ampla possibilidade de expansão via extensões.

---

## 7. Node.js

Ambiente que permite executar JavaScript fora do navegador, no lado do servidor — viabilizando o uso da linguagem tanto no Front-end quanto no Back-end.

```bash
node --version
```

---

## 8. NPM

Gerenciador de pacotes do ecossistema Node.js, responsável por instalar, atualizar e remover dependências do projeto.

Arquivo central de configuração: **`package.json`**

```bash
npm install
```

---

## 9. Iniciando um Projeto React

```bash
npx create-react-app meu-projeto-react
cd meu-projeto-react
code .
npm start
```

> O `npx` roda pacotes sem exigir instalação global. O `create-react-app` monta automaticamente toda a estrutura inicial (build, Babel, servidor de desenvolvimento, scripts, etc.).

---

## 10. Organização do Projeto React

| Item | Finalidade |
|---|---|
| `node_modules/` | Armazena os pacotes e dependências instaladas |
| `public/` | Guarda arquivos públicos (HTML, JSON, imagens) |
| `src/` | Contém o código-fonte JS e React da aplicação |
| `.gitignore` | Especifica o que o Git não deve rastrear |
| `package.json` | Lista dependências e dados do projeto |
| `package-lock.json` | Trava as versões exatas das dependências instaladas |

### Arquivos principais
- **`index.js`** → porta de entrada da aplicação; renderiza o `App` no DOM
- **`App.js`** → componente principal (raiz) da aplicação
- **`App.css`** → estilização específica do componente App
- **`index.css`** → estilos aplicados globalmente

---

## 11. Deploy

Etapa em que a aplicação é levada para produção, envolvendo compilação, ajuste do ambiente, testes finais e disponibilização ao público.

---

## 12. Vercel

Plataforma voltada para deploy e hospedagem de aplicações web modernas.

**Recursos principais:**
- Integração direta com o GitHub
- Deploy automático a cada push
- CDN global com escalabilidade automática
- Suporte a rollback e Serverless Functions

---

## 13. Fluxo Geral do Processo

```
VS Code → Desenvolvimento em React → Git → Commit → Push → GitHub → Vercel → Deploy → Aplicação no Ar
```

---

## ✅ Atividade Prática

1. Criar uma aplicação em React
2. Colocar o projeto sob controle de versão com Git
3. Fazer commit e push para o GitHub
4. Conectar o repositório à Vercel
5. Executar o deploy e disponibilizar a URL pública

## 👥 Atividade em Grupo

Produzir um relatório técnico em PDF (mínimo de 5 páginas) sobre um framework Front-end, cobrindo: características principais, vantagens, aplicações no mercado de trabalho e um exemplo prático de uso.

---

## 📝 Síntese

```
Controle de Versão → Git → GitHub → Node.js + NPM → React → Vercel → Deploy
```

Esse conjunto de conceitos sustenta a organização de projetos, o trabalho em equipe, o acompanhamento de mudanças e a publicação de aplicações Web.

---

**Referência:** Material da disciplina Frameworks Front-end — Configuração do Ambiente de Desenvolvimento, Prof. Me. Deivison S. Takatu.