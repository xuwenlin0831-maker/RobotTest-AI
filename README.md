# RobotTest-AI

RobotTest-AI 当前聚焦一件事：让团队通过同一份 Skill，把需求资料整理成符合 Teambition（TB）17 列导入模板的测试用例。

本仓库第一阶段主推 **Codex 项目式使用**，同时提供 ChatGPT 网页端的简化兼容说明。当前不包含 TB 自动上传，也未打包为 Plugin。

## 当前版本

- Skill：`vehicle-testcase-lifecycle`
- 版本：`v0.2.0`
- 状态：规划中－待试用
- 输出标准：TB 17 列模板

## Skill 固化了什么

- 正式 Excel 保持模板原有 17 列、字段顺序和前三行不变。
- 不新增“用例状态”列；用例状态不是当前模板生成字段。
- “编写人”必须填写，且必须是 TB 企业内有效成员。
- 缺少编写人或其他导入关键字段时，停止正式生成并集中追问。
- 非必填字段无法确认时允许留空，但必须进入评审清单。
- 本地生成和外部上传分为两级确认；生成文件不等于获得上传 TB 或发送文件的授权。

## Codex 快速开始

1. 克隆本仓库，并在 Codex 中打开仓库根目录。
2. 新开对话，输入 `$vehicle-testcase-lifecycle` 显式调用 Skill。
3. 提供生成范围、来源资料、编写人、创建日期、用例等级和用例类型。
4. 明确要求生成本地 TB Excel；生成后人工评审，再决定是否上传 TB。

推荐首次使用直接复制：

```text
使用 $vehicle-testcase-lifecycle，按“派生用例输出”模式生成 TB 导入文件。

生成范围：
来源资料：
编写人：
创建日期：
用例等级：
用例类型：

请先检查关键输入是否完整。完整则生成本地文件和评审清单；不完整则一次性列出缺失项。不要上传 TB，不要发送文件，不要修改外部系统。
```

详细操作见 [Codex 使用教程](docs/Codex使用教程.md)。

## ChatGPT 网页端

本阶段没有将 Skill 打包为 Plugin，因此普通 ChatGPT 网页对话不能仅靠 GitHub 链接获得与 Codex 完全相同的项目级约束。网页端可作为兼容入口，详细边界和提示词见 [ChatGPT 网页端使用](docs/ChatGPT网页端使用.md)。

## 仓库结构

```text
RobotTest-AI/
├── .agents/skills/vehicle-testcase-lifecycle/  # 唯一正式 Skill
├── docs/
│   ├── Codex使用教程.md
│   ├── ChatGPT网页端使用.md
│   └── 常见问题FAQ.md
├── examples/对话示例.md
├── .gitignore
└── README.md
```

仓库通过白名单式 `.gitignore` 排除本地生产用例、会议材料、PPT 工程和临时输出，避免误上传内部资料。

## 使用边界

- AI 负责生成和校验候选文件，人工负责业务审核和最终上传。
- 当前不自动上传 TB，不自动发送文件或消息。
- 基础库治理必须由用户显式选择，Skill 只输出变更建议，不直接修改基础库。
- 未完成真实 TB 非生产试导入前，不把当前版本标记为“已验证”。

## 更多资料

- [常见问题 FAQ](docs/常见问题FAQ.md)
- [完整对话示例](examples/对话示例.md)
- [Skill 规则](.agents/skills/vehicle-testcase-lifecycle/SKILL.md)
- [TB 模板规则](.agents/skills/vehicle-testcase-lifecycle/references/tb_template_schema.md)
- [验收清单](.agents/skills/vehicle-testcase-lifecycle/tests/acceptance-checklist.md)
