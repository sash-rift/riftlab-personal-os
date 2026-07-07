# Decision Council — Plan

A reusable skill that helps an individual or small team make a bounded business decision by convening a board of independent functional advisors, then synthesizing their conflicting positions into a single recommendation with a clear owner.

> The skill owns the process. The advisors own the perspectives. The human owns the decision.

**Core principle:** Convene only when the decision earns it. Most decisions are answered by the skill directly. The board is invited when a decision has real uncertainty, real tradeoffs, and a costly downside — and only the advisors whose lenses genuinely conflict are seated.

This skill is a demonstration of *when a workflow earns custom agents* — the honest contrast to a deterministic skill (meeting intelligence) and the lightweight counterpart to Deep Research.

---

## Why this earns agents (integrity check)

The same four-blocker gate we teach, applied to this workflow:

| Blocker | Passes? | Why |
| --- | --- | --- |
| **Parallel independent work** | ✅ | The advisors evaluate the same brief simultaneously with no dependency between them. This is fan-out, not a dependent chain. |
| **Context isolation for independence** | ✅ | Each advisor reasons in its own window and never sees the others' positions. Independence is where the accuracy comes from (Page, below). |
| **Context pollution** | ✅ (light) | Each advisor's domain research stays in its own window instead of flooding the main thread. |
| **Different model / cost** | optional | Advisors run on a mid-tier model; synthesis runs on the top-tier model. |
| **Restriction** | minimal | Not the primary justification. |

It passes on **parallelism + independence**, honestly — not on hand-waving. The earlier four-stage council design (Context → Options → Challenge → Decision) was a *dependent chain* and should be a skill; this role-based board is fan-out and earns the agents.

**Guardrails (the anti-theater discipline):**
1. Default roster is four. The gate seats only the advisors whose lenses conflict for the specific decision.
2. Every seat must conflict. If two advisors would say the same thing, merge them.
3. No seat without independent work. An advisor that only opines from a title is a lens in a skill, not an agent.
4. The gate runs first. Clear or low-stakes decisions are answered directly, no board.

---

## Framework stack

Each component is grounded in established management science or analytic tradecraft. This is the credibility layer — nothing invented.

| Component | Framework | Source | Grounds |
| --- | --- | --- | --- |
| **Should we convene?** | Cynefin + Vroom-Yetton-Jago | Snowden; Vroom & Yetton 1973 | Classify the situation, then choose participation level (decide / consult / convene). |
| **Why a board beats one mind** | Diversity Prediction Theorem | Scott Page, *The Difference*, 2007 | Collective error = average individual error − predictive diversity. Independent diverse lenses are mathematically more accurate; when diversity collapses, the wisdom evaporates. |
| **How the board runs** | Multiple Advocacy | Alexander George, APSR 1972 | Structured, balanced debate among advocates from different functions; the leader synthesizes. Built to avoid both groupthink and destructive conflict. |
| **Each advisor's rigor** | Key Assumptions Check + Red Team (SAT) + Premortem | Heuer & Pherson 2010; Klein, HBR 2007 | Each advisor stress-tests its own position in its own domain. |
| **When the board agrees** | Dialectical Inquiry / Devil's Advocacy | Mason & Mitroff 1981; Schwenk 1990 | Structured dissent against a forming consensus catches shared error that per-advisor checks miss. Convened conditionally, only on convergence. |
| **The quality bar** | Decision Quality (6 elements) | Spetzler / Howard, Stanford SDG | Rubric the final recommendation must satisfy. |
| **Who owns it** | RAPID / DACI | Bain; Atlassian | Decision rights, accountable owner, next action. |

**Keystone:** Multiple Advocacy is literally a model of a leader hearing structured competing advocacy from functional advisors before deciding. That *is* a C-suite board, formalized in 1972. Page's theorem is the rebuttal to "why not one model with three lenses": independence is where the accuracy comes from, and you only get true independence with separate contexts.

---

## The default cast

Four functional lenses chosen to cover the tension axes of almost any business decision. The C's optimize for upside; Legal owns whether it can actually be done without blowing up later.

