---
on:
  workflow_dispatch:
  issues:
    types: [opened]
engine: copilot
safe-outputs:
  add-comment:
permissions:
  issues: read
  contents: read
  pull-requests: read
jobs:
  filter:
    runs-on: ubuntu-latest
    outputs:
      should-run: ${{ steps.check.outputs.result }}
    steps:
      - id: check
        env:
          LABELS: ${{ toJSON(github.event.issue.labels.*.name) }}
        run: |
          if echo "$LABELS" | grep -q '"bug"'; then
            echo "result=true" >> "$GITHUB_OUTPUT"
          else
            echo "result=false" >> "$GITHUB_OUTPUT"
          fi

if: needs.filter.outputs.should-run == 'true'

tools:
  github:
---

# Bug Issue Responder

Triagem do relatório de bug: "${{ github.event.issue.title }}" e adicione um comentário com um resumo dos próximos passos.

Ao final do comentário, escreva um poema sobre bugs no código e como eles são resolvidos, para alegrar o dia coloque um emoji que transmita alegria.


//[ "${{ github.event_name }}" = "workflow_dispatch" ] ||
