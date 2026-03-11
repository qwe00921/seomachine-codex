# GitHub Copilot Instructions

Use `AI-ASSISTANTS.md` as the shared behavior contract for this repository.

Key requirements:
- Treat slash-style prompts (`/research`, `/write`, `/optimize`, etc.) as mapped workflow commands from `.claude/commands/`.
- Use context files in `context/` before generating or rewriting content.
- Save outputs to existing workflow directories (`research/`, `drafts/`, `rewrites/`, `published/`).
- Run content scrubbing after `/write` and `/rewrite` via `data_sources/modules/content_scrubber.py`.
