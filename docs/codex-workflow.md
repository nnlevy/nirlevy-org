# Codex PR Workflow

## Labels
- `codex-ready`: reviewed by a human (optional).
- `automerge`: safe to automerge (docs-only changes, UI copy, styling, non-sensitive bugfixes).

## Auto-merge policy
- Label `automerge` to trigger this workflow.
- PR must be ready for review (not draft).
- PR author must be `chatgpt-codex-connector` or branch must start with `codex/`.

### Never auto-merge
The workflow exits without automerging when files match any denylist pattern:
- `**/*wrangler*.{json,toml}`
- `**/.github/workflows/**`
- `**/src/**/stripe*`
- `**/src/**/payments*`
- `**/src/**/auth*`
- `**/src/**/sessions*`
- `**/src/**/worker/**/env*`
- `**/routing/**`
- `**/redirect`
- `**/canonical`
- `**/migrations/**`
- `**/*.sql`

### Merge behavior
- `pull_request_target` workflow scans changed files on `opened`, `synchronize`, `reopened`, `ready_for_review`, and `labeled` events.
- If no denylist matches, it enables GitHub auto-merge (`squash`) for the PR.
- If repository auto-merge is disabled, it falls back to API merge only when mergeability is clean.

## PR title format
Use `[codex]` prefix so these PRs are searchable across the portfolio:

- `[codex] add safe automerge workflow`

## Scope
This file documents workflow behavior only. The workflow does not make runtime code changes.
