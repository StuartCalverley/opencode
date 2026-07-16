---
name: github-process
description: >-
  GitHub workflow rules and best practices. Use when working with git, branches,
  commits, or any GitHub operations. Enforces safety checks and approval
  workflows.
---

# GitHub Process

## Branch Management

- **Before branching**: Ask the user which branch they want to branch off of (default: `main`).
- **Ensure base branch is up to date**: Before creating a new branch, pull the latest changes from the base branch.
- **Before switching branches**: Run `git status` to check for uncommitted changes.
- If changes exist, alert the user and wait for instructions (commit, stash, or discard) before switching.

## Commit Rules

- **Never commit without approval**: Always ask the user for explicit approval before running `git commit`.
- **Commit message**: Ask the user for a commit message. If they decline to provide one, generate a concise, descriptive message based on the changes.
- Present the diff and commit message for review before executing.
- Only commit when the user explicitly says to commit or push.

## Workflow

1. **Pre-flight check** — Always run `git status` before branch operations.
2. **Present changes** — Show `git diff` to the user if changes exist.
3. **Get approval** — Wait for explicit user approval before any commit.
4. **Execute** — Run the git command only after approval.
