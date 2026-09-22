---
name: event-proposal-workflow
description: Route and coordinate BETA-SDC event-proposal work across activity planning, Issue maintenance, message archiving, material naming, sign-in records, and media delivery skills.
---

# BETA-SDC 活动工作流路由

这个 Skill 是 `BETA-SDC/event-proposal` 相关任务的入口和编排器。

它不替代专业 Skill，也不重复所有细则。它负责：

1. 判断用户要做哪类工作。
2. 选择需要调用的专业 Skill。
3. 按正确顺序执行多个 Skill。
4. 处理不同 Skill 之间的冲突。
5. 做统一的最终检查并向用户汇报。

## 专业 Skill 清单

根据任务需要读取以下 Skill：

| Skill | 负责内容 |
| --- | --- |
| `event-proposal-author` | 活动策划、主 Issue、任务拆分、活动推进和收尾 |
| `event-issue-collaboration` | Issue 标题、标签、Sub-issue、分支和 PR |
| `event-proposal-issue-maintainer` | 历史 Issue 整理、角色纠正、标签冲突和规范扫描 |
| `event-message-archive` | 邮件、群通知、报名提醒和宣传文案归档 |
| `event-material-naming` | 学年目录、活动目录和材料文件命名 |
| `event-sign-in-records` | 报名、签到、到场统计和隐私处理 |
| `event-media-capture` | 照片、视频、授权、筛选和 Album 交付 |

专业 Skill 位于：

```text
community/skills/<skill-name>/SKILL.md
```

如果本 Skill 与专业 Skill 或 `community/docs/procedures/event/` 中的正式规范冲突，以正式规范为准。

## 任务路由

### 新建或推进活动

读取顺序：

1. `event-proposal-author`
2. `event-issue-collaboration`
3. `event-material-naming`
4. 按需要读取 `event-message-archive`
5. 按需要读取 `event-sign-in-records`
6. 按需要读取 `event-media-capture`

适用请求：

- “帮我开一个活动”
- “建立活动主 Issue”
- “准备活动材料”
- “拆分活动任务”
- “活动结束后补齐记录”

执行重点：

- 先建立 `[event]` 主 Issue。
- 再补标题、标签和任务 Sub-issue。
- 再确定活动目录和固定文件名。
- 正式发送通知后单独归档。
- 活动结束后补签到、素材和复盘。

### 整理旧 Issue

读取顺序：

1. `event-proposal-issue-maintainer`
2. `event-message-archive`
3. `event-issue-collaboration`
4. `event-material-naming`
5. 按需要读取 `event-proposal-author`

适用请求：

- “按规范整理 Issue”
- “扫描旧 Issue”
- “修正标题和标签”
- “把邮件从主 Issue 拆出来”
- “检查 event 和 message 混用”

执行重点：

- 先扫描全部 Issue，包括已关闭 Issue。
- 先判断 Issue 是活动主入口还是通知归档。
- 活动主 Issue 和通知归档不能混为一个 Issue。
- `[event]` 主 Issue 不得带 `message`。
- `[message]` 归档 Issue 不得带 `event`。
- 不确定时保留原文并记录不确定性，不要凭空重建事实。

### 归档正式通知

读取顺序：

1. `event-message-archive`
2. `event-proposal-issue-maintainer`
3. `event-issue-collaboration`

适用请求：

- “归档这封邮件”
- “把群通知放到 Issue”
- “补一个 message 子 Issue”
- “整理已发送文案”

执行重点：

- 确认对应活动主 Issue。
- 复制实际发送的完整版本。
- 使用 `[message] 活动名称 - 渠道 - YYYY-MM-DD`。
- 邮件使用 `message` + `mail`。
- 群通知使用 `message` + `group-notice`。
- 不添加 `event`。
- 发送时间、发送人、收件范围未知时明确标注，不编造。

### 整理活动目录和材料

读取顺序：

1. `event-material-naming`
2. `event-proposal-author`
3. `event-issue-collaboration`

适用请求：

- “建立活动目录”
- “规范文件名”
- “整理活动材料”
- “补 README、proposal 或 poster-information”

执行重点：

- 学年目录使用 `YYYY-YYYY`。
- 系列活动目录使用 `YYYY-MM-DD-SERIES-两位期数[-specific-topic]`。
- 使用固定文件名：`README.md`、`proposal.md`、`poster-information.md`、`notification-message.md`、`sign-in/`。
- 不使用 `final`、`new`、`latest`、`修改版` 等状态词。
- 同一活动只保留一个主目录。

### 整理签到和到场统计

读取顺序：

1. `event-sign-in-records`
2. `event-proposal-author`
3. `event-material-naming`

适用请求：

- “整理报名和签到”
- “统计活动到场人数”
- “建立 sign-in 目录”
- “清理签到 CSV”

执行重点：

- 文件放在活动目录下的 `sign-in/`。
- 保留数据来源、整理日期、统计口径和异常说明。
- 分开核对报名名单与签到名单。
- 不静默删除重名、补录、特殊标记或人工修正。
- 删除不必要的手机号、学号和其他敏感字段。

