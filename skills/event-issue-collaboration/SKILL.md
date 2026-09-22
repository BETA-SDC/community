---
name: event-issue-collaboration
description: Create, format, assign, label, branch, and review BETA-SDC event Issues, Sub-issues, and Pull Requests.
---

# BETA-SDC Issue 协作

这个 Skill 用于处理 `event-proposal` 中的 Issue 标题、标签、Sub-issue、分支和 Pull Request。

## 标题格式

所有标题使用英文半角方括号前缀，前缀后有一个空格：

```text
[event] 活动名称
[task] 活动名称 - 任务名称
[message] 活动名称 - 渠道 - YYYY-MM-DD
[wrap-up] 活动名称 - 收尾事项
[improvement] 改进事项
[question] 问题简述
[docs] 文档维护事项
```

规则：

- 主活动 Issue 使用 `[event] 活动名称`。
- Sub-issue 必须带 parent 活动名称。
- parent、任务、渠道、日期之间使用前后带空格的 ` - `。
- 日期统一使用 `YYYY-MM-DD`。
- 同一活动的名称保持完全一致。

## 标签

| Issue 类型 | 必要标签 |
| --- | --- |
| 主活动 Issue | `event` |
| 任务 Sub-issue | `task` |
| 邮件归档 | `message` + `mail` |
| 群通知归档 | `message` + `group-notice` |
| 海报或宣传任务 | `task` + `notification-poster` |
| 活动收尾 | `wrap-up` |
| 文档维护 | `documentation` |

绝对不要让同一个 Issue 同时拥有 `event` 和 `message`。

## Sub-issue 内容

任务 Sub-issue 至少写清：

- 任务和交付物
- 执行人
- 截止时间
- 依赖材料、链接或模板
- 提交结果的位置

需要海报、推文或报名宣传时：

- 建立在对应活动主 Issue 下
- assign 执行人
- @ 活动负责人或宣传负责人
- 将参考图、二维码等挂在该 Sub-issue 下

## 分支命名

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

Issue 编号不足两位时补前导零。不要把 `final`、负责人姓名或所有任务堆进分支名。

## Pull Request

PR 至少说明：

- 关联的 Issue
- 新增或修改了哪些材料
- 哪些信息已确认、哪些待确认
- 是否涉及待发送的邮件、群消息或其他公开文案
- 是否需要特别检查时间、地点、预算、嘉宾或报名方式

## 检查命令

```bash
gh issue list --repo BETA-SDC/event-proposal --state all \
  --json number,title,state,labels,parent,url --limit 100
```

检查标题前缀、parent、标签和 `event + message` 混用。已关闭 Issue 也要检查。

## 禁止事项

- 不要写 `[task] 制作海报` 这种没有 parent 的标题。
- 不要使用 `[task]活动名称` 这种缺少空格的前缀。
- 不要使用 `9/16`、`2026.9.16` 等非标准日期。
- 不要把邮件归档标成 `event`。
- 不要把任务只分派在群聊里而不记录负责人。
