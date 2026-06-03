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
- `skills/deep-research/` (SKILL.md + the `framework/` reference files)
- `skills/decision-council/` (SKILL.md + `decision-council-plan.md`)
- `agents/researcher.md`
- `agents/critical-thinker.md`
- `agents/coach.md`
- `agents/oracle.md`, `agents/hermes.md`, `agents/athena.md`, `agents/scribe.md` (the `deep-research` agent team)
- `agents/cmo-advisor.md`, `agents/cfo-advisor.md`, `agents/coo-advisor.md`, `agents/gc-advisor.md` (the `decision-council` advisor board)

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
9. **Install location**: "Where do you want your AI OS to live? This will be a real folder you can open in Finder (Mac) or File Explorer (Windows) and edit directly. Suggested paths: `~/intelligence/`, `~/MyAI/`, or `~/Documents/AI/`. Pick one or give me a custom path."

Do not default to `~/.claude/` — that's a hidden config folder and we want the OS to feel like a real owned thing. If the user explicitly says they want `~/.claude/`, respect it, but otherwise nudge toward a visible folder.

If they give a very short answer to any question, ask one follow-up to get usable detail. Don't interrogate. One follow-up max per question.

## Step 2.5: Check for existing identity files

Before generating any files in Step 3, check what's already at the user's chosen install location. Students often arrive with a `CLAUDE.md` they wrote themselves or inherited from another tutorial — silently overwriting it would lose their work.

For each file Step 3 will write, do this check:

- `<OS_PATH>/CLAUDE.md`
- `<OS_PATH>/agent.md`
- `<OS_PATH>/about-me/identity.md`
- `<OS_PATH>/about-me/voice.md`
- `<OS_PATH>/about-me/current-focus.md`
- `<OS_PATH>/rules/writing-style.md`
- `<OS_PATH>/rules/communication.md`

For each path:

1. **Check existence.** If the file does not exist, skip — Step 3 will create it fresh.

2. **Read it. Triage what's in it:**
   - **Empty or scaffold-only** (no real user content — just placeholder template text, the Anthropic Claude Code quickstart default, an LL2-style draft with `[YOUR ROLE HERE]` markers): treat as safe to replace. Tell the user briefly: "I found an empty/default `<filename>` — I'll back it up and generate a fresh one." Back up first (rename to `<filename>.backup-YYYYMMDD-HHMMSS`), then let Step 3 proceed.
   - **Has real user content** (custom projects named, specific voice rules they wrote, actual context that's clearly theirs): pause and ask. Do not auto-decide.

3. **If real content, show the user:**
   - The file path
   - The first 15-20 lines as a preview
   - Three options, in this order:

     **1) Merge (recommended).** I'll read your file, pull out anything specific to you (your projects, your voice rules, custom context), and weave it into the generated file alongside what we covered in the interview. Your original gets backed up first as `<filename>.backup-YYYYMMDD-HHMMSS`.

     **2) Replace.** Back up your file as `<filename>.backup-YYYYMMDD-HHMMSS`, then generate fresh based only on our interview. Your original content is preserved on disk but won't carry into the new file.

     **3) Keep yours.** Leave your file untouched. I won't generate this one in Step 3. You can integrate manually later.

4. **Apply the chosen action:**
   - **Merge:** Read the user's file. Extract unique signal — anything that's clearly user-written and not template scaffold (project names, real voice rules, specific context). Pass that into Step 3 for the matching file. Step 3 weaves it into the appropriate sections alongside interview content. Back up the original first.
   - **Replace:** Back up the original, then let Step 3 generate fresh.
   - **Skip:** Mark this file path as "skip in Step 3." Move on to the next file.

5. **Always back up before any destructive change.** Backup format: `<filename>.backup-YYYYMMDD-HHMMSS` in the same directory. Same for files under `about-me/` and `rules/` — back up in their respective subdirectories, not at `<OS_PATH>` root.

Apply this check file-by-file. A user may have a `CLAUDE.md` but no `agent.md` — only prompt for files that actually exist.

Also note for folders:

- `<OS_PATH>/about-me/` and `<OS_PATH>/rules/` directories: additive. Create if missing, leave existing alone. Per-file checks above handle their contents.
- `<OS_PATH>/references/` and `<OS_PATH>/projects/`: additive. Step 3 only creates them with `.gitkeep` if they don't already exist; never touches existing contents.

