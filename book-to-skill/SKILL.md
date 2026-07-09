---
name: book-to-skill
description: Turn a book, book notes, or reading-derived framework into a reusable Codex skill for solving a specific problem. Use when the user wants to convert a book into a prompt, agent role, workflow, knowledge base, coaching assistant, writing assistant, analysis framework, or a formal skill with SKILL.md, references, and agent metadata.
---

# Book To Skill

## Overview

Transform a user's book insight into a focused, reusable skill. Treat the book as source material for a capability, not as content to summarize or admire.

## Operating Principle

Create skills that help users solve one concrete class of problems through the book's ideas. Prefer narrow, practical capabilities over broad "book expert" personas. A good generated skill has a clear input, a repeatable workflow, a recognizable output, and at least two realistic test requests.

## Workflow

1. Collect the seed context from the user:
   - Book title
   - Short book introduction
   - The specific help the user wants from the book

2. Enrich and confirm the seed context:
   - Restate the three fields with clearer wording and missing assumptions filled in.
   - Identify the likely user job: decide, diagnose, write, design, coach, research, plan, critique, or practice.
   - Ask for confirmation before choosing the skill direction when the user has provided little detail.
   - If the user already supplied enough detail, proceed and state the assumptions.

3. Propose at least three focused skill directions:
   - Make each option concrete, outcome-driven, and narrow enough to be useful.
   - Avoid generic options such as "book assistant" or "knowledge explainer".
   - For each option, include target user, trigger scenario, input, output, and why the book is suitable.
   - Prefer options that can be tested with a realistic user request in one turn.

4. After the user selects a direction, collect book-derived knowledge for that direction:
   - Ask for the relevant core claims, models, scenes, examples, tactics, terms, and counterexamples from the book.
   - Encourage the pattern `concept: practical meaning + example`.
   - Separate user-supplied notes, direct book memories, and inferred principles.
   - If the user cannot provide enough material, infer at least five knowledge points from the available book information and label them as inferred.

5. Design the generated skill:
   - Define a short hyphen-case skill name.
   - Write a trigger-rich `description` for frontmatter.
   - Define the generated skill's input contract: what the end user should provide first.
   - Design a compact workflow that starts by asking the end user for their concrete need or input.
   - Include an explicit step to read and apply the generated skill's book knowledge.
   - Move detailed book notes to `references/book-knowledge.md`; keep `SKILL.md` procedural.
   - Add 2-3 realistic test requests that should trigger the generated skill.

6. Produce the skill artifact:
   - If the user wants files, create the skill folder and validate it.
   - If the user wants text only, output the complete file contents in fenced markdown blocks.
   - Read `references/generated-skill-template.md` before drafting the final files.
   - Before finalizing, run the quality gate below.

## Quality Bar

- The skill must solve a specific user problem, not merely imitate the book's voice.
- The generated workflow must begin by eliciting the user's actual situation, constraints, and desired output.
- The generated workflow must explicitly apply `references/book-knowledge.md`.
- The generated knowledge must be actionable and formatted for reuse.
- The generated examples must demonstrate the target output, not just describe it.
- The generated skill must avoid claiming unsupported book knowledge. Mark inferred or user-supplied knowledge clearly.
- The generated skill must include at least two realistic user requests for future testing.
- The generated skill must make a default output format clear enough that another agent can follow it without asking for the original conversation.

## Quality Gate Before Finalizing

Revise the generated skill if any answer is "no":

- Can a user trigger it with one natural sentence?
- Does it solve a recurring problem rather than a one-off summary task?
- Does the first response collect the minimum information needed to help?
- Is the book knowledge separated from procedure?
- Are source boundaries clear: user-supplied, remembered, inferred, or external?
- Does the output format match the promised capability?
- Would a second agent know how to test the skill using only the generated files?

## Common Failure Modes

- **Book costume**: The skill only speaks in the author's style but does not solve a task.
- **Too wide**: The skill tries to cover the whole book and becomes a generic mentor.
- **No input contract**: The skill does not tell the end user what to provide.
- **Knowledge dump**: The skill repeats the whole book instead of selecting relevant principles.
- **Unsupported certainty**: The skill presents inferred book knowledge as exact source content.
- **Untestable output**: The skill has no concrete examples or test requests.

## Interview Prompts

Use these prompts sparingly; do not force all questions when the user has already answered them.

- "这本书主要想帮你解决哪个具体问题？"
- "你希望最终的 skill 在什么场景下被调用？用户会怎么说？"
- "它最好输出什么：诊断、方案、文案、清单、教练式对话、决策建议，还是别的？"
- "书里有哪些观点、模型或例子必须保留？"
- "这个 skill 不应该做什么，或者容易误用在哪里？"
- "输出风格更像顾问、教练、编辑、研究员，还是执行助手？"
- "用户第一句话通常会怎么说？"
- "如果这个 skill 做得好，最后交付物应该长什么样？"

## Output Modes

For a full skill, produce:

- `SKILL.md`
- `references/book-knowledge.md`
- `agents/openai.yaml`

For a prompt-only fallback, still structure the result with Role, Background, Preferences, Goals, Constraints, Skills, Knowledge, Examples, OutputFormat, Workflow, and Initialization, but explain that a reusable skill is the stronger form.
