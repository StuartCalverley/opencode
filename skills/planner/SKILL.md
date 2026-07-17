---
name: planner
description: >-
  High-level feature planning. Creates Linear tickets and documents the problem
  and desired outcome. Does not write code or plan implementation details.
---

# Planner Skill

You are helping plan a feature or issue at a high level. Your goal is to capture **what** the problem is and **what** the end result should look like — not how to build it.

## Workflow

### 1. Understand the Request
- Ask clarifying questions if the user's request is ambiguous
- Identify the core problem or opportunity
- Understand what "done" looks like from the user's perspective

### 2. Check for Linear Ticket
- Search for an existing Linear ticket related to the task
- If none exists, create one following the linear skill workflow
- Present the ticket to the user

### 3. Branch Setup
- Run `git status` to check for uncommitted changes
- If changes exist, alert the user and wait for instructions (commit, stash, or discard)
- **Never proceed with uncommitted changes without user approval**
- Ask the user which branch they want to branch off of (default: `main`)
- Pull the latest changes from the base branch to ensure it's up to date
- Create and switch to the new feature branch
- Name the branch descriptively (e.g., `feature/TICKET-id-description`)

### 4. Document the Plan
- Create a `workflow/` directory if it doesn't exist in the project root
- Create a `REQUIREMENTS.md` file in the workflow directory
- Use this template:
  ```markdown
  # TICKET-ID: Feature Title

  ## Problem
  What's broken, missing, or could be better?

  ## Desired Outcome
  What should the end result look like? Describe the user experience or behavior.

  ## Scope
  What's in and what's out for this work.

  ## Linear Ticket
  Link to the Linear ticket.
  ```
- Present the written REQUIREMENTS.md to the user for approval
- Make any requested changes before proceeding

### 5. Update Linear Ticket
- After the user agrees on the REQUIREMENTS.md, update the Linear ticket description
- Add the agreed-upon summary to the ticket description
- Use the `LINEAR_UPDATE_ISSUE` tool to update the ticket

### 6. Stop — Do Not Proceed to Implementation
- The planner workflow ends here
- Do NOT begin coding, creating branches, or making changes to the codebase
- The user will explicitly request implementation when ready
- Planning and implementation are separate workflows

## Output
- Present the Linear ticket URL
- Summarize what was documented
