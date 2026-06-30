# RiftLab Personal AI OS

A personal AI operating system you install as a Claude plugin. It gives Claude a set of skills and a team of thinking agents. A short interview then sets up your identity files so every session knows who you are.

Built for the Applied AI for Knowledge Work course at RiftLab.

## What you get

**Skills** (type `/` to run one, or let Claude reach for it):

- `/aim-coach`: coach any prompt or system instruction into shape
- `/daily-brief`: a morning brief shaped to your role and priorities
- `/meeting-prep`: a strategic brief for any upcoming meeting
- `/humanize`: rewrite AI-sounding text to match your voice
- `/deep-research`: a four-agent research team that returns verified, cited findings
- `/decision-council`: a board of advisors that pressure-tests a real decision and hands back one recommendation

**Agents** that power the work: three thinking partners (researcher, critical-thinker, coach) for direct `@`-mention, plus the two skill teams (oracle, hermes, athena, scribe behind `/deep-research`; CMO, CFO, COO, GC behind `/decision-council`).

## Install

Two steps: install the plugin, then run the interview.

### Step 1: Install the plugin

This adds the skills and agents. Nothing in this repo is executed during install; Claude's plugin system reads the plugin and registers its components.

**Claude Desktop (Cowork):** open the Customize menu, go to the Plugins tab. Under Personal plugins, click the "+" button, choose **Add marketplace**, then **Add from a repository**, and paste:

```
https://github.com/sash-rift/riftlab-personal-os
```

Then install `riftlab-os` from the marketplace.

**Claude Code (Code tab or terminal):**

```
/plugin marketplace add sash-rift/riftlab-personal-os
/plugin install riftlab-os@riftlab
```

### Step 2: Build your identity

The plugin gives Claude capabilities. The interview gives Claude *you*. After installing, follow [INTERVIEW.md](INTERVIEW.md): paste it into Claude, or just say "run the RiftLab OS interview." It asks nine short questions and writes your identity files (CLAUDE.md, voice, rules) into a folder you pick (suggested `~/intelligence/`). Launch Claude from inside that folder and your context loads automatically.

## Where things run

The four light skills (`/aim-coach`, `/daily-brief`, `/meeting-prep`, `/humanize`) run everywhere, including Cowork. `/deep-research` and `/decision-council` run a live agent team. Use the Code tab or the CLI for those two.
