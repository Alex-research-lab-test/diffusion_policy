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
云端 Codex Code Review、真实 Actions 运行和合并规则分别验证。
单人阶段拟使用 PR + required CI 门禁，必需真人批准为 0；双人批准尚未验证。

当前本地准备不代表远程部署、AI 审核或合并阻断已经成功。
