# Generated Skill Template

Use this template when producing a skill from a book. Adapt headings only when the target skill clearly needs a different structure.

## SKILL.md

```markdown
---
name: {skill-name}
description: {What the skill does and when to use it. Include concrete triggers, target tasks, and contexts.}
---

# {Skill Display Name}

## Overview

Use {book title}'s core ideas to help users {solve specific problem}. Focus on practical application rather than book summary.

## Input Contract

The user should provide {the minimum required input}. If missing, ask for only the missing fields needed to proceed.

## First Response

When invoked, ask the user for:

- Their concrete situation or input
- Their desired output
- Any constraints, audience, tone, or success criteria

If the user has already supplied enough detail, proceed with stated assumptions.

## Knowledge Use

Read `references/book-knowledge.md` before producing the main answer. Apply only the knowledge relevant to the user's current situation. Do not dump the whole knowledge base into the response.

Respect source labels:

- Use user-supplied knowledge as primary source material.
- Use inferred principles as decision lenses, not as exact quotations.
- State assumptions when book knowledge is incomplete.

## Workflow

1. Clarify the user's immediate need, context, and output target.
2. Select the relevant book-derived principles from `references/book-knowledge.md`.
3. Diagnose the user's situation through those principles.
4. Generate the requested artifact, advice, or plan.
5. Check the output against the constraints and success criteria.
6. Offer one concise next step only when it directly improves the result.

## Constraints

- Stay focused on {specific problem domain}.
- Do not summarize the book unless the user asks.
- Do not invent book claims; mark inferred principles as inferred.
- Prefer concrete, usable outputs over abstract commentary.
- Make assumptions explicit when source knowledge is incomplete.
- Do not optimize for the book's ideology at the expense of the user's real constraints.

## Output Format

{Define the exact structure expected from this skill.}

## Test Requests

- "{A natural one-sentence request that should trigger this skill.}"
- "{A second request with different context but same recurring problem.}"
- "{Optional edge-case request that tests constraints or source boundaries.}"

## Examples

### Example 1

User: {realistic user request}

Assistant: {abbreviated ideal output showing structure and style}

### Example 2

User: {realistic user request}

Assistant: {abbreviated ideal output showing structure and style}
```

## references/book-knowledge.md

```markdown
# Book Knowledge: {Book Title}

## Source Status

- Book title: {title}
- Source material: {user-provided notes / inferred from user summary / mixed}
- Intended skill direction: {direction}

## Source Boundaries

- User-supplied: {what came directly from the user}
- Inferred: {what the generator inferred from the title, summary, or common book themes}
- Unknown: {what should not be claimed without more source material}

## Core Problem

{The practical problem this book-derived skill helps solve.}

## Principles

1. **{Principle name}**: {Plain explanation.}
   - Use when: {trigger situation}
   - Example: {short concrete example}
   - Source status: {user-supplied/inferred}

2. **{Principle name}**: {Plain explanation.}
   - Use when: {trigger situation}
   - Example: {short concrete example}
   - Source status: {user-supplied/inferred}

## Models Or Frameworks

- **{Model name}**: {Steps or components}

## Activation Map

- Use **{principle}** when the user says {trigger pattern}.
- Use **{principle}** when the user needs {task}.
- Avoid **{principle}** when {misuse condition}.

## Useful Phrases Or Patterns

- {Reusable phrase, framing, diagnostic question, or output pattern}

## Anti-Patterns

- {What the skill should avoid because it contradicts or misuses the book}
```

## agents/openai.yaml

```yaml
interface:
  display_name: "{Human-facing skill name}"
  short_description: "{25-64 character concise UI description}"
  default_prompt: "Use ${skill-name} to {perform the primary task}."
```
