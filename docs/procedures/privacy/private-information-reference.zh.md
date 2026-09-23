# 私有信息引用说明

中文 | [English](./private-information-reference.md)

> 本文档说明公开仓库如何引用保存在 [`BETA-SDC/community-private-information`](https://github.com/BETA-SDC/community-private-information) 中的私有或非公开信息。

## 什么时候使用私有仓库

当社区或活动工作需要保存对内部工作有用、但不适合公开入库的信息时，使用私有仓库：

- 私有文字、内部备注、联系方式或访问说明
- 通过私有 Issue 或 Pull Request 上传的图片
- 截图、表格、扫描件、非公开 PDF 等附件
- 单个活动相关的私密支持材料

不要把私有内容复制到公开仓库。公开文档本身应当可读，只为有权限的人补充私有链接。

## 纯文本引用

当公开文档需要指向私有文字时，先在私有仓库中建立 Markdown 文件，再从公开文档链接过去：

```markdown
私有备注：[内部文字资料](https://github.com/BETA-SDC/community-private-information/blob/main/text/example.md)
```

活动相关的私有文字优先放在：

```text
community-private-information/activities/YYYY-YYYY/YYYY-MM-DD-activity-slug/text/
```

## 图片引用

使用私有图片时：

1. 在 `community-private-information` 的私有 Issue 或 Pull Request 中上传图片。
2. 复制 GitHub 生成的 `github.com/user-attachments/assets/...` 链接。
3. 在公开 Markdown 中引用该链接。

优先使用普通链接：

```markdown
[查看私有参考图](https://github.com/user-attachments/assets/xxxx-xxxx-xxxx)
```

只有当图片裂图后公开页面仍然可理解时，才使用嵌入图片：

```markdown
![私有参考图](https://github.com/user-attachments/assets/xxxx-xxxx-xxxx)
```

## 附件引用

非公开 PDF、表格、截图、扫描件等附件放在：

```text
community-private-information/attachments/
```

如果是活动专属文件，则放在：

```text
community-private-information/activities/YYYY-YYYY/YYYY-MM-DD-activity-slug/attachments/
```

只有在没有权限的人仍能理解公开文档时，才从公开文档链接到私有附件。

## 公开文档要求

- 公开文档应直接说明公开事实。
- 私有链接只补充内部细节，不替代公开说明。
- 不要把敏感个人信息写入链接文字。
- 不要在公开文本中提及访问码、手机号、财务细节或敏感上下文。
- 如果某个私有引用对执行工作很重要，应同时说明可以向谁申请访问权限。
