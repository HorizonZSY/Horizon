---
name: ra-predoc
description: 经济学研究助理（RA）/ predoc 岗位的搜索、筛选、申请材料（CV、cover letter、写作样本、代码样本）与 coding test 准备；入职后的 RA 工作规范。当用户说"找 RA""predoc""研究助理岗位""准备 coding test""做个代码样本""RA 怎么干活"时使用。
argument-hint: [search | apply <岗位> | codetest | codesample | onboard]
---

# /ra-predoc — RA / Predoc 路线

先读 `workflow/rules.md` 并全程遵守。岗位记录使用 `applications/tracker.csv`（`type` 列填 `RA`）。

## search — 岗位搜索与筛选

渠道（每个岗位注明来源与发布日期）：

- 美国及国际 predoc：predoc.org、NBER RA 招聘列表、EconJobMarket、AEA JOE
- 英国：jobs.ac.uk（检索 research assistant / research officer + economics）、各校经济系与研究中心的招聘页、政策研究机构的招聘页
- 聚合工具（可选）：ericleonen/findmypredoc、ruanyn2025/predoc_watcher_app、xmwu0124/predocker（见 `workflow/github-resources.md`）

筛选表（写入 `applications/ra/shortlist.md`）：

| 岗位 | 机构/PI | 研究领域 | 技能要求 | 期限 | 地点与签证 | 截止 | 匹配分 | 来源 |
|---|---|---|---|---|---|---|---|---|

匹配分依据：研究领域与申博方向的重合度（RA 经历主要价值在于推荐信与研究训练）、技能要求与现有技能的差距、PI 的推荐信分量、签证可行性（以官方签证规定为准，不凭记忆判断）。

## apply <岗位> — 申请材料

1. **CV**：技能栏每项配证据（如 "Stata — staggered DID replication, see github.com/…"）；研究经历写问题与方法，不写空泛职责
2. **Cover letter**（≤ 1 页）：
   - 第 1 段：申请哪个岗位；一句话说明与岗位研究方向的连接
   - 第 2 段：与岗位要求逐项对应的证据（技能 → 项目 → 可查看的产出）
   - 第 3 段：研究兴趣与长期计划（申博）如何与该岗位衔接
   - 第 4 段：可入职时间、签证状态
   与 PI 研究的连接点只写可核实事实；个人动机由用户写
3. **写作样本**：硕士/本科论文的精简版（通常 10–20 页，以岗位要求为准）
4. **代码样本**：见 `codesample`

输出到 `applications/ra/<岗位-slug>/`，并更新 tracker。

## codetest — coding test 准备

常见形式：限时笔试（数小时）或 take-home（数天），以岗位说明为准。练习清单（Stata / R / Python 任选岗位要求的语言，每题计时）：

1. 读入多个原始文件，统一变量名与类型，处理缺失值编码
2. merge（1:1、m:1）并检查匹配率，解释未匹配样本
3. reshape 长宽转换；按组生成滞后/差分/增长率
4. 描述统计表并导出为 LaTeX/Excel
5. 带固定效应的回归，按合理层级聚类标准误，解释系数的经济量级
6. 事件研究图（含置信区间）
7. 交错 DID：用一种异质稳健估计量复现，并与 TWFE 对比
8. 把以上整理为一键运行的项目（master 脚本 + 相对路径 + README）

每道题做完后：检查代码能否在全新环境从原始数据一键复现；写 3 句话说明结果。

## codesample — 代码样本

把一个已有研究（如毕业论文的 DID 分析）整理成公开的复现包，结构参考 Gentzkow–Shapiro 的 "Code and Data for the Social Sciences" 与 gslab RA 手册：

```
replication/
  README.md          问题、数据来源与获取方式、运行步骤、软件版本
  data/raw/          只读；受限数据不入库，README 说明获取方式
  data/derived/
  code/01_clean.*    一个脚本只做一件事
  code/02_analysis.*
  code/03_figures.*
  output/tables/ output/figures/
  run_all.*          一键运行
```

检查：无绝对路径；随机种子固定；原始数据未被覆盖；每张表图可追溯到生成它的脚本。

## onboard — 入职后的 RA 工作规范

依据 gslab-econ/ra-manual（现为 gentzkow/lab-manual-archive）与 kylebarron/ra-guide：

- 版本控制：所有代码进 git，提交信息写清改了什么
- 目录：原始数据只读，派生数据可由代码重新生成
- 自动化：结果由脚本生成，不手工改表
- 记录：每周给 PI 一页进展（完成 / 发现 / 问题 / 下周计划），决策与假设写入项目日志
- 学习资源：Alalalalaki/Guide2EconRA（编程与计量课程索引）

同时维护一份"推荐信素材"清单：自己独立完成的分析、提出并被采纳的建议、PI 的正面反馈。申博时交给 PI 作为推荐信参考（见 `/phd-apply referees`）。
