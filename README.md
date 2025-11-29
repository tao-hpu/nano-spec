# nano-spec

> Spec-driven thinking, nano-sized docs.

A lightweight task specification methodology for AI-assisted development. Inspired by [Kiro's Spec-Driven Development](https://kiro.dev/docs/specs/), but minimal and practical.

## Why nano-spec?

| Approach | Docs | Overhead | Best For |
|:---|:---:|:---:|:---|
| No spec | 0 | None | Trivial tasks |
| **nano-spec** | 4 | Low | Most tasks |
| Kiro SPEC | 3+ | High | Complex features |

**nano-spec** hits the sweet spot: enough structure to think clearly, not so much that you're writing docs instead of code.

## The 4 Documents

```
tasks/{task-name}/
├── README.md   # Context: What & Why
├── todo.md     # Plan: Tasks & Acceptance Criteria
├── doc.md      # Output: Decisions & Conclusions
└── log.md      # Journey: Daily progress & learnings
```

| Document | Purpose | When to Write |
|:---|:---|:---|
| README.md | Background, goals, scope, dependencies | At start |
| todo.md | Checklist + acceptance criteria | At start, update as you go |
| doc.md | Technical decisions, schemas, diagrams | During & after |
| log.md | Daily notes, blockers, discoveries | Daily |

## Quick Start

### Manual
```bash
cp -r template/ tasks/my-new-task/
```

### With Claude Code
```
/nano-spec create my-new-task "Brief description of the task"
```

### With Codex CLI
```
codex "Create a nano-spec for: my task description"
```

### With Gemini CLI
```
gemini "Create a nano-spec for: my task description"
```

## Core Principles

1. **Boundary first** - Define what's in/out of scope before coding
2. **Acceptance criteria** - Know when you're done
3. **Decisions documented** - Future you will thank present you
4. **Progress logged** - Track the journey, not just the destination

## Example

See [examples/nhsa/](./examples/nhsa/) for a real-world example (NHSA medical insurance data integration).

## Tool Support

| Tool | Config Location | Status |
|:---|:---|:---:|
| Claude Code | `.claude/commands/nano-spec.md` | Ready |
| OpenAI Codex | `.codex/AGENTS.md` | Ready |
| Gemini CLI | `.gemini/instructions.md` | Ready |
| Cursor | Copy to `.cursorrules` | Manual |
| Windsurf | Copy to rules | Manual |

## Installation

### For Claude Code
```bash
# Copy to your project
cp -r .claude/commands/nano-spec.md /your-project/.claude/commands/

# Or copy the whole template folder
cp -r template/ /your-project/tasks/_template/
```

### For Codex CLI
```bash
cp .codex/AGENTS.md /your-project/.codex/
```

### For Gemini CLI
```bash
cp -r .gemini/ /your-project/
```

## Philosophy

> "Think before you code, even with AI."

AI coding assistants are powerful, but they work better when you know what you want. nano-spec is a thinking framework that happens to produce documents.

The documents aren't the point. **Clarity is.**

## License

MIT

## Contributing

PRs welcome. Keep it nano.
