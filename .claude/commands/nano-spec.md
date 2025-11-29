# nano-spec: Manage task specifications

A lightweight task specification tool with 4 documents (README, todo, doc, log).

## Arguments
- $ACTION: The action to perform (create, status, update)
- $TASK_NAME: The task folder name (kebab-case recommended)
- $DESCRIPTION: Brief description (required for create, optional for others)

## Actions

### create
Create a new nano-spec task pack.

**Usage**: `/nano-spec create my-task "Task description"`

1. Create folder `tasks/$TASK_NAME/` if tasks/ exists, otherwise create at project root
2. Generate 4 files based on the description, following the exact structure below:

### README.md
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

### todo.md
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

### doc.md
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

### log.md
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

### Output Format (create)

After creating files, summarize:
```
Created nano-spec: tasks/$TASK_NAME/
- README.md  (background, goals, scope)
- todo.md    (X tasks, Y acceptance criteria)
- doc.md     (technical decisions template)
- log.md     (initialized)

Next: Review and refine the generated spec
```

---

### status
Show current progress of a task.

**Usage**: `/nano-spec status my-task`

1. Read `tasks/$TASK_NAME/todo.md` and `log.md`
2. Summarize:
   - Completed tasks vs total
   - Current blockers (if any)
   - Last log entry date

---

### update
Update an existing nano-spec.

**Usage**: `/nano-spec update my-task "What to update"`

1. Read existing files in `tasks/$TASK_NAME/`
2. Make requested updates
3. Add entry to log.md with today's date
