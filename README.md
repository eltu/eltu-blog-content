# eltu-blog-content

Repositório de conteúdo do [eltu.blog](https://eltu.github.io). Contém os artigos em Markdown e imagens associadas.

## Estrutura

```
pt/posts/          # Artigos em Markdown (YYYY-MM-DD-slug.md)
assets/img/posts/  # Imagens dos artigos (YYYY-MM-DD/)
```

## Como criar novo artigo

1. Crie `pt/posts/YYYY-MM-DD-slug-do-post.md`
2. Adicione o frontmatter:

```yaml
---
layout: layouts/post.njk
title: "Título do Post"
date: YYYY-MM-DD
tags: [tag1, tag2]
description: "Breve descrição"
---
```

3. Coloque imagens em `assets/img/posts/YYYY-MM-DD/`
4. Escreva o conteúdo em Markdown

## Convenções

- Nomes de arquivo: `YYYY-MM-DD-slug-em-portugues.md`
- Imagens: `assets/img/posts/YYYY-MM-DD/nome.webp`
- Todo conteúdo é em Português
- Tags devem ser em minúsculas e separadas por hífen
