---
name: meeting-prep
description: Prepare for an upcoming meeting. Classifies the meeting, researches what's needed (the company, the people, the history, or the strategy), and produces a brief built for that specific meeting. Use when the user says "prep me for [meeting]", "meeting prep", "I have a call with [person]", "help me get ready for", or describes a meeting they need to walk into prepared.
---

# Meeting Prep

You prepare the user for one specific meeting. There is no canonical brief, because meetings are not alike: a sales call needs company research, an interview needs research on the people, an internal sync needs last time's open items, a kickoff needs an agenda, a negotiation needs strategy. What is canonical is the flow. Classify the meeting, ask only what you can't infer, gather what that type needs, and render a brief shaped to it.

Two disciplines hold throughout: cite where each fact came from, and show nothing rather than pad. A short brief that's all signal beats a long one with filler.

## Phase 0: Load the lens

Read `about-me/identity.md` if it exists, for the user's role. Role shapes what a good outcome looks like and what's worth researching. That's the only file you load up front.

Pull more only if the meeting calls for it: read `about-me/current-focus.md` only when the meeting connects to an active project and tying the prep to that work helps. Don't load it by default.

This brief is a working document the user reads before walking in, not published content, so don't load voice rules. Just write it tight and direct, no filler.

## Phase 1: Classify and fill the gaps

**Identify the meeting.** If a calendar connector is available, find the event (title, time, attendees, description). Otherwise, the user names it.

**Classify the type** from the title and who's attending. Most meetings fall into one of these, and the type decides everything downstream:

- **External / sales:** a prospect, customer, partner, or vendor.
- **Interview:** hiring, being hired, or a reference call.
- **Internal sync / 1:1:** people inside the user's own org.
- **Kickoff / planning:** starting something, or structuring a decision.
- **Negotiation / high-stakes:** a deal, a conflict, or a conversation with real downside.

If the title and attendees make the type obvious, don't ask. If they don't, ask.

**Ask only the gaps, batched into one short message.** The one question almost always worth asking is the goal: "What do you want to walk out with?" Add a second only when the type or focus is genuinely unclear: "What should I focus on, the company, the people, the agenda, or the strategy?" Don't interrogate. Infer everything you can; ask for the rest once.

## Phase 2: Gather what the type needs

Route by type. Don't run a fixed pipeline; pull only the sources that matter for this meeting.

| Type | Gather |
| --- | --- |
| External / sales | the company (what they do, recent news, funding, size); the person (role, tenure, background); the recent email thread; any past notes |
| Interview | the people's backgrounds and the company/role; recent news; what they likely care about |
| Internal sync / 1:1 | the last meeting's notes and open action items; the recent email thread |
| Kickoff / planning | the objective, prior decisions, who owns what; a draft agenda with rough time blocks |
| Negotiation / high-stakes | the strategic picture: the other side's goal and their alternative if this doesn't land; likely objections; the decision criteria |

Tools, used as the type requires: web search for a company or a person, Granola for past meeting notes, Gmail for the email thread, the calendar event for who's in the room. None of this comes from a maintained contact list.

**Inventory before you write.** Note what you actually found and where the gaps are. If a person has no online presence and no prior history, say so rather than inventing a profile. If you can't find the company's recent news, say that too. Gaps named are more useful than gaps papered over.

## Phase 3: Synthesize, by type

Turn what you gathered into something usable in the room.

- **The outcome is universal.** Every brief names one outcome to aim for, framed as a concrete result that moves things forward, not "have a good meeting." Where it helps, add a backup outcome and a walk-away minimum.
- **Research-heavy types** (external, interview): synthesize the findings into who they are, what they likely care about, and the few talking points and questions that follow.
- **Strategy types** (negotiation, high-stakes): work out the other side's view (their goal, their alternative), and pre-empt the one or two likely objections, each paired with the interest underneath it and how you'd frame it before it's raised.
- **Agenda types** (kickoff, planning): build the actual agenda, the decision points, and who needs to be in each part.

## Phase 4: Render

A spine that adapts to the type, not a fixed template. Always lead with the meeting and the outcome; include the type-specific blocks; always close with the questions to ask.

```
# Meeting Prep: [Person / Team], [Date, Time]

## Goal
[The one outcome to aim for, in a sentence the user could write down before walking in. Add backup / walk-away if relevant.]

## [Type-specific block(s)]
- External/sales:  Company snapshot · Who you're meeting · What changed since last contact
- Interview:       Who you're meeting · Company/role context · What they likely care about
- Internal/1:1:    Last time · Open action items · What's unresolved
- Kickoff/planning: Objective · Agenda with time blocks · Decision points · Owners
- Negotiation:     The other side's view · Their alternative · Objections, pre-empted

## Questions to Ask
- [A question that surfaces what you need]
- [A question that tests an assumption you're carrying in]

## Risks  [include only when there's a real one]
- [What could go wrong, what's sensitive, the one thing not to bring up]

## Sources & Gaps
- [Where the facts came from; what you couldn't find]
```

Drop any block that's empty. A brand-new contact with no history gets a short brief and a few warm-up questions, not padding.

## Phase 5: Self-review before delivering

1. Could the user use this in the room, or is it generic advice? If generic, sharpen or cut.
2. Is the goal a concrete outcome that moves things, not "have a good meeting"?
3. Did I gather what *this type* needs, and skip what it doesn't?
4. Are the questions things the user can actually say out loud?
5. Did I cite sources and name the gaps, rather than invent to fill them?
6. Any em dashes? Replace.
