---
name: deep-research
description: Multi-agent deep research producing verified, actionable insights with source evaluation and confidence scoring. Use when asked to "research deeply", "investigate", "do comprehensive research", or when a topic needs multi-angle analysis with verified data.
---

# Deep Research Skill

Multi-agent research workflow producing verified, actionable insight.

**Core principle:** Accuracy over volume. Every claim needs a source. Judgment over procedures.

---

## Agents

This workflow uses four specialized agents, provided by the `riftlab-os` plugin. Spawn each one by its plugin-scoped name: `riftlab-os:oracle`, `riftlab-os:hermes`, `riftlab-os:athena`, `riftlab-os:scribe`.

**Framework files (orchestrator: resolve before Phase 1).** The source-quality and process rules live in this skill's own `framework/` directory, next to this `SKILL.md`. Determine the absolute path to that directory on this machine, and use it wherever `[FRAMEWORK_DIR]` appears below. The agents run in their own context, so you must pass the resolved absolute path into each invocation; a bare relative path will not resolve from inside an agent.

| Agent      | Role                                                                    | Model  | Tools                  |
| ---------- | ----------------------------------------------------------------------- | ------ | ---------------------- |
| **Oracle** | Decomposes topic into angles, sets quality criteria                     | Sonnet | Read, Write            |
| **Hermes** | Executes queries, collects raw data with full metadata                  | Sonnet | Read, WebSearch, Write |
| **Athena** | Evaluates (CRAAP, confidence) AND analyzes (patterns, tensions, themes) | Sonnet | Read, Write            |
| **Scribe** | Transforms analysis into narrative synthesis                            | Opus   | Read, Write            |

---

## Standard Agent Context

**Every agent invocation must include this context block.** This ensures all agents have consistent temporal awareness and research context.

### Context Block Template

```
RESEARCH CONTEXT:
- Current date: [YYYY-MM-DD]
- Topic: [topic-slug]
- Research folder: Research/[topic]/
- Decision: [One-line summary from context.md]

TEMPORAL GUIDANCE:
- "Recent" means: [current-year - 1] to [current-year] (e.g., 2025-2026)
- Prefer data from: [current-year - 1] and [current-year]
- Flag as potentially outdated: Pre-[current-year - 2] data
- Include year in search queries to improve relevance

TOPIC TYPE: [Inferred type - see below]
EXPECTED DATA AVAILABILITY: [Based on topic type]
```

### Topic Type Inference

During context gathering, infer the topic type to set realistic expectations:

| Topic Type | Examples | Tier 1-3 Likely? | Primary Sources | Set Expectation |
|------------|----------|------------------|-----------------|-----------------|
| **Public company data** | Revenue, financials, headcount | YES | SEC filings, earnings, annual reports | High confidence achievable |
| **Major tech markets** | Cloud, AI, cybersecurity | YES | Gartner, Forrester, IDC reports | High confidence achievable |
| **Niche software markets** | Live polling, specific SaaS verticals | RARELY | Aggregators, trade publications | Expect Tier 5-6, report ranges |
| **Competitive intelligence** | Pricing, features, positioning | YES | Official websites, product pages | High confidence from primary sources |
| **User behavior/needs** | Pain points, preferences, adoption | SOMETIMES | Academic research, surveys, reviews | Mix of tiers, triangulate |
| **GTM/marketing tactics** | Channels, CAC, conversion rates | RARELY | Practitioner blogs, case studies | Expect Tier 5-6, look for patterns |
| **Technical architecture** | How things work, implementations | SOMETIMES | Documentation, papers, posts | Varies by topic maturity |

### Setting Expectations

After identifying topic type, inform the user:

**For niche/tactical topics:**
> "For [topic type], Tier 1-3 research firm data is typically not publicly available. This research will synthesize available sources with appropriate confidence caveats. [Specific area] will likely have higher confidence (official sources available). Is this acceptable?"

**For well-covered topics:**
> "For [topic type], analyst reports and primary sources are likely available. We should be able to achieve high confidence on key claims."

This sets realistic expectations WITHOUT asking "what confidence do you need?" - everyone wants comprehensive research, but they should know what's achievable.

---

