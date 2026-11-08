# Payment Use Invoice Skill

一个用于动态制作 Plantation Shutters `Payment Use Invoice` 的 Codex Skill。

它会从当前项目的 `原始数据` 文件夹中识别：

- 固定的 Y070 发票模板；
- 固定的成品窗价格表；
- 最新有效的 `[柜号] Order List & QTY` 文件。

然后动态生成：

`Original Invoice of [柜号] - Payment Use.xlsx`

## 功能

- 从订单文件名自动提取柜号和 Invoice Number
- 动态识别订单工作表、表头和有效数据行
- 保留原始订单顺序及 G/H 列备注
- 区分 PVC、Wood、Pine、Gear Rod 和 Free replacement
- 从价格表重新匹配单价并标记 TBC
- 整理 Lock、Hidden Hinges 和特殊窗型
- 排除免费重做订单的独立配件及特殊窗型费用
- 自动填写 Date 和 ETD
- 保留 Y070 模板格式并检查打印效果

## 安装

将本仓库复制到个人 Codex skills 目录：

```text
~/.codex/skills/payment-use-invoice/
```

Windows 示例：

```text
C:\Users\<用户名>\.codex\skills\payment-use-invoice\
```

复制后应保持以下结构：

```text
payment-use-invoice/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── invoice-rules.md
```

## 使用

在 Codex 中输入：

```text
请使用 $payment-use-invoice 制作当前柜号的发票。
```

项目目录中需要存在：

```text
制作发票/
└── 原始数据/
    ├── Original Invoice of Y070 - Payment Use.xls
    ├── 成品窗价格.xlsx
    └── [柜号] Order List & QTY.xlsx
```

## 文件说明

- `SKILL.md`：Skill 入口、触发范围和执行流程。
- `references/invoice-rules.md`：价格、备注、颜色、配件、固定行及质量检查规则。
- `agents/openai.yaml`：Codex 界面名称、简介和默认提示词。

## 注意事项

- Skill 不包含客户订单、价格表或发票模板等业务文件。
- 每次执行都会重新扫描订单文件，不应复用上一次的柜号或订单数据。
- 如果存在多个无法区分的订单文件，Skill 会要求用户确认。
- 如果同柜号输出文件已存在，Skill 不应未经确认直接覆盖。

