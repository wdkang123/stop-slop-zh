# stop-slop-zh

[中文](README.md) | [English](README.en.md)

中文 AI 味清洗规则库。去除模型腔、公众号腔、总结腔、假深刻、商务黑话和过度结构化表达。

`stop-slop-zh` 是一个面向中文写作的 LLM Skill / Prompt Rules / Style Guide。它不是把中文变短，也不是把所有文字改成同一种“犀利风格”。它要做的事更窄：帮助模型删掉没有信息增量的套话，保留事实、判断、场景、限制和作者声音。

Inspired by [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop). This project focuses on Chinese prose and is not a direct translation.

## What This Is

这是一个给 LLM 使用的中文写作 Skill。你可以把它当成一组可复制的改写规则，用来处理中文博客、技术文章、产品分析、项目汇报、个人复盘和社交媒体内容。

它可以用于：

- Claude Skills
- Claude Project Knowledge
- ChatGPT Custom Instructions
- Cursor Rules
- Codex 任务提示
- Gemini CLI / 其他 Agent 的 system prompt
- 中文博客改写
- 技术文章改写
- 产品分析改写
- 汇报材料改写
- 个人文章去 AI 味

## What It Catches

它主要处理这些中文 AI 味：

- 开场铺垫
- 假深刻
- 公众号式升华
- 总结腔
- 商务黑话
- 抽象名词堆叠
- 过度结构化
- 机械三段式
- “是什么/为什么/怎么做”滥用
- 技术文章空泛介绍
- 产品分析空话
- 过度均匀的段落节奏
- 没有人、没有动作、没有场景的句子

很多词不是永远不能用。问题通常不在词本身，而在它是否替代了具体信息。比如“闭环”在某些团队里有明确流程含义，可以保留；如果它只是“做完”的装饰词，就应该删掉。

## Quick Start

方式一：直接复制 `SKILL.md` 到 LLM 的 system prompt 或 custom instructions。

方式二：把整个 `stop-slop-zh` 目录作为 Claude Skill 使用。`SKILL.md` 是主规则，`references/` 下的文件按需加载。

方式三：在 Cursor / Codex 中引用：

```text
请读取 stop-slop-zh/SKILL.md，并在改写中文文本时遵守 references/ 下的规则。
```

方式四：单次使用 prompt：

```text
请按照 stop-slop-zh 的规则，清洗下面这段中文文本的 AI 味。只改表达，不改变事实。
```

更多接入方式和可复制 prompt 见 [docs/USAGE.zh.md](docs/USAGE.zh.md)。英文使用指南见 [docs/USAGE.en.md](docs/USAGE.en.md)。

## Example

Before:

> 随着人工智能技术的快速发展，越来越多的开发者开始关注 AI Agent 的应用落地。不可否认的是，AI Agent 不仅是一种技术趋势，更是未来软件开发范式的重要变革。本文将从多个维度出发，系统分析 AI Agent 的核心价值、应用场景与发展路径。

After:

> 最近很多开发者开始试 AI Agent。问题不在于它是不是“趋势”，而在于它能不能真的替你完成一段工作：读文件、改代码、跑测试、提交结果。本文只讨论一件事：AI Agent 在开发场景里到底能落到哪一步。

## Scoring

每篇文本按 5 个维度评分，每项 1-10 分，总分 50：

- Directness 直接度
- Specificity 具体度
- Rhythm 节奏自然度
- Human Voice 人味
- Density 信息密度

判定方式：

- 43-50：可以发布
- 35-42：需要局部修改
- 25-34：需要重写关键段落
- 25 以下：建议整篇重写

评分细则见 [references/scoring.zh.md](references/scoring.zh.md)。

## What This Is Not

- 不是中文润色器
- 不是爆款标题生成器
- 不是洗稿工具
- 不是敏感词过滤器
- 不是反 AI 工具
- 不是把文字变短的工具
- 不是把所有文字改成同一种风格

## Project Structure

```text
stop-slop-zh/
  .github/
    ISSUE_TEMPLATE/
    PULL_REQUEST_TEMPLATE.md
  README.md
  README.en.md
  LICENSE
  SKILL.md
  CHANGELOG.md
  CONTRIBUTING.md
  ROADMAP.md
  docs/
    USAGE.zh.md
    USAGE.en.md
  references/
    phrases.zh.md
    structures.zh.md
    examples.zh.md
    scoring.zh.md
    domain-guides.zh.md
  samples/
    blog.before.md
    blog.after.md
    tech.before.md
    tech.after.md
    report.before.md
    report.after.md
    personal.before.md
    personal.after.md
```

## Contributing

欢迎贡献短语、结构、示例和场景规则。请先阅读 [CONTRIBUTING.md](CONTRIBUTING.md)，并优先使用 GitHub issue 模板提交：

- 新增中文 AI 味短语
- 新增 before/after 示例
- 新增场景规则
- 规则误伤反馈

贡献时请说明问题、改法和例外场景。不要只提交一个“禁用词”。

## License

MIT.
