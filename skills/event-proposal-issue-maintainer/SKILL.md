---
name: event-proposal-issue-maintainer
description: Maintain and normalize BETA-SDC event-proposal GitHub Issues according to the activity, Issue collaboration, and message archive guidelines.
---

# BETA-SDC 活动 Issue 维护

这个 Skill 用于维护 `BETA-SDC/event-proposal` 仓库中的活动 Issue、Sub-issue、标签和通知归档。

目标很明确：

- 一个活动主 Issue 只负责描述活动本身。
- 一条已经正式发送的邮件、群通知或宣传文案，必须单独归档为 `[message]` Sub-issue。
- 主活动 Issue 和通知归档不能同时承担两个角色，也不能同时带 `event` 和 `message` 标签。

## 适用场景

遇到以下请求时使用本 Skill：

- “整理旧 Issue”
- “按规范修改 Issue”
- “把邮件从主 Issue 拆出来”
- “检查 event 和 message 混用”
- “归档已发送通知”
- “规范化活动 Issue、标签、标题或 Sub-issue”

## 权威文档

在操作前阅读仓库中的对应规范：

- `community/docs/procedures/event/README.zh.md`
- `community/docs/procedures/event/issue-collaboration-guidelines.zh.md`
- `community/docs/procedures/event/message-archive-guidelines.zh.md`
- `community/docs/procedures/event/event-proposal-repo-naming-regulation.zh.md`
- `community/docs/procedures/event/sign-in-record-guidelines.zh.md`
- `community/docs/procedures/event/media-capture-guidelines.zh.md`

如果本 Skill 与这些规范冲突，以仓库中的正式规范为准。

## 核心模型

### 主活动 Issue

主活动 Issue 的标题格式：

```text
[event] 活动名称
```

主活动 Issue 至少说明：

- 活动名称或暂定名称
- 活动目的和背景
- 时间、地点和形式
- 初步负责人
- 相关成员
- 关键截止时间
- 是否需要海报、报名表、通知或其他材料

主活动 Issue 应使用：

- 标签：`event`
- 不使用：`message`、`mail`、`group-notice`

活动主 Issue 可以是不完整的早期入口，但不能把正式通知全文当作唯一正文。

### 通知归档 Issue

正式发送后的邮件、微信群/飞书群通知、报名提醒、时间地点变更、公众号文案等，使用独立的 `[message]` Sub-issue。

标题格式：

```text
[message] 活动名称 - 渠道 - YYYY-MM-DD
```

渠道示例：

- `邮件通知`
- `微信群通知`
- `飞书群通知`
- `公众号推文`

通知归档必须：

- 是对应活动主 Issue 的 Sub-issue
- 至少有 `message` 标签
- 邮件追加 `mail`
- 群通知追加 `group-notice`
- 完整保留实际发送版本
- 记录发送渠道、发送时间、发送人、收件范围
- 已知信息不足时明确写“原记录未保留”，不能编造

通知归档不应使用：

- `event` 标签
- `[event]` 标题前缀

### 其他 Sub-issue

任务：

```text
[task] 活动名称 - 任务名称
```

收尾：

```text
[wrap-up] 活动名称 - 收尾事项
```

每个任务 Sub-issue 应尽量写清楚：

- 任务内容和交付物
- 负责人
- 截止时间
- 依赖材料或链接
- 结果提交位置

## 最重要的判断规则

### 不允许的混用

发现以下任一情况，就要检查并整理：

- 标题是 `[event]`，但正文主要是邮件或群通知全文
- 标题是 `[message]`，但标签含 `event`
- 标签同时含 `event` 和 `message`
- 主活动 Issue 的正文只有一封通知，没有活动概览
- 通知正文写在活动主 Issue 中，但没有独立 `[message]` 子项

### 如何判断正文是不是通知

以下内容通常表示正文是通知而不是活动主 Issue：

