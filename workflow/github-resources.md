# GitHub 资源索引：Research Proposal / 研究助理 / 申博

检索日期：2026-09-24。方法：以 `github.com` 为限定域的网页检索（约 16 组查询），对其中 14 个项目打开页面核对了内容。

- ★ 数为打开页面时显示的数字，只列出实际打开过的项目；其余项目只根据检索摘要收录，使用前请自行打开确认。
- 本索引并未穷尽 GitHub 上的同类项目，只保留与"经济学 + proposal 驱动的申博 + RA"最相关的部分，共 55 个仓库。

## 0. 阶段 × 本仓库 skill × 可叠加的外部项目

| 阶段 | 本仓库 skill | 可叠加的外部项目 |
|---|---|---|
| 选题与新颖性 | `/rp-scope` | NoviScl/AI-Researcher（新颖性过滤思路）、voidful/academic-skills 的 idea-generation、zbsaygin/econ-skills 的 lit-review |
| 文献检索 | `/rp-scope` Step 2 | OpenAlex / Semantic Scholar MCP、zotero-mcp、Imbad0202/academic-research-skills 的 deep-research |
| 起草 proposal | `/rp-draft` | hanlulong/econ-writing-skill、chrisblattman/claudeblattman 的 proposal-write |
| 审稿 | `/rp-review` | hugosantanna/clo-author 的 `/review --peer`、econ-writing-skill 的 review-checklist |
| 套磁 | `/phd-outreach` | mak-raiaan/ColdEmailPhDMSc、voidful/academic-skills 的 professor-fit-analyser |
| 申请管理 | `/phd-apply` | zhanglj37/Tutorial-on-PhD-Application、gentzkow 实验室手册、glwjr/dossier |
| RA / predoc | `/ra-predoc` | findmypredoc、kylebarron/ra-guide、gslab RA 手册 |

---

## 1. Research Proposal / 基金申请写作