## Step 3: Generate identity files

Using the user's answers, write these files at their chosen install location (the path from question 7 — referred to below as `<OS_PATH>`, e.g., `~/intelligence/`).

**Honor Step 2.5's decisions for each file.** If a file was marked "skip," do not write it. If marked "merge," weave the extracted signal from the existing file into the appropriate sections of the generated file alongside interview content. If marked "replace" (or the file didn't exist), generate normally.

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

## Step 3.9: Before you install — read this once

Steps 4 through 4.55 copy files into the user's Claude config directory. These are running on a machine you don't fully know, so before any command, do three things.

**1. Detect the OS and shell.** Determine whether you're on macOS/Linux (bash/zsh) or Windows (PowerShell). Every path and command below has a form for each. Never run a macOS command on Windows or the reverse — that's the single most common way this install breaks.

**2. Know the target — same place, written two ways:**

| | macOS / Linux | Windows (PowerShell) |
| --- | --- | --- |
| Claude config root | `~/.claude/` | `$env:USERPROFILE\.claude\` |
| Skills install to | `~/.claude/skills/` | `$env:USERPROFILE\.claude\skills\` |
| Agents install to | `~/.claude/agents/` | `$env:USERPROFILE\.claude\agents\` |

When a step shows a Unix command, translate it for Windows:

| Unix (macOS/Linux) | Windows (PowerShell) |
| --- | --- |
| `mkdir -p <dir>` | `New-Item -ItemType Directory -Force -Path <dir>` |
| `cp -r <src> <dst>` | `Copy-Item -Recurse -Force <src> <dst>` |
| `rm -rf <dir>` | `Remove-Item -Recurse -Force <dir>` |

**3. The rule for every command below: the command is an example, the result is the requirement.** Each step states what must exist when it's done — a named file or folder at a target path. *That end state is the thing that matters; the exact command is just the usual way to reach it.* So:

- Run the form that matches the user's actual OS.
- **If no shell is available, or you can't confirm the shell is writing to the user's real machine** (this can happen in Cowork, whose shell may run in a sandbox separate from the user's computer), **use your own file-writing tools instead** to place the files at the target paths. What matters is the file landing in the right place, not which mechanism put it there.
- **After every step, verify the end state** — confirm the named file or folder actually exists at the target. If it isn't there, the step did not succeed: retry, or switch method. Never report a step complete without confirming the files exist.

## Step 4: Install skills

Skills live at `~/.claude/skills/` where Claude discovers them automatically. Install directly there, no symlinks. (Skills are infrastructure, not identity files. They don't need to live in the visible OS folder.)

**What this step does:** copies six skill folders from the cloned repo (`<REPO_PATH>`) into the skills directory — one folder per skill. Recursive copy, because each skill is a folder (some carry sub-folders). Follow the Step 3.9 rule: run the form matching the OS, or use your file tools if the shell may be sandboxed.

macOS / Linux:

```
mkdir -p ~/.claude/skills
# one recursive copy per skill folder
cp -r <REPO_PATH>/skills/aim-coach ~/.claude/skills/
cp -r <REPO_PATH>/skills/daily-brief ~/.claude/skills/
cp -r <REPO_PATH>/skills/meeting-prep ~/.claude/skills/
cp -r <REPO_PATH>/skills/humanize ~/.claude/skills/
cp -r <REPO_PATH>/skills/deep-research ~/.claude/skills/
cp -r <REPO_PATH>/skills/decision-council ~/.claude/skills/
```

Windows (PowerShell) — same six copies, translated:

```
New-Item -ItemType Directory -Force -Path $env:USERPROFILE\.claude\skills | Out-Null
Copy-Item -Recurse -Force <REPO_PATH>\skills\aim-coach       $env:USERPROFILE\.claude\skills\
Copy-Item -Recurse -Force <REPO_PATH>\skills\daily-brief     $env:USERPROFILE\.claude\skills\
Copy-Item -Recurse -Force <REPO_PATH>\skills\meeting-prep    $env:USERPROFILE\.claude\skills\
Copy-Item -Recurse -Force <REPO_PATH>\skills\humanize        $env:USERPROFILE\.claude\skills\
Copy-Item -Recurse -Force <REPO_PATH>\skills\deep-research   $env:USERPROFILE\.claude\skills\
Copy-Item -Recurse -Force <REPO_PATH>\skills\decision-council $env:USERPROFILE\.claude\skills\
```

**Verify (required):** confirm a `SKILL.md` now exists at each `…/.claude/skills/<name>/SKILL.md` (all six). For `deep-research` and `decision-council`, also confirm their sub-folders arrived — `deep-research/framework/` (four files) and `decision-council/decision-council-plan.md` — the skills read from them at runtime. If any are missing, the recursive copy didn't take; redo it or use your file tools.

If any of these already exist at `~/.claude/skills/<name>`, ask before overwriting. Back up first (`~/.claude/skills/<name>.backup-YYYYMMDD`).

**If you're in Cowork and hit a permission prompt writing to `~/.claude/`**: this is normal. Cowork sometimes asks for confirmation when writing into the hidden `.claude` folder. Tell the user plainly: "Cowork is asking permission to write to your hidden Claude config folder. Approve it so I can install the skills there." Then proceed. Do not abandon the step or fall back to alternate locations. Do not try to bypass it with osascript or symlink tricks.

## Step 4.5: Fetch Anthropic's skills (docx, pdf, pptx, internal-comms)

Four Anthropic skills round out the kit. `docx`, `pdf`, and `pptx` are bundled with Claude Desktop's Cowork by default, but **Claude Code (CLI and Desktop Code tab) does not ship with them**. So we fetch all four from Anthropic's open skills repo for Code/CLI access. `internal-comms` is Apache 2.0; the others are source-available — the user is fetching their own copy from Anthropic, not us redistributing.

Steps:

1. Clone Anthropic's skills repo to a temp location. (`--depth 1` grabs only the latest snapshot — faster, smaller.)
   - macOS / Linux: `git clone --depth 1 https://github.com/anthropics/skills.git /tmp/anthropic-skills`
   - Windows (PowerShell): `git clone --depth 1 https://github.com/anthropics/skills.git $env:TEMP\anthropic-skills`

