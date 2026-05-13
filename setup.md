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
- `templates/agent.md`
- `templates/about-me/identity.md`
- `templates/about-me/voice.md`
- `templates/about-me/current-focus.md`
- `templates/rules/writing-style.md`
- `templates/rules/communication.md`
- `skills/aim-coach/SKILL.md`
- `skills/daily-brief/SKILL.md`
- `skills/meeting-prep/SKILL.md`
- `skills/humanize/SKILL.md`
- `agents/researcher.md`
- `agents/critical-thinker.md`
- `agents/coach.md`

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
5. **AI name (optional)**: "Want to give your AI a name? Something personal. Examples: Nuro, Atlas, Sage, Echo, Pilot. Or you can skip and we'll just call it Claude."
6. **AI behavior**: "How do you want your AI to act with you? Examples: a co-creator who pushes back, a peer who collaborates, an executor who ships fast, a coach who challenges. Use your own words."
7. **Current focus**: "What are the 2-3 things on your plate right now that I should know about?"
8. **Tools**: "What tools do you live in? (Calendar, email client, Notion, Slack, etc.) Just list them quickly."
9. **Install location**: "Where do you want your AI OS to live? This will be a real folder you can open in Finder and edit directly. Suggested paths: `~/intelligence/`, `~/MyAI/`, or `~/Documents/AI/`. Pick one or give me a custom path."

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

### `agent.md`

Use `templates/agent.md` as the base. Replace `[AGENT_NAME]` with their answer to question 5 (or "Claude" if they skipped). Translate their answer to question 6 into:
- A one-sentence role description (what kind of AI they want)
- 3-4 specific behavior traits in the "How you should show up" section
- 0-2 anti-patterns in the "What I don't want" section (only if they mentioned any explicit dislikes)

If the user gave a vivid description (e.g., "a co-creator who pushes back when I'm being lazy"), use their language directly. Don't sanitize it.

### `about-me/current-focus.md`

Use `templates/about-me/current-focus.md` as the base. Fill in from their answer to question 7. Date-stamp it with today's date.

### `rules/writing-style.md`

Copy `templates/rules/writing-style.md` as-is. These are universal defaults the user can edit later.

### `rules/communication.md`

Copy `templates/rules/communication.md` as-is.

### `references/` and `projects/`

Create both as empty folders with a `.gitkeep` file. The user populates these over time.

## Step 4: Install skills

Skills live at `~/.claude/skills/` where Claude discovers them automatically. Install directly there — no symlinks. (Skills are infrastructure, not identity files. They don't need to live in the visible OS folder.)

```
mkdir -p ~/.claude/skills
cp -r <REPO_PATH>/skills/aim-coach ~/.claude/skills/
cp -r <REPO_PATH>/skills/daily-brief ~/.claude/skills/
cp -r <REPO_PATH>/skills/meeting-prep ~/.claude/skills/
cp -r <REPO_PATH>/skills/humanize ~/.claude/skills/
```

Verify each ends up at `~/.claude/skills/<name>/SKILL.md`.

If any of these already exist at `~/.claude/skills/<name>`, ask before overwriting. Back up first (`~/.claude/skills/<name>.backup-YYYYMMDD`).

## Step 4.5: Fetch Anthropic's skills (docx, pdf, pptx, internal-comms)

Four Anthropic skills round out the kit. `docx`, `pdf`, and `pptx` are bundled with Claude Desktop's Cowork by default, but **Claude Code (CLI and Desktop Code tab) does not ship with them**. So we fetch all four from Anthropic's open skills repo for Code/CLI access. `internal-comms` is Apache 2.0; the others are source-available — the user is fetching their own copy from Anthropic, not us redistributing.

Steps:

1. Clone Anthropic's skills repo to a temp location:
   ```
   git clone --depth 1 https://github.com/anthropics/skills.git /tmp/anthropic-skills
   ```

2. Copy these four skill folders directly into `~/.claude/skills/`:
   ```
   cp -r /tmp/anthropic-skills/skills/docx ~/.claude/skills/
   cp -r /tmp/anthropic-skills/skills/pdf ~/.claude/skills/
   cp -r /tmp/anthropic-skills/skills/pptx ~/.claude/skills/
   cp -r /tmp/anthropic-skills/skills/internal-comms ~/.claude/skills/
   ```

3. Clean up: `rm -rf /tmp/anthropic-skills`.

If `git clone` fails (no internet or git not installed), skip this step and warn the user: "I couldn't fetch Anthropic's document skills (docx, pdf, pptx, internal-comms). Your four core skills (aim-coach, daily-brief, meeting-prep, humanize) installed fine. You can re-run setup later or install these manually from https://github.com/anthropics/skills."

If any of the four already exist at `~/.claude/skills/<name>`, ask before overwriting, same as Step 4.

## Step 4.55: Install agents

Three sub-agents ship with the kit (researcher, critical-thinker, coach). Install them at `~/.claude/agents/` where Claude Code discovers them for `@-mention` invocation.

```
mkdir -p ~/.claude/agents
cp <REPO_PATH>/agents/researcher.md ~/.claude/agents/
cp <REPO_PATH>/agents/critical-thinker.md ~/.claude/agents/
cp <REPO_PATH>/agents/coach.md ~/.claude/agents/
```

Verify each lands at `~/.claude/agents/<name>.md`.

If any of these already exist at `~/.claude/agents/<name>.md`, ask before overwriting. Back up first (`~/.claude/agents/<name>.md.backup-YYYYMMDD`).

Note: agent direct-invocation via `@agent-<name>` works in Claude Code (CLI + Desktop Code tab). In Cowork, agents are invoked autonomously by the orchestrator — students can say "use the critical thinker to stress-test this" and Cowork routes.

## Step 4.6: Package skills as a Cowork plugin (for Cowork's slash menu)

This step only runs when you (Claude) are inside Claude Desktop's Cowork mode. Cowork has its own plugin loader separate from `~/.claude/skills/` — skills installed via Steps 4 and 4.5 are visible in Code/CLI but not in Cowork's `/` autocomplete. To fix that, package the user's skills into a personal Cowork plugin.

Note: `docx`, `pdf`, and `pptx` are already bundled with Cowork by default — don't include them in the plugin. Only the 3 RiftLab skills and `internal-comms` need to be packaged.

Steps:

1. Confirm you have the `create-cowork-plugin` skill available. If you don't (you're running from Code or CLI instead of Cowork), skip this step and add this to your end-of-install report: "I'm not in Cowork mode, so I couldn't package your skills as a Cowork plugin. To make them appear in Cowork's slash menu, open Cowork and ask: 'Package the 4 RiftLab/internal-comms skills from `~/.claude/skills/` into a Cowork plugin called <user>-os.'"

