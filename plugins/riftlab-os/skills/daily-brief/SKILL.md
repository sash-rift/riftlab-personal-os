---
name: daily-brief
description: Generate a morning brief that gives a 30-second read on the day. Pulls the calendar, inbox, and open threads, then prioritizes by content signal and synthesizes across sources instead of listing them. Adapts to the user's role and current focus. Use when the user says "daily brief", "morning brief", "what's my day", "prep me for today", or starts the day asking what's ahead.
---

# Daily Brief

You produce a morning brief that gives the user a clear read on their day in 30 seconds. A brief is not a list. It leads with the bottom line, connects items across sources, and surfaces the one thing that would otherwise slip. The current calendar and inbox are raw material, not the output.

Run this as a pipeline. The work that matters happens in the middle: scoring by signal (Phase 2) and synthesizing (Phase 3). Everything before is gathering, everything after is formatting.

## Phase 0: Load the lens

Read these from the user's OS folder if they exist. They decide what counts as signal *today*:

- `about-me/identity.md`: the user's role. A lawyer's "time-sensitive" is a filing date; a founder's is an investor reply. Use the role to shape what you flag.
- `about-me/current-focus.md`: active projects, what's hot this week, who's in play. This is the priority lens, and it replaces any maintained contact list.
- `about-me/voice.md`: tone for the brief itself.
- `agent.md`: if it gives you a name, you can sign on with it ("Nuro here. Morning, Sash.").

If any are missing, run on general heuristics and don't block. Never make the user create a file to get a brief.

## Phase 1: Gather, in parallel

Pull every source at once. Each has a fixed recipe.

**Calendar.** If a calendar connector is available (Google Calendar or similar), fetch today plus tomorrow morning, in the user's timezone. If not, ask once: "Paste today's calendar or tell me what's on it."

**Inbox.** If an email connector is available, pull the last 24-36 hours, unfiltered for now (Phase 2 scores it). A query like `in:inbox newer_than:1d` is the starting point. If not, ask once: "Anything urgent in your inbox I should flag?"

**Open threads.** What the user left hanging yesterday.
- First try the session logs: list Claude session files modified in the last day (`~/.claude/projects/<project>/*.jsonl` on the Code CLI) and scan the last ~50 messages of each for: "let me think about that", "remind me to", "I'll do X later"; a "want me to..." offer that was never taken; TODOs created but not finished; decisions parked ("we'll come back to this").
- If those logs aren't available on this surface, fall back to recent conversation memory, or ask: "Anything from yesterday still hanging?"
- Cap at 3. Keep the ones most likely to matter today.

**Mode.** Interactively, batch every missing-connector question into one short message; don't interrogate source by source. Headless (scheduled/cron), never ask: make a reasonable call, mark the section "none", and move on.

## Phase 2: Score the inbox by signal

The smart layer, and it applies to the inbox only. The calendar isn't scored; it's the day's timeline and gets laid out in order at render. Rank inbox items by what's detectable in the message itself. No contact roster is needed or used.

Ranked high to low:

- flagged IMPORTANT or starred by the mail system
- a real human, not bulk: a personal sender name, not a `no-reply@` / notification / marketing domain, and no `List-Unsubscribe` header (that header is a near-certain sign the message is bulk)
- the user is in **To**, not Cc, and the recipient list is short
- conversational state: someone replied to a thread the user started, or is directly asking the user something
- time-sensitive content: deadline, payment or invoice, RSVP, reschedule or cancellation, "confirm by", "need this by"
- relevance: names an active project or a person from `current-focus.md`

Skip notifications, digests, marketing, and newsletters. Cap the inbox section at ~5 items. Over the cap, keep the most time-sensitive and the most relevant to today, and drop the rest silently.

Use what `identity.md` implies is high-stakes for this person's work to break ties, especially for terse items where no keyword fires on its own.

## Phase 3: Synthesize

This is what makes it a brief. Three moves, in order.

1. **Connect across sources.** For each meeting on today's timeline, check whether an email, thread, or open item bears on it. If so, attach a one-line prep note to that timeline entry ("the redline that landed at 11pm is for this; read it first"). For each high-signal email, check whether it touches a meeting today or a current-focus project, and tie them together. The connection is the value; an isolated calendar and an isolated inbox are two lists.
2. **Find the bottom line.** From everything gathered, state the 1-3 outcomes that define a good day, plus any overnight surprise. Write this last, place it first.
3. **Find the slip.** The high-consequence thing with no calendar trigger and no email chasing it: the work `current-focus.md` says matters that nothing today forces. This is the single most useful thing a brief surfaces, because nothing else will.

## Phase 4: Render

Five sections. Each opens with a one-line topic sentence that carries the section's bottom line.

```
# [Weekday], [Month Day, Year]

## Bottom Line
[One dense paragraph. The 1-3 outcomes that define a good day, plus any overnight surprise. Readable on its own in 30 seconds. This is the whole brief if the user reads nothing else.]

## Schedule
[One assessment line on the shape of the day: "Heavy afternoon, the morning's your only deep-work block." Then lay the day out as a timeline, grouped by part of day. Attach a prep note only where one is needed.]

Morning
- [HH:MM] [Meeting] (prep note if needed)
- [HH:MM] [Meeting]

Afternoon
- [HH:MM] [Meeting]

Reminders & all-day
- [All-day events, reminders, anything due today with no set time]

[If the calendar is empty: "No meetings. The day is yours."]

## Decision Queue
- [The decision]. Options: [A] / [B] / [C]. Recommend [X]. Decide by [time].
[Only items that create or resolve a decision. If none, "Nothing needs a decision today."]

## Don't Forget
[The one thing that would slip. Drop this section entirely if nothing is genuinely fragile.]
```

Every item answers "so what?" Never name a thing without its significance. "Legal emailed about the data-sharing agreement" is a list entry. "Legal wants sign-off on a retention clause that conflicts with yesterday's privacy commitment; decide before tomorrow's partner review" is a brief.

An empty section says "None" rather than disappearing, except "Don't Forget", which is dropped when nothing is fragile. Don't manufacture urgency to fill it.

## Voice

- Open with one warm line that uses the user's name ("Morning, Sash."). The greeting is the only human flourish; the brief itself is terse.
- After the greeting, no filler. Don't say "Here's what's on your plate." Put the plate down.
- Match `voice.md`. No em dashes. If the user prefers terse, be terse.
- Use the user's own words for projects ("Project Eagle", not "the platform initiative").

## Self-review before delivering

1. Did I synthesize, or just list? If two sources never connect, I listed.
2. Is the Bottom Line the actual bottom line, or just the first thing I found?
3. Does every item answer "so what?"
4. Can the whole brief be read in 30 seconds? If not, cut.
5. Is the schedule a clean timeline, with prep notes only where genuinely needed?
6. Did I respect the caps (inbox ~5, open threads 3)?
7. Did I flag the one thing they'd be angry to miss?
8. Any em dashes? Replace.
