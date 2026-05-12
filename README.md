# RiftLab Personal OS

A personal AI operating system you can install in 5 minutes by pasting one prompt into Claude.

This kit gives you the architecture that effective AI users build for themselves: a place for your identity, your voice, your rules, your projects, and your skills. Once installed, every Claude session you start (Desktop, Cowork, or Code) knows who you are and what you care about.

## What you'll get

After install, your AI OS will live at `~/.claude/`:

- **CLAUDE.md** — top of your AI's mind every session. Knows your role, voice, current focus.
- **about-me/** — identity, voice rules, current-focus. Makes Claude sound like it knows you.
- **rules/** — your behavioral defaults (how you want responses formatted, what to avoid).
- **references/** — empty to start. Domain knowledge you add over time (people, tools, glossary).
- **skills/** — three ready-to-use workflows:
  - `/aim-coach` — refine any prompt or system instruction through coaching
  - `/daily-brief` — morning brief that adapts to your role and priorities
  - `/meeting-prep` — strategic brief for any upcoming meeting

## Install (zero friction)

You need **Claude Desktop's Code tab or Cowork mode** (or Claude Code CLI). The install will not work in plain claude.ai Chat because Chat cannot write files to your computer.

### Step 1: Open Claude Desktop's Code tab or Cowork mode.

### Step 2: Paste this prompt:

```
Install my personal AI OS using https://github.com/sash-rift/riftlab-personal-os — follow setup.md.
```

### Step 3: Answer the interview.

Claude will ask you about 6-7 questions: your name, role, what you do day to day, your writing voice, current focus, tools you use, and where you want the OS installed (default is `~/.claude/`). Takes about 5 minutes.

### Step 4: Done.

Open a new Claude session anywhere (Desktop Chat, Cowork, Code, CLI). Type `/` and your skills appear. Your CLAUDE.md is loaded automatically.

## Other ways to install

If you'd rather see what Claude is doing before letting it run, two alternate paths:

**Manual ZIP download.** Click the green "Code" button on this repo's GitHub page → "Download ZIP". Unzip somewhere. Then in Claude Desktop tell it: "Follow the setup.md recipe in /Users/me/Downloads/riftlab-personal-os-main/."

**Git clone.** If you have git installed and want a local copy: `git clone https://github.com/sash-rift/riftlab-personal-os`. Then in Claude Desktop: "Follow the setup.md recipe in /Users/me/riftlab-personal-os/."

All three paths produce the same result: a fully scaffolded `~/.claude/` with your customized CLAUDE.md, identity files, rules, and three working skills.

## After install

Your AI OS is yours. Edit any file. Add new skills (use `/aim-coach` to help you write them). Update `about-me/current-focus.md` whenever your priorities shift. The system grows with you.

Three things to try first:

1. `/aim-coach` — give it a prompt you've been struggling with. Let it coach you.
2. `/daily-brief` — run it tomorrow morning before opening email.
3. `/meeting-prep` — point it at your next meeting on the calendar.

## What this is not

This is not a finished AI personality. It's a scaffold. The first day it knows the basics you told it. The hundredth day it knows you, because you've been living in it.

Built for the Applied AI for Knowledge Work course at Rift Lab.
