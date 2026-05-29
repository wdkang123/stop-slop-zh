# stop-slop-zh

[中文](README.md) | [English](README.en.md)

A Chinese AI-prose cleanup rulebook. It helps remove model-like phrasing, public-account rhetoric, summary voice, fake profundity, business jargon, and over-structured rhythm from Chinese writing.

`stop-slop-zh` is an LLM Skill / Prompt Rules / Style Guide for Chinese prose. It does not try to make every text short, cold, sharp, or casual. It tries to keep facts, judgment, scenes, constraints, and author voice while cutting template-like filler.

Inspired by [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop). This project focuses on Chinese prose and is not a direct translation.

## What This Is

Use this repository as a Chinese writing skill for LLMs. It can guide edits for Chinese blogs, technical posts, product analysis, project reports, personal essays, social posts, and long-form notes.

It can be used with:

- Claude Skills
- Claude Project Knowledge
- ChatGPT Custom Instructions
- Cursor Rules
- Codex task prompts
- Gemini CLI or other agent system prompts
- Chinese blog rewriting
- Technical article editing
- Product analysis editing
- Report cleanup
- Personal essay cleanup

## What It Catches

- Throat-clearing Chinese openings
- Fake profundity
- Public-account style elevation
- Summary voice
- Business jargon
- Abstract noun stacking
- Over-structured rhythm
- Mechanical three-part structure
- Overuse of “what / why / how”
- Vague introductions in technical articles
- Empty product-strategy language
- Uniform paragraph rhythm
- Sentences with no person, action, or scene

These are not banned words. Many phrases are valid in the right context. The problem is when they replace concrete information.

## Quick Start

Option 1: Copy `SKILL.md` into your LLM system prompt or custom instructions.

Option 2: Use the whole `stop-slop-zh` folder as a Claude Skill. `SKILL.md` contains the core instructions, and `references/` provides deeper rules on demand.

Option 3: In Cursor or Codex, reference it like this:

```text
Please read stop-slop-zh/SKILL.md and follow the rules under references/ when editing Chinese text.
```

Option 4: Use a one-off prompt:

```text
Please clean the AI-like Chinese prose in the following text according to stop-slop-zh. Only change expression; do not change facts.
```

## Example

Before:

> 随着人工智能技术的快速发展，越来越多的开发者开始关注 AI Agent 的应用落地。不可否认的是，AI Agent 不仅是一种技术趋势，更是未来软件开发范式的重要变革。本文将从多个维度出发，系统分析 AI Agent 的核心价值、应用场景与发展路径。

After:

> 最近很多开发者开始试 AI Agent。问题不在于它是不是“趋势”，而在于它能不能真的替你完成一段工作：读文件、改代码、跑测试、提交结果。本文只讨论一件事：AI Agent 在开发场景里到底能落到哪一步。

## Scoring

Score each text on five dimensions, 1-10 each, for a total of 50:

- Directness
- Specificity
- Rhythm
- Human Voice
- Density

Interpretation:

- 43-50: publishable
- 35-42: needs local edits
- 25-34: rewrite key sections
- Below 25: rewrite the whole piece

See [references/scoring.zh.md](references/scoring.zh.md) for the full rubric.

## What This Is Not

- Not a Chinese polish tool
- Not a viral-title generator
- Not a paraphrasing or plagiarism tool
- Not a sensitive-word filter
- Not an anti-AI tool
- Not a shortening tool
- Not a tool that forces every text into one style

## License

MIT.

