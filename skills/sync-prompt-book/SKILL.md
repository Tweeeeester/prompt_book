---
name: sync-prompt-book
description: Pull the latest prompt book from the repo and sync CLAUDE.md, workflow docs, and skills to local Claude Code config. Use when the user says "sync prompt book", "update claude config", or "/sync-prompt-book".
tools: Bash, Read
---

# Sync Prompt Book

Pull the latest changes from the prompt book repository and update local Claude Code config files.

## Step 1: Pull Latest Changes

```bash
git -C ~/Development/prompt_book pull
```

Report whether anything was updated or already up to date.

## Step 2: Sync Global CLAUDE.md

```bash
cp ~/Development/prompt_book/CLAUDE.global.md ~/.claude/CLAUDE.md
```

## Step 3: Sync Workflow Docs

```bash
mkdir -p ~/docs
cp ~/Development/prompt_book/claude-code-workflow.md ~/docs/claude-code-workflow.md
```

## Step 4: Sync Skills

Copy any skill directories from the repo into the local skills folder:

```bash
mkdir -p ~/.claude/skills
for skill_dir in ~/Development/prompt_book/skills/*/; do
  skill_name=$(basename "$skill_dir")
  cp -r "$skill_dir" ~/.claude/skills/"$skill_name"
done
```

## Step 5: Report

Tell the user what was synced:
- `~/.claude/CLAUDE.md` — global Claude defaults
- `~/docs/claude-code-workflow.md` — workflow reference
- Any skills copied to `~/.claude/skills/`

If `git pull` showed new commits, summarize the changes at a high level.
