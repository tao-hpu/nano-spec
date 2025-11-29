# nano-spec Instructions for Gemini CLI

## What is nano-spec?
A lightweight task specification methodology using 4 documents:
- README.md (Context)
- todo.md (Plan + Acceptance Criteria)
- doc.md (Technical Decisions)
- log.md (Progress Journal)

## When to Create a nano-spec
- User asks to "create a spec for..."
- User asks to "plan a task..."
- User describes a multi-step development task
- User wants to document a technical decision

## How to Generate

### Step 1: Understand the Task
Ask clarifying questions if the description is vague:
- What's the end goal?
- What's explicitly NOT in scope?
- Are there dependencies on other work?

### Step 2: Create Files
Generate in `tasks/{task-name}/` or project root:

**README.md**: Background, goals, scope (in/out), dependencies
**todo.md**: Phased tasks (research/implement/verify) + acceptance criteria
**doc.md**: Key decisions, technical details, open questions
**log.md**: Today's date with "Task created" entry

### Step 3: Confirm
Show user what was created and ask if adjustments needed.

## Updating Existing Specs
- Read all 4 files first to understand context
- Keep acceptance criteria aligned with changes
- Add log entry for significant updates

## Key Principles
1. Boundary first - scope before code
2. Acceptance criteria - know when done
3. Decisions documented - for future reference
4. Progress logged - track the journey
