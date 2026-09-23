# Issue 协作规范

中文 | [English](./issue-collaboration-guidelines.md)

> 本文档说明活动协作中 Issue、Sub-issue、标签、分支和 Pull Request 的使用方式。完整活动流程见 [活动与宣传](./README.zh.md)。

## 标题规则

所有 Issue 和 Sub-issue 标题都应使用英文半角方括号作为类型前缀。

通用规则：

- 前缀使用 `[event]`、`[task]`、`[message]` 等固定形式
- 前缀后空一格，再写活动名称或事项名称
- Issue 标题和正文推荐使用 English，便于跨成员、跨工具检索；中文完全允许，不要求为了语言统一而强行翻译
- 活动主 Issue 通常只写活动名称，不需要额外字段
- Sub-issue 标题必须带上 parent 活动名称或事项名称，不能只写任务本身
- Sub-issue 使用前后带空格的 ` - ` 分隔 parent、任务、渠道、日期等字段，让父子关系和事项层级更清楚
- 同一活动的活动名称应保持一致
- 涉及日期时统一使用 `YYYY-MM-DD`

系列活动的主 Issue 标题应包含系列名称、期号和本期主题。English 是推荐写法，中文写法同样有效：

```text
[event] Beta Meet 08 - The Field Experience of an Ecologist
[event] Beta Meet 第8期 - 王璟老师的科幻讲座
```

Beta Meet 的期号沿用已有编号继续递增。阅读交流会已经并入 Beta Meet，不再另起一套期号：

```text
阅读交流会第1期 -> Beta Meet 第8期
阅读交流会第2期 -> Beta Meet 第9期
阅读交流会第3期 -> Beta Meet 第10期
```

任务和消息归档必须复制 parent 的活动名称，不能自行改写语言或期号：

```text
[task] Beta Meet 08 - The Field Experience of an Ecologist - Create poster
[message] Beta Meet 第8期 - 王璟老师的科幻讲座 - 邮件通知 - 2026-09-23
```

> [!TIP]
> Issue 标题使用活动实际采用的语言即可，但同一活动的主 Issue、Sub-issue 和消息归档必须保持名称完全一致。不要写成 `[task] Create poster` 或 `[task] Beta Meet 08-The Field Experience of an Ecologist-Create poster`。

Issue 标题规则与仓库目录命名规则分别管理。`event-proposal` 的活动目录和文件名继续使用现有的 `YYYY-MM-DD-SERIES-两位期数[-specific-topic]` 规则；不要把 Issue 标题中的中文期号直接套用到目录名。

## 常用标题格式

| 类型 | 用途 | 标题格式 |
| --- | --- | --- |
| `[event]` | 活动主 Issue | `[event] 活动名称` |
| `[improvement]` | 流程、制度、工具或协作方式改进 | `[improvement] 改进事项名称` |
| `[task]` | 分配给成员执行的具体任务 | `[task] 活动名称 - 任务名称` |
| `[message]` | 正式发送通知的归档 | `[message] 活动名称 - 渠道 - YYYY-MM-DD` |
| `[wrap-up]` | 活动复盘、素材整理或收尾事项 | `[wrap-up] 活动名称 - 收尾事项` |
| `[question]` | 临时问题、信息待确认或讨论事项 | `[question] 问题简述` |
| `[docs]` | 文档维护、修正、补充或整理 | `[docs] 文档名称或维护事项` |

示例：

```text
[event] Math Help Room
[improvement] 建立活动创建标准流程
[task] Math Help Room - 制作报名表
[message] Math Help Room - 邮件通知 - 2026-09-09
[wrap-up] Group Birthday Ceremony - 整理照片素材
[question] 是否需要统一报名表模板
[docs] 更新活动流程说明
```

## 标签规则

建议使用少量稳定标签，不为每个活动单独创建新标签。

| 标签 | 使用对象 | 用途 |
| --- | --- | --- |
| `event` | 主 Issue | 活动或活动相关事项主入口 |
| `internal-improvement` | 主 Issue | 内部流程、协作方式、制度或工具改进 |
| `documentation` | Issue 或 PR | 文档维护或文档修改 |
| `task` | Sub-issue | 分配给成员执行的具体任务 |
| `message` | Sub-issue | 已正式发送的消息或文案归档 |
| `mail` | Sub-issue | 与邮件有关 |
| `group-notice` | Sub-issue | 与微信群、飞书群等群通知有关 |
| `notification-poster` | Sub-issue | 与海报、推文或宣传物料有关 |
| `wrap-up` | 主 Issue 或 Sub-issue | 活动结束后的复盘、素材整理或收尾事项 |

使用建议：

- 活动主 Issue 至少添加 `event`
- 内部改进提议至少添加 `internal-improvement`
- 文档维护事项添加 `documentation`
- 任务分配类 Sub-issue 至少添加 `task`
- 消息归档类 Sub-issue 至少添加 `message`
- 邮件归档建议使用 `message` + `mail`
- 群通知归档建议使用 `message` + `group-notice`
- 海报、推文、报名宣传物料任务建议使用 `task` + `notification-poster`
- 活动结束后的复盘或素材整理建议使用 `wrap-up`

## Sub-issue 分配

进入执行阶段后，负责人应把可以独立推进的工作拆成 Sub-issue，并 assign 给对应成员。

Sub-issue 应写清楚：

- 任务内容和交付物
- 负责人或执行人
- 截止时间或回收时间点
- 需要依赖的材料、链接、模板或前置确认
- 完成后在哪里提交结果，例如 Pull Request、评论附件、共享文档或对应目录

> [!IMPORTANT]
> 海报、推文、报名宣传物料等任务应在对应活动主 Issue 下创建 Sub-issue，并 @ 活动负责人或宣传负责人。图片、二维码、参考图等素材应作为 Sub-issue 附件提交。

## 分支命名

活动进入执行阶段后，从 Issue 页面创建对应分支。分支名称应尽量简短、可识别，并和活动相关。

推荐格式：

```text
两位issue编号-活动短名
```

示例：

```text
05-standard-workflow
12-math-help-room
18-group-birthday
```

Issue 编号统一使用两位数字，不足两位时在前面补 `0`。如果早期分支或引用中已经出现一位编号，应在后续整理时更正。

## Pull Request

活动材料准备到可以审核的状态后，提交 Pull Request。PR 中建议说明：

- 关联的 Issue
- 本次新增或修改了哪些活动材料
- 哪些信息已经确认，哪些仍需负责人确认
- 是否涉及待发送的邮件、群聊消息或其他公开文案
- 是否需要特别检查时间、地点、预算、嘉宾信息或报名方式

负责人审核 Pull Request 后，可以提出修改意见。修改完成并确认无误后，再合并分支。
