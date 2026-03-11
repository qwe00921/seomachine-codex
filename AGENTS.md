# AGENTS.md

This repository was originally built for Claude Code slash commands. This file adapts the same workflow for Codex-style agents.

## Core Goal

Preserve the existing command-driven content workflow (`/research`, `/write`, `/optimize`, etc.) while running inside Codex.

## Command Compatibility Layer

When a user message starts with `/`, treat it as a workflow command.

1. Parse the command name and arguments from the user message.
2. Load the matching command spec from `.claude/commands/`.
3. Follow the process in that spec.
4. Save outputs to the expected directories and naming patterns.
5. Return a short execution summary with output file paths.

## Supported Slash Commands

- `/research` -> `.claude/commands/research.md`
- `/write` -> `.claude/commands/write.md`
- `/rewrite` -> `.claude/commands/rewrite.md`
- `/analyze-existing` -> `.claude/commands/analyze-existing.md`
- `/optimize` -> `.claude/commands/optimize.md`
- `/performance-review` -> `.claude/commands/performance-review.md`
- `/publish-draft` -> `.claude/commands/publish-draft.md`
- `/article` -> `.claude/commands/article.md`
- `/priorities` -> `.claude/commands/priorities.md`
- `/cluster` -> `.claude/commands/cluster.md`
- `/content-calendar` -> `.claude/commands/content-calendar.md`
- `/research-serp` -> `.claude/commands/research-serp.md`
- `/research-gaps` -> `.claude/commands/research-gaps.md`
- `/research-trending` -> `.claude/commands/research-trending.md`
- `/research-performance` -> `.claude/commands/research-performance.md`
- `/research-topics` -> `.claude/commands/research-topics.md`
- `/landing-write` -> `.claude/commands/landing-write.md`
- `/landing-audit` -> `.claude/commands/landing-audit.md`
- `/landing-research` -> `.claude/commands/landing-research.md`
- `/landing-publish` -> `.claude/commands/landing-publish.md`
- `/landing-competitor` -> `.claude/commands/landing-competitor.md`
- `/scrub` -> `.claude/commands/scrub.md`

## Agent References

If a command requires specialized analysis, use the corresponding role specs in `.claude/agents/`.

## Required Context Inputs

Before content generation commands, check and use:

- `context/brand-voice.md`
- `context/writing-examples.md`
- `context/style-guide.md`
- `context/seo-guidelines.md`
- `context/features.md`
- `context/internal-links-map.md`
- `context/target-keywords.md`
- `context/competitor-analysis.md`

## File Output Rules

- Keep all output in existing workflow folders: `research/`, `drafts/`, `rewrites/`, `published/`.
- Use date-based file names in `YYYY-MM-DD`.
- Do not overwrite user-authored files unless explicitly asked.

## Scrubbing Requirement

For `/write` and `/rewrite`, run content scrubbing immediately after saving article content:

```bash
python3 -c "from data_sources.modules.content_scrubber import scrub_file; scrub_file('PATH_TO_FILE', verbose=True)"
```

`/scrub` should call the same module on the provided file path.

## Data Source Commands

Commands that rely on GA4, GSC, or DataForSEO should use:

- `data_sources/config/.env`
- `data_sources/requirements.txt`
- modules in `data_sources/modules/`

If credentials are missing, continue with best-effort analysis and explicitly state limitations.

## Non-Goals

- Do not rewrite `.claude/` command specs unless requested.
- Do not introduce new dependencies unless necessary for a requested feature.
