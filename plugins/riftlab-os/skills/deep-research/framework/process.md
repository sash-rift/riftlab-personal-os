# Research Process

This document defines the systematic process for conducting research. It is grounded in established research methodology from information science, systematic review practices, and professional research standards.

---

## Theoretical Foundation

This framework draws from established research methodologies:

1. **Systematic Review Methodology** (Cochrane Collaboration, PRISMA)
   - Structured search protocols
   - Explicit inclusion/exclusion criteria
   - Reproducible methodology
   - Bias assessment

2. **Information Literacy Standards** (ACRL Framework)
   - Authority is constructed and contextual
   - Information creation as a process
   - Information has value
   - Research as inquiry
   - Scholarship as conversation

3. **CRAAP Test** (California State University, Chico)
   - Currency: Timeliness of information
   - Relevance: Importance to your needs
   - Authority: Source of information
   - Accuracy: Reliability and correctness
   - Purpose: Reason information exists

4. **Triangulation** (Denzin, 1978)
   - Data triangulation: Multiple data sources
   - Investigator triangulation: Multiple researchers
   - Methodological triangulation: Multiple methods
   - Theory triangulation: Multiple theoretical perspectives

5. **Grounded Theory** (Glaser & Strauss)
   - Theory emerges from data
   - Systematic data collection
   - Constant comparative analysis
   - Theoretical sampling

---

## Research Phases

The research process consists of seven phases, each with defined inputs, activities, outputs, and quality gates.

```
┌─────────────────────────────────────────────────────────────────────┐
│  PHASE 1        PHASE 2         PHASE 3         PHASE 4            │
│  Context    →   Planning    →   Collection  →   Evaluation         │
│  Gathering      & Scoping       & Search        & Filtering        │
└─────────────────────────────────────────────────────────────────────┘
                                        │
┌─────────────────────────────────────────────────────────────────────┐
│  PHASE 5        PHASE 6         PHASE 7                            │
│  Analysis   →   Synthesis   →   Validation                         │
│  & Patterns     & Narrative     & Review                           │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Phase 1: Context Gathering

### Purpose

Establish the research foundation by understanding what we are researching FOR. Research without context produces generic findings that cannot be actioned.

### Theoretical Basis

From grounded theory: research questions emerge from context. From ACRL: "Information has value" - value is determined by the context in which it will be used.

### Activities

1. **Identify the Decision**
   - What decision will this research inform?
   - Who will use this research?
   - What actions might result from the findings?

2. **Establish Current State**
   - What already exists? (product, organization, constraints)
   - What resources are available? (budget, time, expertise)
   - What has been tried before?

3. **Surface Assumptions**
   - What assumptions should we test, not accept?
   - What biases might we bring to the research?
   - What do we think we know that might be wrong?

4. **Define Success Criteria**
   - What would "good enough" research look like?
   - What confidence level is required for decision-making?
   - What gaps are acceptable?

### Inputs

- User's research request
- Access to internal knowledge (documents, history, constraints)

### Outputs

**Context Document** containing:
```markdown
## Research Context

### Decision to Inform
[What decision will this research support?]

