---
name: phd-apply
description: 申博项目管理：建立选校清单并核实要求与截止日期、倒排时间线、准备 SOP/PS/CV/推荐人资料包/写作样本、面试准备、每周检查进度。当用户说"申博规划""选校""做时间线""写 SOP/PS""准备推荐信材料""模拟面试""这周该做什么"时使用。
argument-hint: [list | timeline | sop <项目slug> | referees | interview <slug> | weekly]
---

# /phd-apply — 申请管理

先读 `workflow/rules.md` 并全程遵守。追踪表见 `workflow/templates/tracker.csv`（首次使用时复制到 `applications/tracker.csv`），SOP 结构见 `workflow/templates/sop-outline.md`。

## list — 选校清单

对每个项目核实并写入 tracker（每项附官网 URL 与查阅日期，**不凭记忆填**）：

- 学位体系与入学时间
- 截止日期（区分：录取截止 / 奖学金截止 / 资助联盟截止，三者常常不同）
- 必交材料：research proposal（字数上限、是否计入参考文献）、PS/SOP、CV、推荐信数量、成绩单、语言成绩、写作样本
- 资助路径与是否需要导师事先同意
- 是否需要先联系导师（导师制 vs 委员会制）

不同体系的一般差异（仅作核查提示，以官网为准）：

| 体系 | 核心材料 | 研究计划 | 资助要点 |
|---|---|---|---|
| 英国 | Research proposal + PS + 推荐信 | 通常需要 | ESRC DTP（苏格兰为 SGSSS）、校级奖学金、CSC；资助截止常早于录取截止 |
| 香港 | Research proposal + PS | 需要 | HKPFS（规则逐年更新，查 RGC 官网）、校级 studentship |
| 欧洲大陆 | 多为申请具体职位或研究生院 | 视项目而定 | 职位多自带资助 |
| 美国经济学 | SOP（研究兴趣）+ 推荐信 + 数学背景 | 一般不要求正式 proposal | 项目整体资助；可参考 PaulTran47/econ-grad-app-deadlines 的截止汇总 |
| 中国大陆申请-考核制 | 研究计划 + 推荐信 + 面试 | 需要 | 以各校招生简章为准 |

## timeline — 倒排时间线

以每个项目最早的相关截止日（通常是奖学金/资助截止）为 T，倒排：

| 时间点 | 任务 |
|---|---|
| T−16 周 | `/rp-scope` 完成；选校清单初版 |
| T−12 周 | proposal v1（`/rp-draft`）；联系推荐人并发资料包 |
| T−10 周 | `/rp-review` 第 1 轮；A 层导师套磁（`/phd-outreach`） |
| T−8 周 | proposal v2；SOP/PS 初稿；CV 定稿 |
| T−6 周 | B 层导师套磁；按导师反馈 adapt proposal |
| T−4 周 | `/rp-review` 第 2 轮；写作样本定稿 |
| T−2 周 | 全部材料定稿；提醒推荐人 |
| T−3 天 | 提交（不压线） |

若今天距 T 已不足 16 周，压缩方案：合并 scope 与 draft，只做 1 轮 review，套磁只做 A 层。把时间线写进 `applications/timeline.md`，逐项有日期。

## sop <项目slug> — SOP / PS

按 `templates/sop-outline.md`：

- 美国经济学风格 SOP 参考 Gentzkow–Shapiro 实验室手册中的比例：个人叙述 <10%，过往经历（含 RA）10–20%，独立研究 20–30%，拟开展的研究 >50%
- 英国 PS 通常更短，重点是：为什么这个项目/导师、已具备的训练、研究计划摘要、职业目标；与 proposal 不重复
- 个人经历与动机段落由用户本人写（`rules.md` 第 3 节）；skill 负责结构、事实核对、删减、与 proposal 的一致性检查
- 输出到 `applications/<项目slug>/docs/sop-v<N>.md`

## referees — 推荐人资料包

为每位推荐人生成 `applications/docs/referee-<代号>.md`（不写真实姓名以外的敏感信息，且目录已 gitignore）：

1. 申请清单：项目、截止日期、提交方式（系统邀请/邮件）
2. 附件：CV、proposal 摘要或 SOP 草稿
3. 3–5 条推荐人亲眼见过的具体事实（课程成绩与排名、论文工作、展示的某项能力），供其参考
4. 提醒节奏：T−14 天、T−7 天、T−2 天各一次简短提醒

不代写推荐信正文。

## interview <slug> — 面试准备

基于 proposal 生成题库并模拟：

- 研究问题：为什么是这个问题？政策或学术意义用一句话怎么说？
- 识别：核心假设是什么？如果前趋势检验不通过怎么办？最强的反对意见是什么？
- 数据：拿不到主数据怎么办？样本量和功效够吗？
- 贡献：和最接近的那篇文献相比，增量是什么？
- 匹配：为什么选这位导师/这个系？你能为组里带来什么？
- 规划：三年计划？第一年做什么？
- 反问：准备 5 个问题（组会、合作方式、资助、毕业去向、训练课程）

模拟模式：一次问一个问题，用户回答后给出 (1) 回答是否直接回答了问题 (2) 缺少的证据或数字 (3) 一个更短的改写版本。

## weekly — 每周检查

读 `applications/tracker.csv` 与 `applications/timeline.md`，输出：

1. 本周到期任务
2. 已逾期任务
3. 发出超过 10 个工作日未回复的套磁 → 提示 `/phd-outreach <slug> followup`
4. 推荐人待提醒
5. 截止日期查阅日期超过 30 天的项目 → 提示重新核实

输出控制在 15 行以内，按紧急程度排序。
