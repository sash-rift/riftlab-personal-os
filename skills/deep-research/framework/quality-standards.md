# Quality Standards

This document defines what constitutes quality in research. It establishes standards for accuracy, completeness, objectivity, and verifiability that all agents must meet.

---

## Theoretical Foundation

Quality in research is not subjective. This framework draws from established quality criteria:

1. **Lincoln & Guba's Trustworthiness Criteria** (1985)
   - Credibility (internal validity)
   - Transferability (external validity)
   - Dependability (reliability)
   - Confirmability (objectivity)

2. **Research Quality Framework** (Spencer et al., 2003)
   - Contribution (advancing knowledge)
   - Defensibility (methodology)
   - Rigor (systematic approach)
   - Credibility (well-founded claims)

3. **Information Quality Dimensions** (Wang & Strong, 1996)
   - Accuracy
   - Completeness
   - Consistency
   - Timeliness

4. **GRADE Framework** (Guyatt et al., 2008)
   - Used in systematic reviews for evidence quality
   - Study design, risk of bias, inconsistency, indirectness, imprecision

---

## 1. Accuracy Standards

Accuracy means research findings correctly represent reality. Claims must be true to their sources and appropriately qualified.

### 1.1 Claim Accuracy

**Definition:** Every claim in research output must accurately represent what the source says.

**Requirements:**

| Requirement | Standard | Verification |
|-------------|----------|--------------|
| Faithful representation | Claims match source meaning | Spot-check against original |
| No overgeneralization | Scope matches source scope | Compare claim scope to source |
| No false precision | Numbers match source precision | Verify exact figures |
| Attribution | Claims attributed to sources | Citations present |

**Violations:**

| Violation | Example | Correct Approach |
|-----------|---------|------------------|
| Misrepresentation | Source says "may increase" → Report says "increases" | Preserve hedging |
| Overgeneralization | Source says "in North America" → Report says "globally" | Preserve scope |
| False precision | Source says "approximately 50%" → Report says "50.0%" | Match precision |
| Missing attribution | "Studies show..." without citation | Name the study |

### 1.2 Numerical Accuracy

**Definition:** Numbers must be reported exactly as they appear in sources, with appropriate context.

**Requirements:**

| Requirement | Standard |
|-------------|----------|
| Exact figures | Report numbers as stated in source |
| Units | Include units (millions, billions, %) |
| Base | Include base for percentages ("50% of N=500 respondents") |
| Time period | Include date/period for time-sensitive data |
| Definition | Note how the number is defined |

**Example of proper numerical reporting:**
```
Market size: $2.16B in 2024
- Source: Gartner Report, September 2024
- Definition: North American enterprise polling software
- Methodology: Survey of 500 enterprises, weighted by revenue
- Confidence: HIGH
```

**Example of improper numerical reporting:**
```
Market size: $2.16B (WRONG - missing context)
Market is over $2B (WRONG - loses precision)
Market is $2.16B globally (WRONG - overgeneralizes geography)
```

### 1.3 Temporal Accuracy

**Definition:** Time-sensitive information must include publication dates and note potential staleness.

**Requirements:**

| Data Type | Currency Requirement |
|-----------|---------------------|
| Market size | Data ≤2 years old, or flag as potentially outdated |
| Technology adoption | Data ≤2 years old, or flag |
| Company information | Data ≤1 year old, or verify still current |
| Academic research | Note publication year; may be relevant despite age |
| Historical facts | Date is context, not limitation |

**Staleness flags:**
- Data 2-3 years old: "Note: Data from [year]. Market conditions may have evolved."
- Data >3 years old: "Caution: Data from [year]. May not reflect current state."

---

## 2. Completeness Standards

Completeness means research adequately covers the research question without significant gaps.

### 2.1 Coverage Requirements

**Definition:** Research must address all aspects of the research question with sufficient depth.

**Requirements:**

| Aspect | Standard |
|--------|----------|
| Question coverage | All parts of research question addressed |
| Angle coverage | All approved angles researched |
| Data point minimum | 10-15 data points per angle (minimum) |
| Source diversity | Multiple sources per major claim |
| Perspective diversity | Multiple viewpoints represented where relevant |

