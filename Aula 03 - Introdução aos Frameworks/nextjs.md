# ▲ Next.js

## O que é

Framework construído **sobre o React**, voltado para aplicações Web modernas e **full-stack**. Acrescenta uma série de recursos que o React puro não oferece nativamente.

---

## Recursos que o Next.js adiciona ao React

- **Roteamento baseado em arquivos**
- **Renderização no lado do servidor (SSR)**
- **Server Components**
- Otimização automática de **imagens e fontes**
- Gerenciamento de **páginas e layouts**
- **APIs e funcionalidades de backend** embutidas
- Otimizações voltadas a **desempenho e SEO**

---

## Criando um Projeto Next.js

```bash
npx create-next-app@latest meu-projeto
cd meu-projeto
code .
npm run dev
```

---

## Estrutura do Projeto

| Item | Função |
|---|---|
| `node_modules/` | Dependências instaladas |
| `public/` | Arquivos estáticos (não passam pelo build) |
| `app/` | Diretório principal (**App Router**) — páginas, layouts, estilos |

> Os arquivos `page.js` definem as páginas da aplicação; a organização das pastas dentro de `app/` é o que determina as rotas automaticamente.

---

## Next.js x React puro

| React puro | Next.js |
|---|---|
| Precisa de bibliotecas externas para rotas (ex: React Router) | Roteamento baseado em arquivos, nativo |
| Renderização apenas no client-side (CSR) | Suporta SSR e Server Components |
| Sem otimizações automáticas de imagem/fonte | Otimização de imagens e fontes embutida |
| Sem recursos de backend integrados | Permite criar rotas de API dentro do próprio projeto |
| SEO mais trabalhoso (conteúdo renderizado no navegador) | SEO otimizado por padrão, graças à renderização no servidor |

---

## Deploy

O Next.js é mantido pela **Vercel**, o que torna o deploy praticamente direto: basta conectar o repositório do GitHub à Vercel para publicar a aplicação com CI/CD automático.