### 整理照片和视频

读取顺序：

1. `event-media-capture`
2. `event-proposal-author`
3. `event-issue-collaboration`

适用请求：

- “整理活动照片”
- “上传活动视频”
- “检查素材是否能发布”
- “补活动素材链接”

执行重点：

- 横屏、16:9、稳定、主体完整和背景干净优先。
- 重要场景保留多张照片或多条视频。
- 检查屏幕、文档、群聊和工牌中的敏感信息。
- 需要授权的人员，发布前确认授权。
- 素材按日期和活动名称整理到 Beta College Album。
- 活动主 Issue 或 `[wrap-up]` 记录链接素材位置。

## 组合任务执行顺序

### 新建一个完整活动

```text
event-proposal-author
  -> event-issue-collaboration
  -> event-material-naming
  -> event-message-archive
  -> event-sign-in-records
  -> event-media-capture
```

并非每个活动都需要最后三个 Skill。只有实际涉及通知、签到或素材时才读取和执行。

### 整理历史活动

```text
event-proposal-issue-maintainer
  -> event-message-archive
  -> event-issue-collaboration
  -> event-material-naming
  -> event-sign-in-records
  -> event-media-capture
```

先纠正 Issue 的角色，再处理通知、标题、材料、签到和素材。不要先改文件名或标签，再猜 Issue 的角色。

### 活动结束收尾

```text
event-proposal-author
  -> event-sign-in-records
  -> event-media-capture
  -> event-issue-collaboration
```

收尾记录使用主 Issue 或 `[wrap-up]` Sub-issue，不要把活动复盘混进 `[message]` 通知归档。

## 冲突处理优先级

当多个 Skill 给出的建议看起来冲突时，按以下优先级处理：

1. `community/docs/procedures/event/` 中的正式规范
2. `event-proposal-issue-maintainer`
3. `event-message-archive`
4. `event-issue-collaboration`
5. `event-proposal-author`
6. `event-material-naming`
7. `event-sign-in-records`
8. `event-media-capture`

具体原则：

- Issue 的角色和标签冲突，优先按 Issue 维护规则处理。
- 通知正文和归档方式冲突，优先按通知归档规则处理。
- 活动目录和文件命名冲突，优先按材料命名规则处理。
- 事实、日期、发送渠道不确定时，不用格式规则掩盖事实不确定性。

## 统一检查

### Issue 检查

```bash
gh issue list --repo BETA-SDC/event-proposal --state all \
  --json number,title,state,labels,parent,url --limit 100
```

检查：

- `[event]` 是否有 `event` 标签。
- `[message]` 是否有 `message` 标签。
- 是否存在 `event + message` 混用。
- 通知归档是否有 parent。
- 任务是否有 `task` 标签和 assignee。
- 日期是否使用 `YYYY-MM-DD`。

专门检查混用：

```bash
gh issue list --repo BETA-SDC/event-proposal --state all \
  --json number,title,labels,url --limit 100 |
  jq '[.[] | select(
    ([.labels[].name] | index("event")) and
    ([.labels[].name] | index("message"))
  )]'
```

结果必须是空数组。

### 文件检查

进入 `event-proposal` 仓库后检查：

```bash
git diff --check
git status --short
find 2026-2027 -maxdepth 2 -type f | sort
```

确认：

- 活动目录属于正确学年。
- 目录和文件名符合命名规则。
- 主活动目录有 `README.md`。
- 签到资料在 `sign-in/`。
- 没有不必要的原始个人信息。
- 正式通知没有只保存在草稿文件中。

## 不确定性处理

遇到以下情况不要自行补全：

- 找不到对应活动主 Issue。
- 无法确认通知是邮件还是群通知。
- 原文中日期、地点或时间互相矛盾。
- 无法确认发送人或收件范围。
- 无法判断材料属于哪个活动。

正确做法：

1. 先读取 Issue 历史、评论、活动目录和关联文件。
2. 保留原始内容。
3. 在说明中记录依据和不确定点。
4. 只有在无法安全推进时才向用户提问。

## 禁止事项

- 不要把所有专业规则复制进新的大文件，专业细则应留在对应 Skill。
- 不要在没有读取相关专业 Skill 的情况下执行跨领域任务。
- 不要让一个 Issue 同时承担活动主入口和通知归档。
- 不要创建没有 parent 的通知归档 Sub-issue。
- 不要凭空编造日期、发送人、渠道、统计数据或授权状态。
- 不要在没有确认隐私风险时复制原始报名表或群聊内容。
- 不要把素材、签到和通知工作只记录在聊天中而不留下可追踪入口。

## 完成报告

完成任务后，向用户简要报告：

- 识别出的任务类型。
- 读取并使用了哪些专业 Skill。
- 修改或创建了哪些 Issue、文件或目录。
- 哪些检查已通过。
- 哪些信息仍不确定。
- 是否 commit、push；除非用户明确要求，不要自行提交。
