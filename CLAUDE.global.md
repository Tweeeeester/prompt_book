# Global Claude Code Defaults

Applies to all projects. Project-level CLAUDE.md overrides anything here.

---

## Workflow

Follow this process for all new projects:

@~/docs/claude-code-workflow.md

---

## How I Work

- Before starting any task, confirm you understand the goal — ask if unclear
- For non-trivial tasks, outline your approach before writing any code
- MUST NOT make large sweeping changes without checking first
- Work in small, focused steps — one thing at a time
- After implementing, verify your changes work before declaring done

## Code Style (Universal)

- Write clean, readable code over clever code
- MUST leave the codebase cleaner than you found it
- MUST NOT leave debug code, console.logs, or commented-out code behind
- Use consistent naming conventions — follow whatever the project already uses
- MUST NOT commit secrets, API keys, or credentials under any circumstances

## Git

- Commit frequently with clear, descriptive messages
- Format: `type: short description` (e.g. `feat: add login form`, `fix: handle null user`)
- Each commit should represent one logical change
- MUST NOT commit directly to main — all work happens on a feature branch
- Branch naming: `feat/<name>`, `fix/<name>`, `chore/<name>` branched off `main`
- MUST update `CHANGELOG.md` before every commit — log what changed and why
  - Use format: `## [Unreleased]` section with `### Added / Changed / Fixed` bullets
  - One entry per logical change, not per file touched

## Verification

- Run tests after any non-trivial change — don't assume it works
- If no tests exist, say so rather than skipping verification silently
- Call out breaking changes explicitly before implementing them

## Communication

- If something is ambiguous, ask before assuming
- If you hit a blocker or something unexpected, say so immediately
- Keep responses focused — don't pad with unnecessary explanation
- If I ask for a plan, give the plan — don't also write the code unless asked
- Always use `yyyy-mm-dd` format for dates

---

## Project Setup Checklist

When starting a new project from scratch, MUST complete in order:
1. Write `SPEC.md` before any code
2. Scaffold project and initialize git
3. Define and document the branching strategy
4. Create `CHANGELOG.md` with an initial `## [Unreleased]` section
5. Create project-level `CLAUDE.md`
6. Confirm clean build/run before first feature
