# Enforced GitHub Action Workflows

This repository contains reusable GitHub Actions workflows enforced across the ElementX AI organization.

## Workflows

### Verify PR Title

Ensures pull request titles follow the [Conventional Commits](https://www.conventionalcommits.org/) format using [action-semantic-pull-request](https://github.com/amannn/action-semantic-pull-request).

Triggers on PR open, edit, and synchronize events.

### Code Quality Check

Runs code quality checks using [elementx-ai/code-quality-check](https://github.com/elementx-ai/code-quality-check) on pull requests and pushes to `main`. Only checks changed files.
