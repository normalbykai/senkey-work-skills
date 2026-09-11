# 项目技能集合

按各 Agent 实际识别的项目级目录归纳。将本目录中的 `.agents` 和 `.claude` 文件夹复制或合并到目标项目根目录，保留目录层级；不需要再套一层 `senkai-skills` 文件夹。已有同名技能时先比较内容，避免覆盖项目自定义规则。

## 技能清单

- `local-git-commit`：用于检查当前仓库的未提交改动，并生成符合中文规范的提交主题和变更概述。只有在用户明确要求时才会创建本地提交；默认不会推送到远端，避免未经确认地改变 Git 历史或发布代码。
- `plan-before-implementation`：用于需要先评审方案的任务。必须由用户显式调用，启用后 Agent 只会调研并交付方案文档；必须等用户确认方案后，才会进入代码修改、提交、部署等实施环节。
- `solution-fit-review`：用于在实施前独立评估用户提出的技术或产品方案是否符合实际目标、现有系统和成本约束；输出聚焦最终采纳的方案，避免将可行但不合适的实现直接落地。
- `skill-doc-sync`：用于新增或实质调整项目 skill 时，同步更新外部 Markdown 技能清单，简要说明其用途、适用场景及必要的启用边界；默认更新本仓库的 `README.md`，也可遵从用户指定的文档。

```text
项目根目录/
├── .agents/
│   └── skills/
│       ├── local-git-commit/
│       │   ├── SKILL.md
│       │   └── agents/openai.yaml
│       ├── plan-before-implementation/
│       │   ├── SKILL.md
│       │   └── agents/openai.yaml
│       ├── solution-fit-review/
│       │   ├── SKILL.md
│       │   └── agents/openai.yaml
│       └── skill-doc-sync/
│           ├── SKILL.md
│           └── agents/openai.yaml
└── .claude/
    └── skills/
        ├── local-git-commit/
        │   └── SKILL.md
        ├── plan-before-implementation/
        │   └── SKILL.md
        ├── solution-fit-review/
        │   └── SKILL.md
        └── skill-doc-sync/
            └── SKILL.md
```

| 工具 | 项目技能目录 | 显式调用 | 禁止自动调用配置 |
| --- | --- | --- | --- |
| Codex | `.agents/skills/` | `$plan-before-implementation` | `agents/openai.yaml` 中 `allow_implicit_invocation: false` |
| Claude Code | `.claude/skills/` | `/plan-before-implementation` | `SKILL.md` 顶部 `disable-model-invocation: true` |

以上显式调用配置仅针对 `plan-before-implementation`：先只读调研并交付方案文档，经用户明确确认后才实施。

`local-git-commit` 可根据查看改动、拟定提交信息或本地提交的请求自动匹配，也可在 Codex 中用 `$local-git-commit`、在 Claude Code 中用 `/local-git-commit` 调用。自动匹配只允许分析，创建提交仍须用户明确要求，默认不推送。

复制后若未出现在技能列表中，重新打开项目会话。

维护时同步同名技能的正文约束，分别保留宿主配置。打包时包含以点开头的目录。

目录规则来源：[Codex 官方文档](https://learn.chatgpt.com/docs/build-skills)、[Claude Code 官方文档](https://code.claude.com/docs/en/skills)。
