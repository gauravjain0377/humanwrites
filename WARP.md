# WARP.md

This file provides guidance to WARP (warp.dev) when working with this repository.

## What this repo is

A **Claude Code skill** for humanizing AI-generated text — implemented entirely as Markdown. Detects and fixes **33 AI writing patterns**, from inflated language and em dash overuse to passive voice and filler transitions.

**Author:** [Gaurav Jain](https://github.com/gauravjain0377)  
**Repo:** https://github.com/gauravjain0377/humanwrites  
**Version:** 1.0.0

---

## Key files

| File | Purpose |
|------|---------|
| `SKILL.md` | The skill definition — YAML frontmatter + full editor prompt with all 33 patterns |
| `README.md` | Installation, usage, pattern reference, and examples |
| `WARP.md` | This file — guidance for Warp terminal users |
| `LICENSE` | MIT |

`SKILL.md` is the source of truth. When behavior changes, update `SKILL.md` first, then update `README.md` to stay consistent.

---

## Installing in Claude Code

**Recommended (clone the repo):**

```bash
git clone https://github.com/gauravjain0377/humanwrites.git ~/.claude/skills/humanwrites
```

**Manual (skill file only):**

```bash
mkdir -p ~/.claude/skills/humanwrites
cp SKILL.md ~/.claude/skills/humanwrites/
```

**Update to latest:**

```bash
cd ~/.claude/skills/humanwrites && git pull
```

---

## Using the skill

In Claude Code:

```
/humanwrites

[paste your text here]
```

---

## Making changes safely

### Versioning (keep in sync)

- `SKILL.md` has a `version:` field in its YAML frontmatter
- `README.md` has a "Version History" section
- Always update both when bumping version

**When to bump:**
- New pattern → minor version (e.g. 3.0.0 → 3.1.0)
- Bug fix or example tweak → patch version (e.g. 3.0.0 → 3.0.1)
- Structural overhaul → major version (e.g. 3.0.0 → 4.0.0)

### Adding a new pattern

1. Add the pattern to `SKILL.md` under the appropriate section
2. Include a `**Before:**` and `**After:**` example
3. Add a row to the pattern table in `README.md`
4. Bump version in both files
5. Add a note to README.md version history

### Pattern numbering

Keep numbers stable — do not renumber existing patterns. New patterns continue from the current highest number. **Current highest:** 33.

### Editing `SKILL.md`

- Preserve valid YAML frontmatter formatting and indentation
- Keep the patterns consistent with the README table
- When adding before/after examples, make them realistic — not obviously made-up

### Documenting non-obvious fixes

If you change the prompt to handle a tricky failure mode (e.g. a repeated mis-edit or an unexpected tone shift), add a short note to `README.md`'s version history describing what was fixed and why.