## What it does

`implement-direct` turns one ticket, a small spec, or an agreed conversation plan into verified commits. It uses **test-after**: implementation comes first, followed by checks and any necessary tests.

The workflow scales verification to the change. It requires evidence for changed behavior, without requiring a red-green cycle or prior approval of test seams.

## When to reach for it

You invoke this by typing `/implement-direct`, and the agent won't reach for it on its own.

| Situation | Skill |
| --- | --- |
| One decided task, with tests after implementation | `implement-direct` |
| One task with test-first development | [implement](https://aihero.dev/skills-implement) |
| A whole spec with dependent tickets and test-after | [implement-spec-direct](https://github.com/wtksana/skills/blob/main/docs/engineering/implement-spec-direct.md) |

## Prerequisites

Use the branch where the work should be committed. Tracker references require the project's configured tracker; a local file or conversation plan works without a remote tracker.

## Verification and review

Tests target observable behavior and acceptance criteria. A small documentation edit may need link and formatting checks; a changed API or bug fix may need contract and regression tests. Required repository checks still apply.

The original ordering stays: typechecks and focused tests during the run, the full test suite at the end, then [code-review](https://aihero.dev/skills-code-review) and a commit to the current branch.

## Common questions

**Does test-after mean skipping tests?**

No. The order changes, and the verification effort follows the impact. Existing checks or a concrete manual check can suffice for reversible, low-impact edits.

**Will it push, open a PR, or close the ticket?**

Like the original skill, it ends with a commit to the current branch. Pushing, opening a PR, and closing the ticket are not added by this variant.

**Does this also fix the original review ordering?**

No. It only replaces the TDD instruction. The original review-before-commit ordering remains, so a review based only on committed changes can miss uncommitted work.

## It's working if

- The implementation addresses one agreed task.
- Verification demonstrates the changed behavior and reports any gaps.
- Typechecks and focused tests run during implementation, and the full suite runs at the end.
- A code review runs before the commit on the current branch.

## Where it fits

This is the test-after build step after [to-tickets](https://aihero.dev/skills-to-tickets). [implement-spec-direct](https://github.com/wtksana/skills/blob/main/docs/engineering/implement-spec-direct.md) coordinates several tickets; [ask-matt](https://aihero.dev/skills-ask-matt) maps the available flows.
