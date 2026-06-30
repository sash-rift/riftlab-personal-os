---
name: decision-council
description: Convene a board of independent functional advisors (CMO, CFO, COO, GC) to make a bounded business decision, then synthesize their conflicting positions into one recommendation with a clear owner. Use when asked to "convene the council", "run a decision council", "should we [decision]", or when a high-stakes, cross-functional decision needs separated perspectives. Convenes agents only when the decision earns it.
---

# Decision Council Skill

Convene a board of independent advisors to make a bounded business decision.

> The skill owns the process. The advisors own the perspectives. The human owns the decision.

**Core principle:** Convene only when the decision earns it. Most decisions are answered directly. The board is invited when a decision has real uncertainty, real tradeoffs, and a costly downside — and only the advisors whose lenses conflict are seated.

Full rationale, frameworks, and sources: `decision-council-plan.md` (in this skill folder).

---

## Advisors

Four custom agents provided by the `riftlab-os` plugin, spawned by their plugin-scoped names `riftlab-os:cmo-advisor`, `riftlab-os:cfo-advisor`, `riftlab-os:coo-advisor`, `riftlab-os:gc-advisor`. They run in **parallel** and in **isolation** — no advisor sees another's position.

| Advisor | Lens | Argues | Model |
| --- | --- | --- | --- |
| **cmo-advisor** | Market timing, demand, competitive window, positioning | Move — the window closes | Sonnet |
| **cfo-advisor** | Capital, unit economics, downside, runway | De-risk — a bad call is costly to unwind | Sonnet |
| **coo-advisor** | Capacity, delivery quality, support load, execution | We must deliver this well | Sonnet |
| **gc-advisor** | Legal, regulatory, contractual, liability, IP | Here's what must be true, and the conditions | Sonnet |

Each advisor distributes the adversarial function internally — it runs a Key Assumptions Check and a domain premortem on its own position. There is **no separate Challenge agent**.

---

## Standard Context Block

Every advisor invocation must include this block:

```
DECISION CONTEXT:
- Current date: [YYYY-MM-DD]
- Decision: [one-line, stated as a choice]
- Decision slug: [slug]
- Decision folder: Decisions/[slug]/
- Brief: Decisions/[slug]/_brief.md
- Stakes / reversibility: [from intake]

YOUR JOB:
- Evaluate ONLY through your lens. Argue it honestly.
- Work in isolation. You do not see other advisors' positions.
- Run a Key Assumptions Check and a premortem before finishing.
- Write your position to Decisions/[slug]/_positions/[seat].md
```

---

## Orchestration Flow

```
Phase 0       Phase 1      Phase 2      Phase 3              Phase 4         Phase 5
Intake   →    Gate    →    Frame   →    Convene board   →   Synthesis  →    Log + QA
(Direct)      (Direct)     (Direct)     (Advisors ×N,        (Direct,        (Direct)
                                        PARALLEL)            top-tier model)
```

The skill (you, the orchestrator) runs Phases 0–2, 4, 5 directly. Only Phase 3 spawns agents.

---

## Folder Structure

```
Decisions/[slug]/
├── context.md                       # Phase 0
├── _brief.md                        # Phase 2 (handoff contract)
├── _positions/                      # Phase 3 (one per seated advisor)
│   ├── cmo.md  cfo.md  coo.md  gc.md
└── [YYYY-MM-DD]-[slug]-decision.md  # Phase 4 (the brief + log)
```

---

## Phase 0 — Intake

**Actor:** You, direct. No agents.

Interview the user across five dimensions. Ask only what's missing; infer the rest from context and confirm it back. Save everything to `Decisions/[slug]/context.md`. The brief (Phase 2) is built *from* this — but not all of it goes in (see the lean rule below).

### The interview

**1. The decision**
| Ask | Why it matters |
| --- | --- |
| What exactly is being decided, stated as a choice between named options? | A vague question produces a vague council |
| What's the deadline, and what's driving it? | Sets acceptable depth and urgency |
| How reversible is this? What's the cost of being wrong? | Drives the gate and the confidence bar |

**2. Options**
| Ask | Why it matters |
| --- | --- |
| What options are already on the table? | Anchors advisors on real paths |
| Is "do nothing / wait / run a reversible test" live? | Prevents a false binary |

**3. Owner & stakeholders**
| Ask | Why it matters |
| --- | --- |
| Who owns this decision (who decides)? | The synthesis must hand it to a named owner |
| Who must give input? Who's affected? | Surfaces stakeholder risk |

