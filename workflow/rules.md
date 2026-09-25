# 共享规则（所有 skill 必须遵守）

本文件是 `/rp-scope` `/rp-draft` `/rp-review` `/phd-outreach` `/phd-apply` `/ra-predoc` 的共同约束。skill 与本文件冲突时，以本文件为准。

## 1. 证据与引用

- **任何文献都必须核实存在**：用 WebFetch / WebSearch 打开 DOI、期刊页、NBER、RePEc/IDEAS、SSRN 或 arXiv 页面，确认作者、年份、标题一致后才能引用。
- 每条核实过的文献记入该申请目录下的 `refs.md`，格式：
  `| 作者 (年份) | 标题 | 链接/DOI | 核实日期 · 等级(page/search) | 在本文中的用途 |`
- 无法核实 → 标 `[UNVERIFIED]`，**不得进入定稿**。不凭记忆补全作者或年份。
- 不编造：数据数值、教授论文、招生信息、截止日期、字数要求、资助规则。凡是院校要求，一律以官网为准，并记录 URL 与查阅日期。
- 无需 API key 的检索入口（优先用这些，结果可复现）：
  - OpenAlex：`https://api.openalex.org/works?search=<关键词>&per_page=10`
  - Semantic Scholar：`https://api.semanticscholar.org/graph/v1/paper/search?query=<关键词>&fields=title,year,authors,venue,externalIds,citationCount&limit=10`
  - Crossref：`https://api.crossref.org/works?query=<关键词>&rows=10`
  - 经济学工作论文：NBER、IDEAS/RePEc、SSRN 的站内搜索页
- 记录检索式：每次文献检索把实际使用的查询词和数据源写进产出文件，便于复查"是否漏检"。
- **网络受限时的降级方案**：云端会话的网络策略可能屏蔽上述站点（WebFetch 返回 `EGRESS_BLOCKED`）。此时：
  1. 改用 WebSearch 检索（可用 `allowed_domains` 限定到 nber.org、ideas.repec.org、ssrn.com、doi.org、期刊出版商域名）
  2. `refs.md` 的"核实日期"列后注明核实等级：`page`（打开过原始页面）或 `search`（仅在检索结果中匹配到标题、作者、年份）
  3. 支撑核心论证的文献应达到 `page` 等级；只有 `search` 等级的，在 notes 中列出，提醒用户在本地或放开网络后复核
  4. 告诉用户被屏蔽的域名，建议在云环境设置的 Network access 中加入允许列表：`api.openalex.org`、`api.semanticscholar.org`、`api.crossref.org`、`doi.org`、`www.nber.org`、`ideas.repec.org`、`papers.ssrn.com`

## 2. 表述

- **假设必须可证伪**：每个假设写明预测方向，以及"若观察到 X，则该假设被拒绝"。
- **不使用强度膨胀修辞**：避免"首次""填补空白""革命性""唯一""前所未有"等。确需声称新颖性时，写明检索范围（数据源、查询词、时间），例如："在 OpenAlex 与 NBER 以 … 检索，未找到使用 … 数据识别 … 的研究"。
- **不使用"不是…而是…"式论证**：直接陈述主张，再给证据。
- 数字优先于形容词；主动语态；每段首句是主题句；删掉开场白式句子。
- 给用户做解释时优先朴素解释；涉及动机、心理层面的推测必须附带可证伪条件。

## 3. 作者性与学术诚信

- 以下内容由 AI 提供事实与批注，**最终措辞由用户本人写**：研究动机中的个人经历、套磁邮件里"为什么是这位导师"的段落、SOP/PS 的个人叙述。
- 遵守目标院校关于生成式 AI 的政策；若申请要求声明 AI 使用情况，如实声明。
- 不代替推荐人写推荐信正文；可以帮用户准备给推荐人的资料包。

## 4. 隐私

- 仓库是 public。个人档案放 `workflow/profile.local.md`，具体申请产出放 `applications/`，两者已在 `.gitignore` 中排除。
- 不把 GPA、推荐人姓名、导师往来邮件等写进被 git 跟踪的文件。

## 5. 文件约定

```
workflow/profile.local.md          个人档案（从 profile.template.md 复制）
applications/tracker.csv           总追踪表（从 templates/tracker.csv 复制）
applications/<slug>/               一个研究题目或一个项目一个目录
  01-scope.md                      /rp-scope 产出
  refs.md                          核实过的文献
  02-proposal-v<N>.md              /rp-draft 产出
  02-notes-v<N>.md                 字数、占位符、未核实项
  03-review-v<N>.md                /rp-review 产出
  outreach/<导师-slug>.md          /phd-outreach 产出
  docs/                            SOP、CV、推荐人资料包等
```

- `<slug>` 用小写短横线：题目级如 `agri-subsidy-price-volatility`，项目级如 `2027-glasgow-econ-phd`。
- 同一题目投多个项目时：题目级目录放核心版 proposal，项目级目录放 `/rp-draft adapt` 生成的改编版。
- 新版本另存为 `v<N+1>`，不覆盖旧版。

## 6. 修改文件后的汇报

每次新建或修改文件后，在回复末尾按四项汇报：

1. **行数**：每个文件的行数变化（前→后）。新建文件要说明为什么不并入已有文件
2. **删除**：删了什么，没有就写"无"。校正（行号、引用信息等）单独列出
3. **重复**：与已有内容重复的行数，以及是否标了出处。不复制整段原文
4. **只留三行**：如果整份产出只能保留三行，保留哪三行

## 7. 语言

- 与用户对话用中文。
- proposal、套磁邮件、SOP、cover letter 默认英文；目标为中国大陆项目时用中文。
