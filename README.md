# claude-workflow

Reusable GitHub Actions workflow for Claude Code integration.

## What this is

A public reusable workflow that enables any GitHub repo to respond to `@claude` mentions in issues, comments, and pull requests. Because GitHub only allows reusable workflows from public repos to be called cross-repo in personal accounts, this repo is public. It contains no secrets — those are injected at runtime from each calling repo.

## How to wire it into a new repo

1. Add `ANTHROPIC_API_KEY` to the repo's secrets
   (Settings → Secrets and variables → Actions → New repository secret)

2. Copy `caller-template.yml` to `.github/workflows/claude.yml` in your repo

3. Push — the workflow is live

## Files

| File | Purpose |
|------|---------|
| `.github/workflows/claude.yml` | Reusable workflow — the implementation |
| `caller-template.yml` | Copy this into calling repos |

## How it works

The reusable workflow contains the full job implementation. Calling repos supply:
- The event triggers (`issue_comment`, `issues`, `pull_request_review`, etc.)
- The `if:` condition that filters for `@claude` mentions
- `secrets: inherit` to pass `ANTHROPIC_API_KEY`

Updates to this repo propagate automatically to all callers (they reference `@main`).

## Pinning to a specific version

Replace `@main` with a tag for stability:

```yaml
uses: teunispolak/claude-workflow/.github/workflows/claude.yml@v1.0.0
```
