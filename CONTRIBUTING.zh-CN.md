[English](./CONTRIBUTING.md) | [简体中文](./CONTRIBUTING.zh-CN.md)

# 贡献说明

这个仓库封装的是一个 Codex skill。贡献时要优先保证三个目标：可发现性、渐进式加载，以及审查质量。

## 目标

- 让 Codex 容易发现这个 skill
- 让核心说明保持简短、具体
- 把重型参考内容放进 `reference/`
- 提高审查准确性，但不要把触发元数据写得臃肿

## 仓库约定

### 必需文件

- `SKILL.md`
- `agents/openai.yaml`

### 可选支持文件

- `reference/*.md`
- `assets/*`
- `scripts/*`

### 当前结构

```text
code-review-codex/
|-- SKILL.md
|-- README.md
|-- README.zh-CN.md
|-- CONTRIBUTING.md
|-- CONTRIBUTING.zh-CN.md
|-- agents/
|   `-- openai.yaml
|-- reference/
|-- assets/
`-- scripts/
```

## 编辑规则

### `SKILL.md`

- `name` 没有迁移理由就不要改。
- `description` 只写触发条件。
- `description` 必须以 `Use when...` 开头。
- 不要在 `description` 里概括完整工作流。
- 正文只保留流程和导航，不堆详细参考资料。

### `agents/openai.yaml`

- `display_name` 保持对人类可读。
- `short_description` 要能概括 skill 范围，但不要重复整份 README。

### `reference/`

- 重型指南放这里，不放进 `SKILL.md`。
- 尽量一类主题一个文件。
- 文件名使用小写加连字符。

### `README*`

- `README.md` 是英文主文档。
- `README.zh-CN.md` 是中文补充文档。
- 两个文件顶部都必须有语言切换链接。
- 中英文中的安装和使用示例要保持一致。

### `CONTRIBUTING*`

- `CONTRIBUTING.md` 是英文主文档。
- `CONTRIBUTING.zh-CN.md` 是中文补充文档。
- 两边的贡献规则要保持同步。

## 新增或更新参考指南

如果要新增语言或专题指南：

1. 把文件放到 `reference/`。
2. 文件名要清晰，使用小写和连字符。
3. 只有在 skill 需要主动把读者导向该文件时，才在 `SKILL.md` 里加链接。
4. 如果支持范围变了，要同步更新中英文 README。

## 验证清单

合并前请确认：

- `SKILL.md` frontmatter 是合法 YAML
- `name` 和 `description` 仍然匹配预期触发行为
- `agents/openai.yaml` 存在，且和 skill 名称范围一致
- 四个文档里的语言切换链接都可用
- 安装路径示例仍符合 Codex 约定
- 新增的参考文件要么被引用，要么其命名足够可发现

## 建议的手工验证

安装后，使用一个全新的 Codex 会话。

### 显式调用测试

向 Codex 提示：

```text
Use code-review-codex to review these changes for bugs, regressions, and missing tests.
```

预期结果：

- 审查输出结构清晰
- bug 和风险优先级靠前
- 不会被格式细节主导

### 自然触发测试

向 Codex 提示：

```text
Review these changes for security issues and maintainability problems.
```

预期结果：

- Codex 会把它识别成代码审查任务
- 回答会强调 findings、严重性和具体审查意见

## 非目标

- 不要把这个 skill 变成通用编程教程。
- 不要把 `reference/` 的大段内容复制回 `SKILL.md`。
- 不要新增无实际价值的辅助文档，除非它确实改善了安装、贡献或双语可用性。