## Orchestration Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  PHASE 0        PHASE 1         PHASE 2         PHASE 3         PHASE 4    │
│  Context    →   Planning    →   Research    →   Analysis    →   Synthesis  │
│  (Direct)       (Oracle)        (Hermes ×N)     (Athena)        (Scribe)   │
│                                                                             │
│                                                 PHASE 5                     │
│                                             →   Review                      │
│                                                 (Direct)                    │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Note**: Athena now handles both evaluation (CRAAP, confidence, pitfalls) AND analysis (cross-reference, patterns, tensions, themes). This eliminates handoff fidelity loss between separate evaluation and analysis agents.

---

## Folder Structure

All research outputs are saved to `Research/[topic]/`:

```
Research/[topic]/
├── context.md                      # Phase 0: User context
├── _plan.md                        # Phase 1: Oracle output
├── _raw/                           # Phase 2: Hermes outputs
│   ├── 01-[angle-slug].md
│   ├── 02-[angle-slug].md
│   └── ...
├── _analysis.md                    # Phase 3: Athena output (evaluation + analysis)
└── [YYYY-MM-DD]-[topic]-synthesis.md  # Phase 4: Scribe output
```

---

## Phase 0: Context Gathering

**Actor:** You (orchestrator, direct conversation)

**Purpose:** Understand what we're researching FOR before any external research.

**Why this matters:** If context is wrong or incomplete, every agent downstream operates on flawed premises. Garbage in, garbage out. This phase requires the same rigor as the research itself.

---

### The Five Dimensions of Context

#### Dimension 1: DECISION

**Why it matters:** Research without a clear decision is just information gathering. The decision shapes what's relevant, what depth is needed, and what recommendations are useful.

**Questions to ask:**

| Question | Why It Matters |
|----------|----------------|
| What specific decision will be made based on this research? | Focuses the research on actionable outcomes |
| Who is the decision maker? | Affects framing, depth, and format |
| What options are being considered? | Helps structure comparative analysis |
| What's the timeline for the decision? | Determines acceptable research depth |
| What's at stake? (Investment, reversibility, risk) | Sets the confidence bar |

**Red flags to probe:**
- "I just want to learn about X" → Push for the underlying decision
- "We're exploring options" → What would make you choose one over another?
- Vague timeline → When does this need to be decided? What's driving that?

**Example good vs weak:**
| Weak | Strong |
|------|--------|
| "Research the polling market" | "Decide whether to enter the enterprise polling market in Q2" |
| "Learn about competitors" | "Choose which 2 competitors to position against for launch" |

---

#### Dimension 2: CURRENT STATE

**Why it matters:** Recommendations must fit reality. Without knowing what exists, agents will suggest things that are impossible, redundant, or misaligned.

**Questions to ask:**

| Question | Why It Matters |
|----------|----------------|
| What exists today? (Product, service, offering) | Baseline for what's possible |
| Who is your current audience? How many? | Calibrates market size relevance |
| What resources are available? (Budget, team, skills) | Constrains recommendations |
| What technical/operational capabilities exist? | Determines feasibility |
| What's been tried before? What worked/failed? | Avoids repeating past mistakes |

**Red flags to probe:**
- "We're pre-launch" → What's built? What's your runway?
- "Small team" → How small? What skills?
- "Limited budget" → What's the actual range?

**Example good vs weak:**
| Weak | Strong |
|------|--------|
| "We're a startup" | "Pre-revenue, 2 founders, $50K runway, MVP with 100 beta users" |
| "We have some traction" | "500 WAU, 10% week-over-week growth, $0 revenue, enterprise waitlist of 12" |

---

#### Dimension 3: KNOWLEDGE GAP

**Why it matters:** Don't research what you already know. Focus agents on actual unknowns. Surface assumptions that might be wrong.

**Questions to ask:**

| Question | Why It Matters |
|----------|----------------|
| What do you already know about this topic? | Avoids redundant research |
| What do you *think* you know but aren't certain? | Identifies assumptions to validate |
| What would change your mind about the decision? | Focuses on pivotal unknowns |
| What's the cost of being wrong? | Determines required confidence |
| What have you already researched? | Avoids duplication |