**4. Context & constraints**
| Ask | Why it matters |
| --- | --- |
| What facts, metrics, or prior decisions are relevant? | Separates knowns from assumptions |
| What budget, capacity, or hard limits bound this? | Keeps options feasible |
| Which internal files should advisors read? | Routes scoped research to real evidence |

**5. Success & risk tolerance**
| Ask | Why it matters |
| --- | --- |
| What does a good outcome look like in 6–12 months? | Becomes the decision criteria |
| How much downside is acceptable here? | Calibrates how hard the lenses push back |

| Weak intake | Strong intake |
| --- | --- |
| "Should we grow faster?" | "Launch the Pro tier in Q3, or harden it and wait until Q1?" |
| "Get me some input." | "$40k build cost, 2-person team at capacity, churn risk if we ship rough." |

### Capture the owner's lean — then quarantine it

The user almost always has a preferred option. **Ask for it and write it down — in `context.md`, NOT in the brief.** The lean tells *you* (the synthesizer) what to weigh later and what to stress-test, but if it reaches the advisors it poisons their independence and manufactures consensus around the owner's prior. Interview the lean out so it can't leak into Phase 2.

If the input is too thin to frame the decision, ask follow-ups. **Do not convene a board on a fog.**

---

## Phase 1 — The Gate

**Actor:** You, direct. This is the most important step — it decides whether agents run at all.