2. Copy these four skill folders into the skills directory (same recursive copy as Step 4):

   macOS / Linux:
   ```
   cp -r /tmp/anthropic-skills/skills/docx ~/.claude/skills/
   cp -r /tmp/anthropic-skills/skills/pdf ~/.claude/skills/
   cp -r /tmp/anthropic-skills/skills/pptx ~/.claude/skills/
   cp -r /tmp/anthropic-skills/skills/internal-comms ~/.claude/skills/
   ```
   Windows (PowerShell):
   ```
   Copy-Item -Recurse -Force $env:TEMP\anthropic-skills\skills\docx          $env:USERPROFILE\.claude\skills\
   Copy-Item -Recurse -Force $env:TEMP\anthropic-skills\skills\pdf           $env:USERPROFILE\.claude\skills\
   Copy-Item -Recurse -Force $env:TEMP\anthropic-skills\skills\pptx          $env:USERPROFILE\.claude\skills\
   Copy-Item -Recurse -Force $env:TEMP\anthropic-skills\skills\internal-comms $env:USERPROFILE\.claude\skills\
   ```

3. Clean up the temp clone: `rm -rf /tmp/anthropic-skills` (macOS/Linux) or `Remove-Item -Recurse -Force $env:TEMP\anthropic-skills` (Windows).

**Verify (required):** confirm `SKILL.md` exists at each of the four `…/.claude/skills/{docx,pdf,pptx,internal-comms}/`. If the clone failed, handle it per the note below — don't silently skip the verify.

If `git clone` fails (no internet or git not installed), skip this step and warn the user: "I couldn't fetch Anthropic's document skills (docx, pdf, pptx, internal-comms). Your four core skills (aim-coach, daily-brief, meeting-prep, humanize) installed fine. You can re-run setup later or install these manually from https://github.com/anthropics/skills."

If any of the four already exist at `~/.claude/skills/<name>`, ask before overwriting, same as Step 4.

## Step 4.55: Install agents

The kit ships two kinds of agents, both installed at `~/.claude/agents/` where Claude Code discovers them.

- **Three thinking-partner agents** (researcher, critical-thinker, coach) — invoked directly by the user via `@-mention`. One for each kind of stuck.
- **Eight skill-internal agents** (oracle, hermes, athena, scribe for `deep-research`; cmo-, cfo-, coo-, gc-advisor for `decision-council`) — orchestrated automatically by their parent skill, not meant for direct `@-mention`. They must be installed for those two skills to run.