| Advisor | Lens | Grounding frameworks | Tends to argue |
| --- | --- | --- | --- |
| **CMO** (opportunity) | Market timing, demand, competitive window, positioning | STP; demand & timing; brand equity | *Move — the window closes.* |
| **CFO** (economics) | Capital allocation, unit economics, downside, runway | Capital allocation / ROIC; CAC-LTV, margin, payback; expected value | *De-risk — a bad call is expensive to unwind.* |
| **COO** (feasibility) | Capacity, delivery quality, support load, execution risk | Theory of Constraints / bottlenecks; execution premortem | *We can't deliver this well right now.* |
| **GC** (permissibility & risk) | Legal, regulatory, contractual, liability, compliance, IP | Risk classification (likelihood × severity); precedent | *Here's what has to be true — and the conditions to proceed.* |

The adversarial function is **distributed**: each advisor runs a Key Assumptions Check and a domain premortem on its own position. That covers per-lens rigor without a standing Challenge seat. But distributed self-critique cannot catch a blind spot *shared across every lens* — when the board converges, each advisor's internal check passes and the group is still wrong together. So a **challenger** is convened **conditionally** (Phase 3.5): not as a fixed stage in a dependent chain (the design we rejected below), but as a red-team spawned only when the board agrees, to test whether the agreement is real. One more seat, and only when convergence earns it — the minimum-agents discipline holds.

---

## Architecture

```
Phase 0        Phase 1      Phase 2      Phase 3            Phase 3.5          Phase 4        Phase 5
Intake    →    Gate    →    Frame   →    Convene board  →   Challenge      →   Synthesis  →   Log + QA
(Direct)       (Direct)     (Direct)     (Advisors ×N,      (Challenger,        (CEO /         (Direct)
                                          PARALLEL)          CONDITIONAL)        Direct, Opus)
```

- **The skill owns** intake, the gate, the shared decision brief, convening, synthesis, and the log.
- **The agents are the advisors only** — parallel, independent, each in its own context.
- **The CEO / synthesis is the orchestrator** (the skill, or the human) — not a peer agent.

### Folder structure

```
Decisions/[decision-slug]/
├── context.md                       # Phase 0: intake
├── _brief.md                        # Phase 2: the shared decision brief (handoff contract)
├── _positions/                      # Phase 3: advisor outputs (one per seat)
│   ├── cmo.md
│   ├── cfo.md
│   ├── coo.md
│   ├── gc.md
│   └── challenger.md                # Phase 3.5: only if the board converges
└── [YYYY-MM-DD]-[slug]-decision.md  # Phase 4: the Decision Council Brief + log
```

---

## Phase 0 — Intake (context gathering)

**Actor:** Orchestrator, direct conversation. No agents yet.

**Purpose:** A decision badly framed is a decision badly made. The brief built here is the only shared context the advisors get, so it must be right.

Five dimensions. Ask only what's missing; infer the rest and confirm.

### Dimension 1 — The decision
| Question | Why it matters |
| --- | --- |
| What exactly is being decided, stated as a choice? | A vague question produces a vague council |
| What's the deadline / what's driving it? | Sets acceptable depth |
| How reversible is it? | Reversible, low-stakes calls may not need a board |
| What's at stake if it goes wrong? | Sets the confidence bar and the gate result |

*Weak: "Should we grow faster?" → Strong: "Launch the Pro tier in Q3 or harden it and wait until Q1?"*

### Dimension 2 — Options on the table
| Question | Why it matters |
| --- | --- |
| What options are already being considered? | Anchors the advisors on real paths |
| Is "do nothing / wait / reversible test" a live option? | Prevents a false binary |

### Dimension 3 — Owner & stakeholders (RAPID)
| Question | Why it matters |
| --- | --- |
| Who owns this decision? | The synthesis must hand it to a named owner |
| Who must provide input? Who is affected? | Surfaces stakeholder risk |

### Dimension 4 — Context & constraints
| Question | Why it matters |
| --- | --- |
| What facts, metrics, docs, or prior decisions are relevant? | Separates knowns from assumptions |
| What budget, capacity, or hard constraints bound this? | Keeps options feasible |
| What internal files should advisors read? | Routes scoped research |

