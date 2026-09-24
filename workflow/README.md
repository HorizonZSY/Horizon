# 研究计划与申博工作流

## 总览

```
                  ┌──────────────────────── /phd-apply（贯穿全程）────────────────────────┐
                  │  list 选校核实 → timeline 倒排 → sop / referees → interview → weekly │
                  └──────────────────────────────────────────────────────────────────────┘

profile.local.md
      │
      ▼
 /rp-scope ──门槛──► /rp-draft ──► /rp-review ──(未达标, ≤3 轮)──┐
 选题/文献/新颖性      起草核心版       三方审稿+引用核查          │
 假设/识别/数据          ▲                                      │
                        └──────────── 修改计划 MUST/SHOULD ◄────┘
                                          │ 达标
                                          ▼
                              /phd-outreach  find → fit → email → followup
                                          │ 导师积极回复
                                          ▼
                              /rp-draft adapt（按项目/导师改编）→ /rp-review → 提交

 并行路线：/ra-predoc  search → apply → codetest / codesample → onboard
          （RA 经历 → 更强的推荐信与研究训练 → 回到申博主线）
```

## 各阶段的输入、产出与门槛

| 阶段 | 命令 | 输入 | 产出 | 进入下一步的门槛 |
|---|---|---|---|---|
| 1. 选题 | `/rp-scope <方向> --slug <slug>` | 种子想法、档案 | `01-scope.md`、`refs.md` | ≥8 篇已核实文献；无 SAME；假设有拒绝条件；识别假设 + 检验；数据获取方式已核实 |
| 2. 起草 | `/rp-draft <slug>` | scope、官方要求 | `02-proposal-v1.md`、`02-notes-v1.md` | 字数内；主张—证据映射无空缺；占位符清单已交给用户 |
| 3. 审稿 | `/rp-review <slug>` | proposal、refs | `03-review-v1.md` | 无 FATAL；MAJOR ≤ 2；总分 ≥ 75（最多 3 轮） |
| 4. 套磁 | `/phd-outreach <slug> find` 等 | 定稿 proposal、scope | `outreach/*.md`、tracker 更新 | A 层导师已联系；回复已分类处理 |
| 5. 改编 | `/rp-draft <slug> adapt <项目>` | 核心版、导师论文、官方要求 | 项目级 proposal | 只改结构/匹配/贡献表述，不改问题与设计 |
| 6. 申请 | `/phd-apply list / timeline / sop / referees / interview` | tracker、档案 | 时间线、文书、推荐人资料包、面试题库 | 所有材料在 T−3 天前定稿 |
| 周检 | `/phd-apply weekly` | tracker、timeline | 本周待办（≤15 行） | — |

## 首次使用

1. `cp workflow/profile.template.md workflow/profile.local.md`，填写
2. `mkdir -p applications && cp workflow/templates/tracker.csv applications/tracker.csv`
3. 在本仓库目录启动 Claude Code，运行 `/rp-scope <你的研究方向> --slug <目录名>`

## 共同规则

见 `rules.md`。要点：

- 文献必须核实存在才能引用，无法核实标 `[UNVERIFIED]` 且不进定稿
- 截止日期、字数、资助规则以官网为准，记录 URL 与查阅日期
- 假设写明拒绝条件；不用强度膨胀修辞；不用"不是…而是…"式论证
- 个人动机、"为什么是这位导师"段落由用户本人写
- 个人信息只放 `profile.local.md` 与 `applications/`（已 gitignore，仓库是 public）

## 这套流程借鉴了哪些 GitHub 项目

| 设计 | 来源 |
|---|---|
| 模板闸门：没有官方要求就不按默认结构硬写 | chrisblattman/claudeblattman（proposal-write） |
| 审稿意见分 MUST / SHOULD / DISAGREE | chrisblattman/claudeblattman |
| 审稿人只评不改、作者不自评 | hugosantanna/clo-author |
| 三位模拟审稿人 + 100 分量表 | hanlulong/econ-writing-skill（review-checklist） |
| 新颖性判定：与最相似论文逐篇比对 | NoviScl/AI-Researcher |
| 引用完整性闸门 | Imbad0202/academic-research-skills |
| 套磁邮件结构与字数 | mak-raiaan/ColdEmailPhDMSc、zhanglj37/Tutorial-on-PhD-Application |
| SOP 比例 | gentzkow/lab-manual-archive（PhD Applications） |
| RA 工作规范、复现包结构 | gslab-econ/ra-manual、kylebarron/ra-guide |

完整清单见 `github-resources.md`。
