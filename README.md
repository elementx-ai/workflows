# Enforced GitHub Action Workflows

This repository contains reusable GitHub Actions workflows enforced across the ElementX AI organization.

## Workflows

### Verify PR Title

Ensures pull request titles follow the [Conventional Commits](https://www.conventionalcommits.org/) format using [action-semantic-pull-request](https://github.com/amannn/action-semantic-pull-request).

Triggers on PR open, edit, and synchronize events.

### Code Quality Check

Runs code quality checks using [elementx-ai/code-quality-check](https://github.com/elementx-ai/code-quality-check) on pull requests and pushes to `main`. Only checks changed files.

### Codeowners Merge

Allows CODEOWNERS to self-merge pull requests using [elementx-ai/code-owner-self-merge](https://github.com/elementx-ai/code-owner-self-merge). Triggers on PR open, issue comments, and PR review submissions. Uses a GitHub App token (configured via `CODEOWNERS_APP_ID` and `CODEOWNERS_APP_PRIVATE_KEY`) to perform squash merges.
