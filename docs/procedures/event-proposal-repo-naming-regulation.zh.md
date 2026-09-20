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

Issue 标题、Sub-issue 标题、分支名称和标签规则仍以 [活动建立规范流程](./event-creation-workflow.zh.md) 为准。

## 基本原则

- **目录表达活动，文件表达材料类型。** 活动名称和日期放在活动目录名中，文件名尽量使用稳定的材料类型名称。
- **文件名使用英文小写和连字符。** 使用 `kebab-case`，避免空格、中文标点、大小写混用和临时描述。
- **日期使用 `YYYY-MM-DD`。** 日期用于活动目录或确实需要区分日期的材料，不随意写成 `9.16`、`0916` 或自然语言日期。
- **序号使用两位数字。** 活动目录末尾序号使用 `01`、`02`，不要使用 `1`、`2`。
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
    YYYY-MM-DD-activity-name-两位序号/
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

现有示例：

- [2026-2027](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027)
- [2026-09-09-math-help-group-01](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-09-math-help-group-01)
- [2026-09-16-group-birthday-ceremony-01](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-16-group-birthday-ceremony-01)

## 学年目录命名

学年目录使用：

```text
YYYY-YYYY
```

示例：

- [2026-2027](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027)

学年目录只用于区分活动归属学年，不用于表达部门、活动类型或负责人。

## 活动目录命名

活动目录使用：

```text
YYYY-MM-DD-activity-name-两位序号
```

字段说明：

- `YYYY-MM-DD`：活动预计举行日期；如果是连续多日活动，使用开始日期
- `activity-name`：活动英文短名，使用小写英文和连字符
- `两位序号`：同一天或同名活动需要区分时使用，默认从 `01` 开始

示例：

- [2026-09-09-math-help-group-01](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-09-math-help-group-01)
- [2026-09-16-group-birthday-ceremony-01](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-16-group-birthday-ceremony-01)

不推荐：

```text
2026.09.09 Math Help
2026-09-09-math-help-group-1
group-birthday-final
生日会材料
```

## 活动材料文件命名

### 活动策划案

活动策划案统一命名为 `proposal.md`。

示例：

- [2026-09-09-math-help-group-01/proposal.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-09-math-help-group-01/proposal.md)
- [2026-09-16-group-birthday-ceremony-01/proposal.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/proposal.md)

不推荐把活动名重复写进文件名，例如 `math-help-room-proposal.md`。活动名已经由上级目录表达。

### 海报信息表

海报信息表统一命名为 `poster-information.md`，内容应来自 [海报信息模板](https://github.com/BETA-SDC/event-proposal/blob/main/template-for-poster-information.md)。

示例：

- [2026-09-09-math-help-group-01/poster-information.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-09-math-help-group-01/poster-information.md)
- [2026-09-19-self-study-check-in/poster-information.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-19-self-study-check-in/poster-information.md)

### 通知文案

通知文案草稿建议命名为 `notification-message.md`。

如果同一活动有多个正式发送渠道，建议在文件内容中分节记录，而不是在文件名中堆叠渠道名称。正式发送后的归档仍应在对应活动主 Issue 下创建 `[message]` 类型 Sub-issue，文件只作为分支中的材料草稿或备份。

历史上已经出现的 [notation-message.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/notation-message.md) 可暂时保留；后续新增文件建议使用 `notification-message.md`，必要时再单独开 Pull Request 纠正历史文件名。

### 签到记录

签到记录放在 `sign-in/` 目录下，具体命名参考 [签到记录整理规范](./sign-in-record-guidelines.zh.md)。

现有样例：

- [sign-in/README.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/README.md)
- [sign-in/00-summary.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/00-summary.csv)
- [sign-in/01-registered-attended.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/01-registered-attended.csv)
- [sign-in/02-registered-absent.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/02-registered-absent.csv)
- [sign-in/03-registered-cancelled.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/03-registered-cancelled.csv)
- [sign-in/04-unregistered-attended.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-group-birthday-ceremony-01/sign-in/04-unregistered-attended.csv)

## 何时新增文件

只有当材料需要被长期追踪、复用或审核时，才应新增仓库文件。以下内容适合入库：

- 活动策划案
- 海报信息表
- 通知文案草稿或备份
- 签到统计和整理说明
- 复盘中需要长期保留的结构化材料

以下内容不建议直接放入仓库：

- 原始照片和视频，应上传到 [Beta College Album](https://westlakeu.sharepoint.com/sites/beta-college/Album/Forms/AllItems.aspx?viewid=f4bff7b2%2Ddd12%2D43eb%2Da665%2Dd945dfd194c3)
- 包含大量个人信息的原始报名表、Excel 或截图
- 可以通过 Issue 附件保存的一次性图片、二维码或参考图
- 没有整理说明的临时文件

## 提交前检查

- [ ] 活动目录符合 `YYYY-MM-DD-activity-name-两位序号`
- [ ] 活动目录序号使用两位数字，例如 `01`
- [ ] 文件名使用英文小写和连字符
- [ ] 策划案使用 `proposal.md`
- [ ] 海报信息表使用 `poster-information.md`
- [ ] 通知文案草稿优先使用 `notification-message.md`
- [ ] 签到记录放在 `sign-in/` 目录，并符合 [签到记录整理规范](./sign-in-record-guidelines.zh.md)
- [ ] 文件名中没有 `final`、`new`、`latest`、`修改版` 等状态词
- [ ] 没有把照片、视频或不必要的个人敏感信息直接提交到仓库