**Coverage assessment:**

| Level | Definition |
|-------|------------|
| Complete | All angles covered, all key questions answered, multiple sources |
| Adequate | Most angles covered, key questions answered, some single-source claims |
| Partial | Some angles covered, gaps in key questions, limited sources |
| Insufficient | Major angles missing, key questions unanswered |

### 2.2 Gap Documentation

**Definition:** Gaps in research must be explicitly documented, not hidden.

**Requirements:**

Every gap must include:
1. **What was sought** - The specific data point or answer
2. **What was found** - What was available (if anything)
3. **Why the gap exists** - No data? Poor quality only? Outside scope?
4. **Impact assessment** - How does this gap affect conclusions?
5. **What would fill it** - Future research that would address the gap

**Gap impact levels:**

| Impact | Definition | Action Required |
|--------|------------|-----------------|
| Critical | Cannot answer research question without it | Flag prominently, consider expanding search |
| Significant | Weakens conclusions | Flag in synthesis, note limitation |
| Minor | Would strengthen but not required | Note in limitations section |

### 2.3 Negative Evidence

**Definition:** Research must document what was NOT found, not just what was found.

**Requirements:**

- Searched but not found is valuable information
- Document failed searches with query details
- Distinguish "doesn't exist" from "couldn't find"
- Include in synthesis: "No evidence was found for X despite searching Y"

---

## 3. Objectivity Standards

Objectivity means research presents evidence fairly without bias distorting conclusions.

### 3.1 Bias Recognition

**Definition:** Researchers must recognize and account for biases in sources and in their own approach.

**Source biases to identify:**

| Bias Type | Description | Detection |
|-----------|-------------|-----------|
| Commercial bias | Source profits from a particular conclusion | Check who funded/published |
| Confirmation bias | Source only presents supporting evidence | Look for counter-evidence |
| Selection bias | Non-representative sample | Check sample methodology |
| Survivorship bias | Only successes included | Ask about failures |
| Reporting bias | Favorable results more likely published | Look for unpublished data |
| Cultural bias | Assumes one cultural context | Check geography/demographics |

**Researcher biases to mitigate:**

| Bias Type | Description | Mitigation |
|-----------|-------------|------------|
| Confirmation bias | Seeking evidence for existing beliefs | Actively search for counter-evidence |
| Anchoring | Over-weighting first information found | Continue searching after first results |
| Authority bias | Over-trusting prestigious sources | Apply CRAAP regardless of prestige |
| Recency bias | Over-weighting recent information | Include historical context |

### 3.2 Balanced Representation

**Definition:** Research must fairly represent multiple perspectives where they exist.

**Requirements:**

| Requirement | Standard |
|-------------|----------|
| Multiple viewpoints | If debate exists, represent it |
| Proportional representation | Minority views noted but not over-weighted |
| Steel-manning | Present opposing views in their strongest form |
| Explicit disagreement | Note where sources conflict |

**Balanced representation does NOT mean:**
- False equivalence (treating fringe views as equal to consensus)
- Both-sides-ism (manufacturing debate where none exists)
- Withholding judgment (if evidence clearly supports one position)

### 3.3 Conflict of Interest Handling

**Definition:** Sources with conflicts of interest must be flagged and weighted appropriately.

**Conflict identification:**

| Conflict Type | Example | Handling |
|---------------|---------|----------|
| Financial | Vendor describing own market | Tag [VENDOR CLAIM], seek independent verification |
| Professional | Consultant promoting their methodology | Note conflict, seek corroboration |
| Ideological | Advocacy group on their issue | Note perspective, include opposing views |
| Competitive | Company describing competitors | Cross-reference with other sources |

**Handling conflicts:**

1. **Disclose** - Note the conflict in the citation
2. **Corroborate** - Seek independent verification
3. **Weight appropriately** - Don't treat as objective evidence
4. **Don't exclude automatically** - Conflicted sources may still have useful data

