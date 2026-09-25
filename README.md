# Horizon

研究计划（research proposal）、研究助理（RA / predoc）与申博的可复用工作流，以 Claude Code skills 的形式组织。

## 内容

```
.claude/skills/
  rp-improve/     /rp-improve    【主入口】优化/补全已有 proposal：诊断断链与缺节 → 填充 → 优化；可逐节、问答式、按审稿意见执行
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
  templates/                语料模板、proposal 骨架、审稿量表、套磁邮件、SOP 结构、导师适配表、追踪表
```

## 快速开始

```bash
cp workflow/profile.template.md workflow/profile.local.md   # 填写个人档案
mkdir -p applications && cp workflow/templates/tracker.csv applications/tracker.csv
claude                                                       # 在本目录启动 Claude Code
```

已有 proposal（主路径）：

```
/rp-improve <proposal 路径>                     # 诊断 + 填充 + 优化；加 --section 或 --interview 可一节一节来
/rp-review <目录名>                             # 三方审稿，输出修改计划
/rp-improve <目录名> --review 03-review-v1.md   # 执行修改计划；与审稿循环，最多 3 轮
```

从零开始：`/rp-scope` → `/rp-draft` → `/rp-review`。之后的步骤：`/phd-outreach <目录名> find`、`/phd-apply weekly`。

## 隐私

本仓库是 public。`workflow/profile.local.md` 与 `applications/` 已在 `.gitignore` 中排除，只保存在本地。如果把仓库改为 private，并希望在云端会话中也保留这些文件，可删除 `.gitignore` 中对应的两行。
