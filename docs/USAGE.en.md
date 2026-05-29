# Usage Guide

`stop-slop-zh` can be used in two ways:

1. As a full Skill, where the LLM reads `SKILL.md` and `references/`.
2. As a one-off prompt, where you paste the core rules into the current chat.

The full folder is recommended. `SKILL.md` contains the core behavior, while `references/` provides phrase lists, structural patterns, examples, scoring, and domain-specific rules.

## Claude Skills

Use the whole repository folder as a Skill:

```text
stop-slop-zh/
  SKILL.md
  references/
```

Then prompt:

```text
Please use stop-slop-zh to clean the AI-like Chinese prose below. Only change expression; do not change facts.
```

For longer text, include the domain:

```text
This is a Chinese technical blog post. Please use stop-slop-zh to remove AI-like prose while preserving terminology, code logic, limitations, and real debugging details.
```

## Claude Project Knowledge

Upload these files to Project Knowledge:

- `SKILL.md`
- `references/phrases.zh.md`
- `references/structures.zh.md`
- `references/examples.zh.md`
- `references/scoring.zh.md`
- `references/domain-guides.zh.md`

Project instructions:

```text
When I ask you to edit Chinese prose, follow stop-slop-zh/SKILL.md.
When phrase-level, structure-level, scoring, or domain-specific judgment is needed, refer to the files under references/.
```

## ChatGPT Custom Instructions

If space is limited, copy the `Role`, `Core Rules`, and `Workflow` sections from `SKILL.md`.

Suggested instruction:

```text
When editing Chinese prose, follow stop-slop-zh: remove model-like phrasing, public-account rhetoric, summary voice, fake profundity, business jargon, abstract noun stacking, and over-structured rhythm. Only change expression; do not change facts or add unsupported information. Do not force every text into one style. Preserve technical accuracy in technical writing, author voice in personal essays, and facts, risks, and next steps in project reports.
```

## Cursor / Codex

Reference the repository in a task:

```text
Please read stop-slop-zh/SKILL.md and follow the rules under references/ when editing Chinese text.
```

More specific:

```text
Please use stop-slop-zh to clean this Chinese project report. Preserve completed items, unfinished items, risks, owners, dates, and next steps. Remove phrases like “持续优化”, “形成闭环”, and “有序推进” when they add no concrete information.
```

## Gemini CLI / Other Agents

Put `SKILL.md` into the system prompt, or ask the agent to read it at the start:

```text
Read SKILL.md and apply stop-slop-zh rules when editing Chinese prose. Load references only when needed.
```

## One-off Prompts

Direct rewrite:

```text
Please clean the AI-like Chinese prose below according to stop-slop-zh. Only output the revised text. Do not change facts, add new information, or force the text to be shorter.
```

Analyze then rewrite:

```text
Please analyze the following Chinese text according to stop-slop-zh. First list the main sources of AI-like prose, then provide a revised version. Preserve facts, terminology, scenes, and author voice.
```

Score-based edit:

```text
Please score the following text using the five stop-slop-zh dimensions: Directness, Specificity, Rhythm, Human Voice, and Density. Score each from 1 to 10. Then only revise the two lowest-scoring dimensions.
```

## Recommended Workflow

1. Identify the text type.
2. Locate whether the AI-like prose comes from phrases, structure, rhythm, abstraction, or forced elevation.
3. Preserve facts, numbers, scenes, actions, limits, failures, and judgment.
4. Remove filler that adds no information.
5. Check that the result still sounds like the original author, not another template.
