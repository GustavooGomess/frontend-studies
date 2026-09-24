# 🎨 Aula 07 — Frameworks CSS

**Disciplina:** Frameworks Front-end
**Foco:** Revisão de CSS (propriedades, box model, Flexbox e responsividade) e introdução aos Frameworks CSS com Tailwind.
**Professor:** Prof. Me. Deivison S. Takatu

---

## 📌 Sumário

- Cascading Style Sheets (CSS)
- Aplicação do CSS (in-line, interno e externo)
- Propriedades do CSS
- Class e ID
- Box Model
- Flexbox
- Layouts responsivos
- Atividade 01
- O que é um Framework CSS?
- Tailwind CSS
- Atividade 02

---

## 1. Cascading Style Sheets (CSS)

O CSS não define apenas cores e fontes: ele controla **margens, alinhamentos, larguras, alturas e elementos flutuantes**, garantindo páginas organizadas e responsivas.

### Estrutura

```css
seletor {
  propriedade: valor;
}
```

| Parte | O que faz | Exemplo |
|---|---|---|
| **Seletor** | Indica em qual tag HTML a regra será aplicada | `body` |
| **Propriedade** | Define o atributo a ser modificado | `background-color` |
| **Valor** | Especifica a configuração desejada | `#FF0000` (vermelho) |

### HTML antigo × CSS

```html
<!-- HTML -->
<body bgcolor="#FF0000">
```

```css
/* CSS: mais flexível e padronizado */
body { background-color: #FF0000; }
```

---

## 2. Aplicação do CSS

| Tipo | Como é feito | Quando usar |
|---|---|---|
| **In-line** | Atributo `style` direto no elemento | Testes ou ajustes pontuais |
| **Interno** | Tag `<style>` no cabeçalho da página | Estilo usado em uma única página |
| **Externo** | Arquivo `.css` ligado com a tag `<link>` | **Mais recomendado**: organiza e reutiliza em várias páginas |

```html
<!-- In-line -->
<p style="color: red; font-size: 20px;">Este é um texto em vermelho e maior</p>

<!-- Interno -->
<style>
  p { color: blue; font-size: 18px; }
</style>

<!-- Externo -->
<link rel="stylesheet" href="estilos.css">
```

---

## 3. Propriedades do CSS

| Propriedade | Função | Exemplo |
|---|---|---|
| `color` | Cor do texto | `color: #ff0000;` |
| `background-color` | Cor de fundo | `background-color: blue;` |
| `font-family` | Fonte do texto | `font-family: Arial, sans-serif;` |
| `font-size` | Tamanho do texto (px, em, rem, %) | `font-size: 1.2rem;` |
| `margin` | Espaço **fora** das bordas | `margin: 10px 5px 15px 20px;` (top, right, bottom, left) |
| `padding` | Espaço **dentro** das bordas | `padding: 10px 20px;` (vertical, horizontal) |
| `border` | Espessura, estilo e cor da borda | `border: 2px solid black;` |
| `width` / `height` | Dimensões do elemento | `width: 300px; height: 200px;` |
| `display` | Como o elemento é renderizado | `block`, `inline`, `flex` |
| `position` | Método de posicionamento | `relative`, `absolute`, `fixed` |
| `top`, `right`, `bottom`, `left` | Posição precisa (com `position`) | `top: 10px; left: 20px;` |
| `text-align` | Alinhamento horizontal do texto | `center`, `justify` |

### Exemplo completo

```css
body {
  margin: 20px;
  padding: 0;
  background-color: #f0f0f0;
  font-family: Arial, sans-serif;
}

.exemplo {
  color: #ff0000;
  background-color: #0000ff;
  font-family: 'Courier New', monospace;
  font-size: 18px;
  margin: 20px;
  padding: 15px;
  border: 2px solid black;
  width: 300px;
  height: 200px;
  display: block;
  position: relative;
  top: 10px;
  left: 20px;
  text-align: center;
}
```

