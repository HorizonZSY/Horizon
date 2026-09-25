---
name: rp-review
description: 对 research proposal 做对抗式审稿（模拟计量审稿人、领域专家、招生/资助评审三方），按 100 分量表打分，找出致命缺陷，核查引用，输出分级修改计划。当用户说"帮我审一下 proposal""挑毛病""打个分""还有什么问题"时使用。
argument-hint: <slug> [--version <N>] [--focus identification|literature|feasibility|writing]
---

# /rp-review — 对抗式审稿

先读 `workflow/rules.md` 并全程遵守。评分量表见 `workflow/templates/review-rubric.md`。

输入：`applications/<slug>/02-proposal-v<N>.md`（默认最新版）、`refs.md`、`01-scope.md`（如有）、目标项目官方要求（如 notes 中有记录）。

产出：`applications/<slug>/03-review-v<N>.md`。

## 角色分离

审稿阶段**只评不改**：不直接修改 proposal 文件（借鉴 hugosantanna/clo-author 的 worker–critic 分离：critic 不能编辑，creator 不能给自己打分）。修改在用户确认修改计划后，由 `/rp-improve <slug> --review 03-review-v<N>.md` 生成下一版。

## Step 1 — 三位审稿人独立审阅

依次扮演三位审稿人，每位独立完成 (a)–(d)，不参考其他审稿人的意见：

| 审稿人 | 关注点 |
|---|---|
| R1 计量经济学者 | 识别假设是否写清、是否可检验；估计量选择（如交错 DID 是否仍用 TWFE）；标准误；功效；内生性来源是否穷举 |
| R2 领域专家（按题目设定，如发展经济学/农业经济学） | 文献是否漏掉关键脉络；贡献是否真实存在；情境知识（政策细节、制度背景）是否准确 |
| R3 招生/资助评审（如 ESRC DTP 面板、系招生委员会） | 3–4 年内能否完成；数据是否真的拿得到；与导师/系的匹配；表达是否让非本领域评审看懂 |

每位审稿人输出：

- **(a) 复述**：用 3 句话复述本研究的问题、设计、贡献。复述与作者意图有偏差，本身就记为清晰度问题
- **(b) 拒绝理由**：最可能导致拒绝的 3 条理由，按可能性排序
- **(c) 问题清单**：每条包含
  - 严重度：`FATAL` / `MAJOR` / `MINOR`
  - 位置：章节 + 原文引用（必须引用原文，不能泛泛而谈）
  - 问题：一句话
  - 修改建议：具体到可执行
  - 如何验证已修复：一句话
- **(d) 评分**：按 review-rubric.md 各维度打分，每项附一句依据

规则：

- 不写空泛的表扬；优点最多列 3 条，且要具体
- 批评必须可检验：给不出"如何验证已修复"的批评，降级或删除
- `FATAL` 只用于 review-rubric.md 列出的致命情形

## Step 2 — 引用核查

对 proposal 引用的每篇文献：

1. 是否出现在 `refs.md` 且已核实；不在的，按 `rules.md` 现场核实
2. 抽查引用的论断是否与原文一致（至少抽查支撑核心论证的 3 篇，打开摘要或正文对照）
3. 结果列表：`通过 / 不存在 / 信息有误 / 论断与原文不符`

任何"不存在"或"论断与原文不符"都记为 `FATAL`。

## Step 3 — 主编汇总

以主编身份合并三份审稿意见：

1. 去重合并，保留最严重的定级
2. 总分 = 三位审稿人分数的平均；列出分歧超过 2 分的维度并说明原因
3. 修改计划，每条归入一类（借鉴 claudeblattman 对审稿意见的分类）：
   - **MUST**：所有 FATAL + 两位及以上审稿人提出的 MAJOR
   - **SHOULD**：其余 MAJOR
   - **CONSIDER**：MINOR
   - **DISAGREE**：审稿意见本身有误或不适用，写明理由（允许反驳审稿人，但理由要可检验）
4. 给出下一版的执行顺序（先改识别与数据，再改文献，最后改表达）

## 输出模板（03-review-v<N>.md）

```markdown
# Review of <slug> v<N>
日期：YYYY-MM-DD ｜ 总分：xx/100 ｜ FATAL: n ｜ MAJOR: n ｜ MINOR: n

## 主编结论（3–5 句）
## 修改计划（MUST / SHOULD / CONSIDER / DISAGREE）
## 引用核查结果
## 评分汇总表（维度 × R1/R2/R3/均值）
## R1 计量审稿意见（a–d）
## R2 领域审稿意见（a–d）
## R3 评审面板意见（a–d）
```

## 循环与停止条件

- 用户确认修改计划 → `/rp-improve <slug> --review 03-review-v<N>.md` 生成 v<N+1> → 再次 `/rp-review`
- 停止条件（同时满足）：无 FATAL；MAJOR ≤ 2；总分 ≥ 75
- 最多 3 轮。3 轮后仍不满足，说明卡在哪一类问题，并判断是否应回到 `/rp-scope` 换题或换设计
- 每轮在输出开头列出上一轮 MUST 项的处理情况：已解决 / 部分解决 / 未解决