### Current State
- Product/Organization: [What exists today]
- Constraints: [Time, budget, resources, technical limitations]
- Prior attempts: [What's been tried, what worked/failed]

### Assumptions to Test
- [Assumption 1]: [Why we might be wrong]
- [Assumption 2]: [Why we might be wrong]

### Success Criteria
- Required confidence level: [HIGH/MEDIUM acceptable]
- Acceptable gaps: [What we can live without]
- Timeline: [When research is needed]

### Stakeholder Context
- Primary user: [Who will act on this]
- Their expertise level: [Novice/Intermediate/Expert]
- Preferred format: [Detailed report / Executive summary / Data tables]
```

### Quality Gate

- [ ] Decision to be informed is clearly articulated
- [ ] Current state is documented (not assumed)
- [ ] Assumptions are surfaced explicitly
- [ ] User confirms context is accurate

**Gate:** Research does not proceed until context is confirmed.

---

## Phase 2: Planning & Scoping

### Purpose

Decompose the research question into searchable, bounded components. Define explicit quality criteria for each component based on context.

### Theoretical Basis

From systematic review methodology: pre-defined search protocol with explicit inclusion/exclusion criteria. From information science: search strategy formulation.

### Activities

1. **Decompose Research Question**
   - Break into 3-5 distinct angles
   - Each angle should be independently searchable
   - Angles should collectively answer the research question
   - Minimize overlap between angles

2. **Formulate Search Strategy**
   - Define key terms, synonyms, and related concepts
   - Identify databases/sources to search
   - Plan query variations

3. **Set Quality Criteria per Angle**
   - Minimum source tier for core claims
   - Acceptable source tier for supporting information
   - Domain-specific requirements (from evidence-standards.md)
   - Pitfalls to specifically watch for

4. **Define Inclusion/Exclusion Criteria**
   - What sources will be included?
   - What sources will be excluded and why?
   - Date boundaries
   - Geographic boundaries (if applicable)
   - Language boundaries (if applicable)

### Inputs

- Context Document (from Phase 1)
- Evidence Standards framework (for quality criteria)

### Outputs

**Research Plan** containing:
```markdown
## Research Plan

### Research Question
[The overarching question to answer]

### Angles

#### Angle 1: [Name]
**Scope**: [Specific boundaries of this angle]
**Key questions**:
1. [Specific question]
2. [Specific question]
3. [Specific question]

**Search strategy**:
- Key terms: [term1, term2, term3]
- Synonyms: [alt1, alt2]
- Source types to prioritize: [Research firms, official docs, etc.]
- Databases/platforms: [Where to search]

**Quality criteria**:
- Minimum tier for core claims: [Tier 1-3]
- Acceptable for supporting info: [Tier 4-5]
- Domain-specific rules: [From evidence-standards.md]
- Pitfalls to watch: [Echo chambers, vendor marketing, etc.]

**Inclusion criteria**:
- Date range: [e.g., 2022-present]
- Geography: [e.g., North America, Global]
- Source types: [e.g., Include research reports, exclude social media]

**Exclusion criteria**:
- [e.g., Exclude sources >3 years old]
- [e.g., Exclude vendor marketing without corroboration]

**Must-find data points**:
- [Specific data point needed]
- [Specific data point needed]

**Nice-to-have data points**:
- [Would strengthen but not required]

#### Angle 2: [Name]
[Same structure]

### Overall Parameters
- Total angles: [N]
- Target completion: [Timeline]
- Confidence threshold: [Minimum acceptable for recommendations]
```

### Quality Gate

- [ ] Each angle is distinct (minimal overlap)
- [ ] Each angle is bounded (not open-ended)
- [ ] Quality criteria are explicit for each angle
- [ ] Inclusion/exclusion criteria are defined
- [ ] Search strategy is actionable
- [ ] User approves plan before execution

**Gate:** Collection does not begin until plan is approved.

---

## Phase 3: Collection & Search

### Purpose

Execute the search strategy systematically, collecting raw data according to the defined protocol.

### Theoretical Basis

From systematic review: reproducible, documented search execution. From information retrieval: precision vs recall trade-offs, query refinement.

### Key Principles

1. **Search Systematically**
   - Execute planned queries before exploratory queries
   - Document every query and its results
   - Note what was NOT found, not just what was found

2. **Collect Raw Data**
   - Extract exact quotes and numbers
   - Capture source metadata (URL, date, author, publication)
   - Do not interpret during collection
   - Preserve context around data points

3. **Apply Quality Criteria in Real-Time**
   - Use the quality criteria from the Research Plan
   - Filter obvious noise during collection (Tier 7 spam)
   - Prioritize sources that meet minimum tier
   - Note when minimum tier cannot be met

4. **Document Search Process**
   - Reproducibility: another researcher could repeat the search
   - Transparency: decisions are documented

### Activities

1. **Execute Planned Queries**
   - Run each query from the search strategy
   - Capture first 10-20 relevant results per query
   - Note if a query returns poor results (refine or document failure)

2. **Extract Data Points**
   - For each relevant source:
     - URL, title, date, author, publication
     - Exact quote or data point
     - Page/section location
     - Initial tier assessment
   - Do NOT editorialize or interpret

3. **Identify Gaps**
   - What data points could not be found?
   - What quality level was achievable?
   - What additional queries might help?

4. **Refine Queries (if needed)**
   - Based on initial results, adjust search terms
   - Document rationale for refinement

### Inputs

- Research Plan (from Phase 2)
- Access to search tools (WebSearch)

### Outputs

**Raw Findings** per angle:
```markdown
## Raw Findings: [Angle Name]

### Search Execution Log

| Query | Date | Results | Notes |
|-------|------|---------|-------|
| [query 1] | [date] | [N results, M relevant] | [any issues] |
| [query 2] | [date] | [N results, M relevant] | [any issues] |

### Data Points Collected

#### DP-001
- **Claim**: [Exact claim or quote]
- **Value**: [The specific number or fact]
- **Source**: [Publication name]
- **Author**: [If available]
- **Date**: [Publication date]
- **URL**: [Link]
- **Location**: [Page, section, paragraph]
- **Initial tier**: [1-7, preliminary assessment]
- **Context**: [Surrounding context that affects interpretation]

#### DP-002
[Same structure]

### Data Not Found

| Sought | Why Not Found | Impact |
|--------|---------------|--------|
| [Data point sought] | [No sources, poor quality only, etc.] | [Critical / Important / Minor] |

### Search Refinements Made

| Original Query | Refined To | Rationale |
|----------------|------------|-----------|
| [original] | [refined] | [why] |
```

### Quality Gate

- [ ] All planned queries were executed (or documented why not)
- [ ] Data points include source metadata
- [ ] Initial tier assessments are made
- [ ] Gaps are documented explicitly
- [ ] Search log is reproducible

**Gate:** Proceed to Evaluation when collection is complete for all angles.

---

## Phase 4: Evaluation & Filtering

### Purpose

Apply rigorous evaluation to collected data. Assign confidence levels, detect pitfalls, and filter unreliable information.

### Theoretical Basis

From CRAAP test: systematic evaluation criteria. From systematic review: risk of bias assessment. From information literacy: critical evaluation of sources.

### Key Principles

1. **Evaluate Against Criteria**
   - Apply the quality criteria defined in the Research Plan
   - Use evidence-standards.md as the reference
   - Be consistent across all data points

2. **Assign Confidence Levels**
   - HIGH, MEDIUM, LOW, or UNVERIFIED
   - Based on source tier, methodology, corroboration
   - Confidence can only decrease when combined

3. **Detect Pitfalls**
   - Echo chambers
   - Vendor marketing
   - Precision without methodology
   - Outdated data
   - Sample bias
   - Survivorship bias

4. **Document Reasoning**
   - Why was confidence assigned this level?
   - What pitfalls were detected?
   - What could increase confidence?

### Activities

1. **Source Evaluation**
   - For each source, apply CRAAP:
     - Currency: When was it published? Is it current?
     - Relevance: Does it address the research question?
     - Authority: Who created it? What are their credentials?
     - Accuracy: Is it supported by evidence? Can it be verified?
     - Purpose: Why does this information exist? What bias might it have?

2. **Tier Classification**
   - Confirm or adjust initial tier assessment
   - Use evidence-standards.md definitions
   - Document rationale for tier assignment

3. **Pitfall Detection**
   - Check for each pitfall in the catalog
   - Flag detected pitfalls
   - Note impact on confidence

4. **Confidence Assignment**
   - Assign confidence level per data point
   - Document the criteria that determined the level
   - Flag UNVERIFIED claims explicitly

5. **Filtering Decisions**
   - Mark data points as: INCLUDE / INCLUDE WITH CAVEAT / EXCLUDE
   - Document rationale for exclusions

### Inputs

- Raw Findings (from Phase 3)
- Evidence Standards framework
- Research Plan quality criteria

### Outputs

**Evaluated Findings** per angle:
```markdown
## Evaluated Findings: [Angle Name]

### Source Assessment

| Source | CRAAP Score | Tier | Include? | Rationale |
|--------|-------------|------|----------|-----------|
| [Source 1] | C:Y R:Y A:Y A:N P:Y | 4 | Yes | Authority unclear but methodology present |
| [Source 2] | C:N R:Y A:Y A:Y P:N | 6 | Caveat | Promotional but contains useful data |
| [Source 3] | C:Y R:Y A:N A:N P:N | 7 | No | SEO content, no original research |

### Evaluated Data Points

#### DP-001
- **Claim**: [Claim]
- **Source**: [Source]
- **Tier**: [Confirmed tier]
- **CRAAP**: Currency: [Y/N], Relevance: [Y/N], Authority: [Y/N], Accuracy: [Y/N], Purpose: [Y/N]
- **Confidence**: [HIGH/MEDIUM/LOW/UNVERIFIED]
- **Confidence rationale**: [Why this level]
- **Pitfalls detected**: [None / List]
- **Status**: [INCLUDE / INCLUDE WITH CAVEAT / EXCLUDE]

### Pitfalls Detected

#### Echo Chamber Instances
- **Claim**: [The repeated claim]
- **Sources involved**: [List of sources]
- **Primary source found**: [Yes/No]
- **Action**: [Flagged as UNVERIFIED]

#### Vendor Marketing Instances
- **Claim**: [The claim]
- **Source**: [The vendor]
- **Conflict of interest**: [Description]
- **Action**: [Tagged as VENDOR CLAIM]

#### Other Pitfalls
[Similar structure for each detected pitfall]

### Filtering Summary

| Category | Count |
|----------|-------|
| Total data points collected | [N] |
| INCLUDE (full confidence) | [N] |
| INCLUDE WITH CAVEAT | [N] |
| EXCLUDE | [N] |

### Confidence Distribution

| Confidence | Count | Percentage |
|------------|-------|------------|
| HIGH | [N] | [%] |
| MEDIUM | [N] | [%] |
| LOW | [N] | [%] |
| UNVERIFIED | [N] | [%] |

### Quality Criteria Compliance

| Criterion | Met? | Notes |
|-----------|------|-------|
| Minimum tier for core claims | [Y/N] | [Details] |
| Required data points found | [Y/N] | [What's missing] |
| Pitfall detection complete | [Y/N] | [Details] |
```

### Quality Gate

- [ ] All data points have confirmed tier assignments
- [ ] All data points have confidence levels
- [ ] CRAAP evaluation completed for key sources
- [ ] Pitfalls detected and documented
- [ ] Filtering decisions are documented with rationale
- [ ] Quality criteria compliance is assessed

**Gate:** Proceed to Analysis when evaluation is complete.

---

## Phase 5: Analysis & Pattern Identification

### Purpose

Cross-reference findings, identify patterns, surface tensions, and synthesize meaning from evaluated data.

### Theoretical Basis

From grounded theory: constant comparative analysis. From triangulation: convergence and divergence of data sources. From meta-analysis: systematic combination of findings.

### Key Principles

1. **Cross-Reference Across Angles**
   - Same finding from multiple angles → increased confidence
   - Conflicting findings → tension to surface
   - Single-source findings → note limitation

2. **Identify Patterns**
   - Themes that emerge across multiple data points
   - Trends supported by evidence
   - Gaps that consistently appear

3. **Surface Tensions**
   - Where data conflicts
   - Where sources disagree
   - Where evidence is ambiguous

4. **Connect to Context**
   - How do findings relate to the decision context?
   - Which findings are most relevant to the user's situation?
   - What context is missing that would change interpretation?

### Activities

1. **Build Cross-Reference Matrix**
   - Map findings across angles
   - Identify convergence (multiple sources agree)
   - Identify divergence (sources conflict)

2. **Theme Identification**
   - What patterns emerge from the data?
   - What do multiple data points together suggest?
   - Name and define each theme with supporting evidence

3. **Tension Mapping**
   - Where do findings conflict?
   - What might explain the conflict?
   - How should the conflict be resolved (or flagged)?

4. **Gap Analysis**
   - What questions remain unanswered?
   - What data would strengthen conclusions?
   - What limitations affect the analysis?

5. **Contextual Mapping**
   - Which findings apply to the user's context?
   - Which require context we don't have?
   - Which findings need caveats based on context?

### Inputs

- Evaluated Findings (from Phase 4)
- Context Document (from Phase 1)

### Outputs

**Analysis Document**:
```markdown
## Analysis: [Research Topic]

### Cross-Reference Matrix

| Finding | Angle 1 | Angle 2 | Angle 3 | Angle 4 | Confidence |
|---------|---------|---------|---------|---------|------------|
| [Finding A] | HIGH | MEDIUM | - | HIGH | **STRONG** (convergent) |
| [Finding B] | HIGH | CONFLICT | - | - | **TENSION** |
| [Finding C] | MEDIUM | - | - | - | **WEAK** (single source) |

### Themes

#### Theme 1: [Theme Name]

**Definition**: [What this theme captures]

**Supporting Evidence**:
- DP-001: [Claim] (Angle 1, HIGH)
- DP-015: [Claim] (Angle 2, MEDIUM)
- DP-023: [Claim] (Angle 3, HIGH)

**Confidence**: [HIGH/MEDIUM/LOW based on convergence]

**Interpretation**: [What this theme means for the research question]

#### Theme 2: [Theme Name]
[Same structure]

### Tensions

#### Tension 1: [Name]

**Conflict**: [Description of conflicting findings]

**Source A says**: [Position with evidence]
**Source B says**: [Position with evidence]

**Possible explanations**:
1. [Different definitions being used]
2. [Different time periods]
3. [Different methodologies]

**Resolution**: [How to handle in synthesis - pick one with rationale, report both, flag for user]

### Gaps

| Gap | Impact | What Would Fill It |
|-----|--------|-------------------|
| [Missing data] | [HIGH/MEDIUM/LOW] | [What research would answer this] |

### Contextual Relevance

| Finding | Applicable to User Context? | Notes |
|---------|----------------------------|-------|
| [Finding] | Yes / Partially / Unknown | [Why, what context needed] |

### Findings Requiring Additional Context

| Finding | Context Needed | Why |
|---------|----------------|-----|
| [Finding] | [What's missing] | [How it affects interpretation] |
```

### Quality Gate

- [ ] Cross-reference matrix complete
- [ ] Themes identified with supporting evidence
- [ ] Tensions surfaced (not hidden)
- [ ] Gaps documented
- [ ] Contextual relevance assessed
- [ ] Confidence levels reflect convergence/divergence

**Gate:** Proceed to Synthesis when analysis is complete.

---

## Phase 6: Synthesis & Narrative

### Purpose

Transform analyzed findings into actionable insight. Build narrative, provide recommendations, communicate uncertainty appropriately.

### Theoretical Basis

From research communication: translation of findings for decision-makers. From information literacy: ethical use of information. From academic writing: argumentation with evidence.

### Key Principles

1. **Narrative Over Aggregation**
   - Tell the story the data reveals
   - Don't just list findings
   - Connect evidence to insight to implication

2. **Preserve Specifics**
   - Numbers, names, sources remain specific
   - No generalizing away quantitative detail
   - Citations accompany claims

3. **Communicate Uncertainty**
   - Confidence levels are stated
   - Limitations are acknowledged
   - UNVERIFIED claims are flagged

4. **Ground Recommendations**
   - Every recommendation ties to evidence
   - Context fit is assessed
   - Missing context is flagged

### Activities

1. **Structure the Narrative**
   - Executive summary (the essential insight)
   - Context (what we're researching for)
   - Findings organized by theme (not by source)
   - Tensions and trade-offs
   - Implications
   - Recommendations
   - Limitations

2. **Write with Evidence**
   - Claims are supported by citations
   - Numbers are preserved with sources
   - Confidence is stated for key claims

3. **Develop Recommendations**
   - Each recommendation grounded in evidence
   - Each recommendation checked against context
   - Missing context flagged explicitly

4. **Acknowledge Limitations**
   - What couldn't be verified
   - What gaps remain
   - What would strengthen the research

### Inputs

- Analysis Document (from Phase 5)
- Context Document (from Phase 1)
- Evaluated Findings (from Phase 4)

### Outputs

**Synthesis Report**: [See output-standards.md for full structure]

### Quality Gate

- [ ] Executive summary captures essential insight
- [ ] Findings are organized by theme, not aggregated by source
- [ ] Numbers are preserved with sources
- [ ] Confidence levels are stated
- [ ] Tensions are surfaced, not hidden
- [ ] Recommendations are grounded in evidence AND context
- [ ] Missing context is flagged
- [ ] Limitations are acknowledged

**Gate:** Proceed to Validation when synthesis is complete.

---

## Phase 7: Validation & Review

### Purpose

Verify synthesis accuracy, check for errors, and iterate based on feedback.

### Theoretical Basis

From peer review: external validation. From quality assurance: verification and validation. From user-centered design: iteration based on feedback.

### Key Principles

1. **Verify Accuracy**
   - Do claims in synthesis match source data?
   - Are numbers accurately represented?
   - Are citations correct?

2. **Check Completeness**
   - Are all key findings represented?
   - Are limitations adequately communicated?
   - Is the research question answered?

3. **Iterate Based on Feedback**
   - Small fixes: edit directly
   - Structural changes: edit directly
   - Major rework: re-run specific phase

### Activities

1. **Self-Verification**
   - Spot-check claims against sources
   - Verify numbers match
   - Check citation accuracy

2. **Completeness Check**
   - Compare synthesis to analysis themes
   - Ensure gaps and limitations are present
   - Verify recommendations are grounded

3. **User Review**
   - Present synthesis for feedback
   - Gather questions and concerns
   - Iterate as needed

### Inputs

- Synthesis Report (from Phase 6)
- All prior phase outputs (for verification)
- User feedback

### Outputs

- Final validated report
- Iteration log (what changed and why)

### Quality Gate

- [ ] Claims verified against sources
- [ ] Numbers spot-checked for accuracy
- [ ] Completeness check passed
- [ ] User feedback incorporated
- [ ] Final report approved

---

## Handoff Contracts

Each phase produces outputs that serve as inputs to subsequent phases. These contracts ensure consistent data flow.

### Contract: Context → Planning

```yaml
context_document:
  decision_to_inform: string
  current_state:
    product_or_org: string
    constraints: list[string]
    prior_attempts: list[string]
  assumptions_to_test: list[string]
  success_criteria:
    confidence_threshold: enum[HIGH_REQUIRED, MEDIUM_ACCEPTABLE]
    acceptable_gaps: list[string]
    timeline: string
  stakeholder_context:
    primary_user: string
    expertise_level: enum[NOVICE, INTERMEDIATE, EXPERT]
```

### Contract: Planning → Collection

```yaml
research_plan:
  research_question: string
  angles: list[angle]

angle:
  name: string
  scope: string
  key_questions: list[string]
  search_strategy:
    key_terms: list[string]
    synonyms: list[string]
    source_types: list[string]
    platforms: list[string]
  quality_criteria:
    minimum_tier: int  # 1-7
    acceptable_tier: int  # 1-7
    domain_rules: list[string]
    pitfalls_to_watch: list[string]
  inclusion_criteria: list[string]
  exclusion_criteria: list[string]
  must_find: list[string]
  nice_to_have: list[string]
```

### Contract: Collection → Evaluation

```yaml
raw_findings:
  angle_name: string
  search_log: list[search_execution]
  data_points: list[data_point]
  data_not_found: list[gap]

search_execution:
  query: string
  date: date
  results_count: int
  relevant_count: int
  notes: string

data_point:
  id: string
  claim: string
  value: string
  source: string
  author: string
  date: date
  url: string
  location: string
  initial_tier: int
  context: string

gap:
  sought: string
  why_not_found: string
  impact: enum[CRITICAL, IMPORTANT, MINOR]
```

### Contract: Evaluation → Analysis

```yaml
evaluated_findings:
  angle_name: string
  source_assessments: list[source_assessment]
  evaluated_data_points: list[evaluated_data_point]
  pitfalls_detected: list[pitfall_instance]
  confidence_distribution: dict[confidence_level, int]

source_assessment:
  source: string
  craap: craap_score
  tier: int
  include: enum[YES, CAVEAT, NO]
  rationale: string

craap_score:
  currency: bool
  relevance: bool
  authority: bool
  accuracy: bool
  purpose: bool

evaluated_data_point:
  id: string
  claim: string
  source: string
  tier: int
  craap: craap_score
  confidence: enum[HIGH, MEDIUM, LOW, UNVERIFIED]
  confidence_rationale: string
  pitfalls: list[string]
  status: enum[INCLUDE, CAVEAT, EXCLUDE]

pitfall_instance:
  type: string
  claim: string
  sources: list[string]
  action_taken: string
```

### Contract: Analysis → Synthesis

```yaml
analysis:
  cross_reference_matrix: list[cross_reference_row]
  themes: list[theme]
  tensions: list[tension]
  gaps: list[gap]
  contextual_relevance: list[relevance_assessment]

cross_reference_row:
  finding: string
  angle_results: dict[string, confidence_level]
  overall_confidence: enum[STRONG, MODERATE, WEAK, TENSION]

theme:
  name: string
  definition: string
  supporting_evidence: list[evidence_reference]
  confidence: confidence_level
  interpretation: string

evidence_reference:
  data_point_id: string
  claim: string
  angle: string
  confidence: confidence_level

tension:
  name: string
  conflict_description: string
  positions: list[position]
  possible_explanations: list[string]
  resolution: string

position:
  source: string
  claim: string
  evidence: string

gap:
  description: string
  impact: enum[HIGH, MEDIUM, LOW]
  what_would_fill: string

relevance_assessment:
  finding: string
  applicable: enum[YES, PARTIALLY, UNKNOWN]
  context_needed: string
```

---

## Decision Points

Research is not purely linear. These decision points may trigger iteration.

### Decision: Insufficient Quality

**Trigger:** Evaluation reveals most data points are Tier 5-7 or UNVERIFIED.

**Options:**
1. **Expand search** - Try additional queries, different platforms
2. **Lower threshold** - With explicit caveat in synthesis
3. **Flag gap** - Document that quality data doesn't exist
4. **Seek primary sources** - Targeted search for Tier 1-3 sources

**Decision criteria:** Importance of the data point to the research question.

### Decision: Echo Chamber Detected

**Trigger:** Multiple sources cite the same number with no primary source trail.

**Options:**
1. **Search for primary source** - Dedicated search for original research
2. **Flag as UNVERIFIED** - Do not use in recommendations
3. **Report range** - If multiple different numbers exist, report range

**Decision criteria:** Centrality of the claim to the research question.

### Decision: Conflict Between Sources

**Trigger:** Two credible sources give incompatible information.

**Options:**
1. **Investigate cause** - Different definitions? Different time periods?
2. **Report both** - With explanation of the tension
3. **Prefer higher tier** - If one source is clearly more authoritative
4. **Seek tiebreaker** - Find third source to resolve

**Decision criteria:** Can the conflict be explained? Is resolution possible?

### Decision: Context Insufficient

**Trigger:** Findings require context we don't have to interpret.

**Options:**
1. **Request context** - Ask user for missing information
2. **Flag in synthesis** - "This recommendation requires X context"
3. **Provide conditional recommendation** - "If X, then Y; if not X, then Z"

**Decision criteria:** Can we proceed without the context, or is it blocking?

### Decision: Scope Expansion Needed

**Trigger:** Initial angles don't cover an important dimension discovered during research.

**Options:**
1. **Add angle** - With user approval
2. **Note gap** - Document in synthesis as area for future research
3. **Partial coverage** - Cover what we can within current scope

**Decision criteria:** How critical is the missing dimension? Time/resource constraints?

---

## Quality Assurance

Cumulative quality checks at each phase ensure research integrity.

### Phase 1 (Context) QA

- Decision to inform is specific (not vague)
- Current state is documented (not assumed)
- Assumptions are explicit

### Phase 2 (Planning) QA

- Angles are distinct and bounded
- Quality criteria are specific
- Search strategy is actionable

### Phase 3 (Collection) QA

- Search log is reproducible
- Data points have metadata
- Gaps are documented

### Phase 4 (Evaluation) QA

- Tier assignments are justified
- Confidence levels are consistent
- Pitfalls are detected and flagged

### Phase 5 (Analysis) QA

- Cross-reference shows convergence/divergence
- Themes are supported by evidence
- Tensions are surfaced

### Phase 6 (Synthesis) QA

- Claims match source data
- Numbers are accurate
- Recommendations are grounded

### Phase 7 (Validation) QA

- Verification complete
- Feedback incorporated
- Final approval obtained

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2024-01-27 | Initial framework |

