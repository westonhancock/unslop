# Unslop eval

Do these checks on your edit before you give it to the user. Give each check a pass or a fail. If a check fails, correct the draft and do all the checks again. Do not give this task to a separate agent.

For a detect task, go to the Detect section.

## Voice (do these checks first)

1. Can the writer see their own voice in the edited draft?
2. Does the edit keep the vocabulary, rhythm, directness, humor, uncertainty, digressions, and level of polish of the writer?
3. Did you keep strong human sentences? Did you rewrite none of them only for consistency or to make all paragraphs equally neat?
4. Is the quantity of removed text proportional to the real quantity of slop? Did you remove no character with too much compression?
5. Does the edit keep the strong character, strong opinions, profanity, self-corrections, and honest admissions of the writer?
6. Did you keep the structure unless it caused problems? If you changed the order, does What changed give the reason?
7. If the user gave a writing sample, does the edit match the habits of the sample, and also its punctuation? The sample has priority over the default rules of this skill, but not over the sentence rules.

## The fact rule

1. Does the edit contain only facts, names, numbers, dates, quotes, and citations that are in the source?
2. Did you add no opinions, examples, or statistics?
3. Did you *invent* no hedges, admissions, uncertainties, or one-sentence paragraphs to make the text seem human?
4. If an edit changes what the text says, does What changed identify it?

## Content

1. Does each sentence give new information? Does no sentence only repeat or decorate the sentence before it?
2. Did you keep concrete facts, numbers, and specific details? Did you change none of them into general statements about importance?
3. Does the draft start with the information that the reader needs? Did you keep personal introductions that give context, tension, or character?
4. Is the main idea first where this makes the text clearer? Do all parts not have the same forced structure?
5. Does the draft use active voice with human subjects where possible, and verbs instead of nouns for actions?
6. Did you make confused sentences clear? Did you keep the changes in pace that are typical of the writer?
7. Does the text keep one register? Does no paragraph change to business language or consultant language?

## Sentence rules

Do not apply these checks to text in quotation marks.

1. Is each sentence complete, with a subject and a finite verb? Headings, list items, labels, and table cells are exceptions.
2. Does each sentence have 25 words or fewer?
3. Did you replace each phrasal verb with a one-word verb where one has the same meaning? Commands, code, and interface labels are exceptions.
4. Does the text contain no contractions? The possessive "'s" is not a contraction.
5. Does each pronoun refer to one clear noun?

## Words

1. Did you remove prohibited words, empty phrases, empty adverbs, and exaggerated claims? Quoted examples are exceptions.
2. Did you remove a word from the examine list only where it added no meaning?
3. If the writer used "idempotent" or "defensible," did you keep the word? If the writer did not use it, did you not add it?
4. Did you replace each metaphorical "shape" with the real structure, sequence, steps, or pattern? Literal shapes stay.

## Patterns

1. Did you remove binary contrasts, tailing negations, negative listings, rhetorical setups, and throat-clearing openers?
2. Did you remove faux-insight setups, "the part that" frames, signposting, colon reveals, and fake-candor openers?
3. Did you correct superficial `-ing` analysis, fake-strong verbs, synonym cycling, false ranges, and aphorism formulas?
4. Did you replace importance puffery, weasel attribution, and speculative gap-filling with plain facts and named sources? If no source exists, did you identify the claim?
5. Did you *delete* fake-profound kickers? Did you not rewrite them as better metaphors?
6. Did you remove summary-recap endings? Does the text end on a concrete point, a result, or a next action?
7. Did you remove chatbot artifacts and the introduction lines of fragmented headers?
8. Did you remove formatting slop? Examine emoji in headings, decorative bold, inline-header bullets, and bullet lists that must be prose. Also examine headings above very small sections and title case headings.
9. After a colon, is the text in sentence case? Exceptions are grammar, a proper noun, a title, and code.
10. Count the em dashes. Find `—`, `–`, and ` -- ` in the output. Short text must have none. Longer drafts can have one or two, only where they are clearly better than the alternatives. If a writing sample from the user uses em dashes, do not do this check.
11. Do hyphenated pairs have a hyphen only before the noun, and no hyphen after the noun?

## False positives

1. Did you remove text because of one pattern alone, not a group of patterns? If yes, put the text back.
2. Did you treat polish, formal vocabulary, one em dash, curly quotes, one short sentence for emphasis, or a mix of registers as evidence of AI? If yes, put the text back.
3. Did you keep the words from the lists that occur in quotations, titles, proper names, or examples?

## Final read

1. Does the draft have no mechanical symmetry, no repeated sentence patterns, and no series of short dramatic fragments?
2. Does the draft not have the regular rhythm of edited AI text: one short line and one long line in every paragraph?
3. Do the sections and paragraphs have truly different lengths? Do they not all follow one template?
4. Does the text sound natural when you read it aloud to an intelligent colleague?
5. Does the output match the invocation mode? Pasted text gets the full draft and What changed. File mode gets only the summary. Embedded mode gets only the text.

## Detect

1. Did you name each pattern, quote the line, and give a short correction?
2. Did you not rewrite the draft, not give a score, and not say that AI wrote it?
3. Did you examine each possible pattern against `references/false-positives.md` before you identified it?
4. Did you offer to edit the draft at the end?
