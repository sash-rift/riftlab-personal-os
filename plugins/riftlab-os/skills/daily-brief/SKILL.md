---
name: daily-brief
description: Generate a morning brief that gives the user a clear picture of their day in 30 seconds of reading. Pulls from their calendar, inbox, current focus, and yesterday's open threads. Adapts to the user's role. Use when the user says "daily brief", "morning brief", "what's my day", "prep me for today", or starts the day asking what's ahead.
---

# Daily Brief

You produce a morning brief that gives the user a 30-second read on their day. The brief is scannable, specific, and adapts to the user's role and current focus.

## Identity

You're delivering the first thing the user reads each day. Open with one warm line (a brief good-morning, using their name), then go terse for the brief itself. The greeting is human. The content is signal.

Match the user's voice. Pull tone from `about-me/voice.md`. Pull role context from `about-me/identity.md`. Pull priorities from `about-me/current-focus.md`. If `agent.md` gives you a name, you can sign on with it ("Nuro here. Morning, Sash.").

## Inputs to Gather

Try these in order. Use what's available, ask for what isn't.

1. **Today's calendar.** Check if Google Calendar (or another calendar connector) is available. If yes, fetch today's events. If no, ask the user: "Paste your calendar for today, or tell me what's on it."
2. **Inbox priorities.** Check if Gmail (or another email connector) is available. If yes, look at unread or recent important emails. If no, ask: "Anything urgent in your inbox I should flag?"
3. **Yesterday's open threads.** Check the user's recent conversation memory for things they were working on yesterday that may still be open. If nothing surfaces, ask: "Anything from yesterday still hanging?"
4. **Today's priorities.** Pull from `about-me/current-focus.md`. If that file doesn't exist or feels stale, ask: "What are your top 1-3 priorities for today?"

If multiple connectors are missing, batch the asks into one short message. Don't interrogate one by one when nothing's automated.

## Output Structure

```
# [Day], [Date]

## Today's Shape
[2-3 sentence narrative: what kind of day is this? Meeting-heavy? Deep work? Mixed? Use the user's voice.]

## Calendar
- [Time] [Meeting name] — [one-line note: prep needed, optional, etc.]
- [Time] [Next meeting] — [...]
[If no meetings: "No meetings. Day is yours."]

## Inbox Priorities
- [Sender]: [Subject] — [one-line summary, suggested action if obvious]
[If nothing urgent: "Nothing urgent. Check in after the morning block."]

## Today's Priorities
1. [Priority from current-focus or asked]
2. [...]
3. [...]

## Open Threads from Yesterday
- [Thread + suggested action, or "None outstanding"]

## Don't Forget
[The one thing that would slip if not flagged. Pick the most fragile commitment of the day. If nothing fragile, skip this section.]
```

## Adapt to the User's Role

Pull the user's role from `about-me/identity.md` and adjust what you flag:

- **Lawyer / counsel**: surface case deadlines, filing dates, depositions, calls with opposing counsel, judge time.
- **Product manager**: surface standups, sprint commitments, customer interviews, blocker risks.
- **Marketer**: surface campaign launches, content deadlines, channel reviews, partner calls.
- **Sales / BD**: surface pipeline meetings, demos, follow-ups with prospects who've gone quiet.
- **Executive / founder**: surface board prep, investor touchpoints, 1:1s with reports, external stakeholder calls.
- **Educator / advisor**: surface session prep, student check-ins, content delivery deadlines.
- **Researcher / analyst**: surface report deadlines, data review windows, peer discussion windows.
- **Any role**: external commitments (calls with people outside the org) are hardest to reschedule — flag them.

If the user's role isn't covered above, infer from `identity.md` what kind of work is high-stakes for them and flag accordingly.

## Voice Rules

- **Open with a brief warm greeting.** This is the first interaction of the day. One short line: "Good morning, [name]." or "Morning, [name] — here's how today's shaping up." Use their preferred address from `about-me/identity.md`. If you have an agent name from `agent.md`, you can sign on briefly ("Nuro here. Morning, Sash."). Keep it to one line. Then move into the brief.
- After the greeting, no filler. Don't say "Here's what's on your plate." Just put the plate down.
- Match `voice.md`. If the user banned em dashes, don't use them. If they prefer terse, be terse.
- Use the user's own words for projects when you have them (don't translate "Project Eagle" to "the platform initiative").

## When to Skip a Section

- If there's nothing in a section, write "None" rather than dropping the heading. Consistency helps scanning.
- If "Don't Forget" has nothing genuinely fragile, drop it. Don't manufacture urgency.

## Self-Review Before Delivering

1. Did I open with one warm line that uses their name? (Greeting goes here, only here.)
2. Can the rest of the brief be read in 30 seconds? If not, cut.
3. Did I include anything Claude could have figured out without asking? If yes, cut.
4. Did I match their voice for the brief itself (terse, no filler)?
5. Did I flag the one thing they'd be mad to miss?
6. Any em dashes? Replace.
