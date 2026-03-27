<div align="center">

# HumanWrites

### Strip the AI. Keep the meaning. Add the soul.

[![Version](https://img.shields.io/badge/version-2.0.3-7c3aed?style=flat-square)](https://github.com/gauravjain0377/humanwrites)
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

### Method 1 — Claude Web UI *(claude.ai)*

1. Click the green **Code** button at the top of this repository and select **Download ZIP**, then extract the folder.
2. Open [claude.ai](https://claude.ai) and create a new **Project**.
3. Drag and drop the extracted `humanwrites` files into your **Project Knowledge**.
4. Done! Any chat within that project will automatically understand how to rewrite your text without needing to prompt it every time.

---

### Method 2 — Claude Code *(Terminal)*

**Option A: Simple Drag & Drop**
1. Download the ZIP and extract it.
2. Move the entire `humanwrites` folder into your `~/.claude/skills/` directory.

**Option B: Terminal Install**
```bash
git clone https://github.com/gauravjain0377/humanwrites.git ~/.claude/skills/humanwrites
```

**Update to the latest version:**

```bash
cd ~/.claude/skills/humanwrites && git pull
```

---

## Usage

Once installed, use it in any Claude conversation:

```
/humanwrites

[paste your AI-generated text here]
```

Or just ask naturally:

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

## What Gets Detected

**33 patterns across 6 categories.** The full skill file has detailed before/after examples for every one. Here's a quick map:

### 📌 Content
AI inflates importance, fakes notability, and adds fake depth with `-ing` phrases.
> *Words to watch:* `pivotal`, `testament`, `serves as a reminder`, `symbolizing`, `reflecting`, `showcasing`, `Experts believe`, `despite challenges`

### 📌 Language
AI avoids simple words, repeats ideas with synonyms, and forces "impressive" structure.
> *Words to watch:* `Additionally`, `landscape`, `vibrant`, `delve`, `underscore`, `boasts`, `It's not just X it's Y`, `from X to Y`

### 📌 Style
AI overuses formatting signals to look organized and punchy.
> *Watch for:* em dashes (—) everywhere · **bolded every phrase** · 🚀 emojis in content · Title Case Every Heading · `cross-functional` hyphenation

### 📌 Communication
AI chatbot phrases that get copy-pasted into real content.
> *Watch for:* `I hope this helps!` · `Let me know if you'd like...` · `Great question!` · `As of my last training update...`

### 📌 Filler & Hedging
AI pads length without adding meaning.
> *Words to watch:* `In order to`, `Due to the fact that`, `could potentially possibly`, `The future looks bright`, `Exciting times lie ahead`

### 📌 New patterns (v2.0.3)
Freshly added — often missed by other tools.
> *Watch for:* `It was determined that` (passive) · `Furthermore / Moreover` openers · `In conclusion` closers · rhetorical questions as transitions · `It is worth noting` · `has become / have emerged` (present perfect overuse)

> Full before/after examples for all 33 patterns are in [`SKILL.md`](SKILL.md).

---

## Full Example

This is a typical LinkedIn post written with AI help — and what it looks like after running `/humanwrites` on it.

**Before (AI-generated):**

> It is worth noting that professional growth is rarely a linear journey. In today's rapidly evolving landscape, those who seek to foster a growth mindset stand as examples of resilience and commitment to excellence.
>
> It's not just about the skills you acquire — it's about the person you're becoming. The interplay between continuous learning, adaptability, and cross-functional collaboration cannot be understated. Furthermore, professionals who align with these values are better positioned to navigate the complexities of modern career development.
>
> - 💡 **Continuous Learning:** Staying ahead requires a commitment to lifelong education and skill enhancement
> - 🚀 **Adaptability:** Embracing change is crucial to remaining relevant in a dynamic environment
> - ✅ **Collaboration:** Working cross-functionally ensures alignment and drives better outcomes
>
> In conclusion, the future belongs to those willing to invest in themselves. I hope this resonates with you. Let me know your thoughts in the comments below!

**Patterns found:** `It is worth noting` · `rapidly evolving landscape` · `not just about X, it's about Y` · `Furthermore` · `cannot be understated` · emoji headers · bold inline-header list · `In conclusion` · `I hope this resonates` · rule of three · copula avoidance (`stand as examples`)

**After (Humanized):**

> I spent two years trying to become the kind of professional who had everything figured out. I didn't.
>
> What actually helped: learning one concrete skill per quarter instead of committing to vague "growth," saying no to meetings where my only job was to listen, and asking questions out loud instead of pretending I already knew the answer.
>
> None of that is new advice. But it's different from what I was told when I started — which was mostly to work hard and stay visible. Visibility without something real behind it is just noise in a louder room.

---

## Contributing

Found a new AI writing pattern? Open a PR:

1. Add it to `SKILL.md` under the appropriate section with a Before/After example
2. Add a row to the pattern table in `README.md`
3. Bump the version in both files (patch for a minor fix, minor for a new pattern)
4. Add a note to the version history below

---

## Version History

- **2.0.3** — Added 8 new patterns (26–33): passive voice, filler transitions, "in conclusion" closers, rhetorical questions, over-explaining, list overuse, "it is worth noting", present perfect overuse
- **2.0.2** — Added Tone Preservation guide and Quick Scan checklist
- **2.0.1** — Improved before/after examples for patterns #3, #7, and #11. Fixed curly quotes example (#18)
- **2.0.0** — Major rewrite. Added personality and soul section. Added self-audit step ("What makes this obviously AI generated?") and second-pass rewrite. Restructured output format
- **1.4.0** — Added pattern #25: hyphenated word pair overuse. Minor wording fixes across existing examples
- **1.3.0** — Added filler and hedging patterns (#22–24): filler phrases, excessive hedging, generic conclusions
- **1.2.0** — Added communication patterns (#19–21): chatbot artifacts, knowledge-cutoff disclaimers, sycophantic tone
- **1.1.0** — Added before/after examples for all 18 patterns. Reorganized into Content, Language, and Style sections
- **1.0.0** — Initial release. 18 patterns based on Wikipedia's Signs of AI writing guide

---

## Further Reading

If you want to go deeper on why AI writing sounds the way it does:

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) — the most complete documented list of AI writing patterns, maintained by WikiProject AI Cleanup. This is the primary research source behind this skill.
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) — the Wikipedia editors working to identify and fix AI-generated articles. Their observations are the empirical foundation for most patterns here.
- [Key insight](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing#Key_characteristics): *"LLMs use statistical algorithms to guess what should come next. The result tends toward the most statistically likely result that applies to the widest variety of cases."* — this is why AI writing feels generic.
- [How to detect AI-generated text](https://en.wikipedia.org/wiki/AI_detection_software) — background on detection methods, and why pattern-based editing beats automated detectors for actual writing quality.

---

## License

MIT © [Gaurav Jain](https://github.com/gauravjain0377)
