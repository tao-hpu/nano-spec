# nano-spec: Create a new task specification

Create a new nano-spec task pack with 4 documents (README, todo, doc, log).

## Arguments
- $TASK_NAME: The task folder name (kebab-case recommended)
- $DESCRIPTION: Brief description of what this task is about

## Instructions

1. Create folder `tasks/$TASK_NAME/` if tasks/ exists, otherwise create at project root
2. Generate 4 files based on the description:

### README.md
- Extract background and goals from description
- Define clear scope (in/out)
- List any obvious dependencies

### todo.md
- Break down into research/implementation/verification phases
- Generate specific acceptance criteria
- Mark what's explicitly out of scope

### doc.md
- Start with summary placeholder
- Add any obvious technical decisions needed
- Leave open questions section

### log.md
- Initialize with today's date
- Add "Task created" entry

## Output Format

After creating files, summarize:
```
Created nano-spec: tasks/$TASK_NAME/
- README.md  (background, goals, scope)
- todo.md    (X tasks, Y acceptance criteria)
- doc.md     (technical decisions template)
- log.md     (initialized)

Next: Review and refine the generated spec
```
