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

# canal-deploy-hacker-news

ChatOps comando de barra para simular a implantação de um canal.

## Instructions

Crie um comando de barra ChatOps chamado /canal-deploy. Quando um usuário postar um comentário em uma issue do GitHub que comece com "/canal-deploy", faça o seguinte:
1) Responda ao comentário confirmando que o comando foi recebido e que a implantação do canal está em andamento.
2) Simule o processo de implantação do canal, incluindo etapas como construçãoo, testes e implantação, com mensagens de status para cada etapa.
3) Se a implantação for bem-sucedida, responda com uma mensagem de sucesso e um poema celebrando a implantação.
4) Se a implantação falhar, responda com uma mensagem de erro útil e um poema sarcástico sobre falhas de implantação, para animar o dia do usuário.
