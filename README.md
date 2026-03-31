# claude-workflow

Reusable GitHub Actions workflow for Claude Code (`@claude`) integration.

## What this is

A public repo hosting a reusable `claude.yml` workflow. Any repo can delegate to it via `uses:`, so updates propagate automatically without copying files.

## How to wire it into a new repo

1. Add `ANTHROPIC_API_KEY` to the repo's secrets
   (Settings → Secrets and variables → Actions → New repository secret)

2. Copy `caller-template.yml` to `.github/workflows/claude.yml` in your repo

3. Push — the workflow is live

## Files

| File | Purpose |
|------|---------|
| `.github/workflows/claude.yml` | Reusable workflow — referenced via `uses:` |
| `caller-template.yml` | Thin caller to copy into consuming repos |

## Known limitation

`claude-code-action` crashes with a null author error on issues or PRs that have prior bot comments from failed workflow runs. Workaround: delete those comments before retrying `@claude`.
