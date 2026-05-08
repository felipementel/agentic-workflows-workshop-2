---
# Trigger - when should this workflow run?
on:
  workflow_dispatch:  # Manual trigger

# Alternative triggers (uncomment to use):
# on:
#   issues:
#     types: [opened, reopened]
#   pull_request:
#     types: [opened, synchronize]
#   schedule: daily  # Fuzzy daily schedule (scattered execution time)
#   # schedule: weekly on monday  # Fuzzy weekly schedule

# Permissions - what can this workflow access?
# Write operations (creating issues, PRs, comments, etc.) are handled
# automatically by the safe-outputs job with its own scoped permissions.
permissions:
  contents: read
  issues: read
  pull-requests: read

# Tools - GitHub API access via toolsets (context, repos, issues, pull_requests)
# tools:
#   github:
#     toolsets: [default]

# Network access
network: defaults

# Outputs - what APIs and tools can the AI use?
safe-outputs:
  create-issue:          # Creates issues (default max: 1)
    max: 5               # Optional: specify maximum number
  # actions:
  # activation-comments:
  # add-comment:
  # add-labels:
  # add-reviewer:
  # allowed-github-references:
  # assign-milestone:
  # assign-to-agent:
  # assign-to-user:
  # autofix-code-scanning-alert:
  # call-workflow:
  # close-discussion:
  # close-issue:
  # close-pull-request:
  # concurrency-group:
  # create-agent-session:
  # create-agent-task:
  # create-code-scanning-alert:
  # create-discussion:
  # create-project:
  # create-project-status-update:
  # create-pull-request:
  # create-pull-request-review-comment:
  # dispatch-workflow:
  # dispatch_repository:
  # environment:
  # failure-issue-repo:
  # footer:
  # group-reports:
  # hide-comment:
  # id-token:
  # link-sub-issue:
  # mark-pull-request-as-ready-for-review:
  # max-bot-mentions:
  # max-patch-files:
  # mentions:
  # merge-pull-request:
  # missing-data:
  # missing-tool:
  # noop:
  # push-to-pull-request-branch:
  # remove-labels:
  # reply-to-pull-request-review-comment:
  # report-failure-as-issue:
  # report-incomplete:
  # resolve-pull-request-review-thread:
  # scripts:
  # set-issue-type:
  # steps:
  # submit-pull-request-review:
  # threat-detection:
  # unassign-from-user:
  # update-discussion:
  # update-issue:
  # update-project:
  # update-pull-request:
  # update-release:
  # upload-artifact:
  # upload-asset:

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
