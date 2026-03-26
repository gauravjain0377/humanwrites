<div align="center">

# HumanWrites

### Strip the AI. Keep the meaning. Add the soul.

[![Version](https://img.shields.io/badge/version-3.0.0-7c3aed?style=flat-square)](https://github.com/gauravjain0377/humanwrites)
[![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](LICENSE)
[![Claude Skill](https://img.shields.io/badge/Claude-Skill-orange?style=flat-square)](SKILL.md)
[![Patterns](https://img.shields.io/badge/AI%20Patterns-33-brightgreen?style=flat-square)](SKILL.md)

A Claude Code skill that detects and removes **33 AI writing patterns**, turning AI-generated text into something that sounds like a real person actually wrote it.

**By [Gaurav Jain](https://github.com/gauravjain0377)**

</div>

---

## Why this exists

Most "humanizer" tools do a surface-level word swap. This skill goes deeper — it targets the *structural* reasons AI writing sounds AI-generated: the inflated importance, the fake transitions, the rhythm that's too perfect, and the voice that has no opinion.

Based on [Wikipedia's "Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) guide — one of the most thorough documented lists of AI writing patterns — plus 8 original additions covering passive voice, filler transitions, rhetorical questions, and more.

---

## Installation

### One command (recommended)

```bash
git clone https://github.com/gauravjain0377/humanwrites.git ~/.claude/skills/humanwrites
```

### Manual (skill file only)

```bash
mkdir -p ~/.claude/skills/humanwrites
curl -o ~/.claude/skills/humanwrites/SKILL.md \
  https://raw.githubusercontent.com/gauravjain0377/humanwrites/main/SKILL.md
```

### Update to the latest version

```bash
cd ~/.claude/skills/humanwrites && git pull
```

---

## Usage

In Claude Code, invoke the skill:

```
/humanwrites

[paste your AI-generated text here]
```

Or ask Claude directly:

```
Please humanize this text: [your text]
```

**What happens next:**

1. Quick scan — flags AI patterns found in your text
2. Draft rewrite — first pass through all 33 patterns
3. Self-audit — "What still sounds AI-generated?"
4. Final rewrite — cleans up any remaining tells
5. Change summary — list of everything that was fixed

---

## Quick Scan

Before a full pass, check for these red flags:

| Red Flag | Signal |
|----------|--------|
| "Additionally" / "Furthermore" / "Moreover" opening a paragraph | ⚠️ |
| "It is worth noting" / "It should be noted" | ⚠️ |
| Em dashes (—) used more than twice | ⚠️ |
| Ends with "In conclusion" or "The future looks bright" | ⚠️ |
| Emoji in content body (🚀 💡 ✅) | ⚠️ |
| Bold headers on every bullet (**Speed:** ...) | ⚠️ |
| "serves as" / "stands as" instead of "is" | ⚠️ |
| "has become" / "have emerged" / "has evolved" | ⚠️ |
| Numbered list where prose would read better | ⚠️ |
| Passive voice: "It was determined", "It has been shown" | ⚠️ |

**Score:** 0–1 = light touch · 2–3 = moderate rewrite · 4–6 = heavy rewrite · 7+ = start over

---

## 33 Patterns Detected

### Content Patterns

| # | Pattern | Before → After |
|---|---------|----------------|
| 1 | **Significance inflation** | "marking a pivotal moment in the evolution of..." → "was established in 1989 to collect regional statistics" |
| 2 | **Notability name-dropping** | "cited in NYT, BBC, FT, and The Hindu" → "In a 2024 NYT interview, she argued..." |
| 3 | **Superficial -ing analyses** | "symbolizing... reflecting... showcasing..." → Remove or provide an actual source |
| 4 | **Promotional language** | "nestled within the breathtaking region" → "is a town in the Gonder region" |
| 5 | **Vague attributions** | "Experts believe it plays a crucial role" → "according to a 2019 survey by..." |
| 6 | **Formulaic challenges** | "Despite challenges... continues to thrive" → Replace with specific facts |

### Language Patterns

| # | Pattern | Before → After |
|---|---------|----------------|
| 7 | **AI vocabulary** | "testament... landscape... showcasing..." → plain, direct words |
| 8 | **Copula avoidance** | "serves as... features... boasts" → "is... has" |
| 9 | **Negative parallelisms** | "It's not just X, it's Y" → State the point directly |
| 10 | **Rule of three** | "innovation, inspiration, and insights" → use the natural number of items |
| 11 | **Synonym cycling** | "protagonist... main character... central figure..." → pick one and stick to it |
| 12 | **False ranges** | "from the Big Bang to dark matter" → list the topics directly |

### Style Patterns

| # | Pattern | Before → After |
|---|---------|----------------|
| 13 | **Em dash overuse** | "institutions—not people—yet this continues—" → commas or periods |
| 14 | **Boldface overuse** | "**OKRs**, **KPIs**, **BMC**" → "OKRs, KPIs, BMC" |
| 15 | **Inline-header lists** | "**Performance:** Performance improved" → rewrite as prose |
| 16 | **Title Case Headings** | "Strategic Negotiations And Partnerships" → "Strategic negotiations and partnerships" |
| 17 | **Emojis** | "🚀 Launch Phase: 💡 Key Insight:" → plain text |
| 18 | **Curly quotes** | `said "the project"` → `said "the project"` |
| 25 | **Hyphenated word pairs** | "cross-functional, data-driven, client-facing" → drop hyphens from common pairs |

### Communication Patterns

| # | Pattern | Before → After |
|---|---------|----------------|
| 19 | **Chatbot artifacts** | "I hope this helps! Let me know if..." → Remove entirely |
| 20 | **Cutoff disclaimers** | "While details are limited based on available sources..." → Find a source or remove it |
| 21 | **Sycophantic tone** | "Great question! You're absolutely right!" → Respond directly |

### Filler and Hedging

| # | Pattern | Before → After |
|---|---------|----------------|
| 22 | **Filler phrases** | "In order to", "Due to the fact that" → "To", "Because" |
| 23 | **Excessive hedging** | "could potentially possibly be argued that" → "may" |
| 24 | **Generic conclusions** | "The future looks bright. Exciting times lie ahead." → Specific plans or facts |

### New in v3.0.0

| # | Pattern | Before → After |
|---|---------|----------------|
| 26 | **Passive voice overuse** | "It was determined that..." → "Researchers found..." |
| 27 | **Filler transition words** | "Furthermore... Moreover... Nevertheless..." → Cut or rewrite |
| 28 | **"In conclusion" closers** | "In conclusion, the research shows..." → State the point directly |
| 29 | **Rhetorical questions** | "But what does this mean for us?" → Just answer it |
| 30 | **Over-explaining the obvious** | Defining "AI" for a tech audience → Remove the definition |
| 31 | **Numbered list overuse** | Everything becomes 1. 2. 3. → prose when it flows better |
| 32 | **"It is worth noting"** | "It should be noted that..." → State it directly |
| 33 | **Present perfect overuse** | "has become... have emerged... has evolved" → past or present tense |

---

## Full Example

**Before (AI-generated):**

> Great question! Here is an essay on this topic. I hope this helps!
>
> AI-assisted coding serves as an enduring testament to the transformative potential of large language models, marking a pivotal moment in the evolution of software development. In today's rapidly evolving technological landscape, these groundbreaking tools—nestled at the intersection of research and practice—are reshaping how engineers ideate, iterate, and deliver, underscoring their vital role in modern workflows.
>
> - 💡 **Speed:** Code generation is significantly faster, reducing friction and empowering developers.
> - 🚀 **Quality:** Output quality has been enhanced through improved training, contributing to higher standards.
> - ✅ **Adoption:** Usage continues to grow, reflecting broader industry trends.
>
> In conclusion, the future looks bright. Exciting times lie ahead as we continue this journey toward excellence. Let me know if you'd like me to expand on any section!

**After (Humanized):**

> AI coding assistants can speed up the boring parts. They're great at boilerplate — config files, the glue code you don't want to write. Not so great at knowing when they're wrong.
>
> I've accepted suggestions that compiled, passed lint, and still missed the point because I stopped paying attention. That's the real risk.
>
> If you treat it like autocomplete and review everything, it's useful. If you use it to avoid thinking, it helps you ship bugs faster.
>
> The only real backstop is tests. Without them, you're judging vibes.

---

## Contributing

Found a new AI writing pattern? Open a PR:

1. Add it to `SKILL.md` under the appropriate section with a Before/After example
2. Add a row to the pattern table in `README.md`
3. Bump the version in both files (patch for a minor fix, minor for a new pattern)
4. Add a note to the version history below

---

## Version History

- **3.0.0** — 8 new patterns (26–33): passive voice, filler transitions, "in conclusion" closers, rhetorical questions, over-explaining, list overuse, "it is worth noting", present perfect overuse. New Quick Scan checklist. Tone Preservation guide. Full README rewrite. *(Gaurav Jain)*
- **2.3.0** — Added pattern #25: hyphenated word pair overuse *(blader)*
- **2.2.0** — Added final "obviously AI generated" audit + second-pass rewrite prompts *(blader)*
- **2.1.1** — Fixed pattern #18 example (curly quotes vs straight quotes) *(blader)*
- **2.1.0** — Before/after examples for all 24 patterns *(blader)*
- **2.0.0** — Complete rewrite based on raw Wikipedia article content *(blader)*
- **1.0.0** — Initial release *(blader)*

---

## References

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) — Primary source
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) — Maintaining organization
- Original skill (v1–v2.3): [blader/humanizer](https://github.com/blader/humanizer)

---

## License

MIT © [Gaurav Jain](https://github.com/gauravjain0377)
