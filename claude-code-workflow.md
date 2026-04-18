# Claude Code Project Workflow

A framework for building projects with Claude Code — use this as a personal reference
or paste it into Claude at the start of a new project to establish shared context.

---

## 1. Plan

### Define the Goal
- What problem does this solve? Write it in one sentence.
- Who is it for, and what does success look like?
- What is explicitly out of scope?

### Set Milestones
- Break the project into 3–5 meaningful phases (e.g. data model → API → UI → auth → deploy)
- Each milestone should produce something testable or demonstrable
- Identify which milestone is the MVP — the minimum that proves the idea works

### Create a Spec Document
Before writing any code, produce a `SPEC.md` covering:
- **Overview** — one-paragraph summary of the project
- **Tech stack** — language, framework, key libraries, and why
- **Architecture** — how the major pieces fit together (a simple diagram or bullet list)
- **Data model** — key entities and their relationships
- **Key features** — ranked by priority
- **Out of scope** — explicit exclusions to prevent scope creep
- **Open questions** — decisions not yet made

> Tell Claude: *"Before we write any code, help me produce a SPEC.md for this project."*

---

## 2. Setup

### Initialize the Project
- Scaffold the project structure (`create-next-app`, `cargo init`, `npm init`, etc.)
- Set up version control: `git init`, create `.gitignore`, make an initial commit
- Configure the package manager and lock file

### Define a Branching Strategy
- Document the branching strategy in `CONTRIBUTING.md` or a `## Git Workflow` section in the README
- Default strategy: feature branches off `main`, merged via PR or direct merge when ready
  - `main` — stable, deployable at all times
  - `feat/<name>` — new features (e.g. `feat/user-auth`)
  - `fix/<name>` — bug fixes (e.g. `fix/login-redirect`)
  - `chore/<name>` — non-functional changes (e.g. `chore/update-deps`)
- Document any deviations from this in the project `CLAUDE.md`

> Tell Claude: *"Our branching strategy is feature branches off main. Create a new branch before starting any feature."*

### Configure Claude Code
- Create a `CLAUDE.md` in the project root — this is Claude's persistent memory across sessions
- Include in `CLAUDE.md`:
  - One-line project description
  - Tech stack and key dependencies
  - Commands to run tests, build, and start the dev server
  - Non-negotiable code style rules (MUST / MUST NOT)
  - Any gotchas or non-obvious architectural decisions
- Keep it under 150 lines — Claude deprioritizes bloated files

> Run `/init` in Claude Code after placing `CLAUDE.md` so Claude acknowledges it.

### Define the Environment
- Set up `.env.example` with all required environment variables (no real secrets)
- Configure linting and formatting (ESLint, Prettier, Ruff, etc.)
- Set up the test runner, even if no tests exist yet

### Verify the Baseline
- Confirm the project starts and builds cleanly before adding any features
- Make a `chore: project setup` commit

---

## 3. Build

### Work in Milestone Slices
- Tackle one milestone at a time — don't jump ahead
- Start each Claude session by stating the current milestone and its goal
- End each milestone with a working, testable state before moving on

### The Feature Loop
For each feature or task:
1. **Describe the goal** — tell Claude what you want, not how to build it
2. **Review the plan** — ask Claude to outline its approach before it codes
3. **Implement** — let Claude write the code
4. **Test** — run tests, check the UI, probe edge cases
5. **Review the diff** — read what changed before accepting it
6. **Update the changelog** — log what changed in `CHANGELOG.md` before committing
7. **Commit** — small, frequent commits with clear messages

### Keep Claude Oriented
- Start each new session with: *"Here's where we are: [milestone]. Here's what we're doing next: [task]."*
- If Claude drifts or produces something off-base, redirect early — don't let it compound
- Use `/clear` to reset context when switching between unrelated tasks

### Testing Strategy
- Write or request tests at the feature level, not just at the end
- Ask Claude to verify its own changes: *"Run the tests and confirm everything passes."*
- For UI work, ask for a checklist of things to manually verify

### When Things Go Wrong
- If a change breaks something, revert before asking Claude to debug
- Describe bugs with: what you expected, what actually happened, and any error output
- Add a rule to `CLAUDE.md` if Claude makes the same mistake twice

---

## 4. Wrap Up

### Harden
- Audit for exposed secrets, missing validation, and unhandled errors
- Remove debug code, console logs, and dead code
- Review and finalize the `.env.example`

### Document
- Update the `README.md` with: what it does, how to install, how to run, how to test
- Note any non-obvious decisions in the code or in `CLAUDE.md` for future sessions

### Final Review
- Do a full pass through the diff from the start of the milestone
- Confirm all milestone goals are met before marking it done
- Tag a release or cut a version if relevant

---

## Quick Reference: Useful Claude Prompts

| Situation | Prompt |
|---|---|
| Starting a project | *"Help me write a SPEC.md for this project before we write any code."* |
| Starting a session | *"We're on milestone 2 (API layer). Today's task is X."* |
| Before Claude codes | *"Outline your approach before writing anything."* |
| After a bug | *"Here's what I expected, here's what happened. Diagnose before you fix."* |
| Claude drifting | *"Stop — let's refocus. The goal is just X."* |
| Wrapping a milestone | *"Review what we built against the spec and tell me what's missing."* |
