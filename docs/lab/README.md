# Diffusion Policy 协作测试接入

此分支仅增加 GitHub / Codex 协作配置，不改变模型、训练、数据、推理或硬件逻辑。
上游 MIT 许可和已有 Git 历史保持。

## 规范来源

中央仓库目标为 `Alex-research-lab-test/lab-research-infrastructure`。
实际采用的来源 commit 和本地调整记录在根目录 `lab-infrastructure-version.json`。
更新规范通过项目 PR，不自动覆盖本地配置。

## 本地检查

在单独的协作工具环境安装 `pre-commit==4.6.1` 和 `PyYAML==6.0.3`，使用
Python 3.11+、Node.js 22；不修改原训练环境。

```bash
pre-commit run --all-files --show-diff-on-failure
python tools/lab/check_codex.py
```

工作流使用固定版本 actionlint 校验 `.github/workflows/lab-ci.yml`。
检查范围是新协作文件；不执行整个旧 `tests/`，也不安装 PyTorch/CUDA 训练栈。
以后算法修改必须另附适用模块的实际验证证据。

## 研究记录

`templates/` 提供研究任务、论文到实现映射和实验记录。
它们是空白模板，不能作为已复现论文、已运行实验或已审阅结果的证据。
现有本地自定义代码与实验数据未纳入公开测试。

## 审核与门禁

两个本地角色 `scientific_reviewer`、`code_reviewer` 需在项目新 Codex 会话
验证实际加载；它们不会自动变成 GitHub 云端 reviewer。
客户端必须信任实际 Git 根目录；父目录或旧部署目录的信任记录不能代替。
从项目根启动新的会话，或由用户显式选择只信任该根目录的只读审核 profile。
信任配置属于用户本地设置，不提交到项目，也不自动覆盖现有用户配置。

CLI 0.166.0 的单变量对照和真实审核确认：受信任目录可直接发现现有
`.codex/agents/*.toml`，不必新增项目 `.codex/config.toml`。显式 config_file
注册也是可用方案，但不是本客户端的必需条件。根因、实际线程和审核结果见
中央仓库的 `docs/native-reviewer-acceptance.md`。

云端 Codex Code Review、真实 Actions 运行和合并规则分别验证。
单人阶段拟使用 PR + required CI 门禁，必需真人批准为 0；双人批准尚未验证。

本地原生角色验收不代替本修复发布后的 CI，也不表示任何科学实验已通过。

## 自动科研审核

执行 `research-reproduction` 时主 Agent 根据目标、完整 diff 和科学风险自动分级：
L0 仅格式检查，L1 原生 code_reviewer，L2 两个独立原生 Reviewer；科学影响
不明确时升至 L2。协作配置、Skill 与规范维护也适用，无需用户指定角色。
使用 [审核记录模板](templates/review-record.md) 保存理由、真实角色/线程 ID、
固定 SHA、检查、发现和处置。缺角色或结果不得报告通过，AI 不替代已有门禁。
本次同步分支基于尚未合并的 PR #3，保留其可信根目录说明；来源版本见根目录 JSON。

## 通用科研任务入口

沿用 `research-reproduction`，先理解科研问题、材料、输出与成功标准，再选
官方复现、自定义数据适配、算法改进或分析仿真；失败分析按证据选择路线。
自有数据任务不会默认改用 Push-T。先查现有资料，明确则直接设计方案，
缺关键语义时每轮只澄清 1–3 项；无人值守记录 NEEDS_USER_INPUT，继续不依赖
答案的安全工作。执行中新发现 Action 或评价冲突时暂停受影响操作。
使用 [任务记录模板](templates/research-task.md) 区分已确认决定、假设、阻塞
和授权。训练/预算/数据/硬件边界、原生分级审核及远程门禁保持。
本次分支堆叠在尚未合并的 PR #4 上，保留 PR #3、#4 的全部配置。
