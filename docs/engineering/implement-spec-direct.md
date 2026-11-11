## What it does

`implement-spec-direct` implements an entire spec and its dependent tickets on an integration branch. Each implementer writes the change first, then runs checks and adds the tests needed to verify it.

It preserves the original task graph, worktree, integration, review, PR, and cleanup steps. Only the implementer instruction changes from calling TDD to implementing first and verifying afterward.

## When to reach for it

You invoke this by typing `/implement-spec-direct`, and the agent won't reach for it on its own.

| Situation | Skill |
| --- | --- |
| Whole spec, independent tickets, test-after | `implement-spec-direct` |
| One ticket or a small plan, test-after | [implement-direct](https://github.com/wtksana/skills/blob/main/docs/engineering/implement-direct.md) |
| Whole spec with test-first implementation | [implement-spec](https://aihero.dev/skills-implement-spec) |

## Prerequisites

Provide a spec and tickets with acceptance criteria and dependencies. Tracker-hosted work needs the configured tracker. Parallel execution uses [subagents](https://www.aihero.dev/ai-coding-dictionary/subagent) and independent Git worktrees, as in the original skill. Every subagent starts with a fresh context window, and each ticket gets a new implementer rather than reusing a previous one. Review fixes also use a fresh implementer.

## Integration is part of verification

Each implementer verifies its changes after implementation. The original final [code-review](https://aihero.dev/skills-code-review) still runs on the integration branch, with findings assigned to an implementer for correction.

Optional exploration notes keep the original location outside the repo, accessible to future implementers. The original worktree cleanup step remains.

## Common questions

**Does each ticket call implement-direct?**

No. Both direct skills are user-invoked. The coordinator supplies implementers with explicit test-after instructions.

**Does this change scheduling or PR handling?**

No. The original frontier scheduling, draft PR, tracker resolution, and cleanup instructions are preserved.

## It's working if

- Concurrent implementers have separate worktrees.
- Dependent tickets start after their dependencies are integrated.
- Each delivered ticket has acceptance evidence.
- Code review covers the integration branch and its findings receive fixes.
- The original PR or tracker close-out and worktree cleanup complete.

## Where it fits

This is the test-after orchestration step after [to-spec](https://aihero.dev/skills-to-spec) and [to-tickets](https://aihero.dev/skills-to-tickets). [implement-direct](https://github.com/wtksana/skills/blob/main/docs/engineering/implement-direct.md) handles one task. [ask-matt](https://aihero.dev/skills-ask-matt) maps the available flows.