---

## 4. Verifiability Standards

Verifiability means research can be checked, reproduced, and traced to sources.

### 4.1 Source Documentation

**Definition:** Every claim must be traceable to its source.

**Minimum source information:**

| Element | Required | Purpose |
|---------|----------|---------|
| Publication/Source name | Yes | Identify the source |
| Author (if available) | Yes | Assess authority |
| Date | Yes | Assess currency |
| URL | Yes (if digital) | Enable verification |
| Page/Section | Recommended | Locate specific claim |
| Access date | Recommended (for web) | Document when accessed |

**Citation format:**
```
[Claim] ([Source Name], [Author if available], [Date], [URL])
```

**Example:**
```
Market size is projected to reach $5.6B by 2030
(Gartner Enterprise Polling Report, J. Smith, September 2024,
https://gartner.com/report/12345)
```

### 4.2 Methodology Transparency

**Definition:** Research methodology must be documented so it can be reproduced.

**Required documentation:**

| Element | What to Document |
|---------|------------------|
| Search queries | Exact queries used |
| Platforms searched | Where searches were executed |
| Date of searches | When research was conducted |
| Inclusion criteria | What was included and why |
| Exclusion criteria | What was excluded and why |
| Evaluation criteria | How sources were assessed |

**Reproduction standard:** Another researcher should be able to:
- Execute the same searches
- Apply the same evaluation criteria
- Reach similar (if not identical) conclusions

### 4.3 Audit Trail

**Definition:** Research must maintain a complete trail from raw data to final conclusions.

**Audit trail components:**

```
Raw Data (Phase 3)
    ↓
  [Search log, data points collected]
    ↓
Evaluated Data (Phase 4)
    ↓
  [Tier assignments, confidence levels, filtering decisions]
    ↓
Analysis (Phase 5)
    ↓
  [Cross-reference matrix, theme identification]
    ↓
Synthesis (Phase 6)
    ↓
  [Final report with citations]
```

**Traceability requirement:** Every claim in the final synthesis must trace back through the audit trail to a source.

---

## 5. Actionability Standards

Actionability means research produces findings that can inform decisions.

### 5.1 Relevance to Decision

**Definition:** Research must clearly connect to the decision it is meant to inform.

**Requirements:**

| Requirement | Standard |
|-------------|----------|
| Decision connection | Findings explicitly connect to the stated decision |
| Actionable specificity | Recommendations are specific enough to act on |
| Context fit | Recommendations account for user's context |
| Prioritization | Most important findings are highlighted |

### 5.2 Recommendation Quality

**Definition:** Recommendations must be grounded, specific, and appropriately confident.

**Recommendation requirements:**

| Element | Requirement |
|---------|-------------|
| Evidence link | What evidence supports this recommendation? |
| Confidence level | How confident are we? |
| Context fit | Does this fit the user's situation? |
| Specificity | Is this actionable (not vague)? |
| First step | What is the immediate next action? |
| Success metric | How will we know if it worked? |

**Recommendation quality levels:**

| Level | Criteria |
|-------|----------|
| Strong | HIGH confidence evidence, fits context, specific and actionable |
| Moderate | MEDIUM confidence or partial context fit |
| Tentative | LOW confidence or significant context gaps |
| Conditional | Depends on context we don't have ("If X, then Y") |

### 5.3 Limitation Acknowledgment

**Definition:** Research must honestly communicate what it can and cannot claim.

**Required limitations:**

| Limitation Type | What to State |
|-----------------|---------------|
| Data quality | What couldn't be verified, confidence levels |
| Coverage gaps | What wasn't researched, what's missing |
| Methodology limits | What the approach couldn't capture |
| Scope limits | What's outside the research question |
| Generalizability | How broadly findings apply |

---

## 6. Quality Metrics

Quantitative measures of research quality.

### 6.1 Source Quality Distribution

**Target distribution for quality research:**

| Confidence Level | Target Percentage |
|------------------|-------------------|
| HIGH | ≥30% of key claims |
| MEDIUM | 40-50% of claims |
| LOW | ≤20% of claims |
| UNVERIFIED | ≤10% (flagged, not in recommendations) |