### Cynefin (situation type)
- **Clear** → answer with a rule/checklist. **Stop. No board.**
- **Complicated** → one or two expert lenses may suffice, not a full board.
- **Complex** → full board. *(The council's home turf.)*
- **Chaotic** → stabilize first.
- **Confused** → reframe before proceeding.

### Vroom-Yetton (participation)
Convene the board only when **at least two** are true:
multiple plausible options · meaningful stakes · real uncertainty · stakeholders may disagree · cross-functional · failure is costly or hard to reverse · the user needs a recommendation, not a summary.

**If the gate fails:** produce a short, direct recommendation and stop. State plainly that the decision did not warrant a council. This restraint is the point.

### Dynamic casting
Seat only the lenses that conflict for this decision:

| Decision shape | Seat |
| --- | --- |
| Pricing / launch timing | CMO + CFO + COO |
| New vendor / partner / client | CFO + COO + GC |
| Regulated or contractual move | GC + CFO + CMO |
| High-stakes, cross-functional | all four |

Announce the cast and the reason before convening.

---

## Phase 2 — Frame (the decision brief)

**Actor:** You, direct.

Write `Decisions/[slug]/_brief.md` — the only shared context the advisors receive. Separate facts from assumptions explicitly; advisors must know which is which.

### Write the brief NEUTRAL — do not lead the witnesses

The council is only as independent as the brief lets it be. A brief that pre-loads a conclusion produces four advisors echoing one opinion — consensus that looks like four-lens validation but is really one steer arriving four times. That is diversity collapse, and it defeats the entire point of separate lenses.

Before convening, audit the brief against these rules:

- **State evidence as data, not as a verdict.** Give the Cohort-1 feedback / the metric / the prior result; do not append "which points against Option X." Let each lens decide how much it weighs.
- **Present all options evenhandedly.** Do not label one "owner's lean" or pre-rank them. If the owner has a lean, it goes in `context.md`, not the brief the advisors read.
- **Do not tell advisors which way to weight or which option to scrutinize hardest.** "Stress-test the risky option" is a thumb on the scale. Each lens already knows what to stress-test.
- **No loaded adjectives.** "The proven 4-week format" vs "an untested 2-week intensive" pre-decides the debate. Use neutral descriptors.

If you would not be comfortable handing the same brief to an advisor briefed to argue the *opposite* side, it is not neutral yet.

```markdown
# Decision Brief: [slug]
- Decision (one sentence, as a choice):
- Options (2–4, incl. wait / reversible test) — presented evenhandedly, no pre-ranking:
- Decision criteria (3–5, from the success definition):
- Known facts (as data, no verdicts attached):
- Stated assumptions (flagged as assumptions, not as leanings):
- Constraints (budget, capacity, timeline, hard limits):
- Stakes / reversibility:
- Owner / stakeholders:
- Internal files to consult: [paths]
- Deadline:
```

---

## Phase 3 — Convene the board

**Actor:** The seated advisor agents. **Spawn them in a single parallel batch.**

For each seated advisor, invoke its agent by its plugin-scoped name (`riftlab-os:cmo-advisor`, `riftlab-os:cfo-advisor`, `riftlab-os:coo-advisor`, `riftlab-os:gc-advisor`) with the standard context block. They run concurrently and write to `_positions/[seat].md`.

**Non-negotiables:**
- **Parallel** — independent lenses have no dependency; do not serialize them.
- **Isolation** — never pass one advisor's output to another. Contamination collapses the diversity the council depends on.
- **Scoped research** — internal files first, light external scan only where the lens needs outside facts. This is not Deep Research (see Research Rules).

Wait for all seated advisors to finish before synthesizing.

---

## Phase 4 — Synthesis (the CEO)

**Actor:** You, direct, on the top-tier model. **Not a peer agent.**

1. **Multiple Advocacy** — read all positions. Lay out the competing advocacies fairly. Name where they agree and where they genuinely conflict.
2. **Consensus check — is the agreement real?** When the board is unanimous, do NOT report unanimity as a strong signal until you rule out the brief. Ask: *could every advisor have reached this from the brief alone, regardless of lens?* If the brief named the winning option, pre-loaded a verdict, or told them what to scrutinize, the consensus is likely **manufactured** — a mirror, not corroboration. Say so plainly in the synthesis and down-weight it. Genuine independent convergence (advisors reaching the same place from *different* reasons, on facts the brief left neutral) is gold; flag which kind you actually have.
3. **Resolve, don't list** — make the call. Say what to do, why, what tradeoff is being accepted, and what risk remains. Ban mushy "consider exploring" language.
4. **Decision Quality** — verify the recommendation satisfies all six elements: frame, alternatives, information, values, reasoning, commitment.
5. **RAPID / DACI** — assign owner, accountable executor, who's informed, and the next action with a deadline.

Write the Decision Council Brief (template below) to `Decisions/[slug]/[YYYY-MM-DD]-[slug]-decision.md`.

---

## Phase 5 — Log + Quality Check

**Actor:** You, direct.

**Decision Quality**
- [ ] Decision clearly framed and bounded
- [ ] At least two real alternatives weighed
- [ ] Facts separated from assumptions
- [ ] Criteria and tradeoffs explicit
- [ ] Reasoning from criteria to recommendation visible
- [ ] Owner, next action, deadline set

**Agentic discipline**
- [ ] The gate passed before any agent was convened
- [ ] Each seated advisor had a genuinely conflicting lens
- [ ] Advisors worked in isolation
- [ ] Synthesis resolved tensions rather than listing them
- [ ] Output supports the human as decision-maker

Append the decision log: what was decided, why, who owns it, what triggers a revisit.

---

## Research Rules (what & when)

Scoped research, not Deep Research. Default to a targeted scan.

- **Internal first.** Advisors read the internal files named in the brief before reaching outward.
- **External, light.** Web scan only when the lens depends on outside facts — competitive/demand signal (CMO), cost benchmarks (CFO), regulatory/precedent (GC). A scan, not a literature review.
- **Escalate to the deep-research skill only when** the decision is high-stakes, the domain unfamiliar, the information landscape broad, and the cost of being wrong high. The relevant advisor calls deep-research for its angle; the council stays the orchestrator.

---

## Output Template — Decision Council Brief

```markdown
# Decision Council Brief — [slug]

## Decision
<one-sentence decision as a choice>

## Recommendation
<the chosen path>

## Confidence
<High / Medium / Low — one sentence why>

## Why this path
1. <reason tied to a decision criterion>
2. <reason tied to a decision criterion>
3. <reason tied to a decision criterion>

## The board (positions)
- CMO: <position + one-line rationale>
- CFO: <position + one-line rationale>
- COO: <position + one-line rationale>
- GC:  <position + one-line rationale>

## Where the board conflicted
<the real tension, and how it was resolved>

## Key risks
- Risk: <risk> — Mitigation: <mitigation>
- Risk: <risk> — Mitigation: <mitigation>

## What would change this decision
- <new information or condition that would flip it>

## Next actions (RAPID)
- Owner: <person> — Action: <action> — Deadline: <date>

## Decision log
<what was decided, why, who owns it, what triggers a revisit>
```

---

## Completion Criteria

- [ ] Gate ran first; council convened only if it passed
- [ ] Only conflicting lenses seated; cast and reason announced
- [ ] Brief separated facts from assumptions
- [ ] Advisors ran in parallel, in isolation
- [ ] Synthesis made a clear call with an owner and next action
- [ ] Decision Council Brief + log saved to `Decisions/[slug]/`
