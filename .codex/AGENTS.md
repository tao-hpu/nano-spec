# nano-spec Agent for Codex CLI

## Overview
This agent helps create and manage nano-spec task specifications - a lightweight methodology for AI-assisted development.

## Commands

### Create a new nano-spec
When user says "create nano-spec for {description}" or "new task: {description}":

1. Create folder `tasks/{task-name}/` if tasks/ exists, otherwise create at project root
2. Generate 4 files following the exact structure below:

#### README.md
```markdown
# {Task Name}

## Background
{Why does this task exist? What problem are we solving?}

## Goals
- {Goal 1}
- {Goal 2}

## Scope

### In Scope
- {What's included}

### Out of Scope
- {What's NOT included - be explicit}

## Dependencies
- [ ] {Dependency 1 - e.g., another task, external API, team decision}

## Resources
- {Link to related docs}
- {Link to external references}
```

#### todo.md
```markdown
# TODO

## Research
- [ ] {Research item 1}
- [ ] {Research item 2}

## Implementation
- [ ] {Task 1}
- [ ] {Task 2}
- [ ] {Task 3}

## Verification
- [ ] {Verification step}

---

## Acceptance Criteria

### Must Have
- [ ] {Criterion 1 - specific, measurable}
- [ ] {Criterion 2}

### Nice to Have
- [ ] {Optional criterion}

### Out of Scope
- {Explicitly NOT part of this task's acceptance}
```

#### doc.md
```markdown
# {Task Name} - Technical Document

## Summary
{One paragraph summary of the solution/outcome}

## Key Decisions

### Decision 1: {Title}
- **Options considered**: A, B, C
- **Chosen**: B
- **Rationale**: {Why B?}

## Technical Details

### Architecture / Data Flow
```
{Diagram using ASCII or describe the flow}
```

### Interfaces / Schema
```typescript
// Key interfaces if applicable
interface Example {
  id: string;
  name: string;
}
```

### Implementation Notes
- {Note 1}
- {Note 2}

## Open Questions
- [ ] {Unresolved question 1}
- [ ] {Unresolved question 2}

## References
- {Link 1}
- {Link 2}
```

#### log.md
```markdown
# Development Log

## {YYYY-MM-DD}

### Done
- Task created

### In Progress
- {What's ongoing}

### Blocked
- {What's stuck and why}

### Notes
- {Discoveries, learnings, things to remember}

---

<!-- Copy the template above for each day -->
```

### Update nano-spec
When user says "update spec" or references an existing task:
- Read existing files in the task folder
- Make requested updates
- Keep acceptance criteria in sync with changes

## File Locations
- Look for `tasks/` folder first
- Fall back to project root

## Principles
1. Keep it nano - minimal docs, maximum clarity
2. Acceptance criteria are mandatory
3. Scope boundaries must be explicit
4. Log progress, not just outcomes
