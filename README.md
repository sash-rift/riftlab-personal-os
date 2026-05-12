# Intelligence Starter Kit

A personal AI operating system you can install in 5 minutes by handing this repo to Claude.

This kit gives you the architecture that the most effective AI users build for themselves: a place for your identity, your voice, your rules, your projects, and your skills. Once installed, every Claude session you start (Desktop, Cowork, or Code) knows who you are and what you care about.

## What you'll get

After install, your AI OS will live at `~/.claude/`:

- **CLAUDE.md** — the top of your AI's mind every session. Knows your role, voice, current focus.
- **about-me/** — identity, voice rules, current-focus. The files that make Claude sound like it knows you.
- **rules/** — your behavioral defaults (how you want responses formatted, what to avoid).
- **references/** — domain knowledge (people, tools, glossary) loaded when relevant.
- **skills/** — three ready-to-use workflows:
  - `aim-coach` — refine any prompt or system instruction through coaching
  - `daily-brief` — morning brief that adapts to your role and priorities
  - `meeting-prep` — strategic brief for any upcoming meeting

## How to install

You have three paths. All three work. Pick whichever surface you live in.

### Path 1: Claude Desktop (Code tab or Cowork)

1. Open Claude Desktop.
2. Start a new session in the **Code** tab or **Cowork** mode.
3. Paste this prompt:

```
Clone https://github.com/[YOUR-GITHUB-HANDLE]/intelligence-starter and follow the setup recipe in setup.md to install my personal AI OS.
```

4. Answer the interview questions Claude asks.
5. Done. Your OS is installed at `~/.claude/`. Skills appear when you type `/`.

### Path 2: Claude Code (CLI)

```bash
git clone https://github.com/[YOUR-GITHUB-HANDLE]/intelligence-starter ~/Downloads/intelligence-starter
cd ~/Downloads/intelligence-starter
claude
> Follow the setup recipe in setup.md to install my personal AI OS.
```

### Path 3: Manual

If you'd rather see what's happening before letting Claude do it: open `setup.md`. The whole recipe is human-readable. You can run the steps yourself.

## After install

Your AI OS is yours. Edit any file, add new skills, evolve the rules as you learn what works. The system grows with you.

Three things to try first:

1. `/aim-coach` — give it a prompt you've been struggling with. Let it refine.
2. `/daily-brief` — run it tomorrow morning before opening email.
3. `/meeting-prep` — point it at your next meeting on the calendar.

## What this is not

This is not a finished AI personality. It's a scaffold. The first day it knows the basics you told it. The hundredth day it knows you, because you've been living in it.

Built for the Applied AI for Knowledge Work course at Rift Lab.
