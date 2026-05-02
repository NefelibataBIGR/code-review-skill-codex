[English](./README.md) | [简体中文](./README.zh-CN.md)

# 适用于 Codex 的 Code Review Codex

参考来源：https://github.com/awesome-skills/code-review-skill

这是一个面向 Codex 的模块化 skill，用来把代码审查变成更结构化、信息密度更高的工作流。

它适用于 PR 审查、补丁审查、架构审查、安全审查，以及多语言仓库中的常规代码质量检查。

## 仓库内容

- `SKILL.md`：skill 主入口和触发元数据
- `agents/openai.yaml`：Codex UI 元数据
- `reference/`：按需加载的语言和专题审查指南
- `assets/`：可复用模板与检查清单
- `scripts/`：辅助脚本，包括 PR 分析工具

## 支持的审查范围

- React
- Vue
- TypeScript
- Python
- Java
- Go
- Rust
- C
- C++
- CSS / Less / Sass
- Qt
- 架构审查
- 性能审查
- 安全审查
- 常见 Bug 模式检查

## Codex 如何使用这个 Skill

Codex 通过 [SKILL.md](./SKILL.md) 中的元数据发现这个 skill。触发描述刻意只强调“什么时候该加载”：

- 审查 pull request
- 审查代码变更
- 做架构审查
- 做安全审查
- 检查代码质量
- 排查 bug
- 输出结构化审查意见

skill 被加载后，Codex 会优先按需读取 `reference/` 下的文件，而不是一次把所有内容都塞进上下文。

## 安装

### 全局安装

把这个仓库克隆或复制到 Codex skills 目录：

```bash
# macOS / Linux
git clone https://github.com/awesome-skills/code-review-skill.git \
  ~/.codex/skills/code-review-codex

# Windows PowerShell
git clone https://github.com/awesome-skills/code-review-skill.git `
  "$env:USERPROFILE\.codex\skills\code-review-codex"
```

### 备用位置

如果你的环境偏向个人 agent skills，也可以复制到：

```bash
~/.agents/skills/code-review-codex
```

安装后需要重启 Codex，让新的 skill 元数据生效。

## 使用方式

### 显式调用

直接在提示词里引用 skill：

```text
Use code-review-codex to review this PR.
Focus on bugs, regressions, security issues, and missing tests.
```

### 自然语言触发

这个 skill 也支持通过普通请求自然触发，例如：

```text
Review these changes for bugs and maintainability issues.
```

```text
Do an architecture review of this refactor.
```

```text
Check this service for security problems before merge.
```

## 审查风格

这个 skill 适合以下类型的 review：

- 优先找 bug 和行为回归，而不是纠缠格式细节
- 明确区分阻塞问题和普通建议
- 关注正确性、安全性、性能和可维护性
- 反馈要具体、可执行
- 只在必要时读取语言专属指南

## 仓库结构

```text
code-review-codex/
|-- SKILL.md
|-- agents/
|   `-- openai.yaml
|-- reference/
|   |-- react.md
|   |-- vue.md
|   |-- typescript.md
|   |-- python.md
|   |-- java.md
|   |-- go.md
|   |-- rust.md
|   |-- c.md
|   |-- cpp.md
|   |-- qt.md
|   |-- css-less-sass.md
|   |-- architecture-review-guide.md
|   |-- performance-review-guide.md
|   |-- security-review-guide.md
|   |-- common-bugs-checklist.md
|   `-- code-review-best-practices.md
|-- assets/
|   |-- review-checklist.md
|   `-- pr-review-template.md
`-- scripts/
    `-- pr-analyzer.py
```

## 维护说明

- `SKILL.md` 只保留触发条件和核心流程，不堆砌大段参考资料。
- 详细模式和最佳实践放进 `reference/`。
- 安装或使用方式变化时，同时更新中英文文档。
- 示例尽量贴近真实代码审查场景。

贡献和验证说明见 [CONTRIBUTING.zh-CN.md](./CONTRIBUTING.zh-CN.md)。
