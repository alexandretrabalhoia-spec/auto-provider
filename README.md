# Site Estático - Auto Provider

Este repositório armazena e serve as páginas estáticas para o domínio `auto-provider.bond`. Utilizamos o Caddy Server em conjunto com um sistema de diretórios onde **cada pasta na raiz do projeto corresponde a uma rota da URL**.

---

## 🚀 Deploy Automático (CI/CD)

O deploy é **100% automatizado**. Qualquer *push* ou aceite de *Pull Request* na branch `main` aciona o GitHub Actions (`.github/workflows/deploy-node.yml`). 

O nosso *runner* (self-hosted) no servidor executa o `git pull` na pasta de produção (`/var/www/auto-provider`). Como são arquivos estáticos servidos pelo Caddy, as mudanças vão ao ar imediatamente, sem necessidade de *build* ou *restart* de containers.

---

## 📂 Como criar uma nova página (Rota)

Para criar uma nova URL, por exemplo `auto-provider.bond/contato`, basta seguir esta regra:

1. Crie uma pasta na raiz com o nome desejado para a rota (ex: `contato/`).
2. Crie um arquivo `index.html` dentro dessa pasta.
3. Faça o *commit* e o *push* para a `main`.

## ✏️ Como editar uma página existente

Basta acessar a pasta da rota desejada (ex: `termos-de-uso-inventores-ideias/`), editar o `index.html` e fazer o *push*. O deploy encarregará de atualizar a página no ar.

---

## 🖼️ Usando Imagens, CSS e JavaScript

Para manter a organização, coloque as imagens e os scripts dentro da mesma pasta da sua rota. 

**Exemplo de estrutura de arquivos:**
```text
/minha-nova-rota
├── index.html
├── script.js
└── banner.png
Como referenciar dentro do index.html:
Como os arquivos estão no mesmo nível da página atual, basta usar o caminho relativo simples:

HTML
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo de Assets</title>
</head>
<body>
    <h1>Página com Imagem e JS</h1>
    
    <img src="banner.png" alt="Banner da Página" style="max-width: 100%;">

    <script src="script.js"></script>
</body>
</html>
