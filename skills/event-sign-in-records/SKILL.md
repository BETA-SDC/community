---
name: event-sign-in-records
description: Organize BETA-SDC event registration, sign-in, attendance statistics, categorized CSV files, and exception notes.
---

# BETA-SDC 签到记录整理

这个 Skill 用于整理活动报名、签到、取消、缺席、现场补录和实际到场统计。

## 适用场景

活动存在以下任一情况时使用：

- 报名
- 签到
- 现场补录
- 临时取消
- 需要统计实际到场人数
- 需要复盘报名转化或缺席情况

签到记录不能只保存在个人表格、聊天记录或临时接龙中。

## 位置和文件

签到记录放在对应活动目录下：

```text
活动目录/
  sign-in/
    README.md
    00-summary.csv
    01-registered-attended.csv
    02-registered-absent.csv
    03-registered-cancelled.csv
    04-unregistered-attended.csv
```

没有某一类人员时，可以省略对应 CSV，或保留空文件并在 README 中说明。

## README 必须包含

- 活动名称
- 数据来源
- 原始数据整理日期
- 统计口径
- 汇总人数
- 每个 CSV 的内容
- 重名、补录、取消、异常标记和人工处理说明

模板：

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
| `03-registered-cancelled.csv` | 报名后取消 |
| `04-unregistered-attended.csv` | 未报名但到场 |

## 说明

- 记录原始标记、异常数据和人工处理方式。
```

## CSV 规则

汇总表至少包含：

```csv
类别,人数
报名且到场,0
报名未到场,0
报名后临时取消,0
报名总人数,0
未报名但参加,0
现场总人数,0
```

分类名单推荐使用：

```csv
序号,姓名
1,姓名
```

如确实需要学号、学院或联系方式，先确认必要性和访问范围，只保留最少字段。

## 统计规则

- 报名名单和签到名单分开核对。
- 确认未报名到场、报名未到场和重复姓名。
- 解释 `1`、`0`、`-1` 等原始标记。
- 人工判断和手动修正必须写入 README。
- 不要静默删除重名、前缀、备注符号或异常记录。
- 如果活动采用不同统计口径，在 README 中明确说明。

## 隐私规则

不要提交包含大量手机号、学号、身份证号、详细联系方式或无关备注的原始表格。不要为了“原样备份”保存不必要的个人信息。

## 完成检查

- `sign-in/README.md` 说明数据来源和整理日期。
- 汇总人数和分类 CSV 对得上。
- 分类名单和统计口径可追溯。
- 异常、重名、补录和人工修正有记录。
- 没有不必要的个人敏感信息。
- 主活动收尾记录链接到了签到目录。
