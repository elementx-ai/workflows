# Enforced GitHub Action Workflows

This repository contains reusable GitHub Actions workflows enforced across the ElementX AI organization.

## Workflows

### Verify PR Title

Ensures pull request titles follow the [Conventional Commits](https://www.conventionalcommits.org/) format using [action-semantic-pull-request](https://github.com/amannn/action-semantic-pull-request).

Triggers on PR open, edit, and synchronize events.

### Code Quality Check

Runs code quality checks using [elementx-ai/code-quality-check](https://github.com/elementx-ai/code-quality-check) on pull requests and pushes to `main`. Only checks changed files.

### Codeowners Merge

A shared (reusable) workflow that allows CODEOWNERS to self-merge pull requests using [elementx-ai/code-owner-self-merge](https://github.com/elementx-ai/code-owner-self-merge). Uses a GitHub App token (configured via `CODEOWNERS_APP_ID` and `CODEOWNERS_APP_PRIVATE_KEY`) to perform squash merges.

Call it from each consuming repo rather than copying it:

```yaml
# .github/workflows/codeowners-merge.yaml
name: Codeowners Merge

on:
  pull_request_target: { types: [opened] }
  issue_comment: { types: [created] }
  pull_request_review: { types: [submitted] }

jobs:
  merge-check:
    if: >
      github.event_name != 'issue_comment' ||
        github.event.issue.pull_request != ''
    uses: elementx-ai/workflows/.github/workflows/codeowners-merge.yaml@main
    secrets: inherit
```

The `if` condition on the calling job prevents the workflow from running on plain issue comments (i.e. comments on issues that are not pull requests).
