# Horizon

研究计划（research proposal）、研究助理（RA / predoc）与申博的可复用工作流，以 Claude Code skills 的形式组织。

## 内容

```
.claude/skills/
  rp-scope/       /rp-scope      选题、文献定位、新颖性检查、可证伪假设、识别策略、数据可行性
  rp-draft/       /rp-draft      起草核心版 proposal；adapt 模式按项目/导师改编
  rp-review/      /rp-review     三方对抗式审稿 + 引用核查 + 分级修改计划
  phd-outreach/   /phd-outreach  导师长名单、适配度分析、套磁邮件、跟进
  phd-apply/      /phd-apply     选校核实、倒排时间线、SOP/PS、推荐人资料包、面试、周检
  ra-predoc/      /ra-predoc     RA/predoc 岗位搜索、申请材料、coding test、代码样本、入职规范
workflow/
  README.md                 工作流总览与各阶段门槛
  rules.md                  所有 skill 的共同规则
  github-resources.md       GitHub 相关项目索引（55 个仓库，分 8 类）
  profile.template.md       个人档案模板 → 复制为 profile.local.md
  templates/                proposal 骨架、审稿量表、套磁邮件、SOP 结构、导师适配表、追踪表
```

## 快速开始

```bash
cp workflow/profile.template.md workflow/profile.local.md   # 填写个人档案
mkdir -p applications && cp workflow/templates/tracker.csv applications/tracker.csv
claude                                                       # 在本目录启动 Claude Code
```

然后依次运行：

```
/rp-scope <研究方向> --slug <目录名>
/rp-draft <目录名>
/rp-review <目录名>
/phd-outreach <目录名> find
/phd-apply weekly
```

## 隐私

本仓库是 public。`workflow/profile.local.md` 与 `applications/` 已在 `.gitignore` 中排除，只保存在本地。如果把仓库改为 private，并希望在云端会话中也保留这些文件，可删除 `.gitignore` 中对应的两行。
