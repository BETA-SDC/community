---
name: event-proposal-author
description: Create and update BETA-SDC activity plans, event Issues, event-proposal materials, and activity wrap-up records.
---

# BETA-SDC 活动策划与推进

这个 Skill 用于从活动想法开始，建立可追踪的活动主 Issue，拆分任务，准备活动材料，并完成活动收尾。

## 适用场景

- 新建活动
- 补全活动主 Issue
- 规划活动材料和截止时间
- 推进活动准备
- 活动结束后整理签到、素材和复盘

## 先读规范

操作前阅读：

- `community/docs/procedures/event/README.zh.md`
- `community/docs/procedures/event/issue-collaboration-guidelines.zh.md`
- `community/docs/procedures/event/event-proposal-repo-naming-regulation.zh.md`
- `community/docs/procedures/event/message-archive-guidelines.zh.md`
- `community/docs/procedures/event/sign-in-record-guidelines.zh.md`
- `community/docs/procedures/event/media-capture-guidelines.zh.md`

## 标准流程

1. 在 `BETA-SDC/event-proposal` 创建 `[event]` 主 Issue。
2. 写清楚活动背景、目的、时间、地点、形式、负责人、协作人员和截止时间。
3. 把海报、报名表、文案、场地、物资、现场执行和素材整理拆成独立 Sub-issue。
4. 给任务 Sub-issue assign 执行人，并写明交付物和提交位置。
5. 从主 Issue 创建分支，在活动目录中准备材料。
6. 提交关联主 Issue 的 Pull Request。
7. 负责人确认时间、地点、报名方式、公开文案和材料路径后再合并。
8. 正式发送通知后，创建 `[message]` Sub-issue 归档。
9. 活动结束后补签到、照片视频位置、反馈、问题和可复用材料。

## 主 Issue 模板

标题：

```text
[event] 活动名称
```

正文：

```markdown
## 活动概览

- 活动名称：
- 活动目的和背景：
- 活动形式：
- 活动负责人：

## 基本信息

- 时间：
- 地点：
- 参与对象：
- 主办方或合作方：

## 协作与执行

- 相关成员：
- 关键截止时间：
- 需要准备的材料：

## 材料与归档

- 活动材料目录：
- 活动策划案：
- 海报信息表：
- 通知归档：
- 签到记录：
- 照片和视频：

## 收尾

- 活动是否如期举行：
- 参与人数或反馈：
- 待复盘问题：
- 可复用材料：
```

## 任务拆分

常见任务：

```text
[task] 活动名称 - 制作海报
[task] 活动名称 - 准备报名表
[task] 活动名称 - 准备通知文案
[task] 活动名称 - 确认场地和设备
[task] 活动名称 - 现场执行
[task] 活动名称 - 整理活动素材
```

每个任务至少写：

- 任务内容和交付物
- 负责人
- 截止时间
- 依赖材料或链接
- 完成后提交到哪里

需要海报时，必须在海报任务中说明用途、截止时间、发布渠道、报名链接、指定图片和图片使用要求，并 @ 活动负责人或宣传负责人。

## 完成前检查

- 主 Issue 有 `event` 标签。
- 主 Issue 不带 `message`、`mail`、`group-notice`。
- 任务已拆成 Sub-issue 并 assign。
- 活动目录、策划案、海报信息和通知草稿路径正确。
- 时间、地点、主办方和报名方式已确认。
- PR 关联主 Issue。
- 已发送通知有独立 `[message]` 归档。
- 活动结束后已补签到、素材和复盘入口。

## 禁止事项

- 不要把活动通知全文写成主 Issue 的唯一正文。
- 不要把所有任务堆在主 Issue 标题或一个 checklist 中。
- 不要在正式通知发送后只保留草稿文件，不建 `[message]` Sub-issue。
- 不要在没有确认时编造时间、地点、负责人或报名方式。
