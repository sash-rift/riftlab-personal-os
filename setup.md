# Setup Recipe

You are setting up a personal AI Operating System for a new user. This is a conversational install. Follow the steps in order. Do not skip steps. Do not run them all at once.

## Step 0: Sanity check your environment

Before greeting the user, verify two things silently:

1. **Filesystem write access.** Can you write a file to the user's home directory? (Most Claude Desktop Code/Cowork sessions and Claude Code CLI can. Plain claude.ai Chat cannot.) If you cannot write files locally, tell the user: "This install needs to write files to your computer. Open Claude Desktop's Code tab or Cowork mode, or use Claude Code in your terminal, then paste the same prompt there." Stop.

2. **The repo is reachable.** Try to access this repo. Use the simplest method available in this session:
   - **Preferred**: `git clone https://github.com/sash-rift/riftlab-personal-os /tmp/riftlab-personal-os` (works wherever git is installed, no GitHub account needed for public repos).
   - **Fallback**: WebFetch the raw files individually from `https://raw.githubusercontent.com/sash-rift/riftlab-personal-os/main/<path>` as you need them.

If git clone works, you have the whole kit at `/tmp/riftlab-personal-os/`. Read files from there. If only WebFetch works, fetch each file just-in-time when this recipe references it.

## Step 0.5: Files you will need

From the cloned repo (or via WebFetch), you'll read:
- `templates/CLAUDE.md`
- `templates/about-me/identity.md`
- `templates/about-me/voice.md`
- `templates/about-me/current-focus.md`
- `templates/rules/writing-style.md`
- `templates/rules/communication.md`
- `skills/aim-coach/SKILL.md`
- `skills/daily-brief/SKILL.md`
- `skills/meeting-prep/SKILL.md`

You'll write customized versions of the templates and exact copies of the skills to the user's chosen install location (default `~/.claude/`).

## Step 1: Greet and orient

Tell the user, in your own words and matching their energy:

- You're about to set up their personal AI OS.
- It will take about 5 minutes of conversation.
- You'll ask a few questions about them, then write the files.
- Everything ends up at `~/.claude/` by default. They can change that.

Then pause and let them respond before proceeding.

## Step 2: Interview

Ask these questions ONE AT A TIME. Wait for the user's answer before asking the next. Do not batch them.

1. **Name and address**: "What's your full name, and what should I call you?"
2. **Role**: "What's your role and where do you work?"
3. **Day-to-day**: "Tell me about what you actually do day to day. Two or three sentences."
4. **Voice**: "How do you write? Direct, reflective, formal, casual? Any patterns you can't stand (em dashes, corporate-speak, fake enthusiasm)?"
5. **Current focus**: "What are the 2-3 things on your plate right now that I should know about?"
6. **Tools**: "What tools do you live in? (Calendar, email client, Notion, Slack, etc.) Just list them quickly."
7. **Install location**: "Where do you want your AI OS to live? This will be a real folder you can open in Finder and edit directly. Suggested paths: `~/intelligence/`, `~/MyAI/`, or `~/Documents/AI/`. Pick one or give me a custom path."

Do not default to `~/.claude/` — that's a hidden config folder and we want the OS to feel like a real owned thing. If the user explicitly says they want `~/.claude/`, respect it, but otherwise nudge toward a visible folder.

If they give a very short answer to any question, ask one follow-up to get usable detail. Don't interrogate. One follow-up max per question.

## Step 3: Generate identity files

Using the user's answers, write these files at their chosen install location (the path from question 7 — referred to below as `<OS_PATH>`, e.g., `~/intelligence/`):

### `CLAUDE.md`

Use `templates/CLAUDE.md` as the base. Replace `[NAME]` with their name.

### `about-me/identity.md`

Use `templates/about-me/identity.md` as the base. Replace placeholders with what they told you in questions 1-3. Write in first person (as if the user wrote it).

### `about-me/voice.md`

Use `templates/about-me/voice.md` as the base. Translate their answer to question 4 into specific rules. Include the universal defaults from the template (no em dashes, no hedging, no filler openings). Add their personal preferences on top.

### `about-me/current-focus.md`

Use `templates/about-me/current-focus.md` as the base. Fill in from their answer to question 5. Date-stamp it with today's date.

### `rules/writing-style.md`

Copy `templates/rules/writing-style.md` as-is. These are universal defaults the user can edit later.

