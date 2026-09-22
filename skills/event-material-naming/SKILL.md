---
name: event-material-naming
description: Create and validate BETA-SDC event-proposal academic-year directories, activity directories, and standard material filenames.
---

# BETA-SDC 活动材料命名

这个 Skill 用于在 `event-proposal` 中建立活动目录、README、策划案、海报信息、通知草稿和签到目录。

## 目录结构

```text
event-proposal/
  YYYY-YYYY/
    YYYY-MM-DD-SERIES-两位期数[-specific-topic]/
      README.md
      proposal.md
      poster-information.md
      notification-message.md
      sign-in/
        README.md
        00-summary.csv
        01-registered-attended.csv
        02-registered-absent.csv
        03-registered-cancelled.csv
        04-unregistered-attended.csv
```

没有系列的活动使用：

```text
YYYY-MM-DD-specific-topic
```

## 学年目录

格式：

```text
YYYY-YYYY
```

学年目录只表示活动所属学年，不写部门、负责人或活动类型。

## 系列活动目录

格式：

```text
YYYY-MM-DD-SERIES-两位期数[-specific-topic]
```

规则：

- 日期使用 `YYYY-MM-DD`，放在最前面。
- `SERIES` 使用稳定、可识别的全大写英文代号。
- 系列代号不包含年份、季节或本期主题。
- 期数使用两位数字，例如 `01`、`02`。
- `specific-topic` 使用英文小写和连字符，可以省略。

示例：

```text
2026-09-29-BETA-MEET-01-the-field-experience-of-an-ecologist
2026-09-09-MATH-HELP-ROOM-01
2026-09-16-GROUP-BIRTHDAY-01-2026-fall
```

## 固定文件名

固定使用：

- `README.md`：目录说明和主 Issue 链接
- `proposal.md`：活动策划案
- `poster-information.md`：海报信息表
- `notification-message.md`：需要长期保留的通知草稿或备份
- `sign-in/`：签到与到场统计

不要把活动名称重复写进 `proposal.md` 文件名。

## README 模板

```markdown
# 活动名称

Main issue: [BETA-SDC/event-proposal#编号](Issue URL)

This directory stores materials for this activity.

## Files

- `proposal.md`: activity proposal
- `poster-information.md`: poster information
- `sign-in/`: sign-in and attendance statistics, if applicable
```

## 不应直接入库的内容

- 原始照片和视频，应上传 Beta College Album。
- 包含大量手机号、学号或其他敏感字段的原始报名表。
- 没有整理说明的临时文件。
- 可以挂在 Issue 附件中的一次性二维码、参考图或截图。

## 禁止事项

- 不要使用空格、中文标点或大小写混用的目录名。
- 不要使用一位期数，如 `BETA-MEET-1`。
- 不要把系列代号写成小写。
- 不要把年份或季节塞进系列代号。
- 不要使用 `final`、`new`、`latest`、`修改版` 等状态词。
- 同一活动只能有一个主目录。

## 检查清单

- 目录属于正确学年。
- 活动目录以日期开头。
- 系列代号稳定且全大写。
- 期数为两位数字。
- 主题为英文小写 kebab-case。
- 有 `README.md` 和主 Issue 链接。
- 固定材料使用标准文件名。
- 没有不必要的媒体或个人敏感信息。
