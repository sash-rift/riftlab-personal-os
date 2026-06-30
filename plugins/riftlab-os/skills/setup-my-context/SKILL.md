---
name: setup-my-context
description: One-time setup for the Personal AI OS. Interviews the user, then writes their personal context files (CLAUDE.md, identity, voice, rules) into the folder they're working in, so every session knows who they are and how they work. Use right after installing the plugin, or when the user says "help me set up my context", "set up my personal OS", "onboard me", "run the RiftLab OS setup", or "personalize my AI".
---

# Set up the Personal AI OS

This is the one-time personalization for the Personal AI OS. The plugin already installed the skills and agents. This runs a short interview, then writes the user's context files into the folder they're working in, so every Claude session knows who they are and how they work. It is self-contained: generate every file from the answers, there is nothing to download.

Work through it in order, conversationally, one question at a time. Say what you are writing as you go ("writing your voice.md now"). Keep the tone warm, brief, and free of filler.

## Before you start

Confirm you can write files on this machine. The Claude Desktop Code tab, Cowork, and the Claude Code CLI all can; plain claude.ai chat cannot. If you cannot write files, tell the user to run this from the Code tab, Cowork, or the CLI, and stop here.

## Step 1: Confirm the folder

The user should already be working in the folder they made for their AI OS, and this builds it there. Check the current working directory and tell them which folder you'll use ("I'll set up your OS here: [folder]. Is that the one you made for this?"). Wait for them to confirm. If they point you at a different existing folder, use that instead. Don't create a new nested folder or invent a path. Call the confirmed folder `<OS_PATH>` below.

Then orient them in a sentence or two: you'll ask a handful of questions, then write their files here; it takes about five minutes.

## Step 2: Interview

Ask these one at a time. Wait for each answer before the next; do not batch them. If an answer is thin, ask one follow-up, then move on.

1. **Name.** "What's your full name?"
2. **Role.** "What's your role, and where do you work?"
3. **Day to day.** "What do you actually do day to day? Two or three sentences is plenty."
4. **Voice.** "How do you write when it sounds like you: direct, reflective, formal, casual? And what can't you stand: em dashes, corporate-speak, fake enthusiasm, anything?"
5. **Your AI.** "Want to name your AI? People use names like Atlas, Sage, or Echo, or skip it and it stays Claude. And how should it act with you: a co-creator that pushes back, a peer that collaborates, an executor that ships fast, a coach that challenges? Use your own words."
6. **Current focus.** "What are the two or three things on your plate right now that I should know about?"
7. **Tools.** "What tools do you live in day to day? Calendar, email, Notion, Slack, whatever. Just list them."

## Step 3: Check for existing files

Before writing anything, look at `<OS_PATH>`. If it already holds a `CLAUDE.md`, or any of the files below with real content the user wrote, don't overwrite silently: tell them what's there, back the file up (append `.backup` and today's date), then write the new version. If a file is empty or just placeholder scaffold, replace it directly. The folders (`about-me/`, `rules/`, `references/`, `projects/`) are additive: create them if missing, never disturb existing contents.

## Step 4: Write the context files

Generate each file below into `<OS_PATH>` from the interview answers. You are writing these from scratch; the structure and defaults are specified here, so you don't need any template. Use the user's own words and don't sanitize their voice. Tell the user as you write each one.

**`CLAUDE.md`** (the root file; it loads into context every session, so keep it lean)
Title it for them ("[Name]'s Intelligence System"). Import only the always-relevant identity, so the file that loads every session stays small:
```
@agent.md
@about-me/identity.md
@about-me/current-focus.md
```
Then add a "Where things live" section that names the rest as files to read on demand, rather than loading them into every session:
- `about-me/voice.md`: read before drafting anything they'll send or publish.
- `rules/writing-style.md`: read before drafting written content.
- `rules/communication.md`: how to format responses; read when it matters.
- `references/` and `projects/`: read the relevant file when that topic comes up.

Keep `CLAUDE.md` well under 200 lines (Anthropic's guidance): a bloated memory file gets followed less, not more. End with a curation rule: review this file monthly, and cut any line that wouldn't cause a mistake if it were removed.

**`about-me/identity.md`**
Who they are, from answers 1 to 3, in the first person: their name, their role and company, and what they actually do day to day. This is what Claude reads to answer questions about their work and background.

**`about-me/voice.md`**
How they write, from answer 4, translated into specific rules. Always include these defaults, which every OS keeps: no em dashes; no hedging ("try to", "might", "could" when you mean the thing); no filler openings ("I hope this finds you well", "Great question"); say it once, plainly. Then layer their stated preferences and dislikes on top, in their words. This file is read before drafting anything they will send or publish.

**`agent.md`**
Their AI's identity, from answer 5. Lead with the name (or "Claude" if they skipped it). Then a one-line statement of the role they want it to play, three or four behavior traits in their language, and zero to two anti-patterns, only if they named things they don't want. Keep it real, not corporate.

**`about-me/current-focus.md`**
The two or three things from answer 6, each with a line of context. Date-stamp it today. Tell them this is the file they'll update most often.

**`rules/writing-style.md`**
Default writing rules, applied any time Claude drafts content: vary sentence length, lead with the point, use active voice and specific nouns, cut throat-clearing and filler, no em dashes. Fold in anything from answer 4 that is about mechanics rather than voice.

**`rules/communication.md`**
Default rules for how Claude responds in conversation: lead with the answer then support it, skip preamble and restating the question, match the format they asked for, be direct without validation theater, and ask one clarifying question when genuinely blocked rather than guessing.

**`references/tools.md`** (optional)
If answer 7 surfaced specific tools, write a short file listing them and what each is used for. Skip it if the list was vague.

Also create `references/` and `projects/` as folders (each with a `.gitkeep`) for the user to grow into. After writing each file, confirm it exists at the target path before moving on.

## Step 5: Orient and hand off

When the files are written, brief the user in their own voice:

- **Where it lives.** Their OS is at `<OS_PATH>`; they can open and edit any file in Finder or File Explorer anytime.
- **The home-folder rule.** Launch Claude from inside that folder (or "Work in this project" in Cowork) and CLAUDE.md loads automatically. Launch from somewhere else and it won't know them. This folder is the AI's home.
- **Their skills.** Already in the `/` menu, installed by the plugin: `/aim-coach`, `/daily-brief`, `/meeting-prep`, `/humanize`, plus `/deep-research` and `/decision-council`, which run a live agent team in the Code tab or CLI. Suggest starting with `/aim-coach` on any prompt, or `/humanize` on any draft that reads as AI-written.
- **It's theirs.** Editing any file changes how Claude shows up next session. `about-me/current-focus.md` is the one to keep fresh.

End with a single line on what to do next. No congratulations padding, and no "Great answer!" along the way.
