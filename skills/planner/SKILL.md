---
name: planner
description: >-
  Plans and sets up new features with proper ticketing, branching, and
  requirements documentation. Use when starting a new feature or task that
  needs proper project management setup.
---

# Planner Skill

You are helping plan and set up a new feature following a structured workflow. Your goal is to ensure proper project management practices before any coding begins.

## Workflow

### 1. Check for Linear Ticket
- Search for an existing Linear ticket related to the task
- If none exists, create one following the linear skill workflow
- Present the ticket to the user

### 2. Pre-Branch Safety Check
- Run `git status` to check for uncommitted changes
- If changes exist, alert the user and wait for instructions (commit, stash, or discard)
- **Never proceed with uncommitted changes without user approval**

### 3. Branch Setup
- Ask the user which branch they want to branch off of (default: `main`)
- Pull the latest changes from the base branch to ensure it's up to date
- Create and switch to the new feature branch
- Name the branch descriptively (e.g., `feature/TICKET-id-description`)

### 4. Requirements Documentation
- Create a `workflow/` directory if it doesn't exist
- Create a `REQUIREMENTS.md` file in the workflow directory
- Collaborate with the user to define requirements for the task
- Include relevant sections based on the task type (design, backend, frontend, etc.)
- Commit and push the requirements file with user approval

### 5. Update Linear Ticket
- After the user agrees on the REQUIREMENTS.md, update the Linear ticket description
- Add the agreed-upon requirements to the ticket description
- Use the `LINEAR_UPDATE_ISSUE` tool to update the ticket

### 6. Commit and Push
- Follow the **github-process** skill for all git operations
- Commit and push the requirements file with user approval

## Output
- Present the Linear ticket URL
- Confirm the branch is set up and ready for development
- Summarize the requirements that were documented
