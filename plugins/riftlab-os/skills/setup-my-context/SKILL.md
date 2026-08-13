---
name: setup-my-context
description: One-time setup for the Personal AI OS. Discovers context the user already has (their CLAUDE.md files, Claude user memory, auto memory, older setups), interviews them to fill the gaps, then writes one organized context system into the folder they're working in, so every session knows who they are and how they work. Nothing they already set up is lost. Use right after installing the plugin, or when the user says "help me set up my context", "set up my personal OS", "onboard me", "run the RiftLab OS setup", or "personalize my AI".
---

# Set up the Personal AI OS

This is the one-time personalization for the Personal AI OS. The plugin already installed the skills and agents. This runs discovery on what the user already has, a short interview to fill the gaps, then writes an organized context system into the folder they're working in. It is self-contained: generate everything from what you find and their answers, there is nothing to download.

Two rules hold the whole thing together. Keep them in mind at every step.

- **Never lose their data.** If a file already has real content the user wrote, back it up and merge into it. Never overwrite it, and never move or delete their originals.
- **One home folder, both surfaces.** Everything goes into the folder they're working in. That folder's `CLAUDE.md` is the file both Claude Code and Cowork read: Claude Code loads it when launched from inside the folder; Cowork loads it as the folder's instructions when they connect the folder. Keep the always-loaded part small, and don't scatter context into places only one surface can see.

Work through the steps in order, conversationally, one question at a time. Say what you're doing as you go. Keep the tone warm, brief, and free of filler.

## Before you start

Confirm you can write files on this machine. The Claude Desktop Code tab, Cowork, and the Claude Code CLI all can; plain claude.ai chat cannot. If you cannot write files, tell the user to run this from the Code tab, Cowork, or the CLI, and stop here.

## Step 1: Confirm the home folder

The user should already be working in the folder they made for their AI OS, and this builds it there. Check the current working directory and confirm it ("I'll set up your OS here: [folder]. Is that the one you made for this?"). Wait for them to confirm. If they point you at a different existing folder, use that instead. Don't create a new nested folder or invent a path. Call the confirmed folder `<OS_PATH>`.

Orient them in a sentence: this folder is their AI's home. In Claude Code they launch from inside it; in Cowork they connect it as their folder. Either way Claude reads the files here and knows them. Tell them it takes about five minutes: you'll look at what they already have, ask a few questions, then write their files here.

## Step 2: Discover what they already have

Most people already have context, even if they never wrote a setup file. Before interviewing, look for it, so you build on it instead of starting from zero. Ask permission in one sentence first ("Mind if I check a couple of standard spots for context you've already built up?"), then check:

- **The home folder and the folders above it** for `CLAUDE.md` and `CLAUDE.local.md`.
- **Their Claude user memory:** `~/.claude/CLAUDE.md`. In Claude Code this loads in every session, so it's a likely place real identity already lives. (You are reading it to harvest what's true, not to write there.)
- **Their auto memory:** `~/.claude/projects/*/memory/MEMORY.md` and the topic files beside it. This is what Claude has been learning about them over time.
- **Anything they name.** Ask: "Do you already have an AI setup, a CLAUDE.md, or a note on how you work somewhere? Point me at it and I'll fold in what's still true." Read a bio or resume if they offer one.

Only read in this step; write nothing yet. If they decline, skip the scan, tell them you'll build from the interview alone, and continue.

## Step 3: Inventory and confirm

Summarize what you found, grouped by source, in plain language. For each item, note how current it looks: use the `modified` dates on memory files where present, and flag anything that reads stale, like an old employer or a finished project. Then ask them to confirm what's still true and what to carry forward. Surface conflicts directly and let them decide. For example: "Your saved context says Director at Microsoft; is that current, past experience to keep as background, or should I drop it?" Nothing gets carried forward silently. If the scan found nothing, say so and move on.

## Step 4: Interview to fill the gaps

Ask only what discovery didn't already answer. Where you found a solid answer, confirm it instead of re-asking ("Your notes already cover your voice well; anything to add or change?"). Ask one at a time, wait for each answer, don't batch. If an answer is thin, ask one follow-up, then move on.

1. **Name.** "What's your full name?"
2. **Role.** "What's your role, and where do you work?"
3. **Day to day.** "What do you actually do day to day? Two or three sentences is plenty."
4. **Voice.** "How do you write when it sounds like you: direct, reflective, formal, casual? And what can't you stand: em dashes, corporate-speak, fake enthusiasm, anything?"
5. **Your AI.** "Want to name your AI? People use names like Atlas, Sage, or Echo, or skip it and it stays Claude. And how should it act with you: a co-creator that pushes back, a peer that collaborates, an executor that ships fast, a coach that challenges? Use your own words."
6. **Current focus.** "What are the two or three things on your plate right now that I should know about?"
7. **Tools.** "What tools do you live in day to day? Calendar, email, Notion, Slack, whatever. Just list them."

