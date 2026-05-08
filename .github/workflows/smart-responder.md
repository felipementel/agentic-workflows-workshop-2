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

Triage bug report: "${{ github.event.issue.title }}" and add-comment with a summary of the next steps.


//[ "${{ github.event_name }}" = "workflow_dispatch" ] ||
