---
name: Slash Command Canal Deploy
on:
  slash_command:
    name: review
    events: [pull_request_comment]  # Only respond to /review in PR comments
permissions:
  contents: read
  pull-requests: read
safe-outputs:
  create-pull-request-review-comment:
    max: 5
  add-comment:
---

# hn-sentiment

Describe what you want the AI to do when this workflow runs.

## Instructions

Crie um comando de barra ChatOps chamado /canal-deploy. Quando um usuário postar um comentário em uma issue do GitHub que comece com "/canal-deploy <url>", onde <url> é a URL de uma notícia do Hacker News (por exemplo, https://news.ycombinator.com/item?id=12345), faça o seguinte:
0) Tudo tem que ser escrito em português do Brasil.
1) Extraia o ID da notícia do Hacker News da URL.
2) Busque até 50 comentários principais dessa notícia na API do Hacker News.
3) Realize uma análise de sentimento no texto do comentário, classificando cada comentário como Positivo, Negativo ou Neutro.
4) Gere um resumo que mostre: o sentimento geral (com a porcentagem de distribuição), os 3 comentários mais positivos (com trecho) e os 3 comentários mais negativos (com trecho).

5) Responda ao comentário original da issue com a análise formatada em Markdown.

Se nenhuma URL for fornecida ou se a URL não for uma notícia válida do Hacker News, responda com uma mensagem de erro útil e um poema sarcástico sobre a importância de fornecer uma URL válida, para animar o dia do usuário.
