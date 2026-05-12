# RiftLab Personal OS

A personal AI operating system you can install in 5 minutes by pasting one prompt into Claude.

This kit gives you the architecture that effective AI users build for themselves: a place for your identity, your voice, your rules, your projects, and your skills. Once installed, every Claude session you start (Desktop, Cowork, or Code) knows who you are and what you care about.

## What you'll get

Your AI OS lives in a folder you pick (suggested: `~/intelligence/`, `~/MyAI/`, or `~/Documents/AI/`). It's a real, visible folder you can open in Finder, edit directly, and version with git if you want.

**The home-folder pattern**: always launch Claude from inside your OS folder (or "Work in this project" in Cowork). Your CLAUDE.md auto-loads from there. If you launch Claude outside the folder, it won't know you. Treat the OS folder as your AI's home base.

Inside the OS folder:

- **CLAUDE.md** — top of your AI's mind every session. Knows your role, voice, current focus.
- **about-me/** — identity, voice rules, current-focus. Makes Claude sound like it knows you.
- **rules/** — your behavioral defaults (how you want responses formatted, what to avoid).
- **references/** — empty to start. Domain knowledge you add over time (people, tools, glossary).
- **skills/** — seven ready-to-use workflows:
  - `/aim-coach` — refine any prompt or system instruction through coaching
  - `/daily-brief` — morning brief that adapts to your role and priorities
  - `/meeting-prep` — strategic brief for any upcoming meeting
  - `/docx` — create, read, edit Word documents (fetched from Anthropic's open skills repo on install)
  - `/pdf` — read, manipulate, create PDF files (fetched from Anthropic)
  - `/pptx` — build, edit, extract from PowerPoint decks (fetched from Anthropic)
  - `/internal-comms` — write status reports, newsletters, FAQs, leadership updates (fetched from Anthropic)

## Install (zero friction)

You need **Claude Desktop's Code tab or Cowork mode** (or Claude Code CLI). The install will not work in plain claude.ai Chat because Chat cannot write files to your computer.

### Step 1: Open Claude Desktop's Code tab or Cowork mode.

### Step 2: Paste this prompt:

```
Install my personal AI OS using https://github.com/sash-rift/riftlab-personal-os — follow setup.md.
```

### Step 3: Answer the interview.

Claude will ask you about 6-7 questions: your name, role, what you do day to day, your writing voice, current focus, tools you use, and where you want the OS folder installed (it'll suggest `~/intelligence/` or similar). Takes about 5 minutes.

### Step 4: Done.

Open a Claude session inside your OS folder (Cowork "Work in this project," Code launched from the folder, or CLI). Type `/` and your skills appear. Your CLAUDE.md loads automatically from the folder. Open your OS folder in Finder and you'll see every file Claude knows about you.

## Other ways to install

If you'd rather see what Claude is doing before letting it run, two alternate paths:

**Manual ZIP download.** Click the green "Code" button on this repo's GitHub page → "Download ZIP". Unzip somewhere. Then in Claude Desktop tell it: "Follow the setup.md recipe in /Users/me/Downloads/riftlab-personal-os-main/."

**Git clone.** If you have git installed and want a local copy: `git clone https://github.com/sash-rift/riftlab-personal-os`. Then in Claude Desktop: "Follow the setup.md recipe in /Users/me/riftlab-personal-os/."

All three paths produce the same result: a fully scaffolded OS folder at the location you pick, with your customized CLAUDE.md, identity files, rules, and seven working skills. CLAUDE.md auto-loads when you launch Claude inside the folder. Skills are available via symlinks into `~/.claude/skills/` for Code/CLI, and via a personal Cowork plugin for Cowork.

## After install

Your AI OS is yours. Edit any file. Add new skills (use `/aim-coach` to help you write them). Update `about-me/current-focus.md` whenever your priorities shift. The system grows with you.

Three things to try first:

1. `/aim-coach` — give it a prompt you've been struggling with. Let it coach you.
2. `/daily-brief` — run it tomorrow morning before opening email.
3. `/meeting-prep` — point it at your next meeting on the calendar.

## What this is not

This is not a finished AI personality. It's a scaffold. The first day it knows the basics you told it. The hundredth day it knows you, because you've been living in it.

Built for the Applied AI for Knowledge Work course at Rift Lab.
