# β书院 SDC Community

β书院学生发展委员会（SDC）的公共资料仓库，用于集中保存组织资料、成员名册、规章制度、会议记录跳转入口和视觉素材。

本仓库以 Markdown、CSV 和常见图片格式为主，方便成员查阅、协作编辑和追踪历史变更。

## 目录

| 目录 | 内容 |
| --- | --- |
| [`members/`](members/) | 按学年保存的 SDC 成员名册 |
| [`docs/`](docs/) | 组织制度、工作流程和参考资料 |
| [`meetings/`](meetings/) | 已迁移的会议记录模板和会议记录跳转入口 |
| [`logos/`](logos/) | β书院、西湖大学及相关视觉素材 |

## 常用资料

- [2026–2027 学年成员名册](members/2026-2027.csv)
- [2025–2026 学年成员名册](members/2025-2026.csv)
- [SDC 成员规范测试题库](docs/resources/member-test/questions.md)
- [文档总入口](docs/README.zh.md)
- [2026 年值日与大扫除规章](docs/regulations/duty_roster_regulation_2026.md)
- [活动与宣传](docs/procedures/event/README.zh.md)
- [素材拍摄与交付规范](docs/procedures/event/media-capture-guidelines.zh.md)
- [为什么使用 GitHub](docs/resources/why-we-use-github.md)
- [Logo 与视觉素材说明](logos/README.md)

## 成员名册

成员名册使用 CSV 格式记录，字段如下：

```text
Name,Github ID,Department,Role
```

- `Name`：成员姓名
- `Github ID`：成员的 GitHub 用户名；暂无信息时留空
- `Department`：所属部门
- `Role`：组织内职务

名册按学年维护。新增、转部门或职务变更时，请同步更新对应学年的 CSV 文件，并在提交记录中说明变更内容。

## 会议记录

会议记录模板和会议记录已经全部迁移至独立的 [`BETA-SDC/meetings`](https://github.com/BETA-SDC/meetings) 仓库。

本仓库的 [`meetings/`](meetings/) 目录仅保留跳转文件：

- [`TEMPLATE.md`](meetings/TEMPLATE.md) 跳转至会议记录模板
- [`2026-2027/2026-09-06.md`](meetings/2026-2027/2026-09-06.md) 跳转至对应会议记录
- [`2026-2027/2026-09-09.md`](meetings/2026-2027/2026-09-09.md) 跳转至对应会议记录

后续新增或修改会议记录时，请直接在 [`BETA-SDC/meetings`](https://github.com/BETA-SDC/meetings) 仓库中进行。

## 文档分类

所有文档统一放在 `docs/` 下，并按用途分为三类：

- `docs/regulations/`：正式制度与必须遵守的规则，回答“什么必须遵守”。
- `docs/procedures/`：可重复执行的工作流程，回答“具体应该怎么做”。
- `docs/resources/`：工具、教程、背景说明和外部参考链接，用于帮助成员完成工作。

## 协作约定

1. 文档优先使用 Markdown，结构化名单优先使用 CSV。
2. 文件名使用清晰、稳定、便于检索的命名方式；会议记录按 `YYYY-MM-DD.md` 命名。
3. 修改资料前先确认所属学年、部门或文档版本，避免覆盖其他时期的内容。
4. 每次提交只处理相互关联的改动，并在提交信息中简要说明修改内容。
5. 涉及成员个人信息的内容应仅保留开展组织工作所必需的信息。

## 使用 GitHub

本仓库通过 GitHub 提供在线查阅、协作编辑和版本追踪。第一次使用 GitHub 时，可以先阅读[《为什么使用 GitHub》](docs/resources/why-we-use-github.md)，了解 Markdown、版本控制和团队协作的基本方式。

仓库地址：[github.com/BETA-SDC/community](https://github.com/BETA-SDC/community)