**Red flags to probe:**
- "I don't know anything" → You must have some hypotheses. What are they?
- Stated "facts" without sources → Where did that come from? Should we verify?
- Strong opinions presented as questions → Are you looking to validate or actually learn?

**Example good vs weak:**
| Weak | Strong |
|------|--------|
| "I need to understand the market" | "I think TAM is ~$500M but that's from a blog post. I assume enterprise buyers care about security but don't have data." |
| "Research competitors" | "I know two incumbents exist. I assume they're focused on large enterprises. I don't know their mid-market positioning or pricing." |

---

#### Dimension 4: CONSTRAINTS

**Why it matters:** Constraints bound the research. Ignoring them produces recommendations that can't be acted on.

**Questions to ask:**

| Question | Why It Matters |
|----------|----------------|
| When does this research need to be complete? | Determines depth possible |
| What's explicitly OUT of scope? | Prevents wasted effort |
| What can't we research? (Proprietary, inaccessible) | Sets realistic expectations |
| What depth is needed? (Overview / Standard / Deep) | Calibrates effort |
| Any sensitive topics to avoid? | Prevents problematic areas |

**Red flags to probe:**
- "As soon as possible" → What's the actual deadline?
- "Everything is relevant" → What would you cut if you had to?
- No constraints stated → There are always constraints. What are yours?

**Depth levels:**
| Level | Description | Data Points | Use When |
|-------|-------------|-------------|----------|
| Overview | Quick scan, key facts | 5-10 per angle | Exploratory, low stakes |
| Standard | Thorough coverage | 10-15 per angle | Most decisions |
| Deep | Comprehensive, verify everything | 20+ per angle | High stakes, strategic |

---

#### Dimension 5: SUCCESS CRITERIA

**Why it matters:** Without success criteria, you can't know when research is "done" or "good enough."

**Questions to ask:**

| Question | Why It Matters |
|----------|----------------|
| What confidence level is required? | Sets evidence standards |
| What would make this research "successful"? | Defines done |
| What format is most useful? | Shapes output |
| Who else will see this? | Affects framing |
| What questions MUST be answered? | Prioritizes effort |

**Confidence requirements:**
| Decision Type | Confidence Needed | Evidence Standard |
|---------------|-------------------|-------------------|
| Strategic (major investment, hard to reverse) | HIGH required | Tier 1-3 sources, multiple corroboration |
| Tactical (smaller bets, reversible) | MEDIUM acceptable | Tier 3-5 sources acceptable |
| Exploratory (learning, no immediate decision) | LOW acceptable | Tier 4-6 acceptable |

**Red flags to probe:**
- "Just give me everything" → What's most important? What can you live without?
- No clear success criteria → How will you know if the research helped?

---

### Context Gathering Process

**Step 1: Initial scan**
Listen to the user's initial request. Identify which dimensions are already clear vs. need probing.

**Step 2: Structured inquiry**
Work through each dimension. Don't ask all questions - focus on gaps and red flags.

**Step 3: Reflect back**
Summarize what you've learned. Let the user correct misunderstandings.

**Step 4: Identify assumptions**
Explicitly state assumptions that emerged. These become things to validate or test.

**Step 5: Confirm and document**
Write context.md and get user confirmation before proceeding.

---

### Handling Incomplete Context

| Situation | Action |
|-----------|--------|
| User doesn't know the answer | Note as "Unknown - to be determined" in context |
| User gives vague answer | Probe with "Can you be more specific about X?" |
| User resists questions | Explain why it matters: "This helps agents avoid [specific failure mode]" |
| Contradictions emerge | Surface them: "Earlier you said X, but now Y. Which is accurate?" |
| User wants to skip context | Explain the risk: "Without this, research may miss the mark. 5 more minutes now saves rework later." |

---

### Context Document Format

Write to `Research/[topic]/context.md`:

