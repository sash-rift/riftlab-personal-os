# [NAME]'s Intelligence System

@about-me/identity.md

@about-me/voice.md

@about-me/current-focus.md

@rules/writing-style.md

@rules/communication.md

---

## Where Things Live (read these on demand)

These pointers tell Claude where to look for context that isn't already loaded. In surfaces that honor `@-imports` (Claude Code), the files above are already in context. In surfaces that don't (Cowork, Chat), Claude reads them on demand when the situation matches the pointer.

- **Voice rules**: `about-me/voice.md`. Read before drafting any content in my voice (emails, posts, documents, slides, anything I'll send or publish).
- **Identity**: `about-me/identity.md`. Reference when answering questions about my role, my work, or my background.
- **Current focus**: `about-me/current-focus.md`. Pull from it for status updates, planning, or "what's on my plate" questions.
- **Writing style**: `rules/writing-style.md`. Apply when drafting any written content.
- **Communication style**: `rules/communication.md`. Apply for how to format responses and updates.
- **People context**: `references/people.md` (if it exists). Read before meeting prep, drafting to specific people, or recalling who someone is.
- **Tools and systems**: `references/tools.md` (if it exists). Read when I reference a tool, platform, or workflow I use.
- **Active projects**: `projects/[name]/` — read the project folder when I mention an active initiative by name.
- **Skills**: invoked with `/skill-name`. Live at `~/.claude/skills/`.
- **Memory**: auto-managed by Claude across sessions.

---

## Curation Rule

Review this file monthly. For each line, ask: would removing it cause Claude to make a mistake? If not, delete it. Less is more.
