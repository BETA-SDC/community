# BETA-SDC Community Agent Instructions

## Event Proposal Work

When a task involves `BETA-SDC/event-proposal` or any of the following topics, first read:

```text
skills/event-proposal-workflow/SKILL.md
```

This applies to:

- Creating or planning an activity
- Updating an activity Issue or Sub-issue
- Reviewing Issue titles, labels, assignees, parents, branches, or Pull Requests
- Archiving emails, group notices, reminders, or publicity copy
- Naming activity directories and material files
- Organizing registration, sign-in, or attendance records
- Reviewing, organizing, or delivering activity photos and videos
- Auditing old Issues or checking `event` and `message` label conflicts

Do not choose a specialist Skill directly before reading the workflow Skill. The workflow Skill is the routing entry point and determines which specialist Skills are needed.

## Specialist Skill Routing

After reading `event-proposal-workflow/SKILL.md`, read only the specialist Skills relevant to the task:

| Task | Specialist Skill |
| --- | --- |
| Activity planning, main Issue, task breakdown, wrap-up | `skills/event-proposal-author/SKILL.md` |
| Issue title, labels, Sub-issues, branches, PRs | `skills/event-issue-collaboration/SKILL.md` |
| Historical Issue cleanup or role/label conflicts | `skills/event-proposal-issue-maintainer/SKILL.md` |
| Email, group notice, reminder, or publicity archive | `skills/event-message-archive/SKILL.md` |
| Activity directory and material filenames | `skills/event-material-naming/SKILL.md` |
| Registration, sign-in, and attendance records | `skills/event-sign-in-records/SKILL.md` |
| Photos, videos, permissions, Album delivery | `skills/event-media-capture/SKILL.md` |

For mixed tasks, follow the execution order and conflict priority in the workflow Skill. Do not load every specialist Skill by default.

## Source Of Truth

Use the formal procedures under:

```text
docs/procedures/event/
```

If an instruction in a Skill conflicts with a formal procedure, follow the formal procedure and update the Skill later if needed.

## GitHub Issue Operations

When inspecting or changing GitHub Issues:

- Confirm the repository is `BETA-SDC/event-proposal`.
- Inspect the full Issue body, labels, state, comments, assignees, parent, and related files before editing.
- Check both open and closed Issues when auditing historical records.
- Preserve the original sent notification text when creating an archive.
- Do not invent dates, channels, senders, recipients, attendance numbers, or authorization status.
- After changes, run the workflow Skill's final checks, especially the `event + message` conflict scan.

## Change Workflow

Before editing:

1. Read the workflow Skill.
2. Read the relevant specialist Skills.
3. Read the corresponding formal procedure.
4. Inspect the current repository or Issue state.
5. State a short implementation update before making changes.

After editing:

1. Run the relevant checks.
2. Review the diff or Issue state.
3. Report changed files or Issue URLs and unresolved uncertainty.
4. Follow the user's instruction about commit and push. If no exception is given, use the repository's normal Git workflow.

## Scope

These instructions apply to the `community` repository and to related `BETA-SDC/event-proposal` maintenance performed from this workspace.