```markdown
# Research Context: [Topic]

**Date**: [YYYY-MM-DD]
**Research Goal**: [Specific, actionable goal]

---

## 1. Decision

**Decision to make**: [Specific decision]
**Decision maker**: [Who]
**Options being considered**: [List]
**Timeline**: [When decision needed]
**Stakes**: [What's at risk, reversibility]

---

## 2. Current State

**Product/Offering**: [What exists today]
**Audience**: [Who, how many]
**Resources**: [Budget range, team size, skills]
**Technical capabilities**: [What's possible]
**History**: [What's been tried, results]

---

## 3. Knowledge Gap

**Already known**:
- [Fact 1]
- [Fact 2]

**Assumptions to test**:
- [Assumption 1]: [Why it might be wrong]
- [Assumption 2]: [Why it might be wrong]

**Key unknowns**:
- [What we need to learn]
- [What would change the decision]

**Cost of being wrong**: [Impact]

---

## 4. Constraints

**Timeline**: [Deadline]
**Out of scope**: [What to exclude]
**Inaccessible**: [What we can't research]
**Depth level**: [Overview / Standard / Deep]
**Sensitivities**: [Topics to handle carefully]

---

## 5. Success Criteria

**Confidence required**: [HIGH / MEDIUM / LOW]
**Must-answer questions**:
1. [Critical question]
2. [Critical question]

**Format preference**: [Report / Data / Recommendations]
**Audience**: [Who will see this]

---

## Notes for Agents

[Specific instructions based on context that agents should know]

- [e.g., "Company is pre-revenue - ignore revenue benchmarks"]
- [e.g., "Focus on North American market only"]
- [e.g., "Founder has technical background - can handle technical depth"]
- [e.g., "Verify the $500M TAM assumption - may be wrong"]
```

---

### Gate

**User confirms context is accurate before proceeding.**

Present summary:
```
Here's what I understand:

**Decision**: [Summary]
**Current state**: [Summary]
**Key unknowns**: [Summary]
**Constraints**: [Summary]
**Success criteria**: [Summary]

Is this accurate? Anything to add or correct?
```

Only proceed when user confirms.

---

## Phase 1: Planning

**Actor:** Oracle agent

**Purpose:** Decompose topic into bounded, searchable angles with quality criteria.

### Invocation

```
Use the `riftlab-os:oracle` agent to create a research plan.

Inputs:
- Research goal: [GOAL from user]
- Context document: Research/[topic]/context.md
- Framework location: [FRAMEWORK_DIR]/

Output location: Research/[topic]/_plan.md
```

### What Oracle Does

1. Reads context document
2. Reads framework/evidence-standards.md for quality criteria
3. Decomposes topic into 3-5 distinct angles
4. Sets search strategy and quality criteria per angle
5. Writes research plan to `_plan.md`

### Gate
**Present plan summary to user. User approves angles before research begins.**

```
Oracle created a research plan with [N] angles:

1. [Angle Name]: [Brief scope]
2. [Angle Name]: [Brief scope]
3. [Angle Name]: [Brief scope]

Quality criteria: [Summary]

Approve this plan to begin research?
```

---

## Phase 2: Research

**Actor:** Hermes agent (one per angle, parallel)

**Purpose:** Execute queries and collect raw data for each angle.

### Invocation (Parallel)

For each angle in the research plan:

```
Use the `riftlab-os:hermes` agent to research angle [N]: [Angle Name].

RESEARCH CONTEXT:
- Current date: [YYYY-MM-DD]
- Topic: [topic-slug]
- Research folder: Research/[topic]/
- Decision: [One-line summary]

TEMPORAL GUIDANCE:
- "Recent" means: [year-1] to [year]
- Include year in queries (e.g., "market size 2024 2025")
- Flag pre-[year-2] data as potentially outdated

Inputs:
- Research plan: Research/[topic]/_plan.md
- Assigned angle: [Angle Name]
- Context: Research/[topic]/context.md
- Framework: [FRAMEWORK_DIR]/

Output location: Research/[topic]/_raw/[NN]-[angle-slug].md
```

**Spawn all Hermes agents in parallel** (one per angle). They are independent and can run concurrently.

### Hermes Search Principles

**Query the TOPIC, not the SOURCE:**

| Wrong (source-biased) | Right (topic-focused) |
|-----------------------|-----------------------|
| "Gartner live polling market" | "live polling software market size 2024 2025" |
| "Forrester audience engagement" | "audience engagement platform TAM analysis" |
| "IDC interactive presentation" | "interactive presentation market revenue growth" |

