# RiftLab Personal Claude OS

A personal AI operating system you can install in 5 minutes by pasting one prompt into Claude.

This kit gives you the architecture that effective AI users build for themselves: a place for your identity, your voice, your rules, your projects, and your skills. Once installed, every Claude session you start (Desktop, Cowork, or Code) knows who you are and what you care about.

## The stack

```
┌─────────────────────────────────────────────────────────────┐
│  YOUR AI OS                                                 │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  IDENTITY    CLAUDE.md, agent.md, about-me/, rules/         │
│              who you are                                    │
│                                                             │
│  SKILLS      /aim-coach, /daily-brief, /meeting-prep,       │
│              /humanize, /deep-research, /decision-council,  │
│              /docx, /pdf, /pptx, /internal-comms            │
│              what your AI can do for you                    │
│                                                             │
│  AGENTS      @researcher        stuck on information?       │
│              @critical-thinker  stuck on a plan?            │
│              @coach             stuck on a decision?        │
│              thinking partners for different kinds of stuck │
│                                                             │
│  WORK        projects/, references/                         │
│              where your stuff lives                         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

Once installed, the same OS runs in two places — and the Code tab is the upgrade:

![Where your AI OS runs: one install, two surfaces (Cowork and the Code tab / CLI)](assets/architecture.svg)

## What you'll get

Your AI OS lives in a folder you pick (suggested: `~/intelligence/`, `~/MyAI/`, or `~/Documents/AI/`). It's a real, visible folder you can open in Finder (Mac) or File Explorer (Windows), edit directly, and version with git if you want.

**The home-folder pattern**: always launch Claude from inside your OS folder (or "Work in this project" in Cowork). Your CLAUDE.md auto-loads from there. If you launch Claude outside the folder, it won't know you. Treat the OS folder as your AI's home base.

Inside the OS folder:

- **CLAUDE.md** — top of your AI's mind every session. Knows your role, voice, current focus.
- **agent.md** — who your AI is to you (name, persona, behavior).
- **about-me/** — identity, voice rules, current-focus. Makes Claude sound like it knows you.
- **rules/** — your behavioral defaults (how you want responses formatted, what to avoid).
- **references/** — empty to start. Domain knowledge you add over time (people, tools, glossary).
- **projects/** — empty to start. One folder per active initiative.

Skills install at `~/.claude/skills/` (where Claude Code looks for them); the Cowork-safe ones are also packaged as a personal Cowork plugin for its slash menu. Ten ready-to-use workflows ship with the kit — eight run anywhere (Code tab, CLI, **and** Cowork); the two marked **(Code tab / CLI only)** run a live agent team that Cowork can't host, so they work only in the Code tab or CLI:

- `/aim-coach` — refine any prompt or system instruction through coaching
- `/daily-brief` — morning brief that adapts to your role and priorities
- `/meeting-prep` — strategic brief for any upcoming meeting
- `/humanize` — rewrite AI-generated or AI-influenced text to remove tells and match your voice
- `/deep-research` — run a four-agent research team (plan → search → evaluate → synthesize) for verified, cited findings on any question **(Code tab / CLI only)**
- `/decision-council` — convene a board of advisors (CMO, CFO, COO, GC) to pressure-test a real decision and return one recommendation with an owner **(Code tab / CLI only)**
- `/docx` — create, read, edit Word documents (fetched from Anthropic's open skills repo on install)
- `/pdf` — read, manipulate, create PDF files (fetched from Anthropic)
- `/pptx` — build, edit, extract from PowerPoint decks (fetched from Anthropic)
- `/internal-comms` — write status reports, newsletters, FAQs, leadership updates (fetched from Anthropic)

Three sub-agents install at `~/.claude/agents/` for direct `@-mention` invocation in Claude Code. Each one is for a different kind of stuck:

- `@agent-researcher` — **Stuck on information?** You don't know something and need verified findings with citations. Applies CRAAP source evaluation and triangulation. Operates on a strict token budget.
- `@agent-critical-thinker` — **Stuck on an opinion or plan?** You have a position and want it stress-tested before you commit. Uses pre-mortem, inversion, second-order, steel-manning, base rates, opportunity cost, 5 Whys.
- `@agent-coach` — **Stuck on a decision?** You've been circling a choice and can't land it. Walks you through GROW (Goal, Reality, Options, Will) one question at a time. Asks, doesn't tell.

Two of the skills bring their own agent teams. These install alongside the three above but run *under* the skill, not by `@-mention`: `/deep-research` orchestrates Oracle, Hermes, Athena, and Scribe; `/decision-council` convenes the CMO, CFO, COO, and GC advisors. You invoke the skill; it runs the team.

**All custom agents — the three thinking partners and the two skill teams — are a Claude Code capability (Code tab + CLI).** Cowork can't invoke agents from `~/.claude/agents/`, so `@-mention` and the two orchestration skills live in the Code tab. The four lightweight skills work everywhere, including Cowork.

## Install (zero friction)

You need **Claude Desktop's Code tab or Cowork mode** (or Claude Code CLI). The install will not work in plain claude.ai Chat because Chat cannot write files to your computer.

### Step 1: Open Claude Desktop's Code tab or Cowork mode.

### Step 2: Paste this prompt:

```
Install my personal AI OS using https://github.com/sash-rift/riftlab-personal-os — follow setup.md.
```

### Step 3: Answer the interview.

Claude will ask you 9 short questions: your name, role, what you do day to day, your writing voice, what you want to name your AI (optional), how you want it to behave, current focus, tools you use, and where you want the OS folder installed (it'll suggest `~/intelligence/` or similar). Takes about 5 minutes.

### Step 4: Done.

Open a Claude session inside your OS folder (Cowork "Work in this project," Code launched from the folder, or CLI). Type `/` and your skills appear. Your CLAUDE.md loads automatically from the folder. Open your OS folder in Finder (Mac) or File Explorer (Windows) and you'll see every file Claude knows about you.

## Other ways to install

If you'd rather see what Claude is doing before letting it run, two alternate paths:

**Manual ZIP download.** Click the green "Code" button on this repo's GitHub page → "Download ZIP". Unzip somewhere. Then in Claude Desktop tell it: "Follow the setup.md recipe in /Users/me/Downloads/riftlab-personal-os-main/."

**Git clone.** If you have git installed and want a local copy: `git clone https://github.com/sash-rift/riftlab-personal-os`. Then in Claude Desktop: "Follow the setup.md recipe in /Users/me/riftlab-personal-os/."

