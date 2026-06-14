# Changelog

## [Unreleased]

### Added
- `README.md` with one-time bootstrap instructions and repo structure overview
- `skills/sync-prompt-book/SKILL.md` — invokable skill (`/sync-prompt-book`) that pulls the repo and re-syncs all local Claude Code config files

### Changed
- Renamed `Claude Code Project Workflow.md` to `claude-code-workflow.md` for consistency
- Updated `CLAUDE.global.md` to reference the renamed workflow file path
- Added `yyyy-mm-dd` date format preference to Communication section of `CLAUDE.global.md`
- Updated `CLAUDE.global.md` with Karpathy LLM coding principles:
  - **Surgical changes**: touch only what you must; clean up orphans your changes created, not pre-existing dead code; match existing style
  - **Simplicity first**: minimum code that solves the problem, no speculative features or premature abstractions
  - **Explicit assumptions**: state assumptions before implementing; present multiple interpretations rather than picking silently
  - **Verifiable goals**: define success criteria before writing code; state a plan with verification steps for multi-step tasks
  - **One question at a time**: never bundle multiple decision-making questions in one response
  - Removed conflicting "MUST leave the codebase cleaner than you found it" rule (superseded by surgical changes principle)
