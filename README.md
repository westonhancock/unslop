# Unslop

Unslop is an agent skill. It edits a draft to make the text clearer and more human, and it keeps the voice of the writer. It can also find AI-slop patterns in a draft without a rewrite.

The skill is plain Markdown. It works in each harness that reads skill instructions, for example Claude Code, Codex, and OpenCode.

## What it finds

If a text seems wrong and you cannot say why, the cause is usually one of the patterns below. Each row gives a pattern, an example, and a better version.

### Text that sounds deep but says nothing

| Pattern | Example | Better |
|---|---|---|
| Not X, it's Y | "This isn't a feature. It's a philosophy." | "The feature saves about an hour a week." |
| Fake-deep closer | "In the end, the best tool is the one you actually use." | Stop at your last real point. |
| Big-deal puffery | "The launch marks a pivotal moment for the company." | "It is the company's first paid product." |
| The fancy metaphor | "Trust is the currency of remote teams." | "Remote teams fail when people stop trusting each other." |
| Trailing "-ing" filler | "We added search, highlighting our commitment to users." | "We added search, so you can find old drafts without leaving the page." |

### Text that delays the main idea

| Pattern | Example | Better |
|---|---|---|
| Throat-clearing | "Here's the thing. Let me be clear." | Write the main idea. |
| Announcing | "Let's dive in. Here's what you need to know." | Start with the content. |
| Secret-knowledge setup | "What nobody tells you about pricing..." | "Most teams set prices too low at launch." |
| The part that | "The part that makes it work is the eval file." | "It works because a separate agent grades the output." |
| The dramatic colon | "The best part: it learns." | "It gets better the more you use it." |
| Fake candor | "Honestly? It depends." | "The answer depends on how often you will use it." |

### Text that is vague where it must be specific

| Pattern | Example | Better |
|---|---|---|
| No source | "Experts agree. Studies show." | Name the study, or remove the claim. |
| Decorated "is" | "The app serves as a centralized hub." | "The app tracks sponsors and due dates in one place." |
| Guessing | "While details are limited, she likely grew up..." | "Her early life is not documented." |
| Abstraction | "The integration improved efficiency." | "The integration cut deploy time from 40 minutes to 4." |

### Rhythm that shows AI

| Pattern | Example | Better |
|---|---|---|
| Everything in threes | "Fast, simple, and powerful." | Keep the two that are true. |
| Synonym changes | "The agent reviews it. The assistant scores it. The tool suggests fixes." | "The agent reviews it, scores it, and suggests fixes." |
| Fragment drama | "That's it. That's the whole thing." | Write a complete sentence. |
| Summary ending | "In conclusion, ultimately, overall..." | Remove it. The reader read the text a short time before. |
| Too many em dashes | "The plan, ambitious and untested, launches Friday." | A comma, period, or parentheses is usually better. |

### Sentence rules

The skill applies these rules to each draft. A writing sample does not change them. Text in quotation marks is the only exception.

| Rule | Example | Better |
|---|---|---|
| No fragments | "We shipped it Friday. On time." | "We shipped it Friday, on time." |
| 25 words or fewer in each sentence | A 40-word spoken sentence | Two or three shorter sentences |
| No phrasal verbs | "We need to find out why." | "We need to learn why." |
| No contractions | "It doesn't scale." | "It does not scale." |
| Clear pronouns | "The API calls the cache, and it fails." | "The API calls the cache, and the cache fails." |

### Words that show AI

delve, leverage, utilize, foster, robust, seamless, streamline, empower, cutting-edge, tapestry, realm, paradigm shift, game changer, meticulous, transformative, elevate, harness, ever-evolving, this changes everything.

The skill uses a different rule for two words: **idempotent** and **defensible**. These are real words, and a writer can use them correctly. The skill never adds them to your draft. If you wrote them, the skill does not change them. Where a model wants to use one of them, the skill writes the plain version: "running it twice is safe," or "this holds up under scrutiny."

The skill prohibits **shape** only as a metaphor. A process, a product, or a strategy has no shape. Name the real thing: the structure, the sequence, the steps, or the layout. Physical shapes, geometry, and visual design can use the word.

The skill also finds emoji in headings, bold text in the middle of sentences, and bullet lists where two sentences are better. It finds "I hope this helps" and more than ten other patterns. `SKILL.md` lists all of them.

## Installation

Paste this text into Claude Code, Codex, or a different harness:

> Install this skill globally: https://github.com/westonhancock/unslop

You can also clone the repository into the skills directory of your harness:

```bash
git clone https://github.com/westonhancock/unslop.git ~/.claude/skills/unslop
```

## Why another skill

Unslop uses parts of two other skills. Where the two skills disagree, Unslop chooses one rule.

[no-ai-slop](https://github.com/petergyang/no-ai-slop) is a careful line editor. Its main rule is the minimum effective edit, and it examines its own work with an eval file. It has two weak points: it finds fewer patterns, and it has no rule against false positives.

[humanizer](https://github.com/blader/humanizer) is a version of [Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing). It has 33 numbered patterns, a strong list of false positives, and a file mode and an embedded mode. Its weak point is that it removes too much. If you use it on a draft with a strong voice, the result is correct but has no voice.

Unslop keeps the careful edit and the eval file from no-ai-slop. From humanizer, it takes the pattern list, the false-positive rules, the invocation modes, and the voice calibration. It also adds two rules that neither skill has.

## The two new rules

**Invented human traits are fabrications.** Most skills list the signs of human writing (hedges, admitted errors, specific numbers, comments in parentheses). They tell the model to keep these signs. A model can easily misread that list as a list of traits to add. Unslop says to keep these traits only when they are true, and never to add them. Readers quickly see that an invented admission or a decorative hedge is false. These invented traits will become the next AI pattern after editors remove the current patterns.

**Edited AI text has its own style.** In some edited drafts, each paragraph has one short line and then one long line. That regular rhythm is as mechanical as the original AI text. The eval file has a check for this rhythm. The false-positive reference ends with a check for too much edit: does the result read like the writer, or like an edited AI draft?

## What it does not do

The skill does not guess if AI wrote a text. Detect mode names each pattern, quotes the line, and gives the correction. The skill does not give a score and does not say who wrote the text. AI detectors only guess. A named pattern is evidence that you can examine.

The skill does not change facts. An edit for voice never changes or adds a fact, number, date, quote, source, or citation. If an edit changes what the text says, the edit is a decision about content. The skill identifies that change and does not include it silently.

## Usage

**Edit a draft.** Paste the draft and start the skill. The result is the edited draft and a short What changed section.

```
/unslop

[your draft]
```

**Find patterns without a rewrite.**

```
/unslop is this AI slop?

[the text]
```

**Edit a file.** The skill edits only prose. It does not change code blocks, frontmatter, or link targets.

```
/unslop clean up the prose in docs/launch-post.md
```

**Match your voice.** Give a sample of your writing. The skill matches your habits. The sample has priority over all style rules in the skill, and also over the em dash rule. The sentence rules are the exception.

```
/unslop here's a sample of how I write: [sample]

Now edit this draft: [draft]
```

## Files

| File | Contents |
|---|---|
| `SKILL.md` | The rules, the patterns, and the procedure |
| `eval.md` | Pass or fail checks that the skill does on its edit before it gives the result |
| `references/false-positives.md` | The things that are not AI patterns, and the human signs to keep |

## License

MIT. The pattern list uses content from [Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) by WikiProject AI Cleanup. It also uses content from [no-ai-slop](https://github.com/petergyang/no-ai-slop) and [humanizer](https://github.com/blader/humanizer), which both have the MIT license.
