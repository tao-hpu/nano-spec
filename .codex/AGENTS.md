# nano-spec Agent for Codex CLI

## Overview
This agent helps create and manage nano-spec task specifications - a lightweight methodology for AI-assisted development.

## Commands

### Create a new nano-spec
When user says "create nano-spec for {description}" or "new task: {description}":

1. Generate a task folder with 4 files:
   - `README.md` - Background, goals, scope
   - `todo.md` - Tasks and acceptance criteria
   - `doc.md` - Technical decisions and documentation
   - `log.md` - Development log

2. Extract from description:
   - What problem is being solved (background)
   - What are the goals
   - What's in/out of scope
   - Break into actionable tasks
   - Define acceptance criteria

### Update nano-spec
When user says "update spec" or references an existing task:
- Read existing files in the task folder
- Make requested updates
- Keep acceptance criteria in sync with changes

## File Locations
- Look for `tasks/` folder first
- Fall back to project root
- Template available in `template/` folder

## Principles
1. Keep it nano - minimal docs, maximum clarity
2. Acceptance criteria are mandatory
3. Scope boundaries must be explicit
4. Log progress, not just outcomes
