# Spring Office Hours Repository

## Purpose
This repository hosts the Spring Office Hours newsletter content, auto-updated via GitHub Actions.

## Key Workflow
- **Auto-update**: Daily at 04:16 UTC via `.github/workflows/daily.yml`
- **Update mechanism**: Downloads `newsletter-cli` from `dashaun-tanzu/newsletter-cli`, runs `./newsletter-cli full-update`, replaces README.md with `spring-update.md`

## YouTube section retry
`newsletter-cli` intermittently emits a `## YouTube:` heading with no entries — historically about a third of scheduled runs. The workflow guards against this:

- After each run it counts the list items under `## YouTube:`. Fewer than `MIN_YOUTUBE_ITEMS` (default 1) means the output is rejected and regenerated.
- Retries use exponential backoff: **15s, 30s, 60s, 120s** across 5 attempts (~3m45s worst case), capped at `MAX_DELAY_SECONDS`.
- If every attempt is still empty, the newest issue is **published anyway**, with the previous issue's YouTube entries carried over into the section, and a `::warning::` in the log. A newsletter always ships.
- The job only fails when `newsletter-cli` produces no usable output at all (crash or missing file) — there is nothing to publish, so README.md is left untouched.

Tune via the `env:` block on the `Run newsletter-cli` step: `MAX_ATTEMPTS`, `INITIAL_DELAY_SECONDS`, `MAX_DELAY_SECONDS`, `MIN_YOUTUBE_ITEMS`.

## Commands
- Manually trigger: GitHub UI → Actions → `daily.yml` → Run workflow
- Local preview: download newsletter-cli and run `./newsletter-cli full-update`

## Constraints
- README.md is generated; avoid manual edits (they'll be overwritten)
- Workflow requires `PAT_TOKEN` or `GITHUB_TOKEN` with `contents: write` permission
- The release lookup calls the GitHub API with an `Authorization` header, raising the rate limit from 60 req/hr (per shared runner IP) to 1000 req/hr