### Dimension 5 — Success & risk tolerance
| Question | Why it matters |
| --- | --- |
| What does a good outcome look like in 6–12 months? | Becomes the decision criteria |
| How much downside risk is acceptable here? | Calibrates how hard GC/CFO push back |

If input is too thin to frame the decision, ask follow-ups before proceeding. Do not convene a board on a fog.

---

## Phase 1 — The gate

**Actor:** Orchestrator, direct.

Two questions decide whether to convene and who to seat.

### Cynefin — what kind of decision is this?
- **Clear** → answer with a rule/checklist. No board.
- **Complicated** → may need one or two expert lenses, not a full board.
- **Complex** → full board: multiple perspectives, probe, synthesize. *(The council's home turf.)*
- **Chaotic** → stabilize first; decide later.
- **Confused** → reframe before proceeding.

### Vroom-Yetton — how much participation?
Convene the board only when **at least two** are true:
- Multiple plausible options exist
- The stakes are meaningful
- There is real uncertainty
- Stakeholders may disagree
- The decision is cross-functional
- Failure is costly or hard to reverse
- The user needs a recommendation, not a summary

If the gate fails, the skill produces a short, direct recommendation and stops. **This is the most on-message moment in the workflow: a skill that decides it doesn't need the agents.**

### Dynamic casting
Seat only the lenses that conflict for this decision:
- Pricing / launch timing → **CMO + CFO + COO**
- New vendor / partnership / client → **CFO + COO + GC**
- Regulated or contractual move → **GC + CFO + CMO**
- High-stakes, cross-functional → **all four**

Name the cast and the reason before convening.

---

## Phase 2 — Frame (the decision brief)

**Actor:** Orchestrator, direct.

Build `_brief.md` — the handoff contract every advisor receives. This is the only shared context; advisors never see each other's work.

```markdown
# Decision Brief: [slug]
- Decision (one sentence, as a choice):
- Options (2–4, incl. wait/reversible test):
- Decision criteria (3–5, from success definition):
- Known facts:
- Stated assumptions (explicitly flagged as assumptions):
- Constraints (budget, capacity, timeline, hard limits):
- Stakes / reversibility:
- Owner / stakeholders:
- Internal files to consult: [paths]
- Deadline:
```

---

## Phase 3 — Convene the board (parallel fan-out)

**Actor:** The seated advisor agents, **run in parallel**.

Each advisor receives: the standard context block + `_brief.md` + its own lens instructions. Each does its scoped research, applies its lens, runs a Key Assumptions Check and a domain premortem, and writes its position to `_positions/[seat].md`.

**Independence is mandatory.** Advisors do not read each other's positions. Contamination collapses the diversity the theorem depends on.

### Advisor output contract (every seat)
```markdown
# [Seat] Position — [slug]
- Position: Recommend / Oppose / Conditional (which option, or which path)
- Top reasons (tied to this lens, 2–4):
- Key assumptions that must hold:
- Domain risks + mitigations (premortem):
- What evidence would flip this position:
- Confidence: High / Medium / Low (one-line why)
```

---

## Phase 3.5 — Dialectical Challenge (conditional)

**Actor:** Orchestrator reads the positions; if the board converged, spawns one challenger agent.

The four advisors self-critique inside their own lens. None of them can see the error the whole board shares — the assumption every lens took for granted, the risk each thought another owned. Page's theorem says the council's accuracy comes from diversity; when the positions converge, that diversity has collapsed and the safeguard is gone. This phase restores it.

**Trigger:** three or more seated advisors land on the same path, or the positions differ only in detail, not direction. If the board is genuinely split, skip it — the tension is already there.

**The challenger is not a lens and not a standing seat.** It is a red-team, convened only on convergence. It is the one agent handed the board's positions on purpose, because its job is to attack them: steelman the strongest rejected option, name the load-bearing shared assumption and show what breaks if it is false, and surface the blind spot no lens owned. It does not decide. It hands the CEO a sharper set of odds.

This is why the conditional design matters: a *fixed* Challenge stage in every run was the dependent-chain council we rejected (Context → Options → Challenge → Decision). Firing it only when the board agrees keeps the fan-out architecture and the minimum-agents discipline while closing the one gap distributed self-critique cannot.

---

## Phase 4 — Synthesis (the CEO)

**Actor:** Orchestrator / human (top-tier model). Not a peer agent.

1. **Multiple Advocacy** — lay the competing positions out fairly. Identify where advisors agree and where they conflict. Name the real tension.
2. **Weigh the challenge (if convened)** — read the challenger's memo. A consensus that survives an honest steelman is genuine corroboration; one that folds when its shared assumption is attacked was manufactured. If the challenge lands, change the call or attach the conditions it exposed.
3. **Resolve, don't list** — make the call. Mushy "consider exploring" language is a failure. Say what to do, why, what tradeoff is being accepted, and what risk remains.
3. **Decision Quality check** — verify the recommendation satisfies the six elements (frame, alternatives, information, values, reasoning, commitment).
4. **RAPID / DACI** — assign owner, accountable executor, who's informed, and the next action with a deadline.

---

## Phase 5 — Decision log + quality check

**Actor:** Orchestrator, direct.

Before returning, verify:

**Decision Quality**
- [ ] The decision is clearly framed and bounded
- [ ] At least two real alternatives were weighed
- [ ] Facts are separated from assumptions
- [ ] Criteria and tradeoffs are explicit
- [ ] The reasoning from criteria to recommendation is visible
- [ ] Owner, next action, and deadline are set

**Agentic discipline**
- [ ] The gate passed before any agent was convened
- [ ] Each seated advisor had a genuinely conflicting lens
- [ ] Advisors worked in isolation (no cross-contamination)
- [ ] The synthesis resolved tensions rather than listing them
- [ ] The output supports the human as decision-maker

Write the decision log: what was decided, why, who owns it, and what should trigger a revisit.

---

## Research rules (what & when)

This is scoped research, not Deep Research. Default to a targeted scan.

**Internal first.** Each advisor reads the internal files named in the brief (metrics, financials, contracts, roadmap) before reaching outward.

**External, light.** Reach to the web only when the advisor's lens depends on outside facts — market/competitor signal (CMO), benchmarks (CFO), regulatory/precedent (GC). Budget: a targeted scan, not a literature review.

**Escalate to Deep Research only when:** the decision is high-stakes, the domain is unfamiliar, the information landscape is broad, and the cost of being wrong is high. In that case the relevant advisor calls the Deep Research skill for its angle — the council stays the orchestrator.

---

## Output template — Decision Council Brief

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

## Teaching framing

- **The foil:** show the dependent-chain council first (Context → Options → Decision) — it's a skill. Then the board — it's agents. Same decision problem; the gate sorts them. That single contrast teaches fan-out vs. chain.
- **Provenance = credibility:** George, Page, Heuer, Vroom-Yetton — management science and intelligence tradecraft, not invented. The grounding is real, not hand-waved.
- **Doubles as the GP-vs-custom demo:** the advisors are custom agents (durable personas, reused every decision); the gate's ad-hoc lookups can use the built-in general-purpose agent.

### Where it sits in the skill ladder
1. Level 1 — checklist/template skill
2. Level 2 — a multi-step content pipeline (sophisticated skill, no agents)
3. Level 3 — Decision Council (skill that convenes agents only when the decision earns it)
4. Level 3+ — Deep Research (heavyweight multi-agent fan-out)

---

## Sources

- Multiple Advocacy — George, *The Case for Multiple Advocacy in Making Foreign Policy*, APSR 1972
- Diversity Prediction Theorem — Page, *The Difference*, 2007
- Structured Analytic Techniques — Heuer & Pherson, 2010
- Vroom-Yetton-Jago decision model — Vroom & Yetton, 1973
- Cynefin — Snowden, cynefin.io
- Decision Quality — Spetzler, Winter & Meyer; Stanford Strategic Decisions Group
- RAPID — Bain & Company; DACI — Atlassian
- Premortem — Klein, *Performing a Project Premortem*, HBR 2007
- Dialectical Inquiry & Devil's Advocacy — Mason & Mitroff, *Challenging Strategic Planning Assumptions*, 1981; Schwenk, *Effects of Devil's Advocacy and Dialectical Inquiry on Decision Making*, 1990
