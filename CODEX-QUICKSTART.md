# Codex Quick Start

Use this guide if you want to run SEO Machine workflows in Codex.

## 1. Install Dependencies

```bash
pip install -r data_sources/requirements.txt
```

## 2. Configure Inputs

1. Fill the core context files:
   - `context/brand-voice.md`
   - `context/features.md`
   - `context/writing-examples.md`
2. Optional but recommended:
   - `context/internal-links-map.md`
   - `context/target-keywords.md`
3. If using analytics/performance workflows, configure:
   - `data_sources/config/.env` (copy from `.env.example`)
   - API credentials for GA4, GSC, DataForSEO

## 3. Use Slash-Style Workflow Prompts in Codex

This repo now includes `AGENTS.md` so you can keep the original command style.

Examples:

```text
/research podcast marketing strategy
/write podcast marketing strategy
/optimize drafts/podcast-marketing-strategy-2026-03-11.md
/rewrite published/old-guide-2024-11-01.md
/performance-review 30
```

## 4. Verify Artifacts

- Research briefs: `research/`
- Draft articles: `drafts/`
- Rewrites: `rewrites/`
- Published-ready content: `published/`

## 5. Useful Local Checks

```bash
python3 test_dataforseo.py
python3 research_quick_wins.py
```

## Notes

- The source workflow definitions remain in `.claude/commands/` and `.claude/agents/`.
- Codex uses those specs through the compatibility instructions in `AGENTS.md`.
