# Codex Workflow

## Labels

- `codex-ready`: human-reviewed or accepted by operator (optional)
- `automerge`: safe to automate merge for this PR

## Safety denylist (never automerged)

Do not merge with `automerge` if PR files match any of these patterns:

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

## PR title format

Use `[codex]` as a prefix for Codex PR titles so they are easy to query.

Examples:

- `[codex] add safe automerge workflow`
- `[codex] tighten search snippet`
