# Unslop

An agent skill that edits drafts into sharper, more human writing without flattening the writer's voice. It can also detect AI-slop patterns without rewriting anything.

It is plain Markdown, so it runs in any harness that loads skill-style instructions: Claude Code, Codex, OpenCode, and others.

## What it catches

If writing feels vaguely off and you can't say why, it's usually one of these. Each row is a real pattern, what it sounds like, and what it should have said.

### Sounds deep, says nothing

| Pattern | It sounds like | Better |
|---|---|---|
| Not X, it's Y | "This isn't a feature. It's a philosophy." | "The feature saves about an hour a week." |
| Fake-deep closer | "In the end, the best tool is the one you actually use." | Stop at your last real point. |
| Big-deal puffery | "The launch marks a pivotal moment for the company." | "It's the company's first paid product." |
| The fancy metaphor | "Trust is the currency of remote teams." | "Remote teams fall apart when people stop believing each other." |
| Trailing "-ing" filler | "We added search, highlighting our commitment to users." | "We added search, so you can find old drafts without leaving the page." |

### Stalling before the point

| Pattern | It sounds like | Better |
|---|---|---|
| Throat-clearing | "Here's the thing. Let me be clear." | Say the thing. |
| Announcing | "Let's dive in. Here's what you need to know." | Just start. |
| Secret-knowledge setup | "What nobody tells you about pricing..." | "Most teams price too low at launch." |
| The dramatic colon | "The best part: it learns." | "It gets better the more you use it." |
| Fake candor | "Honestly? It depends." | "It depends on how often you'll use it." |

### Vague where it should be specific

| Pattern | It sounds like | Better |
|---|---|---|
| Nobody said it | "Experts agree. Studies show." | Name the study, or drop the claim. |
| Dressed-up "is" | "The app serves as a centralized hub." | "The app tracks sponsors and due dates in one place." |
| Guessing out loud | "While details are limited, she likely grew up..." | "Her early life isn't documented." |
| Abstraction | "The integration improved efficiency." | "The integration cut deploy time from 40 minutes to 4." |

### The rhythm gives it away

| Pattern | It sounds like | Better |
|---|---|---|
| Everything in threes | "Fast, simple, and powerful." | Keep the two that are true. |
| Word-swapping | "The agent reviews it. The assistant scores it. The tool suggests fixes." | "The agent reviews it, scores it, and suggests fixes." |
| Fragment drama | "That's it. That's the whole thing." | Write the sentence. |
| Wrap-up ending | "In conclusion, ultimately, overall..." | The reader was just there. Cut it. |
| Em dash flood | "The plan, ambitious and untested, launches Friday." | A comma, period, or parentheses usually reads better. |

### Words that give it away

delve, leverage, utilize, foster, robust, seamless, streamline, empower, cutting-edge, tapestry, realm, paradigm shift, game changer, meticulous, transformative, elevate, harness, ever-evolving, this changes everything.

Plus: emoji headings, bold sprinkled mid-sentence, bullet lists where two sentences would do, "I hope this helps," and a dozen more in `SKILL.md`.

## Why another one

Unslop borrows from two existing skills and resolves the place where they disagree.

[no-ai-slop](https://github.com/petergyang/no-ai-slop) is a disciplined line editor. Its governing rule is the minimum effective edit, and it checks its own work against an external eval file. Its weakness is coverage and the absence of any brake on false positives.

[humanizer](https://github.com/blader/humanizer) is a port of [Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), with 33 numbered patterns, a strong false-positive list, and file and embedded invocation modes. Its weakness is a deletion bias: run it hard and it compresses distinctive prose into something correct and voiceless.

Unslop keeps no-ai-slop's restraint and eval loop, adds humanizer's pattern coverage, false-positive discipline, invocation modes, and voice calibration, and adds two rules neither has.

## The two additions

**Fabricated humanity is a fabrication.** Most skills list the signals of human writing (hedges, confessed errors, specific numbers, asides) and tell the model to preserve them. That list is one prompt away from becoming a generation target. Unslop frames it as *preserve when true, never add*. An invented confession or a decorative hedge reads as fake within a paragraph, and it is the next tell after the current ones get scrubbed.

**De-slopping has its own texture.** Alternating one short punchy line with one long line in every paragraph is a metronome, same as the thing it replaced. The eval checks for it explicitly, and the false-positive reference ends with an over-scrub check: does this read like the writer, or like a de-slopped draft?

## What it refuses to do

Guess whether AI wrote something. Detect mode names the pattern, quotes the line, and gives the fix. It does not score the draft or claim authorship. Detectors guess; named patterns are evidence you can check.

Change facts. A voice pass never alters or invents a fact, number, date, quote, source, or citation. An edit that changes what the text asserts is a content decision, and it gets flagged rather than folded in.

## Install

Paste this into Claude Code, Codex, or another harness:

> Install this skill globally: https://github.com/westonhancock/unslop

Or clone it into wherever your harness keeps skills:

```bash
git clone https://github.com/westonhancock/unslop.git ~/.claude/skills/unslop
```

## Use

**Edit a draft.** Paste it and invoke the skill. You get the edited draft and a short What changed section.

```
/unslop

[your draft]
```

**Detect without rewriting.**

```
/unslop is this AI slop?

[the text]
```

**Edit a file in place.** Prose only; code blocks, frontmatter, and link targets are left alone.

```
/unslop clean up the prose in docs/launch-post.md
```

**Match your voice.** Give it a sample of your own writing and it matches your habits, overriding every style rule in the skill including the em dash guidance.

```
/unslop here's a sample of how I write: [sample]

Now edit this draft: [draft]
```

## Files

| File | What it is |
|---|---|
| `SKILL.md` | The editing rules, patterns, and workflow |
| `eval.md` | Pass/fail checks the skill runs on its own edit before returning it |
| `references/false-positives.md` | What is not an AI tell, and the human signals to preserve |

## License

MIT. The pattern catalog draws on [Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) by WikiProject AI Cleanup, and on the MIT-licensed [no-ai-slop](https://github.com/petergyang/no-ai-slop) and [humanizer](https://github.com/blader/humanizer).
