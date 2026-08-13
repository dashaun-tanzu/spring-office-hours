# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A content repository for the Spring Office Hours newsletter. There is no application code here — the only meaningful artifact is `README.md`, which is **generated** by an external tool.

## Critical: README.md is generated, not authored

`README.md` is overwritten on every run of the daily workflow. Do not hand-edit it expecting changes to stick — the next scheduled run will clobber them. The newsletter logic lives in a separate repo: [`dashaun-tanzu/newsletter-cli`](https://github.com/dashaun-tanzu/newsletter-cli). Edits to formatting, sources, or output structure belong there, not here.

## How the generation works

`.github/workflows/daily.yml` runs at 04:16 UTC daily (and on manual `workflow_dispatch`):

1. Downloads the latest `newsletter-cli` binary from the `dashaun-tanzu/newsletter-cli` releases (Linux amd64, with fallback to the first asset).
2. Runs `./newsletter-cli full-update`, which produces `spring-update.md`.
3. `mv spring-update.md README.md`, deletes the binary, commits with message `Update README.md via newsletter-cli [skip ci]`, and pushes.

The workflow uses `secrets.PAT_TOKEN` if present, falling back to `GITHUB_TOKEN` with `contents: write`.

The API call in step 1 sends an `Authorization` header, which raises the rate limit from the anonymous 60 req/hr (shared per runner IP) to 1000 req/hr.

### Retry on an empty YouTube section

`newsletter-cli` intermittently emits a `## YouTube:` heading with no entries under it — historically on roughly a third of scheduled runs. Step 2 therefore validates its own output instead of trusting it: it counts the list items under the `## YouTube:` heading and, if the count is below `MIN_YOUTUBE_ITEMS` (default 1), discards the output and regenerates with exponential backoff — **15s, 30s, 60s, 120s** across 5 attempts, ~3m45s worst case. The same retry covers a non-zero exit or a missing output file.

Tune via the `env:` block on the `Run newsletter-cli` step: `MAX_ATTEMPTS`, `INITIAL_DELAY_SECONDS`, `MAX_DELAY_SECONDS`, `MIN_YOUTUBE_ITEMS`.

**A newsletter always ships.** If every attempt still comes back empty, the newest generated issue is published anyway, with the YouTube entries from the previous `README.md` spliced into the empty section, and a `::warning::` recorded in the run log. Today's news and releases stay fresh; only the video list is stale.

The job fails in exactly one case: `newsletter-cli` produced no usable output at all (crashed every attempt, or wrote no file). There is nothing to publish then, so `README.md` is left untouched.

Because the carry-over reads the previous `README.md`, a run of consecutive failures keeps re-carrying the same list. The `::warning::` is the signal to look upstream at `newsletter-cli`.

## Local preview

To preview what the next scheduled run will produce:

```bash
# Download the latest newsletter-cli release for your platform, then:
chmod +x newsletter-cli
./newsletter-cli full-update   # writes spring-update.md
```

`spring-update.md` is in `.gitignore` — it's the staging file the workflow renames to `README.md`.

## When making changes here

- Workflow tweaks (schedule, permissions, asset-selection logic) → `.github/workflows/daily.yml`.
- Anything that affects the rendered newsletter content → upstream in `newsletter-cli`, not here.