### `rules/communication.md`

Copy `templates/rules/communication.md` as-is.

### `references/` and `projects/`

Create both as empty folders with a `.gitkeep` file. The user populates these over time.

## Step 4: Install skills (into the OS folder, then symlink)

Skills must live at `~/.claude/skills/` for Claude to discover them via `/`. But we want the OS folder (`<OS_PATH>`) to be the user's single source of truth. So copy the skills into `<OS_PATH>/skills/`, then symlink each one into `~/.claude/skills/`.

Steps:

1. Copy each skill folder from the repo into `<OS_PATH>/skills/`:
   - `<OS_PATH>/skills/aim-coach/SKILL.md`
   - `<OS_PATH>/skills/daily-brief/SKILL.md`
   - `<OS_PATH>/skills/meeting-prep/SKILL.md`

2. For each skill folder, create a symlink in `~/.claude/skills/` pointing to the OS folder copy:
   ```
   mkdir -p ~/.claude/skills
   ln -sfn <OS_PATH>/skills/aim-coach ~/.claude/skills/aim-coach
   ln -sfn <OS_PATH>/skills/daily-brief ~/.claude/skills/daily-brief
   ln -sfn <OS_PATH>/skills/meeting-prep ~/.claude/skills/meeting-prep
   ```

3. Verify each symlink resolves to the OS folder copy.

If the user already has skills at `~/.claude/skills/` with these names, ask before overwriting. If they exist as real folders (not symlinks), offer to back them up first (move to `~/.claude/skills/<name>.backup-YYYYMMDD`).

## Step 4.5: Symlink CLAUDE.md so Claude finds it globally

Claude Code reads `~/.claude/CLAUDE.md` as the user-global CLAUDE.md for every session. Symlink it to the OS folder so the user can edit one file and have it apply everywhere.

```
ln -sfn <OS_PATH>/CLAUDE.md ~/.claude/CLAUDE.md
```

If `~/.claude/CLAUDE.md` already exists as a real file, ask before overwriting. Offer to back it up first (`~/.claude/CLAUDE.md.backup-YYYYMMDD`).

## Step 5: Report and orient

Tell the user, in plain language:

- Where their OS lives. Specifically: "Your AI OS lives at `<OS_PATH>`. Open it in Finder anytime to see or edit your files."
- That symlinks make it work everywhere: `~/.claude/CLAUDE.md` and `~/.claude/skills/<each>` point to the OS folder, so Claude finds them automatically in any session.
- The three skills available: `/aim-coach`, `/daily-brief`, `/meeting-prep`. Suggest they try `/aim-coach` first with any prompt they want to refine.
- That this is THEIR OS. Edit any file in the OS folder and Claude picks up the changes. `about-me/current-focus.md` is the one they'll update most often.
- The curation rule: "Review CLAUDE.md monthly. For each line, ask: would removing it cause Claude to make a mistake? If not, delete it."

End with one sentence on what's next. Do not pad with congratulations. Match their voice.

## Edge cases

- **User explicitly wants `~/.claude/` as the install location**: respect it. Install directly there with no symlinks. Note the trade-off in your report: "Your OS lives in a hidden config folder. You can still edit the files, but they won't show up in Finder by default."
- **User has existing CLAUDE.md at `~/.claude/CLAUDE.md` as a real file**: ask before overwriting. Offer to back it up first (`~/.claude/CLAUDE.md.backup-YYYYMMDD`).
- **User has existing skill folders at `~/.claude/skills/<name>` as real folders (not symlinks)**: ask before replacing. Offer to back them up first.
- **User is on Windows**: symlinks require Developer Mode enabled or admin rights. If `ln -sfn` fails, fall back to copying files instead and warn the user that edits in the OS folder won't auto-propagate. Suggest they enable Developer Mode for the better experience.
- **User refuses an interview question**: skip it. Generate the file with sensible defaults and note that they can edit it.
- **User is in a hurry**: offer a "quick install" that asks only for name, role, and install location. Defaults for the rest. They can fill in later.

## Voice for the install conversation

- Be warm. This is setup, not surgery.
- Be brief. One question at a time. Short responses.
- Be specific about what you're doing. Say "I'm writing your voice.md now" not "Generating files..."
- Match their energy. If they're terse, be terse. If they're chatty, give them room.
- No filler. No "Great answer!" No "That's interesting."
