---
name: event-message-archive
description: Archive sent BETA-SDC activity emails, group notices, reminders, and publicity copy as correctly labeled message Sub-issues.
---

# BETA-SDC 通知归档

这个 Skill 用于把已经正式发送的邮件、群通知、报名提醒、活动变更和宣传文案归档到活动主 Issue 下。

## 什么时候使用

应该归档：

- 活动参与者邮件
- 微信群、飞书群等正式群通知
- 报名开启和报名提醒
- 时间、地点或安排变更
- 公众号、推文和招募文案
- 会影响报名、到场或对外理解的正式信息

通常不归档：

- 群聊闲聊
- 未发送草稿
- 协作者之间的简单确认
- 已被最终版本替代的中间草稿

## 标题和标签

标题：

```text
[message] 活动名称 - 渠道 - YYYY-MM-DD
```

示例：

```text
[message] Math Help Room - 邮件通知 - 2026-09-09
[message] Group Birthday Ceremony - 微信群通知 - 2026-09-16
```

标签：

- 邮件：`message` + `mail`
- 群通知：`message` + `group-notice`
- 不添加：`event`

归档必须是对应活动主 Issue 的 Sub-issue。

## 归档正文模板

```markdown
## 发送信息

- 渠道：邮件通知
- 发送时间：YYYY-MM-DD
- 发送人：
- 收件范围：

## 正文

复制实际发送的完整内容。

## 附件或说明

- 原主 Issue：
- 截图：
- 链接：
- 活动材料目录：
- 通知文案备份：
- 其他说明：
```

## 操作步骤

1. 找到活动主 Issue。
2. 确认原文确实已经发送，而不是草稿。
3. 完整复制实际发送版本，不要只写摘要。
4. 补齐渠道、日期、发送人和收件范围。
5. 信息缺失时写“原记录未保留”，不要编造。
6. 使用 `--parent` 创建 Sub-issue。
7. 添加 `message` 和渠道标签。
8. 在活动主 Issue 中链接归档 Issue。

创建命令：

```bash
gh issue create \
  --repo BETA-SDC/event-proposal \
  --parent MAIN_ISSUE_NUMBER \
  --title "[message] 活动名称 - 邮件通知 - YYYY-MM-DD" \
  --label message \
  --label mail \
  --body-file archive.md
```

## 历史 Issue 整理

如果旧 `[event]` Issue 的正文其实是完整邮件：

- 新建 `[message]` Sub-issue 保存原文。
- 主 Issue 改为活动概览和材料入口。
- 主 Issue 移除 `message`、`mail`、`group-notice`。
- 主 Issue 保留 `event`。
- 归档 Issue 根据实际状态关闭。

如果旧 Issue 已经是 `[message]` 但带 `event`：

- 不要重复创建归档。
- 补齐渠道和日期。
- 移除 `event`。
- 确认 parent；找不到时不要凭空创建。

## 历史信息规则

- 不把活动举办时间当作通知发送时间。
- 不擅自修改原文中的日期、地点或事实矛盾。
- 对日期冲突在“附件或说明”中记录，正文保持原样。
- 发送人只能依据明确记录；根据 Issue 作者推断时要注明依据。
- 邮件和群通知渠道不确定时不要猜。

## 完成检查

- 标题符合 `[message] 活动名称 - 渠道 - YYYY-MM-DD`。
- 有 `message`，没有 `event`。
- 有 `mail` 或 `group-notice`。
- 有 parent 活动 Issue。
- 正文是完整发送版本。
- 记录了不确定信息。
- 主 Issue 已链接归档。
