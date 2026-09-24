---
name: phd-outreach
description: 申博套磁全流程：按研究题目筛选潜在导师、做导师适配度分析、准备套磁邮件骨架、安排跟进并记录到追踪表。当用户说"找导师""套磁""给教授写邮件""这个老师适不适合我""跟进一下没回的老师"时使用。
argument-hint: <slug> [find | fit <导师名> | email <导师名> | followup]
---

# /phd-outreach — 导师筛选与套磁

先读 `workflow/rules.md` 并全程遵守。适配表见 `workflow/templates/professor-fit.md`，邮件模板见 `workflow/templates/cold-email.md`。

子命令：

| 子命令 | 作用 | 产出 |
|---|---|---|
| `find` | 按题目生成导师长名单并分层 | `applications/<slug>/outreach/longlist.md` |
| `fit <导师>` | 单个导师的适配度分析 | `applications/<slug>/outreach/<导师-slug>.md` |
| `email <导师>` | 套磁邮件骨架 + 批注 | 追加到同一文件 |
| `followup` | 读追踪表，列出该跟进/该换人的导师 | 对话输出 + 更新 tracker |

## find — 长名单

1. 从 `01-scope.md` 提取 3–5 组关键词（主题 × 方法 × 情境）
2. 渠道（每个候选注明来源）：
   - OpenAlex 作者检索：`https://api.openalex.org/works?search=<关键词>&filter=from_publication_date:<近5年>&per_page=25`，统计高频作者及其机构
   - 目标院系的教师页面、研究中心页面
   - 英国：FindAPhD、jobs.ac.uk 上的项目/岗位；苏格兰社会科学类可查 SGSSS（ESRC 在苏格兰的博士培养联盟）的导师与路径信息
   - 目标院校近年博士论文的致谢/导师信息
3. 初筛条件：近 5 年有相关一作/通讯论文；仍在职；主页未写"不招生"
4. 分层：
   - **A**：主题与方法均匹配，且有招生信号（主页写明招生、在读学生、在研资助项目）
   - **B**：主题或方法之一匹配
   - **C**：仅主题相近
5. 同一院系只能同时联系 1 位导师，长名单中按院系分组标注

## fit — 适配度分析

按 `templates/professor-fit.md` 填写。要求：

- 近 5 年论文取 3–5 篇，逐篇核实（OpenAlex 作者 ID → `https://api.openalex.org/works?filter=author.id:<ID>&sort=publication_date:desc&per_page=10`），每篇写：问题、方法、数据、与我的题目的具体连接点
- 招生信号只记录可核实的事实（主页原文、资助项目页面、在读学生列表），附 URL
- 连接点至少 1 个具体到"他/她的论文 X 的 Y 部分 → 我的题目的 Z"
- 结论：适配分（1–5）+ 建议（联系 / 暂缓 / 放弃）+ 理由

## email — 套磁邮件

结构（参考 mak-raiaan/ColdEmailPhDMSc 与 zhanglj37/Tutorial-on-PhD-Application，详见模板）：

1. 标题：`Prospective PhD applicant (<入学年份>) – <研究主题>`
2. 第 1 段 自我介绍（40–50 词）：当前学位与院校、毕业论文主题与方法
3. 第 2 段 为什么联系您（≤120 词）：**由用户本人写**。skill 只提供：fit 分析中的 2–3 个可核实连接点、一个可以提出的具体问题、对用户初稿的批注
4. 第 3 段 我计划研究什么（60–80 词）：一句话问题 + 设计 + 数据；附 2 页 proposal 摘要
5. 第 4 段 请求（1–2 句）：是否招收该年入学的博士生；本题目是否可能在其指导范围内；如适用，询问是否愿意支持某一资助申请（如 DTP/奖学金）
6. 落款：姓名、当前单位、CV/主页链接

批注用户的第 2 段时检查：是否提到具体论文且信息准确；是否有可以原样发给任何导师的句子（有则标出）；是否有强度膨胀的恭维。

发送规则：

- 附件不超过 2 个 PDF（CV + proposal 摘要），文件名含姓名
- 用毕业后仍长期可用的邮箱（学校邮箱可能在硕士毕业后停用）
- 不群发、不抄送多位导师

## followup — 跟进

读 `applications/tracker.csv`：

- 发出后 10 个工作日无回复 → 列入"可跟进"，给出一段 2–3 句的跟进邮件（重述一句问题 + 是否招生）
- 跟进后再过 10 个工作日无回复 → 标记 `no_reply`，允许联系同院系下一位导师（与 zhanglj37 教程中"两周无回复再联系其他老师"的建议一致）
- 收到回复 → 按回复类型给出下一步：
  - 积极（愿意聊/鼓励申请）→ 准备 20 分钟通话的问题清单（研究设计、资助路径、组内合作方式），并提示运行 `/rp-draft <slug> adapt`
  - 需要更多材料 → 列出需补充的材料
  - 不招生 → 礼貌致谢，询问是否可推荐同事；更新追踪表

每次操作后更新 tracker 中该导师的 `contact_status / contacted_on / follow_up_on / reply` 字段。
