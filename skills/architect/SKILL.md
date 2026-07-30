---
name: architect
description: >-
  Creates proposal and design documents from requirements. Use when you have a
  REQUIREMENTS.md and need to create implementation planning documents before
  coding begins.
---

# Architect Skill

You are helping create planning documents from requirements. This is a collaborative process — always ask for user input on design choices.

## STOP after this skill completes

This skill ends after committing and pushing the proposal and design docs. Do NOT proceed to implementation. The user will initiate the next step separately.

## Workflow

### 1. Read Requirements
- Read the `workflow/REQUIREMENTS.md` file
- Understand the task and constraints
- **Wait for user confirmation** before proceeding to step 2

### 2. Create Proposal
- Create `workflow/proposal.md`
- Include: Problem, Proposed Solution, Key Changes, Success Criteria
- Ask the user about framework/tool preferences (e.g., Tailwind, CSS modules)
- Note if this is design-only or includes functionality
- Listen for any architectural decisions the user mentions
- Ask for the user's opinion on technical approaches, not just design choices
- **Present the proposal to the user and wait for feedback before proceeding**

### 3. Create Design Spec
- Create `workflow/design.md`
- Include detailed specs: colors, typography, layout, spacing, shadows, border-radius
- For new projects, include full color palette and design tokens
- For existing projects, check if global styles exist first
- **Present the design spec to the user and wait for feedback before proceeding**

### 4. Collaborate (Iterative)
- Present both documents to the user
- Ask for feedback and make adjustments
- Listen for architectural decisions and technical preferences
- Ask for the user's opinion on approaches, not just design choices
- Repeat until the user is satisfied with the results
- **Do not proceed until the user explicitly approves both documents**

### 5. Commit and Push
- Check git status for uncommitted changes
- Stage `workflow/proposal.md` and `workflow/design.md`
- Ask for a commit message (suggest: `docs: add [TICKET-ID] proposal and design spec`)
- Commit and push with user approval
- **This skill is now complete. Stop here.**

## Output
- `workflow/proposal.md` — High-level overview
- `workflow/design.md` — Detailed design specifications
- Both files committed and pushed to the feature branch
