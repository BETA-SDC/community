# Sign-In Record Guidelines

[中文](./sign-in-record-guidelines.zh.md) | English

> This document explains how to organize registration, sign-in, and attendance records after an activity.

## Scope

When an activity has registration, sign-in, on-site additions, cancellations, or needs an actual attendance count, organize sign-in records under the activity materials directory. Sign-in records support activity review, registration conversion checks, reimbursement, and activity summaries. They should not remain only in personal spreadsheets, chat records, or temporary group sign-up threads.

See the [group birthday ceremony sign-in example](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/GROUP-BIRTHDAY-01-2026-fall/sign-in), which includes a README and categorized CSV files.

Example files include [README.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/GROUP-BIRTHDAY-01-2026-fall/sign-in/README.md), [00-summary.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/GROUP-BIRTHDAY-01-2026-fall/sign-in/00-summary.csv), [01-registered-attended.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/GROUP-BIRTHDAY-01-2026-fall/sign-in/01-registered-attended.csv), [02-registered-absent.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/GROUP-BIRTHDAY-01-2026-fall/sign-in/02-registered-absent.csv), [03-registered-cancelled.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/GROUP-BIRTHDAY-01-2026-fall/sign-in/03-registered-cancelled.csv), and [04-unregistered-attended.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/GROUP-BIRTHDAY-01-2026-fall/sign-in/04-unregistered-attended.csv).

## Location

Sign-in records should be stored in a `sign-in/` subdirectory under the corresponding activity directory.

Recommended structure:

```text
GROUP-BIRTHDAY-01-2026-fall/
  sign-in/
    README.md
    00-summary.csv
    01-registered-attended.csv
    02-registered-absent.csv
    03-registered-cancelled.csv
    04-unregistered-attended.csv
```

If an activity does not have one category, either omit the corresponding CSV or keep an empty file and explain it in `README.md`.

## README.md Content

`sign-in/README.md` should at least explain:

- Activity name
- Data source, such as registration form, sign-in sheet, group sign-up thread, or on-site additions
- Original data organization date
- Counting rules, such as what sign-in marks `1`, `0`, and `-1` mean
- Summary counts
- What each CSV file contains
- Special notes, such as duplicate names, on-site additions, cancellations, unusual marks, or incomplete data sources

Recommended sections:

```markdown
# Activity Name · Attendance Statistics

Data source: original file or sheet name, organized on YYYY-MM-DD.

## Summary

| Category | Count |
| --- | --- |
| Registered and attended | 0 |
| Registered but absent | 0 |
| Registered then cancelled | 0 |
| Total registered | 0 |
| Unregistered but attended | 0 |
| Total on-site attendance | 0 |

## Files

| File | Content |
| --- | --- |
| `00-summary.csv` | Counts for each category |
| `01-registered-attended.csv` | Registered and attended |
| `02-registered-absent.csv` | Registered but absent |
| `03-registered-cancelled.csv` | Registered then cancelled |
| `04-unregistered-attended.csv` | Unregistered but attended |

## Notes

- Explain the original sheet structure, sign-in mark meanings, unusual data, and manual handling here.
```

## CSV Files

### 00-summary.csv

`00-summary.csv` stores the summary counts. It should usually include at least:

```csv
Category,Count
Registered and attended,0
Registered but absent,0
Registered then cancelled,0
Total registered,0
Unregistered but attended,0
Total on-site attendance,0
```

Where:

- `Total registered` usually equals the sum of registered-and-attended, registered-but-absent, registered-then-cancelled, and other registration-related categories
- `Total on-site attendance` usually equals registered-and-attended plus unregistered-but-attended
- If the activity uses a different counting rule, explain it in `README.md`

### Categorized Lists

Categorized CSV files should usually use two columns: `Index,Name`.

```csv
Index,Name
1,Name
2,Name
```

Common category files:

- `01-registered-attended.csv`: registered and attended
- `02-registered-absent.csv`: registered but absent
- `03-registered-cancelled.csv`: registered then cancelled
- `04-unregistered-attended.csv`: unregistered but attended

If student IDs, colleges, contact information, or other extra fields need to be saved, confirm that those fields are necessary and avoid exposing unnecessary personal sensitive information.

## Organization Rules

- Keep a note about the original data source; do not submit only the final numbers.
- Compare the registration list and sign-in list separately, checking for unregistered attendees, registered absences, and duplicate names.
- Explain special marks from the source data, such as `1` for attended, `0` for absent, and `-1` for cancelled.
- Manual judgments or corrections must be recorded in the notes section of `README.md`.
- If name prefixes, note symbols, duplicate names, or unusual records appear, do not silently delete them. Explain whether they were kept as-is and whether follow-up confirmation is needed.
- Avoid committing original Excel files, screenshots, or files with excessive personal information. If they must be saved, confirm the access scope and privacy risk first.

## Pre-Submission Checklist

- [ ] `sign-in/README.md` explains the data source and organization date
- [ ] Summary counts and category CSV files match each other
- [ ] Registered-and-attended, registered-but-absent, cancelled, unregistered-but-attended, and other relevant categories are organized according to the activity situation
- [ ] Unusual marks, duplicate names, on-site additions, and manual judgments are recorded in the notes
- [ ] Unnecessary phone numbers, student IDs, ID numbers, or other sensitive personal information are not publicly exposed
- [ ] The wrap-up record in the event creation workflow links to the sign-in record location
