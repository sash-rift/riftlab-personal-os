# Catalog of AI Tells

The reference catalog for the `humanize` skill. Read it when identifying tells. No single entry proves AI authorship; act on co-occurrence (see the skill's process).

### Lexical tells (specific words and phrases)

**Inflated verbs**: delve, leverage, utilize, facilitate, foster, harness, elevate, unlock, unleash, navigate (metaphorical), streamline, empower, garner, underscore, showcase, encompass, exemplify, embark, align, resonate.

**Dramatic abstract nouns**: tapestry, landscape (metaphorical), realm, journey, beacon, cornerstone, testament, paradigm, ecosystem, fabric, mosaic, intersection, nexus, frontier, gateway.

**Marketing adjectives**: vibrant, robust, comprehensive, multifaceted, intricate, nuanced, meticulous, pivotal, profound, seamless, cutting-edge, groundbreaking, transformative, innovative, revolutionary, dynamic, holistic, bespoke, enduring, renowned.

**Transition openers as paragraph starts**: Moreover, Furthermore, Additionally, Consequently, Thus, In essence, In summary, In conclusion, Notably, Importantly, Crucially, Ultimately.

**Telltale phrases**:
- "It's important to note that..."
- "It's worth noting..."
- "In today's [fast-paced / digital / ever-evolving] world"
- "When it comes to..."
- "At the heart of..."
- "Plays a [vital / crucial / pivotal] role in..."
- "A testament to..."
- "Stands as a..."
- "Serves as a..."
- "Sheds light on..."
- "Reflects the broader..."
- "Paints a picture of..."
- "The world of [X]"
- "Navigate the complexities of..."

**Sycophantic openers (chat-format leakage)**: "Certainly!", "Absolutely!", "Great question!", "I'd be happy to...", "What a fascinating..."

### Opening tells

- "I hope this finds you well"
- "Just wanted to circle back"
- "Thanks for reaching out"
- "Here's a comprehensive overview of..."
- "Let's dive in"
- "Let me break this down"
- "Here are some thoughts on..."
- "In this [post / article / piece], we'll explore..."

### Closing tells

- "I hope this helps!"
- "Let me know if you need anything else"
- "Feel free to ask if you have any questions"
- "In conclusion, ..."
- "In summary, ..."
- "To wrap up, ..."
- "Overall, ..."
- "Ultimately, ..."

### Sentence and paragraph structure tells

- **Trailing "-ing" clauses** that add vague analysis: "..., highlighting the importance of X." / "..., reflecting a broader trend." / "..., ensuring seamless integration." (GPT-4o uses present-participial clauses about 5x the human rate.)
- **"Not X, but Y"** corrective antithesis. **Banned outright** per the user's voice rules.
- **"Not only... but also..."** parallelism.
- **Rule-of-three triplets** with the longest item last: "fast, reliable, and transformative." Reads as campaign copy.
- **Hedge opener + rule-of-three body + summary closer** as paragraph template.
- **"Challenges → Despite this, X continues to thrive"** pivot.
- **Nominalization-heavy phrases**: "the implementation of," "the optimization of," "the leveraging of" replacing simple verbs.
- **Avoidance of plain "is/are"** in favor of "serves as," "stands as," "represents," "marks," "features," "boasts."
- **Elegant variation**: never reusing the same noun within a paragraph; thesaurus synonyms shoehorned in.
- **Mandatory summary or recap** at the end of every section, even short ones.

### Tonal tells

- Formal impersonal register regardless of topic
- Lower lexical diversity; no idiom, slang, or sentence fragments
- Relentlessly positive or motivational; no genuine ambivalence
- Vague third-party attribution: "Experts argue...", "Industry reports suggest...", "Observers have noted...", "Some critics argue..."
- "Balanced both-sides" framing on every topic, refusing to commit
- Knowledge-cutoff or epistemic disclaimers unprompted ("As of my training data...")
- Defensive collaborative phrasing ("I appreciate the feedback, but...")

### Punctuation tells

- **Em dashes** as rhetorical pivots, often many per piece. The most famous tell. Replace with periods, commas, parens, or colons.
- **Curly smart quotes** ("" '') in contexts where straight quotes are normal
- **Title Case in every heading** ("Impact of Technology and Digitalization")
- **Mechanical bolding** of every keyword instance
- **Colon-then-bold list pattern**: "**Innovation:** AI is reshaping..."
- **Bullet lists with bolded lead-ins** for short prose answers
- **Markdown bleeding into plain text** (`**bold**`, `### header`) where the destination doesn't render markdown
- **Horizontal rule (---) over-separation** between paragraphs
- **Oxford comma always**, even in journalistic registers that drop it
- **Semicolons** bolting independent clauses where humans would split into two sentences
- **Emoji as section dividers** (🔍 ✅ 📊)

### Cadence tells

- **Low burstiness**: uniform sentence length, around 15-20 words, low variance
- **Metronomic rhythm**: every sentence the same S-V-O shape, no fragments, no run-ons
- **No sentence fragments**. Humans use them. AI rarely does.
- **No paragraph ending mid-thought**; everything resolves neatly
- **Parallel syntactic frames** repeated across sentences ("X is Y. X is also Z. X remains W.")
- **Front-loaded topic sentence + three supporting beats** in nearly every paragraph
- **No callbacks**: humans loop back to earlier ideas; AI marches forward
- **No idiosyncratic word choice**: every word is the safest one

### Recent additions (2025-2026)

- **Citation artifacts** leaking into prose: `oaicite`, `contentReference`, `turn0search0`, `oai_citation`, `grok_card` tags
- **Phantom placeholders**: `[article subject]`, `[year]`, `[your name]` left unfilled
- **Hallucinated citations**: DOIs that resolve to wrong papers, 404 URLs with `utm_source` parameters still attached, ISBNs that fail checksum
- **Defensive vocabulary when accused**: "concrete evidence," "good faith," "quality and adherence to policies"
- **U.S. spelling bleed-through** in non-US contexts (or vice versa)
- **Colon-headline pattern**: "AI in 2026: A Comprehensive Guide"
- **Claude family quirks**: "I notice that...", "Let me...", recurring fiction character names (Marcus, Elena, Sarah, Aris, Kael), abstract emotion ("a gnawing ache," "faded into the background"), scene bloat
- **Gemini quirks**: emoji-heavy headers (🌟 🚀), aggressive boldface, "Let's dive in"
- **GPT family quirks**: academic register creep, "papery" feel, em dash overuse

### Domain-specific tells

**Legal drafting**: over-use of "shall," "herein," "notwithstanding the foregoing," "for the avoidance of doubt"; symmetric defined-term capitalization; clauses too clean (no negotiated cruft, no track-change scars)

**Marketing copy**: "Unlock the power of...", "Take your X to the next level," "Game-changing," "Industry-leading," "Best-in-class," "Solution" as a noun, "End-to-end," meta-introductions ("In this article, we'll explore..."), conclusion restating the intro

**Academic writing**: abstract-style opening even in body paragraphs, "This paper argues that...", excessive hedging ("may potentially suggest"), citation-shaped attribution without real citations

**News and journalism**: vague datelines, no named human sources, composite or fictional quotes, "too neat, too vague," every sentence sourced to "experts" or "observers"

**Fiction**: abstract emotion words instead of sensory detail; "let out a breath they didn't know they were holding"; weather-as-mood openers; symmetrical scene structure; AI-favorite names (Marcus, Elena, Aris, Kael)