| 项目 | ★ | 许可 | 内容 | 用法 |
|---|---|---|---|---|
| [chrisblattman/claudeblattman](https://github.com/chrisblattman/claudeblattman) | 460 | MIT | 发展经济学家 Chris Blattman 的 AI 工作流；[proposal-write skill](https://github.com/chrisblattman/claudeblattman/blob/main/skills/proposal-write.md) 为 10 步流程：输入清单 → 自动收集上下文 → 资助方画像 → **模板闸门**（没有申请模板就停止）→ 规划 → 起草 → 保存 → 更新资助方记录；重投时把审稿意见分为 MUST / SHOULD / DISAGREE | 本仓库 `/rp-draft` 的模板闸门、`/rp-review` 的修改计划分类借鉴于此 |
| [wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep) | 16.6k | — | [grant-proposal skill](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep/blob/main/skills/grant-proposal/SKILL.md)：叙事弧 Problem → Why Now → What We Propose → Why It Will Work → What We Will Deliver；支持 NSFC、ERC、NSF 等；外部审稿人按资助机构标准 1–5 打分，最多 2 轮修改 | 参考其叙事弧与"主张—证据矩阵" |
| [borghei/Claude-Skills — research/grants](https://github.com/borghei/Claude-Skills/blob/main/research/grants/SKILL.md) | — | — | 基金申请 skill，含资助方匹配打分、结构校验、预算合理性检查脚本 | 投奖学金/基金时参考 |
| [K-Dense-AI/claude-scientific-writer](https://github.com/K-Dense-AI/claude-scientific-writer) | — | — | 通用科研写作 skill 集，含 research-grants | 备选 |
| [eseckel/ai-for-grant-writing](https://github.com/eseckel/ai-for-grant-writing) | — | — | 用 LLM 写基金申请的资源与提示词清单 | 查找提示词思路 |
| [r02b/Latex-PhD_Proposal_Template](https://github.com/r02b/Latex-PhD_Proposal_Template) | — | — | PhD proposal LaTeX 模板，可上传 Overleaf | 需要 PDF 排版时 |
| [hossainlab/research-proposal-template](https://github.com/hossainlab/research-proposal-template) | — | — | 分章节文件的 proposal LaTeX 模板 | 同上 |
| [quxiaofeng/polyu-comp-research-proposal-template](https://github.com/quxiaofeng/polyu-comp-research-proposal-template) | — | — | 按香港理工大学计算机系要求的非官方 proposal 模板 | 申香港时对照结构 |

## 2. 经济学研究与写作的 Claude Code Skills

| 项目 | ★ | 许可 | 内容 | 用法 |
|---|---|---|---|---|
| [hanlulong/econ-writing-skill](https://github.com/hanlulong/econ-writing-skill) | 620 | MIT | 综合 Cochrane、McCloskey、Shapiro、Head、Bellemare 等 50+ 份写作指南；模块：SKILL.md（各章节写法）、identification-strategies.md（13+ 种识别策略的写法）、review-checklist.md（3 位模拟审稿人 + 100 分量表）、specialized-tasks.md（含基金申请） | 与 `/rp-draft` 叠加使用；安装方式见其 INSTALL.md |
| [hugosantanna/clo-author](https://github.com/hugosantanna/clo-author) | 257 | MIT | 实证经济学研究脚手架，18 个 agent 以 worker–critic 配对互审（critic 不能改文件，creator 不能自评）；命令 `/discover` `/strategize` `/analyze` `/write` `/review --peer [journal]` | 本仓库 `/rp-review` 的角色分离借鉴于此；进入 PhD 后做论文可整体使用 |
| [Imbad0202/academic-research-skills](https://github.com/Imbad0202/academic-research-skills) | 49.4k | CC BY-NC 4.0 | research → write → review → revise → finalize 流水线；deep-research 含 Socratic 引导模式与 PRISMA 系统综述；引用完整性检查（Semantic Scholar 核验、阶段性闸门） | 文献综述与引用核验；非商业许可 |
| [zbsaygin/econ-skills](https://github.com/zbsaygin/econ-skills) | 7 | MIT | read-paper、lit-review（含对抗式新颖性评估）、audit-econ（数学/计量/代码审计）、notation-clean、latex-doc、latex-slide、graph | 需要替换其中的本地路径占位符；假设使用 Zotero + Better BibTeX |
| [franklee16/academic-research-skills](https://github.com/franklee16/academic-research-skills) | — | — | 面向经济、金融、社会科学的 skill 集，按研究生命周期分类 | 备选 |
| [amatray/claude-skills-public](https://github.com/amatray/claude-skills-public) | — | — | 学术经济学家公开的 Claude Code skills | 备选 |
| [meleantonio/awesome-econ-ai-stuff](https://github.com/meleantonio/awesome-econ-ai-stuff) | — | — | 经济学家用 AI skill 索引 | 找更多 skill |
| [O0000-code/awesome-academic-skills](https://github.com/O0000-code/awesome-academic-skills) | — | CC0 | 按研究生命周期组织的学术 skill 索引，标注许可与运行方式 | 找更多 skill |

## 3. 选题与新颖性检查

| 项目 | ★ | 许可 | 内容 |
|---|---|---|---|
| [NoviScl/AI-Researcher](https://github.com/NoviScl/AI-Researcher) | 407 | — | 六个模块：相关文献检索（Semantic Scholar）→ 基于文献生成想法 → 去重（嵌入相似度 0.8 阈值）→ 展开为项目提案 → LLM 排序 → 新颖性/可行性过滤（与检索到的论文逐一比对）。本仓库 `/rp-scope` Step 3 的 SAME / OVERLAP / DIFFERENT 判定借鉴于此 |
| [voidful/academic-skills](https://github.com/voidful/academic-skills) | 129 | MIT | 7 个 skill：paper-reading、idea-generation（发散 → 检索 → 收敛）、experiment-design、proof-writer、paper-writing、paper-review、**professor-fit-analyser**（导师适配度与申请策略，繁体中文） |
| [Paureel/LLM-SCI-GEN](https://github.com/Paureel/LLM-SCI-GEN) | — | — | 用 LLM 生成科学假设的论文清单 |

## 4. AI 研究助理工具（文献检索、阅读、管理）

| 项目 | 内容 |
|---|---|
| [brycewang-stanford/lit-review-agent-tools](https://github.com/brycewang-stanford/lit-review-agent-tools)（★26，CC0） | 70+ 个文献综述 AI 工具索引，分 11 类：一体化 agent/skill、深度研究、自动科研、论文问答、系统综述筛选、MCP 服务器、文献管理、PDF 转结构化数据、引文图谱、写作与审稿、awesome 列表 |
| [ourresearch/openalex-mcp-server](https://github.com/ourresearch/openalex-mcp-server) | OpenAlex 官方 MCP 服务器：文献、引用、作者、机构检索 |
| [xiuyechen/semantic-scholar-mcp](https://github.com/xiuyechen/semantic-scholar-mcp) / [JackKuo666/semanticscholar-MCP-Server](https://github.com/jackkuo666/semanticscholar-mcp-server) | Semantic Scholar MCP：检索论文、引用关系、作者 |
| [54yyyu/zotero-mcp](https://github.com/54yyyu/zotero-mcp) | 把 Zotero 文献库接入 Claude，做语义检索 |
| [yilewang/llm-for-zotero](https://github.com/yilewang/llm-for-zotero) | Zotero 文献库上的研究 agent |
| [blazickjp/arxiv-mcp-server](https://github.com/blazickjp/arxiv-mcp-server) | arXiv 检索与分析 |
| [Future-House/paper-qa](https://github.com/Future-House/paper-qa) | 对论文集做带引用的问答 |
| [stanford-oval/storm](https://github.com/stanford-oval/storm) | 基于检索生成带引用的长综述 |
| [opendatalab/MinerU](https://github.com/opendatalab/MinerU) | PDF 转 Markdown/JSON，便于喂给 LLM |
| [J535D165/pyalex](https://github.com/J535D165/pyalex) | OpenAlex 的 Python 客户端 |

说明：本仓库的 skill 默认直接调用 OpenAlex / Semantic Scholar / Crossref 的公开 API（见 `rules.md`），不依赖以上 MCP。装了 MCP 会让检索更顺手。

## 5. 申博指南

| 项目 | ★ | 内容 |
|---|---|---|
| [zhanglj37/Tutorial-on-PhD-Application](https://github.com/zhanglj37/Tutorial-on-PhD-Application) | 1.1k | 中文。作者为 2022 Fall 量化心理/教育测量方向申请者。覆盖材料、时间线、选校、套磁、面试、资助与录取后。要点：CV（研究经历）+ 推荐信 >> GPA > GRE > TOEFL；同一项目一次只联系一位老师，两周未回复再联系其他老师 |
| [binhu02/Collection-of-advice-for-PhD-application](https://github.com/binhu02/Collection-of-advice-for-PhD-application) | — | 带中文导读的申请攻略合集 |
| [gentzkow/lab-manual-archive — PhD Applications](https://github.com/gentzkow/lab-manual-archive/wiki/PhD-Applications) | — | 经济学。个人陈述比例：个人叙述 <10%、过往经历 10–20%、独立研究 20–30%、拟开展研究 >50%；推荐信需能证明独立研究能力；重视证明类数学课程 |
| [PaulTran47/econ-grad-app-deadlines](https://github.com/PaulTran47/econ-grad-app-deadlines) | — | 251 个经济学 PhD 项目的截止日期（GitHub Pages）；使用前与官网核对 |
| [pliang279/awesome-phd-advice](https://github.com/pliang279/awesome-phd-advice) | — | 申请与读博建议合集，含 SOP 样例库链接 |
| [shaily99/advice](https://github.com/shaily99/advice) | — | 申请、研究、读博相关建议链接 |
| [DolbyUUU/awesome-tips-for-economic-phd](https://github.com/DolbyUUU/awesome-tips-for-economic-phd) | 9 | 经济学期刊编辑讲座、写作、审稿报告、求职资源；偏读博阶段 |
| [antontarasenko/awesome-economics](https://github.com/antontarasenko/awesome-economics) | — | 经济学资源总表 |
| [Swapnil-Gandhi/SoP-Template](https://github.com/Swapnil-Gandhi/SoP-Template) / [vsitzmann/phd-master-application-docs](https://github.com/vsitzmann/phd-master-application-docs) / [Dieselmarble/PhD-Application](https://github.com/Dieselmarble/PhD-Application) | — | SOP 模板与真实申请材料样例（多为 CS 方向，看结构不看内容） |
| [GuangLun2000/summer-research-app](https://github.com/GuangLun2000/summer-research-app) | — | 海外暑研申请指南 |

## 6. 套磁与申请追踪

| 项目 | ★ | 内容 |
|---|---|---|
| [mak-raiaan/ColdEmailPhDMSc](https://github.com/mak-raiaan/ColdEmailPhDMSc) | 126 | 套磁邮件结构：标题写明申请身份 + 入学学期 + 研究方向；自我介绍 40–50 词；研究兴趣段 ≤120 词（引用导师的具体论文，建议本人撰写）；自己的研究 80–100 词；附 CV 与研究陈述 |
| [glwjr/dossier](https://github.com/glwjr/dossier) | — | 全栈申请追踪：项目、要求、截止、推荐人、潜在导师、文书草稿，每周邮件提醒 |
| [shoaibshaikwrk/phd-tracker](https://github.com/shoaibshaikwrk/phd-tracker) | — | 追踪表，含带资助的 PhD 职位、导师、美欧英院系列表 |
| [kishormorol/gradtracker](https://github.com/kishormorol/gradtracker) | — | 社区维护的美加 Fall 2027 申请追踪（导师招生信息、申请费减免） |
| [danialebrat/ProfMailer](https://github.com/danialebrat/ProfMailer) | — | 批量给教授发邮件的桌面程序。**不建议使用**：群发与套磁的个性化要求相冲突，这里只作为反例收录 |

## 7. 研究助理（RA）/ Predoc

| 项目 | ★ | 内容 |
|---|---|---|
| [ericleonen/findmypredoc](https://github.com/ericleonen/findmypredoc) | — | 聚合 NBER、EconJobMarket、PREDOC.org 的 predoc 岗位，用 Anthropic API 抽取岗位信息 |
| [ruanyn2025/predoc_watcher_app](https://github.com/ruanyn2025/predoc_watcher_app) | — | 桌面程序：检索三个 predoc/RA 招聘板，收藏、提醒、追踪申请 |
| [xmwu0124/predocker](https://github.com/xmwu0124/predocker) | — | predoc 岗位追踪 + CV 匹配 + 截止提醒 |
| [gslab-econ/ra-manual](https://github.com/gslab-econ/ra-manual)（现为 gentzkow/lab-manual-archive） | — | Gentzkow–Shapiro 实验室 RA 手册：项目组织、代码与数据规范 |
| [kylebarron/ra-guide](https://github.com/kylebarron/ra-guide) | — | 经济学新 RA 技术指南 |
| [Alalalalaki/Guide2EconRA](https://github.com/Alalalalaki/Guide2EconRA) | 232 | Python/R/Julia/Stata、Git、LaTeX、计算经济学、因果推断课程索引；**不含**找岗位或申请材料内容 |

## 8. 计量复现（用于写作样本 / 代码样本）

| 项目 | 内容 |
|---|---|
| [vikjam/mostly-harmless-replication](https://github.com/vikjam/mostly-harmless-replication) | 用 Stata、R、Python、Julia 复现《Mostly Harmless Econometrics》的表图 |
| [rawatpranjal/econometrics-in-python](https://github.com/rawatpranjal/econometrics-in-python) | Python 计量包索引 |

---

## 外部 skill 安装速查（均来自各项目 README，安装前请阅读原文）

```text
# Imbad0202/academic-research-skills（Claude Code 插件市场）
/plugin marketplace add Imbad0202/academic-research-skills
/plugin install academic-research-skills

# chrisblattman/claudeblattman
/plugin marketplace add chrisblattman/claudeblattman
/plugin install starter-kit@claudeblattman

# hanlulong/econ-writing-skill：在 Claude Code 中让它按
# https://github.com/hanlulong/econ-writing-skill/blob/main/INSTALL.md 安装

# zbsaygin/econ-skills：克隆到别处后把需要的单个 skill 软链接进 ~/.claude/skills/
# （不要直接克隆到 ~/.claude/skills，会与已有 skill 冲突）

# hugosantanna/clo-author：作为项目脚手架 fork 后在其目录中启动 claude
```
