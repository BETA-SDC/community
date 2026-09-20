# Message Archive Guidelines

[中文](./message-archive-guidelines.zh.md) | English

> This document explains how to archive official notices, emails, group messages, and publicity copy after sending. For the full activity workflow, see the [Event Creation Workflow](./event-creation-workflow.md).

## What A Message Archive Is

A message archive is not a random draft file. It is a `[message]` Sub-issue under the corresponding main activity Issue, containing a full copy of what was actually sent.

The archive helps confirm later:

- What was sent
- Which channel was used
- When it was sent
- Who sent it or owned it
- Whether screenshots, links, or recipient scope notes exist

> [!IMPORTANT]
> Archive the final version after it was actually sent. Drafts may be edited in branch files, but the final sent content still needs to be saved in a `[message]` Sub-issue.

## When To Archive

Archive:

- Email notices for activity participants
- Official notices in WeChat, Feishu, or other groups
- Registration opening, registration reminders, time or location changes, and other important messages
- Publicity posts, recruitment copy, and official account copy
- Official information that affects activity arrangements, registration, attendance, or public understanding

Usually do not archive:

- Casual group chat
- Unsent drafts
- Small confirmations only among collaborators
- Intermediate drafts replaced by the final archived version

## Sub-Issue Title

Message archive Sub-issues use:

```text
[message] Activity Name - Channel - YYYY-MM-DD
```

Examples:

```text
[message] Math Help Room - Email notice - 2026-09-09
[message] Group Birthday Ceremony - WeChat group notice - 2026-09-16
```

The activity name should match the main activity Issue. The channel should name the actual sending channel, such as `Email notice`, `WeChat group notice`, or `Official account post`.

## Sub-Issue Content

The archive Sub-issue should include at least:

- Full content of the sent copy
- Sending channel
- Sending time
- Sender or owner
- Screenshots, links, or recipient scope notes, if applicable

Recommended structure:

```markdown
## Sending Information

- Channel:
- Sending time:
- Sender:
- Recipient scope:

## Body

Copy the final sent content here.

## Attachments Or Notes

- Screenshot:
- Link:
- Other notes:
```

## Labels

Message archive Sub-issues should at least add the `message` label.

Add channel labels when useful:

- Email: `message` + `mail`
- Group notice: `message` + `group-notice`

If the archive reveals follow-up work, such as resending, changing a poster, or updating a registration form, create a separate `[task]` Sub-issue instead of mixing task discussion into the archive.
