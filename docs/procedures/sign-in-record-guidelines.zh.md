# 签到记录整理规范

中文 | [English](./sign-in-record-guidelines.md)

> 本文档用于说明活动结束后如何整理报名、签到和到场统计记录。

## 适用场景

当活动存在报名、签到、现场补录、临时取消或需要统计实际到场人数时，应在活动材料目录下整理签到记录。签到记录用于复盘活动参与情况、核对报名转化、支持后续报销或活动总结，不应只保存在个人表格、聊天记录或临时接龙中。

可参考 [集体生日会签到记录样例](https://github.com/BETA-SDC/event-proposal/tree/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in)，其中包含说明文档和分类后的 CSV 文件。

样例文件包括：[README.md](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/README.md)、[00-summary.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/00-summary.csv)、[01-registered-attended.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/01-registered-attended.csv)、[02-registered-absent.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/02-registered-absent.csv)、[03-registered-cancelled.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/03-registered-cancelled.csv) 和 [04-unregistered-attended.csv](https://github.com/BETA-SDC/event-proposal/blob/main/2026-2027/2026-09-16-GROUP-BIRTHDAY-01-2026-fall/sign-in/04-unregistered-attended.csv)。

## 放置位置

签到记录应放在对应活动目录下的 `sign-in/` 子目录中。

推荐结构：

```text
2026-09-16-GROUP-BIRTHDAY-01-2026-fall/
  sign-in/
    README.md
    00-summary.csv
    01-registered-attended.csv
    02-registered-absent.csv
    03-registered-cancelled.csv
    04-unregistered-attended.csv
```

如果活动没有某一类人员，可以省略对应 CSV，或保留空表并在 `README.md` 中说明。

## README.md 内容

`sign-in/README.md` 应至少说明：

- 活动名称
- 数据来源，例如报名表、签到表、微信群接龙、现场补录表等
- 原始数据整理日期
- 统计口径，例如签到标记 `1`、`0`、`-1` 分别代表什么
- 汇总人数
- 每个 CSV 文件的内容
- 需要特别说明的问题，例如重名、补录、取消、异常标记或数据来源不完整

推荐章节：

```markdown
# 活动名称 · 到场信息统计

数据来源：原始文件或表格名称，整理日期 YYYY-MM-DD。

## 汇总

| 类别 | 人数 |
| --- | --- |
| 报名且到场 | 0 |
| 报名未到场 | 0 |
| 报名后临时取消 | 0 |
| 报名总人数 | 0 |
| 未报名但参加 | 0 |
| 现场总人数 | 0 |

## 文件

| 文件 | 内容 |
| --- | --- |
| `00-summary.csv` | 各类别人数 |
| `01-registered-attended.csv` | 报名且到场 |
| `02-registered-absent.csv` | 报名未到场 |
| `03-registered-cancelled.csv` | 报名后临时取消 |
| `04-unregistered-attended.csv` | 未报名但到场 |

## 说明

- 在这里说明原始表格结构、签到标记含义、异常数据和人工处理方式。
```

## CSV 文件

### 00-summary.csv

`00-summary.csv` 用于保存汇总数字，建议至少包含以下行：

```csv
类别,人数
报名且到场,0
报名未到场,0
报名后临时取消,0
报名总人数,0
未报名但参加,0
现场总人数,0
```

其中：

- `报名总人数` 通常等于报名且到场、报名未到场、报名后临时取消等报名相关分类之和
- `现场总人数` 通常等于报名且到场和未报名但参加之和
- 如果活动口径不同，应在 `README.md` 中说明

### 分类名单

分类名单 CSV 推荐使用 `序号,姓名` 两列：

```csv
序号,姓名
1,姓名
2,姓名
```

常用分类文件：

- `01-registered-attended.csv`：报名且到场
- `02-registered-absent.csv`：报名未到场
- `03-registered-cancelled.csv`：报名后临时取消
- `04-unregistered-attended.csv`：未报名但到场

如果需要保存学号、学院、联系方式等额外字段，应确认这些信息确实有必要保留，并避免公开不必要的个人敏感信息。

## 整理规则

- 保留原始数据来源说明，不要只提交整理后的数字。
- 把报名名单和签到名单分开核对，确认是否存在未报名到场、报名未到场和重复姓名。
- 对原始表中的特殊标记保持解释，例如 `1` 表示到场、`0` 表示未到场、`-1` 表示取消。
- 人工判断或手动修正必须写入 `README.md` 的说明部分。
- 如果发现姓名前缀、备注符号、重复姓名或异常记录，不要静默删除，应说明是否保留原样以及是否需要后续确认。
- 不建议提交原始 Excel、截图或包含过多个人信息的文件；如确需保存，应确认访问范围和隐私风险。

## 提交前检查

- [ ] `sign-in/README.md` 已说明数据来源和整理日期
- [ ] 汇总人数和分类 CSV 能互相对应
- [ ] 报名且到场、报名未到场、取消、未报名到场等分类已按活动实际情况整理
- [ ] 异常标记、重复姓名、补录和人工判断已在说明中记录
- [ ] 没有公开不必要的手机号、学号、身份证号等个人敏感信息
- [ ] 活动建立规范流程中的收尾记录已引用签到记录位置
