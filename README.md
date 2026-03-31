# claude-workflow

Canonical source for the Claude Code `"@claude"` GitHub Actions workflow.

## What this is

A public reference repo containing the canonical `claude.yml` workflow file. Copy it into any repo to enable `"@claude"` mentions in issues, comments, and pull requests.

> **Note on reusable workflows:** `claude-code-action` relies on GitHub event context data (`comment.author`) that GitHub does not propagate to cross-repo reusable workflow jobs. The `uses:` delegation pattern therefore doesn't work with this action. The correct distribution model is copying the workflow file directly.

## How to wire it into a new repo

1. Add `ANTHROPIC_API_KEY` to the repo's secrets
   (Settings → Secrets and variables → Actions → New repository secret)

2. Copy `claude.yml` to `.github/workflows/claude.yml` in your repo

3. Push — the workflow is live

## Files

| File | Purpose |
|------|---------|
| `claude.yml` | Canonical workflow — copy to `.github/workflows/claude.yml` |

## Keeping in sync

There is no automatic propagation. When the canonical `claude.yml` changes, update each consuming repo manually by copying the new version.