**Vary terminology for breadth:**
- Different terms for same concept (live polling, audience response, interactive presentation)
- Different data types (market size, revenue, growth rate, TAM, forecast)
- Include years to anchor recency (2024, 2025, forecast 2030)

**Tag sources AFTER finding them:**
- Record: URL, publisher, date, methodology (if stated)
- DO NOT pre-filter by source reputation
- Let Athena evaluate quality - Hermes finds information

**Broaden when needed:**
1. Direct query: "live polling market size 2024" → limited results?
2. Broaden terminology: "audience response software market" → more results?
3. Broaden category: "audience engagement platform market" → even more?

### What Hermes Does

1. Reads assigned angle from research plan
2. Reads framework/evidence-standards.md for tier definitions
3. Constructs topic-focused queries (not source-focused)
4. Varies terminology for maximum breadth
5. Includes year in queries for recency
6. Extracts data points with full metadata (source tagged, not filtered)
7. Flags potential pitfalls observed
8. Documents gaps (what couldn't be found)
9. Writes raw findings to `_raw/`

### Gate
**All Hermes agents complete before proceeding.**

---

## Phase 3: Analysis

**Actor:** Athena agent

**Purpose:** Evaluate data quality AND analyze patterns, tensions, themes.

Athena now handles both evaluation and analysis in a single pass, eliminating handoff fidelity loss.

### Invocation

```
Use the `riftlab-os:athena` agent to evaluate and analyze the research findings.

RESEARCH CONTEXT:
- Current date: [YYYY-MM-DD]
- Topic: [topic-slug]
- Research folder: Research/[topic]/
- Decision: [One-line summary]

Inputs:
- Raw findings: Research/[topic]/_raw/*.md (all Hermes outputs)
- Research plan: Research/[topic]/_plan.md (quality criteria)
- Context: Research/[topic]/context.md
- Framework: [FRAMEWORK_DIR]/

Output location: Research/[topic]/_analysis.md
```

### What Athena Does

**Phase 1 - Evaluation:**
1. Reads all raw findings from Hermes
2. Verifies verbatim claims are preserved
3. Checks scope consistency (geographic, temporal, definitional)
4. Applies CRAAP to each source
5. Assigns confidence levels with rationale
6. Detects pitfalls (echo chambers, vendor marketing, etc.)
7. Makes filtering decisions (include/caveat/exclude)
8. Builds Data Point Registry (single source of truth)

**Phase 2 - Analysis:**
9. Cross-references findings across all angles
10. Identifies convergent findings (corroboration)
11. Identifies divergent findings (tensions)
12. Extracts themes as insights (not categories)
13. Assesses contextual relevance to user's decision
14. Prepares summary for Scribe
15. Writes to `_analysis.md`

### Gate
**Athena completes before proceeding.**

---

## Phase 4: Synthesis

**Actor:** Scribe agent

**Purpose:** Transform analysis into narrative synthesis with grounded recommendations.

### Invocation

```
Use the `riftlab-os:scribe` agent to write the final synthesis.

RESEARCH CONTEXT:
- Current date: [YYYY-MM-DD]
- Topic: [topic-slug]
- Research folder: Research/[topic]/
- Decision: [One-line summary]

Inputs:
- Analysis: Research/[topic]/_analysis.md (includes Data Point Registry)
- Context: Research/[topic]/context.md
- Framework: [FRAMEWORK_DIR]/

Output location: Research/[topic]/[YYYY-MM-DD]-[topic]-synthesis.md
```

### What Scribe Does

1. Reads Athena's analysis (includes evaluation + patterns + themes)
2. Reads context to ground recommendations in user's situation
3. Reads framework/output-standards.md for structure
4. Crafts narrative from themes
5. Preserves verbatim claims and sources (trace to DP Registry)
6. Grounds recommendations in evidence AND context
7. Flags gaps and tensions explicitly
8. Writes synthesis to dated file

### Gate
**Scribe completes. Synthesis ready for review.**

---

## Phase 5: Review

**Actor:** You (orchestrator, direct conversation)

**Purpose:** Present synthesis to user, handle iteration.

### Actions

1. Present executive summary to user
2. Highlight key findings, recommendations, limitations
3. Ask if user has questions or wants changes

### Handling Feedback

| Feedback Type | Action |
|---------------|--------|
| Small fixes (wording, details) | Edit synthesis file directly |
| Structural changes | Edit synthesis file directly |
| Missing analysis | Re-invoke Athena with specific direction |
| Major rework (rare) | Re-invoke appropriate agent |

**Do NOT re-invoke Scribe for small edits.** Edit the file directly.

---

## Quick Reference: Agent Invocations

**Always include the context block in every agent invocation.**

```
# Standard context block (include in ALL agent calls)
RESEARCH CONTEXT:
- Current date: 2026-01-28
- Topic: saas-gtm
- Research folder: Research/saas-gtm/
- Decision: GTM strategy for a B2C SaaS app launch

TEMPORAL GUIDANCE:
- "Recent" means: 2025-2026
- Include year in queries
- Flag pre-2023 data as potentially outdated

# Phase 1: Planning
Use the `riftlab-os:oracle` agent to create a research plan.
[Include context block above]
Context document: Research/[topic]/context.md

# Phase 2: Research (parallel - one per angle)
Use the `riftlab-os:hermes` agent to research angle 1: [Angle Name]
[Include context block above]
Research plan: Research/[topic]/_plan.md

Use the `riftlab-os:hermes` agent to research angle 2: [Angle Name]
[Include context block above]
Research plan: Research/[topic]/_plan.md

[Run all Hermes agents in parallel]

# Phase 3: Analysis (evaluation + patterns + themes)
Use the `riftlab-os:athena` agent to evaluate and analyze findings.
[Include context block above]
Raw findings: Research/[topic]/_raw/
Context: Research/[topic]/context.md

# Phase 4: Synthesis
Use the `riftlab-os:scribe` agent to write synthesis.
[Include context block above]
Analysis: Research/[topic]/_analysis.md
```

---

## Framework Reference

Agents read from `[FRAMEWORK_DIR]/`:

| Document | Used By | Purpose |
|----------|---------|---------|
| `evidence-standards.md` | Oracle, Hermes, Athena | Source tiers, confidence, pitfalls |
| `process.md` | All agents | Phase definitions, handoff contracts |
| `quality-standards.md` | Athena | Accuracy, objectivity, verifiability |
| `output-standards.md` | Scribe | Structure, language, recommendations |

**Note**: Athena now reads both `evidence-standards.md` AND `quality-standards.md` since it handles both evaluation and analysis.

---

## User Approval Gates

| After Phase | Approval Needed |
|-------------|-----------------|
| Phase 0 (Context) | "Is this context accurate?" |
| Phase 1 (Planning) | "Approve these angles to begin research?" |
| Phase 4 (Synthesis) | "Review complete. Questions or changes?" |

---

## Error Handling

| Issue | Action |
|-------|--------|
| Agent fails to complete | Check agent output, re-invoke with clarification |
| Hermes finds no data for angle | Document gap, proceed with other angles |
| Athena flags all data as UNVERIFIED | Surface to user, consider expanding search |
| Tensions unresolved | Surface in synthesis, let user decide |

---

## Invocation Examples

**Explicit:**
```
/deep-research SaaS product GTM strategy
/deep-research "competitive landscape for enterprise collaboration tools"
```

**Natural language:**
```
"Research the market for interactive presentations deeply"
"I need comprehensive research on PLG tactics before we decide"
"Investigate authentication patterns from multiple angles"
```

---

## Cost Model

| Phase | Agent | Model | Estimated Cost |
|-------|-------|-------|----------------|
| 0 | - | - | Free (conversation) |
| 1 | Oracle | Sonnet | Low |
| 2 | Hermes ×3-5 | Sonnet | Low-Medium |
| 3 | Athena | Sonnet | Low-Medium (now does evaluation + analysis) |
| 4 | Scribe | Opus | Medium |
| **Total** | | | **~$2-6** |

No Perplexity costs. All research via WebSearch. Reduced from 5 agents to 4 by merging evaluation and analysis into Athena.