> Material da aula: [deivisontakatu/aula-css](https://github.com/deivisontakatu/aula-css)

### Class e ID

- **Classes** aplicam o mesmo estilo a **vários elementos**, garantindo consistência e facilitando a manutenção.
- **IDs** estilizam elementos **únicos**, além de permitirem navegação por âncora e manipulação precisa via JavaScript.

```css
.botao-primario { background: blue; color: red; padding: 10px; }
#cabecalho-principal { height: 80px; background: #333; }
```

---

## 4. Atividade de Revisão

Revisão do conteúdo em formato de quiz na plataforma **Wayground** (antigo Quizizz): [wayground.com](https://wayground.com/)

---

## 5. Box Model

O **box model** (modelo das caixas) descreve os boxes gerados pelos elementos HTML e as opções de ajuste de margens, bordas, padding e conteúdo.

```
┌───────────────────────────────┐
│ margin                        │
│  ┌─────────────────────────┐  │
│  │ border                  │  │
│  │  ┌───────────────────┐  │  │
│  │  │ padding           │  │  │
│  │  │  ┌─────────────┐  │  │  │
│  │  │  │   content   │  │  │  │
│  │  │  └─────────────┘  │  │  │
│  │  └───────────────────┘  │  │
│  └─────────────────────────┘  │
└───────────────────────────────┘
```

| Camada | Descrição |
|---|---|
| **Content** | Área onde texto e imagens aparecem |
| **Padding** | Espaço entre o conteúdo e a borda |
| **Border** | Linha que envolve o padding e o conteúdo |
| **Margin** | Espaço entre a borda e outros elementos |

**Por que aplicar?**

- Controlar o tamanho dos elementos
- Criar espaçamento e organização visual
- Evitar sobreposição e problemas de dimensionamento
- Construir layouts mais previsíveis
- Facilitar a adaptação para diferentes telas

```css
.box-model {
  background-color: #ffeb99;  /* Content: área amarela onde o texto fica */
  padding: 30px;              /* Padding: espaço interno entre texto e borda */
  border: 5px solid #ff6600;  /* Border: linha laranja em volta do padding */
  margin: 40px auto;          /* Margin: espaço externo */
  width: 250px;               /* Largura do conteúdo */
  font-size: 18px;
}
```

---

## 6. Flexbox

O **Flexbox (Flexible Box Layout)** é um módulo de layout **unidimensional**, projetado para organizar itens em **linhas ou colunas**, com distribuição de espaço e alinhamento.

```css
.container {
  display: flex;
}
```

| Propriedade | Função | Valores |
|---|---|---|
| `flex-direction` | Define o eixo principal | `row`, `column`, `row-reverse`, `column-reverse` |
| `justify-content` | Alinha os itens no eixo principal | `flex-start`, `center`, `flex-end`, `space-between`, `space-around`, `space-evenly` |
| `align-items` | Alinha os itens no eixo transversal | `flex-start`, `center`, `flex-end`, `stretch`, `baseline` |
| `align-content` | Distribui as linhas quando há quebra | `flex-start`, `center`, `flex-end`, `stretch`, `space-between`, `space-around` |
| `flex-wrap` | Permite quebra de linha | `nowrap`, `wrap`, `wrap-reverse` |
| `gap` | Espaçamento entre itens | `gap: 16px;` |

### Exemplo: centralizar tudo

```css
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
```

> Sem `display: flex` (`display: block`), os itens ficam empilhados um embaixo do outro. Com `flex-direction: row`, passam a ficar lado a lado.

---

## 7. Layouts Responsivos

- Técnica de design que **adapta o conteúdo** para diferentes tamanhos de tela (celular, tablet, desktop)
- Melhora a usabilidade e a experiência do usuário
- Reduz a necessidade de criar versões separadas para cada dispositivo

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

---

## ✅ Atividade 01

1. Criar um projeto com `index.html` e `style.css`, incluindo o CSS de forma **externa**, com a tag `<link>`.
2. Adicionar **20 elementos** e atribuir valores em todas as propriedades de **Content, Padding, Border e Margin**.
3. Em seguida, adicionar **20 propriedades de Flexbox** para manipular os elementos e organizá-los de forma responsiva.

| Entrega | Link |
|---|---|
| Repositório | [🔗 Acessar](COLE_O_LINK_AQUI) |
| Deploy | [🌐 Ver online](COLE_O_LINK_AQUI) |

---

## 8. O que é um Framework CSS?

Um framework CSS é um **conjunto de recursos, padrões, classes e componentes** que facilita a criação e a padronização de interfaces web.

Exemplos: **Bootstrap, Tailwind, Bulma, Materialize, Foundation, Semantic UI e Pure.**

### Componentes de um Framework CSS

| Pilar | O que oferece |
|---|---|
| **Layout** | Grid, Flexbox e responsividade |
| **Estilos** | Cores, espaços e tipografia |
| **Componentes** | Botões, cards e navbar |

### O problema do CSS manual

Tudo precisa ser estilizado do zero: botões e cards, formulários e menus, grid e responsividade, espaçamentos e tipografia.

```css
.botao {
  background: #2563eb;
  color: white;
  padding: 12px 24px;
  border-radius: 8px;
}
```

---

## 9. Tailwind CSS

O Tailwind é um framework CSS baseado no conceito **Utility-First**: em vez de componentes prontos, fornece **pequenas classes** que representam propriedades de estilo, combinadas para montar a interface.

> **Uma utility = uma responsabilidade. Várias utilities = um componente.**

| Classe | O que faz |
|---|---|
| `p-6` | Define o padding |
| `text-xl` | Define o tamanho do texto |
| `font-bold` | Define o peso da fonte |
| `bg-blue-600` | Define a cor de fundo |
| `text-white` | Define a cor do texto |
| `px-6 py-3` | Padding horizontal e vertical |
| `rounded-lg` | Define bordas arredondadas |

```html
<!-- Em vez de criar .botao no CSS -->
<button class="bg-blue-600 text-white px-6 py-3 rounded-lg">
  Enviar
</button>

<!-- Um card com utilities -->
<div class="p-6 bg-white rounded-xl shadow">...</div>
```

### 🎯 Propósitos do Tailwind

- **Reduzir o tempo de desenvolvimento:** estilizar direto no HTML com classes utilitárias
- **Aumentar a flexibilidade:** compor componentes sem depender de estilos predefinidos
- **Facilitar a customização:** centralizar e adaptar cores, espaçamentos e tipografia
- **Promover reutilização e consistência:** sistema padronizado de classes e *design tokens*
- **Simplificar o desenvolvimento responsivo:** abordagem *Mobile First* integrada

### Importando o Tailwind

**Opção 1: Play CDN** (ideal para testes). No `<head>` do `index.html`:

```html
<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
```

**Opção 2: Tailwind CLI**

```bash
# Passo 1: instalar o Tailwind CLI
npm install tailwindcss @tailwindcss/cli
```

```css
/* Passo 2: importar no CSS */
@import "tailwindcss";
```

```bash
# Passo 3: integrar ao processo de transformação do CSS
npm install tailwindcss @tailwindcss/postcss postcss
```

**Passo 4:** integração com frameworks. Next.js, Laravel, Angular e Ruby on Rails têm procedimentos próprios de instalação e configuração, com o objetivo de adaptar o Tailwind à estrutura do projeto.

📖 Documentação: [tailwindcss.com/docs](https://tailwindcss.com/docs)

### 🧩 Tailwind CSS IntelliSense

Extensão para editores de código (VS Code) que:

- **Autocompleta classes** e propriedades disponíveis
- **Mostra os estilos** de cada classe durante a codificação
- **Reduz erros de digitação** e facilita o uso das utilities

### 📚 Lista de classes

Cada classe representa uma regra ou conjunto específico de estilos, combinadas diretamente no atributo `class`, sem criar uma regra CSS para cada componente.

Consulta: [tailwind.build/classes](https://tailwind.build/classes)

---

## ✅ Atividade 02

1. Criar um projeto que utilize **pelo menos 30 classes diferentes** do Tailwind CSS, cobrindo cores, tipografia, espaçamentos, dimensões, bordas, posicionamento, flexbox, grid e responsividade.
2. Organizar a entrega em um **repositório** e documentar em um **Markdown** com:
   - Prints do código
   - Prints da aplicação em funcionamento
   - Lista das classes utilizadas com suas funções
   - Link do projeto desenvolvido

| Entrega | Link |
|---|---|
| Repositório | [🔗 Acessar](COLE_O_LINK_AQUI) |
| Deploy | [🌐 Ver online](COLE_O_LINK_AQUI) |

### 📋 Lista de classes utilizadas

| # | Classe | Função |
|:-:|--------|--------|
| 01 | `bg-blue-600` | Cor de fundo |
| 02 | `text-white` | Cor do texto |
| 03 | `px-6 py-3` | Padding horizontal e vertical |
| 04 | `rounded-lg` | Bordas arredondadas |
| 05 | | |
| ... | | |

---

## 📝 Resumo

```
CSS puro → Box Model → Flexbox → Responsividade → Frameworks CSS → Tailwind (Utility-First)
```

Frameworks CSS aceleram a construção de interfaces com **padrões prontos**, e o Tailwind faz isso combinando **pequenas classes utilitárias** direto no HTML.

---

**Referência do material:** Frameworks Front-end — Frameworks CSS, Prof. Me. Deivison S. Takatu.