**What this step does:** copies 11 single-file agents (`.md` each) into the agents directory. These are plain file copies, not recursive — no sub-folders.

macOS / Linux:

```
mkdir -p ~/.claude/agents
# thinking partners (@-mention)
cp <REPO_PATH>/agents/researcher.md ~/.claude/agents/
cp <REPO_PATH>/agents/critical-thinker.md ~/.claude/agents/
cp <REPO_PATH>/agents/coach.md ~/.claude/agents/
# deep-research team
cp <REPO_PATH>/agents/oracle.md ~/.claude/agents/
cp <REPO_PATH>/agents/hermes.md ~/.claude/agents/
cp <REPO_PATH>/agents/athena.md ~/.claude/agents/
cp <REPO_PATH>/agents/scribe.md ~/.claude/agents/
# decision-council board
cp <REPO_PATH>/agents/cmo-advisor.md ~/.claude/agents/
cp <REPO_PATH>/agents/cfo-advisor.md ~/.claude/agents/
cp <REPO_PATH>/agents/coo-advisor.md ~/.claude/agents/
cp <REPO_PATH>/agents/gc-advisor.md ~/.claude/agents/
```

Windows (PowerShell): create the folder with `New-Item -ItemType Directory -Force -Path $env:USERPROFILE\.claude\agents`, then `Copy-Item -Force <REPO_PATH>\agents\<name>.md $env:USERPROFILE\.claude\agents\` for each of the 11 files above.

**Verify (required):** confirm all 11 `.md` files now exist in the agents directory.

If any of these already exist at `~/.claude/agents/<name>.md`, ask before overwriting. Back up first (`~/.claude/agents/<name>.md.backup-YYYYMMDD`).

**Where these actually work:** custom agents — both the three thinking partners and the eight skill-internal ones — are a **Claude Code** capability (CLI + Desktop Code tab). That's where `@agent-<name>` invocation and the multi-agent skills (`deep-research`, `decision-council`) run. **Cowork cannot invoke custom agents from `~/.claude/agents/`**, so the `@-mention` partners and the two orchestration skills are Code-tab features. We still install all 11 here so Code has them; Cowork just won't use them. (This is why Step 4.6 packages only the Cowork-safe skills for Cowork's menu.)

## Step 4.6: Package skills as a Cowork plugin (for Cowork's slash menu)

This step only runs when you (Claude) are inside Claude Desktop's Cowork mode. Cowork has its own plugin loader separate from `~/.claude/skills/` — skills installed via Steps 4 and 4.5 are visible in Code/CLI but not in Cowork's `/` autocomplete. To fix that, package the user's skills into a personal Cowork plugin.

Note: `docx`, `pdf`, and `pptx` are already bundled with Cowork by default, so don't include them in the plugin. And **deliberately leave out `deep-research` and `decision-council`** — they depend on custom agents Cowork can't run, so they don't belong in Cowork's menu. (A student who clicked `/deep-research` there would hit a skill reaching for an agent team that isn't present — a broken first impression. Those two are Code-tab skills; see Step 5.) Package only the 4 lightweight RiftLab skills (`aim-coach`, `daily-brief`, `meeting-prep`, `humanize`) and `internal-comms` — 5 total. These run fully in Cowork.

Steps:

1. Confirm you have the `create-cowork-plugin` skill available. If you don't (you're running from Code or CLI instead of Cowork), skip this step and add this to your end-of-install report: "I'm not in Cowork mode, so I couldn't package your skills as a Cowork plugin. To make them appear in Cowork's slash menu, open Cowork and ask: 'Package the 5 Cowork-safe skills (aim-coach, daily-brief, meeting-prep, humanize, internal-comms) from `~/.claude/skills/` into a Cowork plugin called <user>-os.'"

2. Run `create-cowork-plugin` with these inputs:
   - Plugin name: `<user-firstname-lowercase>-os` (e.g., `sash-os`, `maria-os`)
   - Skills to include: `aim-coach`, `daily-brief`, `meeting-prep`, `humanize`, `internal-comms` (5 total — NOT deep-research or decision-council)
   - Description: "[Their name]'s personal AI OS: aim-coach, daily-brief, meeting-prep, humanize, internal-comms."
   - Source: `~/.claude/skills/` (where Steps 4 and 4.5 installed them)

3. Install the resulting `.plugin` file into Cowork. The user should see it appear under Personal plugins.

4. Verify in Cowork: type `/` and check that the 8 Cowork-safe skills show up (`/aim-coach`, `/daily-brief`, `/meeting-prep`, `/humanize`, `/internal-comms`, plus the bundled `/docx`, `/pdf`, `/pptx`). `/deep-research` and `/decision-council` should NOT appear here — that's intended; they live in the Code tab.

## Step 5: Report and orient

Tell the user, in plain language:

- Where their OS lives. Specifically: "Your AI OS lives at `<OS_PATH>`. Open it in Finder (Mac) or File Explorer (Windows) anytime to see or edit your files."
- **The home-folder pattern**: "Always launch Claude from inside `<OS_PATH>` (or work in this project in Cowork). Your CLAUDE.md and identity files load automatically when you do. If you launch Claude outside this folder, Claude won't know you. The simple rule: this folder is your AI home, work from here."
- Skills are installed at `~/.claude/skills/` for Code/CLI discovery, and packaged as a personal Cowork plugin for Cowork's slash menu.
- The skills available: `/aim-coach`, `/daily-brief`, `/meeting-prep`, `/humanize`, `/deep-research`, `/decision-council` (built into this kit), plus `/docx`, `/pdf`, `/pptx`, and `/internal-comms` (fetched from Anthropic if the network call succeeded). Suggest they try `/aim-coach` first with any prompt they want to refine, or `/humanize` on any draft that reads as AI-generated.
- **The two orchestration skills — and where to run them.** Say this plainly to the user: "Two of your skills, `/deep-research` and `/decision-council`, run a live team of agents — and that only works in the **Code tab** (or the Claude Code CLI), not in Cowork. You won't see them in Cowork's `/` menu; that's deliberate. To use them, open the Code tab in Claude Desktop and type `/deep-research` or `/decision-council` there." Then describe what they do: `/deep-research` runs a four-agent research team (plan → search → evaluate → synthesize) that returns verified, cited findings; `/decision-council` convenes a board of advisors (CMO, CFO, COO, GC) to pressure-test a real decision and hand back one recommendation with an owner. Tell the user to reach for these when the stakes justify the horsepower — not for quick lookups.
- The agents available, framed as the kind of stuck each one solves (this framing matters, surface it clearly):
  - `@agent-researcher` — **Stuck on information?** You don't know something and you need verified findings with citations. Applies CRAAP and triangulation, hard token budget.
  - `@agent-critical-thinker` — **Stuck on an opinion or plan?** You have a position and want it stress-tested before you commit. Uses pre-mortem, inversion, second-order thinking, steel-manning, base rates, opportunity cost, 5 Whys.
  - `@agent-coach` — **Stuck on a decision?** You've been circling a choice and can't land it. Walks you through GROW (Goal, Reality, Options, Will) one question at a time. Asks, doesn't tell.
  - Suggest they try `@agent-critical-thinker` first on any plan or idea they want stress-tested.
- That this is THEIR OS. Edit any file in the OS folder and Claude picks up the changes. `about-me/current-focus.md` is the one they'll update most often.
- The curation rule: "Review CLAUDE.md monthly. For each line, ask: would removing it cause Claude to make a mistake? If not, delete it."

End with one sentence on what's next. Do not pad with congratulations. Match their voice.

## Edge cases

- **User explicitly wants `~/.claude/` as the install location**: respect it. Install identity files directly there alongside the skills. Note the trade-off in your report: "Your OS lives in a hidden config folder. You can still edit the files, but they won't show up in Finder (Mac) or File Explorer (Windows) by default."
- **User has existing skill folders at `~/.claude/skills/<name>`**: ask before replacing. Offer to back them up first as `~/.claude/skills/<name>.backup-YYYYMMDD`.
- **User refuses an interview question**: skip it. Generate the file with sensible defaults and note that they can edit it.
- **User is in a hurry**: offer a "quick install" that asks only for name, role, and install location. Defaults for the rest. They can fill in later.

## Voice for the install conversation

- Be warm. This is setup, not surgery.
- Be brief. One question at a time. Short responses.
- Be specific about what you're doing. Say "I'm writing your voice.md now" not "Generating files..."
- Match their energy. If they're terse, be terse. If they're chatty, give them room.
- No filler. No "Great answer!" No "That's interesting."