**Source tier distribution:**

| Tier | Target |
|------|--------|
| Tier 1-3 | ≥40% of sources for key claims |
| Tier 4-5 | ≤40% of sources |
| Tier 6-7 | ≤20% (for context/discovery only) |

### 6.2 Coverage Metrics

| Metric | Target |
|--------|--------|
| Angles researched / Angles planned | 100% |
| Key questions answered | ≥80% |
| Data points per angle | ≥10 |
| Sources per key claim | ≥2 |
| Gaps documented | 100% of known gaps |

### 6.3 Objectivity Metrics

| Metric | Target |
|--------|--------|
| Conflicts of interest disclosed | 100% |
| Vendor claims tagged | 100% |
| Opposing viewpoints represented | Where they exist |
| Counter-evidence sought | For all major claims |

---

## 7. Quality Checklists

Use these checklists at each phase to ensure quality standards are met.

### Collection Phase Checklist

- [ ] All planned queries executed
- [ ] Data points have full source metadata
- [ ] Search log is complete and reproducible
- [ ] Gaps are documented with impact assessment
- [ ] Negative evidence documented

### Evaluation Phase Checklist

- [ ] All sources assessed with CRAAP
- [ ] All data points have tier assignments
- [ ] All data points have confidence levels
- [ ] All conflicts of interest identified and tagged
- [ ] All pitfalls detected and flagged
- [ ] Filtering decisions documented with rationale

### Analysis Phase Checklist

- [ ] Cross-reference matrix complete
- [ ] Themes supported by multiple data points
- [ ] Tensions surfaced (not hidden)
- [ ] Gaps connected to impact on conclusions
- [ ] Context relevance assessed for all findings

### Synthesis Phase Checklist

- [ ] All claims traceable to sources
- [ ] Numbers match source precision
- [ ] Confidence levels stated for key claims
- [ ] Recommendations grounded in evidence
- [ ] Context fit assessed for recommendations
- [ ] Missing context flagged explicitly
- [ ] Limitations section complete
- [ ] Audit trail maintained

### Final Quality Gate

Before research is considered complete:

- [ ] Accuracy: Claims verified against sources
- [ ] Completeness: All angles covered, gaps documented
- [ ] Objectivity: Biases identified and mitigated
- [ ] Verifiability: Full audit trail, reproducible methodology
- [ ] Actionability: Recommendations are grounded and specific

---

## 8. Quality Failures

Common quality failures and how to address them.

### 8.1 Accuracy Failures

| Failure | Symptom | Fix |
|---------|---------|-----|
| Misquotation | Claim doesn't match source | Verify against original |
| Overgeneralization | Scope broader than source supports | Constrain claim scope |
| False precision | Numbers more precise than source | Match source precision |
| Missing context | Number without methodology/date | Add context or flag |

### 8.2 Completeness Failures

| Failure | Symptom | Fix |
|---------|---------|-----|
| Shallow research | Few data points per angle | Expand search |
| Hidden gaps | Gaps not documented | Document all gaps |
| Single-source claims | Key claims from one source only | Seek corroboration |
| Missing angles | Approved angles not covered | Complete all angles |

### 8.3 Objectivity Failures

| Failure | Symptom | Fix |
|---------|---------|-----|
| Undisclosed conflicts | Vendor claims treated as objective | Tag all conflicts |
| One-sided presentation | Only supporting evidence | Seek counter-evidence |
| False balance | Fringe views over-weighted | Weight by evidence quality |
| Confirmation bias | Only sought confirming data | Actively seek disconfirming |

### 8.4 Verifiability Failures

| Failure | Symptom | Fix |
|---------|---------|-----|
| Missing citations | Claims without sources | Add sources or remove claims |
| Broken audit trail | Can't trace claim to source | Rebuild trail |
| Non-reproducible | Methodology not documented | Document all steps |
| Link rot | URLs no longer work | Archive sources, note access date |

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2024-01-27 | Initial framework |