All three paths produce the same result: a fully scaffolded OS folder at the location you pick, with your customized CLAUDE.md, identity files, and rules. CLAUDE.md auto-loads when you launch Claude inside the folder. All ten skills install at `~/.claude/skills/` for Code-tab/CLI use; the eight Cowork-safe ones are also packaged into a Cowork plugin for its slash menu (the two agent-team skills stay Code-only). Eleven agents install at `~/.claude/agents/` for Claude Code: three thinking partners for direct `@-mention`, plus eight skill-internal agents that power `/deep-research` and `/decision-council`.

## After install

Your AI OS is yours. Edit any file. Add new skills (use `/aim-coach` to help you write them). Update `about-me/current-focus.md` whenever your priorities shift. The system grows with you.

**Confirm it worked (10 seconds):**

- Launch Claude from *inside* your OS folder — it should greet you knowing your name and role. If it doesn't, you launched from the wrong place; the folder is your AI's home base.
- Type `/` and look for your skills. In **Cowork** you'll see 8; in the **Code tab / CLI** you'll see all 10 (the two agent-team skills, `/deep-research` and `/decision-council`, are Code-only by design).
- If anything's missing, ask Claude to "check that all my OS skills and agents are installed" and re-run the step that fell short.

Five things to try first:

1. `/aim-coach` — give it a prompt you've been struggling with. Let it coach you.
2. `/daily-brief` — run it tomorrow morning before opening email.
3. `/meeting-prep` — point it at your next meeting on the calendar.
4. `@agent-critical-thinker` — paste a plan or thesis you want stress-tested.
5. `/deep-research` (in the Code tab) — hand it a question you'd otherwise spend an afternoon researching.

## What this is not

This is not a finished AI personality. It's a scaffold. The first day it knows the basics you told it. The hundredth day it knows you, because you've been living in it.

Built for the Applied AI for Knowledge Work course at Rift Lab.
