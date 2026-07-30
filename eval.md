# Unslop eval

Run this on your own edit before returning it. Answer each check pass or fail. If any check fails, fix the draft and run the checks again. Do not delegate this to a separate agent.

For detect requests, skip to the Detect section.

## Voice preservation (check these first)

1. Would the writer recognize the edited draft as their own voice?
2. Does it preserve the writer's distinctive vocabulary, cadence, bluntness, humor, uncertainty, digressions, and level of polish?
3. Does it leave strong human sentences alone instead of rewriting them for consistency or making every paragraph equally tidy?
4. Is the amount of cutting proportional to the actual slop, with no aggressive compression that stripped out character?
5. Are useful edge, strong opinions, profanity, self-interruptions, and honest admissions still there?
6. Was structure preserved unless it was hurting the piece, with any reorganization explained in What changed?
7. If the user supplied a writing sample, does the edit match its habits, including punctuation, over this skill's defaults?

## The iron rule

1. Does the edit contain no fact, name, number, date, quote, or citation absent from the source?
2. Were no opinions, examples, or stats added?
3. Were no hedges, confessions, uncertainties, or one-word paragraphs *invented* to manufacture humanity?
4. Is any edit that changes what the text asserts flagged in What changed rather than folded in silently?

## Substance

1. Does each sentence know something the one before it didn't, rather than restating or decorating?
2. Are concrete facts, numbers, and specific details protected rather than smoothed into generic importance?
3. Does the draft lead with what the reader needs while keeping personal setup that adds context, tension, or character?
4. Are points front-loaded where that improves clarity, without forcing every unit into the same structure?
5. Does it use active voice with human subjects where possible, and direct verbs over nominalizations?
6. Are genuinely tangled sentences fixed while clear spoken cadence, fragments, and changes in pace remain intact?
7. Does the piece hold one register throughout, with no seam into business abstraction or consultant-ese?

## Words

1. Are banned words, empty filler phrases, often-empty adverbs, and inflated claims removed unless quoted as examples?
2. Were watch-list words cut only where they were doing no work, rather than scrubbed on sight?
3. Were "idempotent" and "defensible" left alone if the writer used them, and never introduced if they weren't already there?

## Patterns

1. Are binary contrasts, tailing negations, negative listings, rhetorical setups, and throat-clearing openers removed?
2. Are faux-insight setups, signposting, colon reveals, and fake-candor openers removed?
3. Are superficial `-ing` analyses, fake-strong verbs, synonym cycling, false ranges, and aphorism formulas fixed?
4. Are importance puffery, weasel attribution, and speculative gap-filling replaced with plain facts and named sources, or flagged when no source exists?
5. Are fake-profound kicker lines *deleted* rather than rewritten into better metaphors?
6. Are summary-recap endings cut so the piece ends on a concrete point, takeaway, or next action?
7. Are chatbot artifacts and fragmented header warm-up lines gone?
8. Is formatting slop removed: emoji headings, decorative bold, inline-header bullets, bullets that should be prose, headers over tiny sections, title case headings?
9. Are colons followed by sentence case unless grammar, a proper noun, a title, or code requires otherwise?
10. Em dash count: scan the output for `—`, `–`, and ` -- `. None in short copy, at most one or two in longer drafts where they clearly beat the alternatives. Skip this check if a user writing sample uses them.
11. Are hyphenated pairs attributive-only, unhyphenated after the noun?

## False positives

1. Did anything get cut on a single isolated tell rather than a cluster?
2. Was polish, formal vocabulary, a lone em dash, curly quotes, one short emphatic sentence, or a mixed register treated as proof of AI? If so, restore it.
3. Were watched phrases inside quotations, titles, proper names, or examples left untouched?

## Final read

1. Does the draft avoid robotic symmetry, repeated sentence shapes, and stacked punchy fragments?
2. Does it avoid the de-slopping metronome: a short punchy line alternating with a long one in every paragraph?
3. Are sections and paragraphs genuinely uneven in length, rather than a uniform template?
4. Would it sound natural read aloud to a sharp colleague?
5. Does the output match the invocation mode: full draft plus What changed for pasted text, summary only for file mode, bare text for embedded?

## Detect

1. Is every pattern named, with the offending line quoted and a short fix?
2. Was nothing rewritten, scored, or claimed to be AI-authored?
3. Were false positives checked against `references/false-positives.md` before flagging?
4. Was an offer to edit the draft included at the end?
