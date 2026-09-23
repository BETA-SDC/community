# event-proposal 仓库文件命名规范（草稿）

中文 | [English](./event-proposal-repo-naming-regulation.md)

> 本文档是 [`event-proposal`](https://github.com/BETA-SDC/event-proposal) 仓库内部文件和目录命名的草稿规范，用于统一活动材料、海报信息、签到记录和通知文案的保存方式。

## 适用范围

本规范适用于 [`event-proposal`](https://github.com/BETA-SDC/event-proposal) 仓库中的文件和目录，包括：

- 学年目录
- 活动材料目录
- 活动策划案
- 海报信息表
- 通知文案文件
- 签到记录目录和 CSV 文件
- 其他与单个活动直接相关的材料

Issue 标题、Sub-issue 标题、分支名称和标签规则仍以 [活动与宣传](./README.zh.md) 为准。Issue 推荐使用 English，但中文也允许；本文件只规定仓库目录和文件命名，不改变 Issue 的语言选择。

## 基本原则

- **目录表达日期、系列、期数和必要主题，文件表达材料类型。** 活动目录名先记录活动日期，再记录系列活动，使活动可以按时间排序，也能识别所属系列；文件名尽量使用稳定的材料类型名称。
- **活动目录以日期开头。** 日期使用 `YYYY-MM-DD`，放在活动目录最前面。
- **系列代号全大写、稳定且可识别。** 系列活动在日期后接系列代号，例如 `BETA-MEET`、`MATH-HELP-ROOM`、`GROUP-BIRTHDAY`。系列代号应表达稳定系列，不放年份、季节或本期主题，也不为了简短而删掉系列固有名称。
- **期数使用两位数字。** 系列代号后接两位期数，例如 `01`、`02`，不要使用 `1`、`2`。
- **主题使用英文小写和连字符，必要时可省略。** 本期具体主题使用 `kebab-case`，避免空格、中文标点、大小写混用和临时描述；如果系列名和期数已经足够清楚，例如 `MATH-HELP-ROOM-01`，可以不加子主题。
- **同一活动只保留一个主目录。** 同一活动的策划、海报、签到、通知和复盘材料都应放在同一活动目录下。
- **避免把状态写进文件名。** 不建议使用 `final`、`new`、`latest`、`修改版` 等词；状态应通过 Git 历史、Pull Request 或文件内容说明。

## 目录结构

推荐结构：

```text
event-proposal/
  README.md
  README.zh.md
  template-for-poster-information.md
  YYYY-YYYY/
    YYYY-MM-DD-SERIES-两位期数[-specific-topic]/
      README.md
      proposal.md
      poster-information.md
      notification-message.md  # 可选
      sign-in/
        README.md
        00-summary.csv
        01-registered-attended.csv
        02-registered-absent.csv
        03-registered-cancelled.csv
        04-unregistered-attended.csv
```

现有示例：

- [2026-2027](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027)
- [2026-09-29-BETA-MEET-01-the-field-experience-of-an-ecologist](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-29-BETA-MEET-01-the-field-experience-of-an-ecologist)
- [2026-09-09-MATH-HELP-ROOM-01](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-09-MATH-HELP-ROOM-01)
- [2026-09-16-GROUP-BIRTHDAY-01-2026-fall](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall)
- [2026-09-19-self-study-check-in](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-19-self-study-check-in)

以上活动目录是当前命名示例。其中 `2026-09-19-self-study-check-in` 是非系列活动示例，其他活动目录使用系列活动命名格式。

## 学年目录命名

学年目录使用：

```text
YYYY-YYYY
```

示例：

- [2026-2027](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027)

学年目录只用于区分活动归属学年，不用于表达部门、活动类型或负责人。

## 活动目录命名

系列活动目录使用：

```text
YYYY-MM-DD-SERIES-两位期数[-specific-topic]
```

字段说明：

- `YYYY-MM-DD`：活动日期，放在最前面
- `SERIES`：系列活动代号，放在日期后，使用全大写英文和连字符，例如 `BETA-MEET`、`MATH-HELP-ROOM`、`GROUP-BIRTHDAY`；系列名应稳定可识别，不放年份、季节或本期主题
- `两位期数`：该系列的第几期，使用 `01`、`02`、`03`
- `specific-topic`：本期活动具体主题，使用英文小写和连字符；如果系列名和期数已经足够清楚，可以省略

示例：

```text
2026-09-29-BETA-MEET-01-the-field-experience-of-an-ecologist
2026-10-15-BETA-MEET-02-topic-of-the-next-session
2026-09-09-MATH-HELP-ROOM-01
2026-09-16-GROUP-BIRTHDAY-01-2026-fall
```

非系列活动目录使用：

```text
YYYY-MM-DD-specific-topic
```

例如 `2026-09-19-self-study-check-in`。

这样命名后，活动会按日期自然排序，同时系列代号和期数仍然清楚。

> [!IMPORTANT]
> 系列活动目录中的 `SERIES` 和两位期数不要省略；只有最后的 `specific-topic` 可以在系列名和期数已经足够清楚时省略，例如 `2026-09-09-MATH-HELP-ROOM-01`。

不推荐：

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

## 活动材料文件命名

### 活动目录说明

每个活动目录建议包含一个 `README.md`，用于简要介绍这个活动目录的内容，并链接对应的活动主 Issue。`README.md` 不需要替代 `proposal.md`，它的作用是让进入目录的人快速知道这个目录是什么、对应哪个 `[event]` Issue、里面有哪些材料。

建议包含：

- 活动名称
- 对应的活动主 Issue，例如 `[event] Beta Meet 08 - The Field Experience of an Ecologist` 或 `[event] Beta Meet 第8期 - 王璟老师的科幻讲座`
- 活动时间或期数信息
- 目录内主要文件说明
- 重要外部链接，例如报名表、Album 文件夹、活动总结等

示例：

```markdown
# BETA MEET 01 · The Field Experience of an Ecologist

Main issue: [BETA-SDC/event-proposal#23](https://github.com/BETA-SDC/event-proposal/issues/23)

This directory stores materials for BETA MEET 01.

## Files

- `proposal.md`: activity proposal
- `poster-information.md`: poster information form
- `sign-in/`: sign-in and attendance statistics, if applicable
```

### 活动策划案

活动策划案统一命名为 `proposal.md`。

示例：

- [2026-09-09-MATH-HELP-ROOM-01/proposal.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-09-MATH-HELP-ROOM-01/proposal.md)
- [2026-09-16-GROUP-BIRTHDAY-01-2026-fall/proposal.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/proposal.md)

不推荐把活动名重复写进文件名，例如 `math-help-room-proposal.md`。活动名已经由上级目录表达。

### 海报信息表

海报信息表统一命名为 `poster-information.md`，内容应来自 [海报信息模板](https://github.com/BETA-SDC/event-proposal/blob/main/template-for-poster-information.md)。

示例：

- [2026-09-09-MATH-HELP-ROOM-01/poster-information.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-09-MATH-HELP-ROOM-01/poster-information.md)
- [2026-09-19-self-study-check-in/poster-information.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-19-self-study-check-in/poster-information.md)

### 通知文案

通知文案草稿不是必需文件。只有当通知内容需要在 Pull Request 中共同编辑、审核或长期保留备份时，才建议新增 `notification-message.md`。

如果同一活动有多个正式发送渠道，建议在文件内容中分节记录，而不是在文件名中堆叠渠道名称。正式发送后的归档仍应在对应活动主 Issue 下创建 `[message]` 类型 Sub-issue，文件只作为分支中的材料草稿或备份。

现有示例文件 [notification-message.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/notification-message.md) 使用该命名；后续新增通知文案草稿也建议使用 `notification-message.md`。

### 签到记录

签到记录放在 `sign-in/` 目录下，具体命名参考 [签到记录整理规范](./sign-in-record-guidelines.zh.md)。

现有样例：

- [sign-in/README.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/README.md)
- [sign-in/00-summary.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/00-summary.csv)
- [sign-in/01-registered-attended.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/01-registered-attended.csv)
- [sign-in/02-registered-absent.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/02-registered-absent.csv)
- [sign-in/03-registered-cancelled.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/03-registered-cancelled.csv)
- [sign-in/04-unregistered-attended.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/04-unregistered-attended.csv)

## 何时新增文件

只有当材料需要被长期追踪、复用或审核时，才应新增仓库文件。以下内容适合入库：

- 活动策划案
- 海报信息表
- 通知文案草稿或备份
- 活动目录说明
- 签到统计和整理说明
- 复盘中需要长期保留的结构化材料

以下内容不建议直接放入仓库：

- 原始照片和视频，应上传到 [Beta College Album](https://westlakeu.sharepoint.com/sites/beta-college/Album/Forms/AllItems.aspx?viewid=f4bff7b2%2Ddd12%2D43eb%2Da665%2Dd945dfd194c3)
- 包含大量个人信息的原始报名表、Excel 或截图
- 可以通过 Issue 附件保存的一次性图片、二维码或参考图
- 没有整理说明的临时文件

> [!CAUTION]
> 仓库适合保存整理后的活动材料和可追溯说明，不适合保存大体积媒体文件或不必要的个人敏感信息。照片、视频放 Album；一次性图片、二维码和参考图优先挂在对应 Sub-issue 附件中。

## 提交前检查

- [ ] 活动目录符合 `YYYY-MM-DD-SERIES-两位期数[-specific-topic]`，非系列活动符合 `YYYY-MM-DD-specific-topic`
- [ ] 系列代号全大写、稳定且可识别，例如 `BETA-MEET`、`MATH-HELP-ROOM`、`GROUP-BIRTHDAY`
- [ ] 期数使用两位数字，例如 `01`
- [ ] 主题和文件名使用英文小写和连字符；主题可在系列名和期数已经清楚时省略
- [ ] 活动目录包含 `README.md`，并链接对应活动主 Issue
- [ ] 策划案使用 `proposal.md`
- [ ] 海报信息表使用 `poster-information.md`
- [ ] 如需保存通知文案草稿，优先使用 `notification-message.md`
- [ ] 签到记录放在 `sign-in/` 目录，并符合 [签到记录整理规范](./sign-in-record-guidelines.zh.md)
- [ ] 文件名中没有 `final`、`new`、`latest`、`修改版` 等状态词
- [ ] 没有把照片、视频或不必要的个人敏感信息直接提交到仓库