- 以“各位同学好”“亲爱的同学们”“Dear Students”等直接面向收件人开头
- 主要内容是号召报名、介绍时间地点、附二维码或群聊入口
- 使用中英文对照的宣传文案
- 包含“请积极报名”“扫描二维码”“欢迎参加”等发送语气
- 没有活动负责人、协作成员、截止时间、材料入口等项目管理信息

### 渠道判断

根据用户、Issue 标题、正文和已有标签判断渠道：

1. 用户明确说是邮件：使用 `邮件通知`，标签 `message` + `mail`。
2. 用户明确说是微信群、飞书群或群聊：使用对应群通知名称，标签 `message` + `group-notice`。
3. 只有 `mail` 标签且没有更强证据时：优先按邮件处理。
4. 只有 `group-notice` 标签且没有更强证据时：按群通知处理。
5. 渠道无法确定时：不要猜。先保留原文，在说明中写明“渠道待确认”，必要时向用户提问。

## 标准工作流

### 1. 获取目标范围

先确认仓库和范围：

```bash
gh issue list --repo BETA-SDC/event-proposal --state all \
  --json number,title,state,labels,parent,url --limit 100
```

检查所有混用项：

```bash
gh issue list --repo BETA-SDC/event-proposal --state all \
  --json number,title,state,labels,parent,url \
  --limit 100 |
  jq -r '.[] |
    select(([.labels[].name] | index("event")) and
           ([.labels[].name] | index("message"))) |
    [.number,.state,.title,( [.labels[].name] | join(",")),.url] |
    @tsv'
```

不要只检查开放 Issue。历史上已经关闭的 Issue 也需要规范化。

### 2. 逐个读取完整内容

对每个候选 Issue 读取：

```bash
gh issue view ISSUE_NUMBER --repo BETA-SDC/event-proposal \
  --json number,title,body,state,labels,comments,author,assignees,parent,url
```

同时检查：

- 是否已有父 Issue
- 是否已经有通知归档子 Issue
- 正文是否是活动信息、通知全文，还是两者混合
- 评论中是否有发送时间、渠道或补充说明
- 对应活动目录、`notification-message.md`、`proposal.md` 是否存在

### 3. 处理 `[event]` 主 Issue 中混入通知的情况

如果 Issue 是活动主 Issue，但正文主要是通知：

1. 从原正文提取并完整保留实际发送版本。
2. 创建新的 `[message]` Sub-issue。
3. 用 `--parent MAIN_ISSUE_NUMBER` 建立父子关系。
4. 将正文放入通知归档的 `## 正文`。
5. 对发送时间、发送人、收件范围等不确定信息明确标注。
6. 将主 Issue 改写为活动概览、基本信息、协作信息、材料入口和历史整理说明。
7. 从主 Issue 移除 `message`、`mail`、`group-notice`，只保留 `event`。
8. 通知归档完成后，根据实际状态关闭归档 Issue；不要为了修改历史记录而关闭仍需处理的开放事项。

创建归档的基本命令：

```bash
gh issue create \
  --repo BETA-SDC/event-proposal \
  --parent MAIN_ISSUE_NUMBER \
  --title "[message] 活动名称 - 邮件通知 - YYYY-MM-DD" \
  --label message \
  --label mail \
  --body-file archive-body.md
```

### 4. 处理 `[message]` 但带 `event` 标签的情况

如果标题已经是 `[message]`，正文也确实是通知：

1. 不要重复创建归档 Issue。
2. 从标题中补齐渠道和 `YYYY-MM-DD` 日期。
3. 移除 `event` 标签。
4. 确保保留 `message`，并按渠道保留 `mail` 或 `group-notice`。
5. 如果能确认活动主 Issue，设置为该主 Issue 的 Sub-issue。
6. 如果找不到活动主 Issue，不要凭空创建。保留独立归档，并在说明中记录“对应活动主 Issue 待确认”。

