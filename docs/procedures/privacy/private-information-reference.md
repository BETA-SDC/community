# Private Information References

[中文](./private-information-reference.zh.md) | English

> This document explains how public repositories should refer to private or non-public information stored in [`BETA-SDC/community-private-information`](https://github.com/BETA-SDC/community-private-information).

## When To Use The Private Repository

Use the private repository when community or activity work needs to preserve information that is useful internally but not suitable for public storage:

- Private text, internal notes, contact details, or access instructions
- Private images uploaded through private Issues or Pull Requests
- Attachments such as screenshots, forms, scans, and non-public PDFs
- Activity-specific private supporting materials

Do not copy private content into a public repository. Keep the public document readable, and only add a private link for people who have access.

## Text References

When a public document needs to point to private text, create a Markdown file in the private repository, then link to it:

```markdown
Private note: [internal text reference](https://github.com/BETA-SDC/community-private-information/blob/main/text/example.md)
```

For activity-specific private text, prefer:

```text
community-private-information/activities/YYYY-YYYY/YYYY-MM-DD-activity-slug/text/
```

## Image References

When using a private image:

1. Upload the image in a private Issue or Pull Request in `community-private-information`.
2. Copy the generated `github.com/user-attachments/assets/...` link.
3. Link to it from the public Markdown.

Prefer a normal link:

```markdown
[View private reference image](https://github.com/user-attachments/assets/xxxx-xxxx-xxxx)
```

Only embed the image if the public page still makes sense when the image is broken:

```markdown
![Private reference image](https://github.com/user-attachments/assets/xxxx-xxxx-xxxx)
```

## Attachment References

For non-public PDFs, forms, screenshots, scans, or spreadsheets, put them under:

```text
community-private-information/attachments/
```

or, for activity-specific files:

```text
community-private-information/activities/YYYY-YYYY/YYYY-MM-DD-activity-slug/attachments/
```

Link to the private file from a public document only when the public text is still understandable without access.

## Public Document Requirements

- Public documents should explain public-facing facts directly.
- Private links should add internal details, not replace the public explanation.
- Do not use sensitive personal details as link labels.
- Do not mention access codes, phone numbers, financial details, or sensitive context in public text.
- If a private reference is essential for operations, also mention who can request access.
