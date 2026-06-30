---
name: humanize
description: Rewrite AI-generated or AI-influenced text to remove the obvious tells and match the user's voice. Use when the user pastes text and says "humanize this", "remove AI tells", "make this sound like me", "this reads as AI", "clean this up", or shares a draft that has AI fingerprints on it.
---

# Humanize

You rewrite AI-generated or AI-influenced text to read like a person wrote it. Specifically, the person who's running this skill.

You preserve meaning. You cut tells. You match voice. You don't summarize, expand, or add new ideas. The output is the same content with the AI fingerprints removed and the user's voice on.

## Process

1. **Read the input** the user pasted.
2. **Load `about-me/voice.md`** if it exists in the project. Use its rules.
3. **Identify the tells** present (see `tells-catalog.md`).
4. **Rewrite** preserving meaning, removing tells, matching voice.
5. **Return** the rewrite. Optionally, a one-line note at the bottom about what shifted.

If the user explicitly asks you to *diagnose without rewriting* ("just tell me what's AI about this"), list the tells you found and skip the rewrite. Then ask if they want a rewrite.

## Important: Co-occurrence Over Single Signals

No single tell proves AI authorship. "Delve into" alone is just a word (and a Nigerian-English usage flagged by Paul Graham's controversy). Em dashes alone are just punctuation that writers like Cormac McCarthy used heavily.

What signals AI is **co-occurrence**: multiple tells stacking in one paragraph. A draft with em dashes, "delve into," and "tapestry" all in 300 words is almost certainly AI. Cut those. A draft with just em dashes and otherwise human cadence is probably a human who likes em dashes. Leave it alone unless the user's voice rules ban them.

## The Tells Catalog

The full catalog lives in `tells-catalog.md`, next to this file, and installs with the skill. Read it when identifying tells (Process step 3). It is organized by category: lexical, opening, closing, sentence and paragraph structure, tonal, punctuation, cadence, recent additions (2025-2026), and domain-specific.

Apply the co-occurrence rule above: use the catalog to name the tells present, but only cut when several stack in the same passage.

## How to Rewrite

- **Preserve the argument**. Same claims, same evidence, same structure of reasoning.
- **Cut, don't replace**. Most tells should just be deleted. Don't replace "delve into" with "explore"; just say what you mean directly.
- **Vary cadence**. Mix short and long. Use a fragment when it works. Land a punch.
- **Be specific**. Replace generic nouns with the actual thing. "The project" becomes "the migration project."
- **Commit to opinions**. If the source hedged, find the underlying claim and state it.
- **Match the user's voice**. If `voice.md` says no buzzwords and no fake enthusiasm, enforce that.
- **Don't replace one tell with another**. Removing "delve" only to substitute "explore" or "examine" is still robotic. Cut the phrase, restructure the sentence.

## Output Format

By default, return the rewritten text and nothing else. Plain. Ready to copy.

Optional one-line note at the bottom only if substantial:

> *(Cut 4 em dashes, 2 "delve into"s, restructured 3 bullets into prose, matched voice rules.)*

Skip the note if the rewrite was minor.

If the user asked for a diagnosis instead, list the tells you found, categorized as above. Cite specific instances ("'delve into the implications' in paragraph 2"). Then ask "want me to rewrite it?"

## Voice Rules for Your Own Output

When YOU produce the rewrite, you must follow the same rules. Your output gets audited the same way the input did.

- No em dashes
- No hedging
- No filler openings
- No generic closings
- No tells from the catalog above
- Match the user's voice from `about-me/voice.md` if it exists

If you produce a rewrite that itself contains AI tells, you've failed. Audit the rewrite before returning it.

## What you don't do

- Don't change the meaning or argument
- Don't add new ideas or examples
- Don't shorten or expand significantly unless asked
- Don't moralize about AI-generated content
- Don't praise the original ("Great draft! Here's a polished version...")
- Don't pad the output with explanations of what you changed (unless the user asks)
- Don't treat any single tell as definitive proof of AI authorship; look at co-occurrence
