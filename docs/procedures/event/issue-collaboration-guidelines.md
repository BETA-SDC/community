# Issue Collaboration Guidelines

[中文](./issue-collaboration-guidelines.zh.md) | English

> This document explains how to use Issues, Sub-issues, labels, branches, and Pull Requests for activity collaboration. For the full activity workflow, see the [Activities and Publicity](./README.md).

## Title Rules

All Issues and Sub-issues should use English half-width square brackets as type prefixes.

General rules:

- Use fixed prefixes such as `[event]`, `[task]`, and `[message]`
- Add one space after the prefix, then write the activity or item name
- A main activity Issue usually contains only the activity name and does not need extra fields
- Sub-issue titles must include the parent activity or item name; do not write only the task itself
- Sub-issues use ` - `, with spaces on both sides, to separate the parent, task, channel, date, or other fields, keeping parent-child relationships and item levels clear
- Keep the activity name consistent for the same activity
- Use `YYYY-MM-DD` for dates

> [!TIP]
> `[event] BETA MEET: The Field Experience of an Ecologist` is a main activity Issue title. `[task] BETA MEET: The Field Experience of an Ecologist - Create poster` is the corresponding Sub-issue title. Do not write `[task] Create poster` or `[task] BETA MEET: The Field Experience of an Ecologist-Create poster`.

## Common Title Formats

| Type | Use | Title Format |
| --- | --- | --- |
| `[event]` | Main activity Issue | `[event] Activity Name` |
| `[improvement]` | Process, regulation, tool, or collaboration improvement | `[improvement] Improvement Item Name` |
| `[task]` | Concrete task assigned to members | `[task] Activity Name - Task Name` |
| `[message]` | Archive of an officially sent notice | `[message] Activity Name - Channel - YYYY-MM-DD` |
| `[wrap-up]` | Activity review, media organization, or wrap-up item | `[wrap-up] Activity Name - Wrap-up Item` |
| `[question]` | Temporary question, information to confirm, or discussion item | `[question] Question Summary` |
| `[docs]` | Documentation maintenance, correction, addition, or organization | `[docs] Document Name or Maintenance Item` |

Examples:

```text
[event] Math Help Room
[improvement] Establish standard activity creation workflow
[task] Math Help Room - Create registration form
[message] Math Help Room - Email notice - 2026-09-09
[wrap-up] Group Birthday Ceremony - Organize photo materials
[question] Should we standardize the registration form template
[docs] Update activity workflow instructions
```

## Label Rules

Use a small and stable label set rather than creating a new label for every activity.

| Label | Applies To | Purpose |
| --- | --- | --- |
| `event` | Main Issue | Main entry for an activity or activity-related item |
| `internal-improvement` | Main Issue | Internal process, collaboration method, regulation, or tool improvement |
| `documentation` | Issue or PR | Documentation maintenance or changes |
| `task` | Sub-issue | Concrete task assigned to a member |
| `message` | Sub-issue | Archive of an officially sent message or copy |
| `mail` | Sub-issue | Related to email |
| `group-notice` | Sub-issue | Related to WeChat, Feishu, or other group notices |
| `notification-poster` | Sub-issue | Related to posters, posts, or publicity materials |
| `wrap-up` | Main Issue or Sub-issue | Post-activity review, media organization, or wrap-up item |

Recommended use:

- Main activity Issues should at least add `event`
- Internal improvement proposals should at least add `internal-improvement`
- Documentation maintenance should add `documentation`
- Task assignment Sub-issues should at least add `task`
- Message archive Sub-issues should at least add `message`
- Email archives should use `message` + `mail`
- Group notice archives should use `message` + `group-notice`
- Poster, post, and registration publicity material tasks should use `task` + `notification-poster`
- Post-activity review or media organization should use `wrap-up`

## Sub-Issue Assignment

After an activity enters execution, the owner should split independently actionable work into Sub-issues and assign them to corresponding members.

Each Sub-issue should explain:

- Task content and deliverables
- Owner or executor
- Deadline or expected collection time
- Required materials, links, templates, or prerequisite confirmations
- Where the result should be submitted, such as a Pull Request, comment attachment, shared document, or directory

> [!IMPORTANT]
> Poster, post, and registration publicity material tasks should be created as Sub-issues under the corresponding main activity Issue, with the activity owner or publicity owner @ mentioned. Images, QR codes, and reference images should be attached to the Sub-issue.

## Branch Names

After an activity enters execution, create the corresponding branch from the Issue page. The branch name should be short, recognizable, and related to the activity.

Recommended format:

```text
two-digit-issue-number-activity-short-name
```

Examples:

```text
05-standard-workflow
12-math-help-room
18-group-birthday
```

Issue numbers should use two digits. If the number has fewer than two digits, add a leading `0`. If older branches or references use one-digit numbers, correct them during later cleanup.

## Pull Requests

After activity materials are ready for review, submit a Pull Request. The PR should explain:

- Linked Issue
- Which activity materials were added or modified
- Which information has been confirmed and which still needs owner confirmation
- Whether it involves emails, group messages, or other public copy that has not yet been sent
- Whether special checks are needed for time, location, budget, guest information, or registration method

After the owner reviews the Pull Request, they may request changes. Merge only after revisions are complete and the content is confirmed.
