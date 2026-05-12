---
name: Daily Digest
on:
  # schedule: weekly on monday around 11:00 AM
  workflow_dispatch:
permissions:
  issues: read
  contents: read
  pull-requests: read
safe-outputs:
  create-issue:
    max: 1
    title-prefix: "[repo status] "
    labels: [report]

tools:
  github:
---

## Instructions

Every 10 minutes
 - Update the readme with the execution data and time, and scan the repository to analyze the folder structure and see if we need to update anything.
 - Also write a new poem at the end of the readme.
 - Create a GitHub issue that summarises all open issues
   and pull requests in this repository. Group them by label. Include the
   total count, the title, the author, and how long each item has been
   open. Title the issue "Daily Digest – <date>".

Create a daily status report for maintainers.

Include
- Recent repository activity (issues, PRs, discussions, releases, code changes)
- Progress tracking, goal reminders and highlights
- Project status and recommendations
- Actionable next steps for maintainers

Keep it concise and link to the relevant issues/PRs.
