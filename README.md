# Book to Skill

`book-to-skill` is a Codex skill that turns a book, book notes, or a reading-derived framework into a reusable skill for solving a specific problem.

It helps an agent interview the user, choose a focused skill direction, separate book knowledge from workflow, generate `SKILL.md`, add a reusable knowledge template, and validate that the generated skill is testable.

## Contents

- `book-to-skill/SKILL.md`
- `book-to-skill/references/generated-skill-template.md`
- `book-to-skill/agents/openai.yaml`

## Use

Install or copy the `book-to-skill` folder into your Codex skills directory:

```bash
~/.codex/skills/book-to-skill
```

Then restart Codex and ask it to use `$book-to-skill` to turn a book into a reusable skill.
