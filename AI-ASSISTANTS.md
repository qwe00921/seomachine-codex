# AI Assistants Guide

This file is the shared behavior contract for AI coding assistants in this repository.

## Goal

Keep the original SEO Machine workflow intact across different AI runtimes.

## Slash Command Compatibility

If a user prompt starts with `/`, interpret it as a workflow command and map it to `.claude/commands/`.

Examples:
- `/research` -> `.claude/commands/research.md`
- `/write` -> `.claude/commands/write.md`
- `/rewrite` -> `.claude/commands/rewrite.md`
- `/optimize` -> `.claude/commands/optimize.md`
- `/article` -> `.claude/commands/article.md`
- `/performance-review` -> `.claude/commands/performance-review.md`
- `/scrub` -> `.claude/commands/scrub.md`

## Required Context

Use these files before generating content:
- `context/brand-voice.md`
- `context/writing-examples.md`
- `context/style-guide.md`
- `context/seo-guidelines.md`
- `context/features.md`
- `context/internal-links-map.md`
- `context/target-keywords.md`
- `context/competitor-analysis.md`

## Output Rules

- Save artifacts to existing project folders:
  - `research/`
  - `drafts/`
  - `rewrites/`
  - `published/`
- Keep date-based file naming (`YYYY-MM-DD`) where command specs require it.
- Avoid overwriting user-authored files unless explicitly requested.

## Scrubbing Rule

For `/write` and `/rewrite`, scrub generated article files immediately after save:

```bash
python3 -c "from data_sources.modules.content_scrubber import scrub_file; scrub_file('PATH_TO_FILE', verbose=True)"
```

`/scrub` should call the same module on the provided path.

## Data Integrations

Commands using GA4/GSC/DataForSEO rely on:
- `data_sources/config/.env`
- `data_sources/requirements.txt`
- `data_sources/modules/`

If credentials are missing, continue with best-effort analysis and clearly state limitations.
