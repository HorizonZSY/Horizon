---
name: rp-draft
description: 撰写或改编 PhD research proposal（英国/欧洲/香港/中国大陆申请-考核制等需要研究计划的项目）。基于 /rp-scope 的产出和目标项目的官方要求起草全文，或把核心版 proposal 改编给某个具体项目/导师。当用户说"写 proposal""起草研究计划""把 proposal 改成投 X 的版本"时使用。
argument-hint: <slug> [adapt <项目slug> --supervisor <导师名>] [--limit <字数>]
---

# /rp-draft — 起草与改编 Research Proposal

先读 `workflow/rules.md` 并全程遵守。结构骨架见 `workflow/templates/research-proposal.md`。

已经有一份 proposal、想优化或补全时，用 `/rp-improve`。本 skill 用于从零起草，以及改编给具体项目。

两种模式：

- **draft**（默认）：`/rp-draft <slug>` → 从 `applications/<slug>/01-scope.md` 起草核心版
- **adapt**：`/rp-draft <slug> adapt <项目slug> --supervisor <导师>` → 把核心版改编给具体项目

## Step 0 — 输入检查（缺一项就停下来问）

| 输入 | 来源 | 缺失时 |
|---|---|---|
| 01-scope.md | `/rp-scope` 产出 | 建议先跑 `/rp-scope`；用户坚持则先在对话中补齐问题、假设、识别、数据四项 |
| 官方要求 | 目标项目官网 | **模板闸门**：抓取官网，记录字数上限、必备章节、格式、是否计入参考文献、URL 与查阅日期。抓取不到就问用户；仍没有则用默认结构，并在 notes 顶部标注"结构未经官方要求核对" |
| refs.md | `/rp-scope` 产出 | 正文只能引用 refs.md 中已核实的文献 |
| 个人档案 | `workflow/profile.local.md` | 提示用户填写；proposal 中与个人经历相关的内容留占位符 |

模板闸门的依据：结构与项目要求不一致通常意味着整篇重写（chrisblattman/claudeblattman 的 proposal-write 同样把"没有申请模板"设为硬停止）。

## Step 1 — 规划

输出一张规划表给用户确认后再写全文：

1. 一句话主张：本研究回答什么问题、用什么设计、预计贡献是什么（≤ 40 词，英文）
2. 章节 × 字数预算（默认比例，按官方要求调整）：

| 章节 | 比例 |
|---|---|
| Title + Summary | 8% |
| Introduction & Research Question | 15% |
| Literature & Gap | 22% |
| Research Design（假设、实证策略、数据、稳健性） | 30% |
| Contribution & Policy Relevance | 7% |
| Timeline & Risks | 10% |
| Fit with Supervisor/Department | 5% |
| 预留 | 3% |

3. 每节 1–3 个要点 + 对应的 refs.md 条目
4. 如果项目是 paper-based thesis：规划 Paper 1/2/3，Paper 1 是 scope 中的主问题，2/3 是自然延伸（换情境、换机制、换方法），每篇一句话

## Step 2 — 起草

按规划逐节写。写作规则（综合 hanlulong/econ-writing-skill 与 claudeblattman 的 voice rules，加上 `rules.md` 第 2 节）：

- 第一段内给出研究问题；动机只用 1 个具体数字或事实，并附来源
- 贡献写成 2–3 条，每条对应一个文献脉络，格式："Relative to [strand], this project [does what], which allows [testable increment]."
- 实证策略写出估计方程（LaTeX），逐项定义符号；写明核心识别假设、对应检验、标准误聚类层级及理由
- 系数解释用经济量级（如"一个标准差的补贴变化对应价格波动下降 x%"）作为预期结果示例时，明确标注为预期，不写成已知结论
- 风险章节每条风险配一个预案（Plan B 数据、替代识别、缩小范围）
- 与导师的匹配段只写可核实的事实（导师的具体论文、方法、项目），个人动机留 `[USER: …]` 占位符由用户本人写

应删除的写法（出现即改）：

- 开场白式句子："In recent years, … has attracted increasing attention."
- 强度膨胀词：first, novel, groundbreaking, fill the gap（除非有检索范围支撑）
- 没有数字的形容词：significant（非统计意义时）、substantial、crucial
- "not … but …" 式对立论证
- 同长度句子连续堆叠、每段都以总结句结尾的 AI 腔

## Step 3 — 自检

写完后逐项检查，结果写进 `02-notes-v<N>.md`：

1. **字数**：每节实际字数 vs 预算；总字数 vs 上限（注明参考文献是否计入）
2. **主张—证据映射**：列出正文中每一个事实性主张 → 对应的 refs.md 条目或数据来源；无对应的标红
3. **占位符清单**：所有 `[USER: …]`、`[TODO]`、`[UNVERIFIED]`
4. **一致性**：摘要、引言、方法三处的研究问题表述一致；假设编号与方法部分一致
5. **官方要求对照**：逐条对照 Step 0 记录的要求

## Step 4 — 保存

- `applications/<slug>/02-proposal-v<N>.md`（顶部元数据：日期、目标项目、字数、版本、基于哪个 scope）
- `applications/<slug>/02-notes-v<N>.md`
- 需要 LaTeX/PDF 时：`pandoc 02-proposal-vN.md -o proposal.pdf`，或使用 r02b/Latex-PhD_Proposal_Template、hossainlab/research-proposal-template（见 `workflow/github-resources.md`）

完成后提示用户：下一步运行 `/rp-review <slug>`。

## adapt 模式

输入：核心版 proposal + 目标导师近 5 年 3–5 篇论文（按 `rules.md` 核实）+ 项目官方要求。

只改这些部分：

1. 字数与结构 → 对齐该项目要求
2. Fit 章节 → 基于导师论文的具体连接点（方法、数据、问题），个人动机仍由用户写
3. 贡献表述 → 调整强调点以对接导师所在文献脉络，并补引 1–2 篇导师相关论文（已核实）
4. 标题可微调

不改：研究问题、识别策略、数据方案。如果为了匹配导师需要改这三项，停下来告诉用户，这相当于换题，应回到 `/rp-scope`。

输出到 `applications/<项目slug>/02-proposal-v1.md`，notes 中列出与核心版的差异。
