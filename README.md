# Atlas

Plataforma EdTech B2B com interface SaaS para gestão escolar preditiva com IA.

## Stack

- Vue 3 (`script setup`)
- Vite 5
- Tailwind CSS 3
- PostCSS + Autoprefixer

## Pré-requisitos

- Node.js 18+
- npm 9+
- Git

## Instalação

```bash
git clone no projeto
cd atlas
npm install
```

## Rodando em desenvolvimento

```bash
npm run dev
```

Depois abra a URL mostrada no terminal (normalmente `http://localhost:5173`).

## Build de produção

```bash
npm run build
```

Os arquivos finais serão gerados na pasta `dist/`.

## Preview local do build

```bash
npm run preview
```

## Scripts disponíveis

- `npm run dev`: inicia servidor de desenvolvimento com hot reload.
- `npm run build`: gera build otimizado para produção.
- `npm run preview`: sobe servidor local para validar o build.

## Estrutura principal

- `src/App.vue`: layout principal, abas e fluxos de UI.
- `src/main.js`: bootstrap da aplicação Vue.
- `src/style.css`: diretivas do Tailwind CSS v3.
- `tailwind.config.js`: configuração de conteúdo do Tailwind.
- `vite.config.js`: configuração do Vite com plugin do Vue.
- `assets/`: imagens usadas no projeto e no pitch.
- `pitch-atlas.md`: deck em Marp Markdown.


## Troubleshooting

- Se `npm install` falhar por versão do Node, atualize para Node 20 LTS.
- Se a porta `5173` estiver ocupada, o Vite sugere outra automaticamente.
- Se o estilo não carregar, confirme se `src/style.css` contém:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```
