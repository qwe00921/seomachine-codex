# SEO Machine

> Fork & Attribution Notice
>
> This repository is an independent fork of the original project:
> [TheCraigHewitt/seomachine](https://github.com/TheCraigHewitt/seomachine).
>
> - Upstream (original): `https://github.com/TheCraigHewitt/seomachine.git`
> - This fork adds multi-assistant compatibility while keeping the original workflow structure.
> - This fork is not officially affiliated with, endorsed by, or maintained by the upstream authors.
> - Original authorship and project credit belong to the upstream repository and contributors.
> - The upstream project license continues to apply to this fork.

SEO Machine is a command-driven AI workspace for long-form SEO content production: research, writing, optimization, and publishing.

## Quick Navigation

- [Quick Start](#quick-start)
- [Runtime Support](#runtime-support)
- [Core Workflow](#core-workflow)
- [Commands](#commands)
- [Required Context Files](#required-context-files)
- [Data Integrations](#data-integrations)
- [Project Structure](#project-structure)
- [Upstream Sync](#upstream-sync)
- [Support and Contributing](#support-and-contributing)
- [License](#license)

## Quick Start

1. Clone this fork:
   ```bash
   git clone https://github.com/qwe00921/seomachine-codex.git
   cd seomachine-codex
   ```
2. Install dependencies:
   ```bash
   pip install -r data_sources/requirements.txt
   ```
3. Create environment files:
   ```bash
   cp .env.example .env
   cp data_sources/config/.env.example data_sources/config/.env
   ```
4. Fill required credentials in `.env` and `data_sources/config/.env` as needed.
5. Fill core context files in `context/` (see [Required Context Files](#required-context-files)).
6. Run your first workflow:
   ```text
   /research your topic
   /write your topic
   /optimize drafts/your-topic-YYYY-MM-DD.md
   ```

For more guided setup:
- General quick start: [QUICK-START.md](QUICK-START.md)
- Codex-specific quick start: [CODEX-QUICKSTART.md](CODEX-QUICKSTART.md)

## Runtime Support

| Runtime | Instruction File(s) |
|---|---|
| Claude Code | `CLAUDE.md` |
| Codex | `AGENTS.md`, `CODEX-QUICKSTART.md` |
| Gemini | `GEMINI.md`, `AI-ASSISTANTS.md` |
| Cursor | `.cursorrules`, `AI-ASSISTANTS.md` |
| Windsurf | `.windsurfrules`, `AI-ASSISTANTS.md` |
| Cline | `.clinerules`, `AI-ASSISTANTS.md` |
| GitHub Copilot | `.github/copilot-instructions.md`, `AI-ASSISTANTS.md` |

Shared cross-runtime behavior is centralized in `AI-ASSISTANTS.md`.

## Core Workflow

### New Content

1. `/research [topic]` -> keyword + SERP research brief in `research/`
2. `/write [topic]` -> article draft in `drafts/`
3. `/optimize [draft-file]` -> optimization report in `drafts/`
4. `/publish-draft [draft-file]` -> publish draft to WordPress (optional)

### Existing Content

1. `/analyze-existing [url-or-file]`
2. `/rewrite [topic-or-analysis]`
3. `/optimize [rewrite-file]`

## Commands

### Core
- `/research [topic]`
- `/write [topic]`
- `/rewrite [topic]`
- `/analyze-existing [url-or-file]`
- `/optimize [file]`
- `/publish-draft [file]`
- `/article [topic]`
- `/cluster [topic]`
- `/content-calendar`
- `/priorities`
- `/performance-review [days]`
- `/scrub [file]`

### Research
- `/research-serp [keyword]`
- `/research-gaps`
- `/research-trending`
- `/research-performance`
- `/research-topics`

### Landing Pages
- `/landing-write [topic]`
- `/landing-audit [file]`
- `/landing-research [topic]`
- `/landing-competitor [url]`
- `/landing-publish [file]`

Detailed command specs live in:
- `.claude/commands/`

Agent role definitions live in:
- `.claude/agents/`

## Required Context Files

Fill these before serious content generation:

- `context/brand-voice.md`
- `context/writing-examples.md`
- `context/style-guide.md`
- `context/seo-guidelines.md`
- `context/features.md`
- `context/internal-links-map.md`
- `context/target-keywords.md`
- `context/competitor-analysis.md`

Example filled context set:
- `examples/castos/`

## Data Integrations

Supported integrations:
- Google Analytics 4
- Google Search Console
- DataForSEO
- WordPress (draft publishing + Yoast meta fields)

Primary docs:
- Analytics/data setup: [data_sources/README.md](data_sources/README.md)
- Additional setup guide: [data-sources-setup.md](data-sources-setup.md)
- WordPress setup: [wordpress/README.md](wordpress/README.md)

WordPress env vars expected by publisher:
- `WORDPRESS_URL`
- `WORDPRESS_USERNAME`
- `WORDPRESS_APP_PASSWORD`

## Project Structure

```text
seomachine-codex/
├── .claude/                   # Commands, agents, skills
├── .github/                   # Copilot instructions
├── context/                   # Brand + SEO context
├── data_sources/              # Integrations and analysis modules
├── drafts/                    # Generated drafts
├── research/                  # Research briefs and reports
├── rewrites/                  # Updated content
├── published/                 # Finalized content
├── topics/                    # Topic ideas
├── wordpress/                 # WP plugin/snippets/docs
├── AGENTS.md                  # Codex instructions
├── AI-ASSISTANTS.md           # Shared runtime rules
├── CLAUDE.md                  # Claude Code instructions
├── GEMINI.md                  # Gemini instructions
├── QUICK-START.md
└── CODEX-QUICKSTART.md
```

## Upstream Sync

Keep this fork up to date with upstream fixes:

```bash
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

## Support and Contributing

- Fork issues: [qwe00921/seomachine-codex issues](https://github.com/qwe00921/seomachine-codex/issues)
- Upstream issues: [TheCraigHewitt/seomachine issues](https://github.com/TheCraigHewitt/seomachine/issues)
- Contribution guide: [CONTRIBUTING.md](CONTRIBUTING.md)

## License

This project is distributed under the [MIT License](LICENSE).  
As a fork, upstream licensing and attribution are preserved.

## Credits

Originally developed in the upstream project for Castos and later open-sourced for broader SEO content workflows.