### 5. 处理通知和活动完全无法区分的情况

不要在不确定时擅自重写或删除内容。应：

- 保留原正文
- 记录冲突或不确定点
- 优先通过 Issue 历史、评论、活动目录和文件名核对
- 仍无法判断时向用户提问

## 通知归档模板

```markdown
## 发送信息

- 渠道：邮件通知
- 发送时间：YYYY-MM-DD；如果未知，写“原记录未保留具体发送时间”
- 发送人：姓名或 GitHub 用户名；如果未知，写“原记录未保留”
- 收件范围：实际范围；如果未知，写“原记录未保留”

## 正文

复制实际发送的完整内容。

## 附件或说明

- 原主 Issue：
- 活动材料目录：
- 通知文案备份：
- 历史整理说明：
```

重要要求：

- 不要只保留摘要。
- 不要润色成新的文案后替代原发送版本。
- 不要把二维码、截图、链接说明误当作完整正文。
- 可以在正文后增加“历史整理说明”，但不要改写原文含义。

## 主活动 Issue 模板

```markdown
## 活动概览

- 活动名称：
- 活动目的：
- 活动形式：
- 活动负责人：

## 基本信息

- 时间：
- 地点：
- 参与对象：

## 协作与执行

- 负责人：
- 相关成员：

## 材料与归档

- 活动材料目录：
- 活动策划案：
- 通知归档：
- 照片和视频：

## 历史整理说明

本 Issue 曾包含早期通知正文，现已按规范拆分到独立的 `[message]` Sub-issue。
```

## 历史信息和不确定性

历史 Issue 经常缺少准确发送时间、发送人或收件范围。处理原则：

- 不补造具体时间。
- 不把活动时间当作邮件发送时间。
- 不把 Issue 作者自动写成发送人，除非正文、评论或用户明确支持；若依据作者推断，写明“根据原 Issue 作者记录整理”。
- 不修正原通知中的事实矛盾；在归档说明中指出矛盾，并保留原文。
- 对明显日期冲突保留原文，同时在归档说明中说明标题日期或活动日期采用的依据。

## 标签检查

整理完成后至少检查：

```bash
gh issue list --repo BETA-SDC/event-proposal --state all \
  --json number,title,state,labels,parent,url --limit 100
```

最终目标：

- `[event]` 主 Issue：有 `event`，没有 `message`
- `[message]` 归档 Issue：有 `message`，没有 `event`
- 邮件归档：有 `mail`
- 群通知归档：有 `group-notice`
- 归档 Issue 能通过 parent 找到活动主 Issue

专门检查错误混用：

```bash
gh issue list --repo BETA-SDC/event-proposal --state all \
  --json number,title,labels,url --limit 100 |
  jq '[.[] | select(
    ([.labels[].name] | index("event")) and
    ([.labels[].name] | index("message"))
  )]'
```

结果必须是空数组。

## 禁止事项

- 不要让一个 Issue 同时承担 `[event]` 和 `[message]` 两种角色。
- 不要让标签同时包含 `event` 和 `message`。
- 不要删除原始通知正文来“整理干净”。
- 不要把正式通知只留在活动目录文件中而不建 `[message]` Sub-issue。
- 不要把未发送草稿当作正式通知归档。
- 不要凭空创造活动主 Issue、发送时间、发送人、收件范围或发送渠道。
- 不要把敏感个人信息复制到新的归档正文中，除非它确实属于实际发送内容且用户明确要求保留。
- 不要因为历史 Issue 很旧或已经关闭就跳过检查。

## 完成标准

完成后应向用户报告：

- 扫描了哪些 Issue
- 哪些 Issue 被改为主活动 Issue
- 新建了哪些通知归档 Sub-issue
- 哪些标签被添加或移除
- 哪些历史信息存在不确定性
- 最终混用扫描结果

除非用户明确要求，否则不要自动提交或推送与 Issue 整理无关的仓库文件改动。
