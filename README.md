# Right Design Group — Org-wide Shared Workflows

Reusable GitHub Actions workflows for all RDG repositories.

## Workflows

### `issue-from-markdown.yml`
Automatically creates GitHub issues from `.github/issues/*.md` spec files when pushed to main.

**Features:**
- Detects new/changed markdown specs on push
- Skips already-linked or completed specs
- Extracts title, applies labels (enhancement, bug, security, performance)
- Updates markdown with `<!-- GitHub Issue: #N -->` link
- Optionally triggers stakeholder review workflow

**Usage in your repo:**
```yaml
# .github/workflows/issue-from-markdown.yml
name: Create Issues from Markdown
on:
  push:
    branches: [main]
    paths:
      - '.github/issues/*.md'
      - '!.github/issues/README.md'
      - '!.github/issues/archive/**'

jobs:
  create-issues:
    uses: Right-Design-Group/.github/.github/workflows/issue-from-markdown.yml@main
    permissions:
      issues: write
      contents: write
      actions: write
```