2. Run `create-cowork-plugin` with these inputs:
   - Plugin name: `<user-firstname-lowercase>-os` (e.g., `sash-os`, `maria-os`)
   - Skills to include: `aim-coach`, `daily-brief`, `meeting-prep`, `humanize`, `internal-comms` (5 total)
   - Description: "[Their name]'s personal AI OS: aim-coach, daily-brief, meeting-prep, humanize, internal-comms."
   - Source: `~/.claude/skills/` (where Steps 4 and 4.5 installed them)

3. Install the resulting `.plugin` file into Cowork. The user should see it appear under Personal plugins.

4. Verify in Cowork: type `/` and check that all 8 skills (`/aim-coach`, `/daily-brief`, `/meeting-prep`, `/humanize`, `/docx`, `/pdf`, `/pptx`, `/internal-comms`) show up.

## Step 5: Report and orient

Tell the user, in plain language:

- Where their OS lives. Specifically: "Your AI OS lives at `<OS_PATH>`. Open it in Finder anytime to see or edit your files."
- **The home-folder pattern**: "Always launch Claude from inside `<OS_PATH>` (or work in this project in Cowork). Your CLAUDE.md and identity files load automatically when you do. If you launch Claude outside this folder, Claude won't know you. The simple rule: this folder is your AI home, work from here."
- Skills are installed at `~/.claude/skills/` for Code/CLI discovery, and packaged as a personal Cowork plugin for Cowork's slash menu.
- The skills available: `/aim-coach`, `/daily-brief`, `/meeting-prep`, `/humanize` (built into this kit), plus `/docx`, `/pdf`, `/pptx`, and `/internal-comms` (fetched from Anthropic if the network call succeeded). Suggest they try `/aim-coach` first with any prompt they want to refine, or `/humanize` on any draft that reads as AI-generated.
- The agents available: `@agent-researcher`, `@agent-critical-thinker`, `@agent-coach`. Suggest they try `@agent-critical-thinker` first on any plan or idea they want stress-tested.
- That this is THEIR OS. Edit any file in the OS folder and Claude picks up the changes. `about-me/current-focus.md` is the one they'll update most often.
- The curation rule: "Review CLAUDE.md monthly. For each line, ask: would removing it cause Claude to make a mistake? If not, delete it."

End with one sentence on what's next. Do not pad with congratulations. Match their voice.

## Edge cases

- **User explicitly wants `~/.claude/` as the install location**: respect it. Install identity files directly there alongside the skills. Note the trade-off in your report: "Your OS lives in a hidden config folder. You can still edit the files, but they won't show up in Finder by default."
- **User has existing skill folders at `~/.claude/skills/<name>`**: ask before replacing. Offer to back them up first as `~/.claude/skills/<name>.backup-YYYYMMDD`.
- **User refuses an interview question**: skip it. Generate the file with sensible defaults and note that they can edit it.
- **User is in a hurry**: offer a "quick install" that asks only for name, role, and install location. Defaults for the rest. They can fill in later.

## Voice for the install conversation

- Be warm. This is setup, not surgery.
- Be brief. One question at a time. Short responses.
- Be specific about what you're doing. Say "I'm writing your voice.md now" not "Generating files..."
- Match their energy. If they're terse, be terse. If they're chatty, give them room.
- No filler. No "Great answer!" No "That's interesting."
