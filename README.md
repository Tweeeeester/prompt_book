# prompt-book

Personal Claude Code configuration — global `CLAUDE.md`, workflow docs, and reusable skills.

## One-Time Setup

Clone the repo (if you haven't already):

```bash
git clone <repo-url> ~/Development/prompt_book
```

Run the bootstrap script to copy everything into place:

```bash
cd ~/Development/prompt_book

mkdir -p ~/docs ~/.claude/skills

# Global Claude defaults
cp CLAUDE.global.md ~/.claude/CLAUDE.md

# Workflow reference (imported by CLAUDE.md via @~/docs/...)
cp claude-code-workflow.md ~/docs/claude-code-workflow.md

# Sync skill (lets you update everything going forward)
cp -r skills/sync-prompt-book ~/.claude/skills/
```

## Keeping Things Updated

After the one-time setup, use the skill from any Claude Code session:

```
/sync-prompt-book
```

This pulls the latest from the repo and re-syncs all files.

## Structure

```
CLAUDE.global.md          # Copied to ~/.claude/CLAUDE.md
claude-code-workflow.md   # Copied to ~/docs/claude-code-workflow.md
skills/
  sync-prompt-book/       # Copied to ~/.claude/skills/sync-prompt-book/
    SKILL.md
```
