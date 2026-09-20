# event-proposal Repository File Naming Rules (Draft)

[中文](./event-proposal-repo-naming-regulation.zh.md) | English

> This draft defines file and directory naming rules inside the [`event-proposal`](https://github.com/BETA-SDC/event-proposal) repository. It is intended to standardize how activity materials, poster information, sign-in records, and notification copy are stored.

## Scope

This guideline applies to files and directories in the [`event-proposal`](https://github.com/BETA-SDC/event-proposal) repository, including:

- Academic year directories
- Activity material directories
- Activity proposals
- Poster information forms
- Notification copy files
- Sign-in record directories and CSV files
- Other materials directly related to a single activity

Issue titles, Sub-issue titles, branch names, and label rules still follow the [Event Creation Workflow](./event-creation-workflow.md).

## Principles

- **Directories describe the series, session number, and session topic; files describe material types.** Activity directory names should prioritize the series so events in the same series naturally group together. Keep file names as stable material type names.
- **Do not put dates in activity directory names.** Activity time is already recorded in Issues, Sub-issues, Pull Requests, message archives, and activity material content, so directories should not start with dates.
- **Use uppercase, stable, and recognizable series codes.** Put the series code first, such as `BETA-MEET`, `MATH-HELP-ROOM`, or `GROUP-BIRTHDAY`. The series code should identify the stable series; do not put the year, season, or session topic in it, and do not shorten away an inherent part of the series name.
- **Use two-digit session numbers.** Put a two-digit session number after the series code, such as `01`, `02`, not `1`, `2`.
- **Use lowercase English and hyphens for the topic.** The specific session topic uses `kebab-case`; avoid spaces, Chinese punctuation, mixed capitalization, and temporary descriptions.
- **Keep one main directory per activity.** Proposal, poster, sign-in, notification, and review materials for one activity should live under the same activity directory.
- **Avoid status words in file names.** Do not use words such as `final`, `new`, `latest`, or `revised`; status should be reflected in Git history, Pull Requests, or file content.

## Directory Structure

Recommended structure:

```text
event-proposal/
  README.md
  README.zh.md
  template-for-poster-information.md
  YYYY-YYYY/
    SERIES-two-digit-session-specific-topic/
      README.md
      proposal.md
      poster-information.md
      notification-message.md  # optional
      sign-in/
        README.md
        00-summary.csv
        01-registered-attended.csv
        02-registered-absent.csv
        03-registered-cancelled.csv
        04-unregistered-attended.csv
```

Existing examples:

- [2026-2027](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027)
- [2026-09-09-math-help-group-01](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-09-math-help-group-01)
- [2026-09-16-group-birthday-ceremony-01](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-16-group-birthday-ceremony-01)

The two activity directories above are historical naming examples. New activity directories should use the new format in this document.

## Academic Year Directory Names

Academic year directories use:

```text
YYYY-YYYY
```

Example:

- [2026-2027](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027)

Academic year directories should only identify the academic year. Do not use them to express departments, activity types, or owners.

## Activity Directory Names

Activity directories use:

```text
SERIES-two-digit-session-specific-topic
```

Field meanings:

- `SERIES`: series code, placed first, using uppercase English letters and hyphens, such as `BETA-MEET`, `MATH-HELP-ROOM`, or `GROUP-BIRTHDAY`; the series name should be stable and recognizable, without the year, season, or session topic
- `two-digit-session`: the session number in that series, using `01`, `02`, `03`
- `specific-topic`: the specific topic of this session, using lowercase English and hyphens

Examples:

```text
BETA-MEET-01-the-field-experience-of-an-ecologist
BETA-MEET-02-topic-of-the-next-session
MATH-HELP-ROOM-01-calculus-review
GROUP-BIRTHDAY-01-2026-fall
```

With this format, activities in the same series naturally group together by directory name. Dates can still be recorded in the [main activity Issue](./event-creation-workflow.md), message archive Sub-issues, `proposal.md`, and `poster-information.md`.

Not recommended:

```text
2026.09.09 Math Help
2026-09-09-math-help-group-1
BETA-MEET-1-the-field-experience-of-an-ecologist
beta-meet-01-the-field-experience-of-an-ecologist
BETA-MEET-01
BETA-MEET-01-final
GROUP-BIRTHDAY-2026-FALL-01
生日会材料
```

## Activity Material File Names

### Activity Directory README

Each activity directory should include a `README.md` that briefly introduces the directory and links to the corresponding main activity Issue. This `README.md` does not replace `proposal.md`; its purpose is to help readers quickly understand what the directory is, which `[event]` Issue it belongs to, and what materials it contains.

It should include:

- Activity name
- Corresponding main activity Issue, such as `[event] BETA MEET - The Field Experience of an Ecologist`
- Activity date or session information
- Main files in the directory
- Important external links, such as registration forms, Album folders, or activity summaries

Example:

```markdown
# BETA MEET 01 · The Field Experience of an Ecologist

Main issue: [BETA-SDC/event-proposal#38](https://github.com/BETA-SDC/event-proposal/issues/38)

This directory stores materials for BETA MEET 01.

## Files

- `proposal.md`: activity proposal
- `poster-information.md`: poster information form
- `sign-in/`: sign-in and attendance statistics, if applicable
```

### Activity Proposal

Activity proposals should be named `proposal.md`.

Examples:

- [2026-09-09-math-help-group-01/proposal.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-09-math-help-group-01/proposal.md)
- [2026-09-16-group-birthday-ceremony-01/proposal.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/proposal.md)

Do not repeat the activity name in the file name, such as `math-help-room-proposal.md`. The activity name is already expressed by the parent directory.

### Poster Information Form

Poster information forms should be named `poster-information.md`, with content based on the [poster information template](https://github.com/BETA-SDC/event-proposal/blob/main/template-for-poster-information.md).

Examples:

- [2026-09-09-math-help-group-01/poster-information.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-09-math-help-group-01/poster-information.md)
- [2026-09-19-self-study-check-in/poster-information.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-19-self-study-check-in/poster-information.md)

### Notification Copy

Notification copy drafts are not required files. Add `notification-message.md` only when the notice needs collaborative editing, review in a Pull Request, or a long-term draft backup.

If one activity has multiple official sending channels, record them as sections inside the file instead of stacking channel names in the file name. After official sending, the archive should still be created as a `[message]` Sub-issue under the corresponding activity main Issue; the file is only a branch material draft or backup.

The historical file [notation-message.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/notation-message.md) may stay for now. New files should use `notification-message.md`; historical names can be corrected later in a separate Pull Request if needed.

### Sign-In Records

Sign-in records go under `sign-in/`. See the [Sign-In Record Guidelines](./sign-in-record-guidelines.md) for detailed naming rules.

Existing examples:

- [sign-in/README.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/README.md)
- [sign-in/00-summary.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/00-summary.csv)
- [sign-in/01-registered-attended.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/01-registered-attended.csv)
- [sign-in/02-registered-absent.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/02-registered-absent.csv)
- [sign-in/03-registered-cancelled.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/03-registered-cancelled.csv)
- [sign-in/04-unregistered-attended.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/04-unregistered-attended.csv)

## When to Add Files

Only add repository files when materials need long-term tracking, reuse, or review. Suitable files include:

- Activity proposals
- Poster information forms
- Notification copy drafts or backups
- Activity directory README files
- Sign-in statistics and organization notes
- Structured review materials that should be kept long-term

The following should not usually be committed directly:

- Original photos and videos, which should be uploaded to the [Beta College Album](https://westlakeu.sharepoint.com/sites/beta-college/Album/Forms/AllItems.aspx?viewid=f4bff7b2%2Ddd12%2D43eb%2Da665%2Dd945dfd194c3)
- Original registration forms, Excel files, or screenshots containing significant personal information
- One-off images, QR codes, or reference images that can be kept as Issue attachments
- Temporary files without organization notes

## Pre-Submission Checklist

- [ ] Activity directory follows `SERIES-two-digit-session-specific-topic`
- [ ] Series code is uppercase, stable, and recognizable, such as `BETA-MEET`, `MATH-HELP-ROOM`, or `GROUP-BIRTHDAY`
- [ ] Session number uses two digits, such as `01`
- [ ] Topic and file names use lowercase English and hyphens
- [ ] Activity directory includes `README.md` and links to the corresponding main activity Issue
- [ ] Proposal uses `proposal.md`
- [ ] Poster information form uses `poster-information.md`
- [ ] If a notification copy draft is saved, it prefers `notification-message.md`
- [ ] Sign-in records are stored under `sign-in/` and follow the [Sign-In Record Guidelines](./sign-in-record-guidelines.md)
- [ ] File names do not contain status words such as `final`, `new`, `latest`, or `revised`
- [ ] Photos, videos, or unnecessary sensitive personal information are not committed directly to the repository
