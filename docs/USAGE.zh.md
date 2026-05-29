# 使用指南

`stop-slop-zh` 可以按两种方式使用：

1. 作为完整 Skill，让 LLM 读取 `SKILL.md` 和 `references/`。
2. 作为一次性提示词，把核心规则贴进当前对话。

推荐优先使用完整目录。`SKILL.md` 负责主规则，`references/` 负责细分场景、短语、结构、示例和评分。

## Claude Skills

把整个仓库目录作为一个 Skill 使用：

```text
stop-slop-zh/
  SKILL.md
  references/
```

使用时可以直接说：

```text
请使用 stop-slop-zh 清洗下面这段中文文本。只改表达，不改变事实。
```

如果文本很长，建议加上场景：

```text
这是一篇技术博客。请使用 stop-slop-zh 清洗 AI 味，优先保留术语、代码逻辑、限制条件和真实踩坑。
```

技术博客可以额外要求读取：

```text
请优先参考 references/tech-blog.zh.md 和 references/examples-tech.zh.md。
```

## Claude Project Knowledge

把这些文件上传到 Project Knowledge：

- `SKILL.md`
- `references/phrases.zh.md`
- `references/structures.zh.md`
- `references/examples.zh.md`
- `references/scoring.zh.md`
- `references/domain-guides.zh.md`
- `references/tech-blog.zh.md`
- `references/examples-tech.zh.md`
- `references/report.zh.md`
- `references/examples-report.zh.md`

Project instructions 可以写：

```text
当我要求你修改中文文本时，请遵守 stop-slop-zh/SKILL.md。
如果需要判断具体短语、结构、评分或场景策略，请参考 references/ 下的规则文件。
```

## ChatGPT Custom Instructions

如果只能放较短内容，优先复制 `SKILL.md` 的 `Role`、`Core Rules` 和 `Workflow`。

推荐写法：

```text
你在修改中文文本时要遵守 stop-slop-zh 的规则：删除模型腔、公众号腔、总结腔、假深刻、商务黑话、抽象名词堆叠和过度结构化表达。只改表达，不改变事实，不添加未经提供的新信息，不把所有文本改成同一种风格。技术文本优先准确，个人文章优先作者声音，项目汇报优先事实、风险和下一步。
```

## Cursor / Codex

在任务里引用仓库：

```text
请读取 stop-slop-zh/SKILL.md，并在改写中文文本时遵守 references/ 下的规则。
```

更具体一点：

```text
请使用 stop-slop-zh 清洗这篇项目汇报。保留已完成、未完成、风险、负责人、时间点和下一步；删除“持续优化”“形成闭环”“有序推进”等没有信息增量的表达。
```

项目汇报可以额外要求读取：

```text
请优先参考 references/report.zh.md 和 references/examples-report.zh.md。
```

## Gemini CLI / 其他 Agent

把 `SKILL.md` 放进 system prompt，或者在任务开始时让 Agent 读取：

```text
Read SKILL.md and apply stop-slop-zh rules when editing Chinese prose. Load references only when needed.
```

## 单次改写 prompt

直接改：

```text
请按照 stop-slop-zh 的规则，清洗下面这段中文文本的 AI 味。只输出改后文本。不要改变事实，不要添加新信息，不要强行缩短。
```

分析后再改：

```text
请按照 stop-slop-zh 的规则分析下面这段中文文本。先列出主要 AI 味来源，再给出改写版本。改写时保留事实、术语、场景和作者语气。
```

按评分改：

```text
请按 stop-slop-zh 的 5 个维度给下面文本打分：Directness、Specificity、Rhythm、Human Voice、Density。每项 1-10 分。然后只修改最低分的两个维度。
```

## 推荐工作流

1. 先判断文本类型。
2. 找出 AI 味来自短语、结构、节奏、抽象还是升华。
3. 优先保留事实、数字、场景、动作、限制、失败和判断。
4. 删除没有信息增量的套话。
5. 最后检查是否还像原作者，而不是像另一个模板。