## Step 5: Reconcile and write the files

Write the files into `<OS_PATH>`, merging confirmed existing context with the interview answers. Existing content the user confirmed is the source of truth for facts; the interview fills gaps and updates; on any conflict you resolved in Step 3, use their decision. Use their own words; don't sanitize their voice. Tell the user as you write each one.

Follow Anthropic's memory guidance for everything you write: keep files short and specific, use headers and bullets, one clear statement per line, and no contradictions across files.

**`CLAUDE.md`** (the root file; both Claude Code and Cowork read it, so it's the spine of the whole system)
Title it for them ("[Name]'s Intelligence System"). Import only the always-relevant identity, so the file that loads every session stays small:
```
@about-me/identity.md
@agent.md
@about-me/current-focus.md
```
Then add a "Where things live" section that names the rest as files to read on demand, rather than loading them into every session:
- `about-me/voice.md`: read before drafting anything they'll send or publish.
- `rules/writing-style.md`: read before drafting written content.
- `rules/communication.md`: how to format responses; read when it matters.
- `references/` and `projects/`: read the relevant file when that topic comes up.

Keep `CLAUDE.md` well under 200 lines (Anthropic's guidance): a bloated memory file gets followed less, not more. End with a curation rule: review this file monthly, and cut any line that wouldn't cause a mistake if it were removed.

**`about-me/identity.md`**
Who they are, from answers 1 to 3 and any confirmed discovery, in the first person: name, role and company, and what they actually do day to day. This is what Claude reads to answer questions about their work and background.

**`about-me/voice.md`**
How they write, from answer 4, translated into specific rules. Always include these defaults, which every OS keeps: no em dashes; no hedging ("try to", "might", "could" when you mean the thing); no filler openings ("I hope this finds you well", "Great question"); say it once, plainly. Then layer their stated preferences and dislikes on top, in their words. Read before drafting anything they'll send or publish.

**`agent.md`**
Their AI's identity, from answer 5. Lead with the name (or "Claude" if they skipped it). Then a one-line statement of the role they want it to play, three or four behavior traits in their language, and zero to two anti-patterns, only if they named things they don't want. Keep it real, not corporate.

**`about-me/current-focus.md`**
The two or three things from answer 6, each with a line of context. Date-stamp it today. Tell them this is the file they'll update most often.

**`rules/writing-style.md`**
Default writing rules, applied any time Claude drafts content: vary sentence length, lead with the point, use active voice and specific nouns, cut throat-clearing and filler, no em dashes. Fold in anything from answer 4 about mechanics rather than voice.

**`rules/communication.md`**
Default rules for how Claude responds in conversation: lead with the answer then support it, skip preamble and restating the question, match the format they asked for, be direct without validation theater, and ask one clarifying question when genuinely blocked rather than guessing.

**`references/tools.md`** (optional)
If answer 7 surfaced specific tools, write a short file listing them and what each is for. Skip it if the list was vague.

Also create `references/` and `projects/` as folders (each with a `.gitkeep`) for the user to grow into.

**Never lose data (applies to every file above).** Before writing any file that already exists with real content the user wrote: read it, keep everything, add only what's missing, show a short summary of what you'll add and what you'll leave untouched, back it up (`.backup` and today's date), and write only after they confirm. A file that's empty or placeholder scaffold you write directly. The folders (`about-me/`, `rules/`, `references/`, `projects/`) are additive: create what's missing, never disturb what's inside. After writing each file, confirm it exists at the target path before moving on.

## Step 6: Orient and hand off

When the files are written, brief the user in their own voice:

- **Where it lives.** Their OS is at `<OS_PATH>`; they can open and edit any file in Finder or File Explorer anytime. Editing any file changes how Claude shows up next session.
- **The home-folder rule.** In Claude Code, launch from inside this folder and `CLAUDE.md` loads automatically. In Cowork, connect this folder (or make it your Cowork project) and it becomes your folder instructions. Work somewhere else and Claude won't know them. This folder is the AI's home.
- **Keep it fresh.** `about-me/current-focus.md` is the one to update most. Once a month, read your context and cut any line that wouldn't cause a mistake if it were gone.
- **Optional, for Cowork power users.** To carry a short version of who they are across every Cowork project, not just this folder, they can paste a few lines into Settings > Cowork > Global instructions. This is a manual step; the folder is still the home for the full system.
- **Their skills.** Already in the `/` menu, installed by the plugin: `/aim-coach`, `/daily-brief`, `/meeting-prep`, `/humanize`, plus `/deep-research` and `/decision-council`, which run a live agent team in the Code tab or CLI. Suggest starting with `/aim-coach` on any prompt, or `/humanize` on any draft that reads as AI-written.

End with a single line on what to do next. No congratulations padding, and no "Great answer!" along the way.
