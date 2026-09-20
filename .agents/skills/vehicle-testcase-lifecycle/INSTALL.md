# 团队安装与更新

## 推荐方式：Codex 项目使用

1. 克隆 `RobotTest-AI` 仓库。
2. 在 Codex 中打开仓库根目录。
3. Codex 从 `.agents/skills/vehicle-testcase-lifecycle` 发现本 Skill。
4. 新开任务并使用 `$vehicle-testcase-lifecycle` 显式调用。

这种方式适合团队统一版本：Skill 与仓库一起更新，不需要成员分别复制文件。

## 可选方式：个人全局安装

如果需要在其他项目中使用，可将完整的 `vehicle-testcase-lifecycle` 文件夹复制到：

```text
$HOME/.agents/skills/vehicle-testcase-lifecycle
```

也可以调用 `$skill-installer`，要求它从 RobotTest-AI 的 GitHub 仓库安装 `.agents/skills/vehicle-testcase-lifecycle`。Private 仓库需要当前环境已经具备相应 GitHub 访问权限。

安装或更新后，如 Skill 未出现，请重启 Codex 或新开任务。不要只复制 `SKILL.md`；`references`、`tests`、`agents`、`skill-registry.yaml` 与 `CHANGELOG.md` 必须一并保留。

## ChatGPT 网页端

本版本尚未打包为 Plugin。普通 ChatGPT 网页对话不能仅通过仓库链接自动加载该 Skill；请使用仓库 `docs/ChatGPT网页端使用.md` 中的兼容流程。若工作区未来安装了对应 Skill 或 Plugin，再使用 `@` 选择。

## 更新

1. 在仓库中执行 `git pull`。
2. 查看 `CHANGELOG.md` 与 `skill-registry.yaml`。
3. 重启 Codex 或新开任务。
4. 用真实或样例需求做一次导出验证；TB 规则变更时按 `tests/acceptance-checklist.md` 检查。

## 团队规则

- 只有 `vehicle-testcase-lifecycle` 负责发布“标准 TB 用例输出”规则。
- 其他 Skill 可提供 PRD 解析、基础库检索或 TB 上传能力，但不得复制或另行维护 TB 输出字段规则。
- 任何规则修改先提交给 Owner 审核；Owner 尚未指定前，不发布正式版本。
