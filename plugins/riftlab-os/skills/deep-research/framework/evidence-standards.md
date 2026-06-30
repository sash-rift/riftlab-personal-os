# Evidence Standards

This document defines what counts as evidence, how to evaluate it, and how to assign confidence. It is the shared reference for all agents in the research workflow.

---

## Purpose

Every claim in research output must be grounded in evidence. This document provides:

1. **Source Tier Classification** - How to categorize sources by reliability
2. **Confidence Taxonomy** - How to assign and communicate certainty levels
3. **Pitfall Catalog** - Common patterns that produce unreliable data
4. **Verification Requirements** - When and how to verify claims
5. **Domain Adaptations** - How standards shift by research domain

Agents reference this document differently:
- **Planner** reads it to set scope-specific quality criteria
- **Searcher** reads it to filter and prioritize during collection
- **Evaluator** reads it to audit compliance and catch issues

---

## 1. Source Tier Classification

Sources are classified into seven tiers based on reliability, methodology transparency, and independence. Higher tiers are more trustworthy but harder to find.

### Tier 1: Primary Research & Official Records

**What it is:** Original data from controlled studies, official regulatory filings, government statistics, peer-reviewed academic research.

**Characteristics:**
- Methodology is documented and reproducible
- Sample sizes are stated
- Data collection methods are transparent
- Subject to peer review or regulatory oversight
- Independence from commercial interests

**Examples:**
- Peer-reviewed journal articles (Nature, JAMA, IEEE)
- SEC filings (10-K, 10-Q, S-1)
- Government statistics (Census, BLS, FDA databases)
- Clinical trial results (ClinicalTrials.gov)
- Academic dissertations with methodology sections

**Trust level:** Highest. Can be cited as fact with HIGH confidence.

**How to identify:**
- Published in recognized academic journals
- Contains methodology section with sample size (n=)
- Filed with regulatory bodies
- DOI or official document numbers
- Institutional affiliation of authors

---

### Tier 2: Official Documentation & First-Party Authoritative Sources

**What it is:** Official documentation from the entity being researched, authoritative industry bodies, standards organizations.

**Characteristics:**
- Direct from the source (company, organization, standards body)
- Documented and versioned
- Subject to legal or professional accountability
- No intermediary interpretation

**Examples:**
- Company annual reports and investor presentations
- Official product documentation and specifications
- Industry standards (ISO, W3C, IETF RFCs)
- Professional body publications (AMA, ABA, IEEE standards)
- Patent filings
- Official press releases (for announcements, not claims)

**Trust level:** High. Reliable for facts about the entity itself. Be cautious of self-serving claims.

**How to identify:**
- Published on official company/organization domains
- Has version numbers or publication dates
- Legal disclaimers present
- Authored by the organization, not about them

**Caveats:**
- Companies may present data favorably
- Press releases are marketing, not journalism
- Self-reported metrics lack independent verification

---

### Tier 3: Research with Transparent Methodology

**What it is:** Industry research, surveys, and reports from credible firms that disclose their methodology.

**Characteristics:**
- Methodology is stated (sample size, collection method, date range)
- Research firm has established reputation
- Distinguishes between data and interpretation
- Acknowledges limitations

**Examples:**
- Gartner, Forrester, IDC reports (with methodology sections)
- McKinsey, BCG, Bain research (with stated methodology)
- Pew Research Center studies
- Industry association surveys (with n= and method)
- Academic working papers (pre-peer review but methodology present)

**Trust level:** High. Reliable when methodology is appropriate for the claim.

**How to identify:**
- Named research firm with reputation
- Sample size stated (n=X)
- Data collection method described
- Time period specified
- Limitations acknowledged

**Caveats:**
- Check who funded the research
- Methodology may be flawed even if stated
- Paywalled reports may only show summaries (methodology hidden)

---

### Tier 4: Expert Analysis & Credentialed Commentary

**What it is:** Analysis from recognized experts, credentialed professionals, and established analysts.

**Characteristics:**
- Author has verifiable expertise in the domain
- Analysis is reasoned and cites sources
- Published in reputable venues
- Distinguishes opinion from fact

**Examples:**
- Named analyst reports (individual analysts at research firms)
- Expert commentary in quality publications
- Whitepapers from credible institutions
- Conference presentations by recognized experts
- Books by domain authorities

**Trust level:** Medium-High. Valuable for interpretation and context. Verify underlying facts independently.

**How to identify:**
- Author credentials are verifiable
- Published in recognized venue
- Cites sources for factual claims
- Expertise matches the topic

**Caveats:**
- Experts can be wrong
- May have undisclosed conflicts of interest
- Opinion presented as fact is common

---

### Tier 5: Quality Journalism & Investigative Reporting

**What it is:** Reporting from established news organizations with editorial standards, fact-checking, and accountability.

**Characteristics:**
- Published by recognized news organizations
- Subject to editorial review
- Sources are cited or described
- Corrections are issued when wrong
- Journalist byline present

**Examples:**
- Wall Street Journal, Financial Times, Reuters, Bloomberg
- New York Times, Washington Post (news sections, not opinion)
- TechCrunch, The Verge, Ars Technica (for tech topics)
- Industry-specific trade publications with editorial standards

**Trust level:** Medium. Good for events, quotes, and reported facts. Verify numbers independently.

**How to identify:**
- Recognized publication name
- Journalist byline
- Sources described (even if anonymous)
- Publication has corrections policy

**Caveats:**
- Breaking news may have errors
- Headlines can be misleading vs. article content
- Opinion sections are Tier 6-7, not Tier 5
- Press release rewrites are not journalism

---

### Tier 6: Aggregator Sites & Secondary Sources

**What it is:** Sites that compile information from other sources, market research aggregators, content farms, SEO-optimized articles.

**Characteristics:**
- Compiles data from other sources (often without clear citation)
- Optimized for search visibility
- May lack editorial oversight
- Often presents numbers without methodology

**Examples:**
- Market research aggregator sites (360researchreports, marketsandmarkets summaries)
- Wikipedia (use for orientation, verify claims via cited sources)
- SEO content sites
- News aggregators without original reporting
- Listicles and "top 10" articles
- Quora, Reddit (for general orientation only)

**Trust level:** Low. Use for discovery and orientation. Never cite as authoritative source.

**How to identify:**
- No clear original reporting
- Numbers appear without methodology
- Heavy SEO optimization (keyword stuffing)
- "According to reports" without naming reports
- Multiple sites have identical numbers (echo chamber signal)

**Caveats:**
- May be accurate but unverifiable
- Echo chamber effect: sites cite each other
- Numbers often lack primary source trail

---

### Tier 7: Unverified Claims & Potentially Biased Sources

**What it is:** Blog posts, social media, vendor marketing, anonymous sources, opinion pieces, user-generated content.

**Characteristics:**
- No editorial oversight
- May have undisclosed conflicts of interest
- Opinions presented as facts
- No accountability for accuracy

**Examples:**
- Personal blogs and Medium articles
- Social media posts
- Vendor marketing materials and case studies
- Anonymous forum posts
- Opinion columns and editorials
- Influencer content
- Press releases presented as news

**Trust level:** Lowest. May contain useful signals but never cite as evidence.

**How to identify:**
- No institutional affiliation
- Author has commercial interest in the topic
- No sources cited
- Promotional language
- "I think" or opinion framing

**Caveats:**
- Can still contain true information
- Useful for discovering what claims exist
- Vendor claims about their own products are especially suspect

---

## 2. Confidence Taxonomy

Every claim in research output must have a confidence level. Confidence reflects both source quality and corroboration.

### HIGH Confidence

**Definition:** Claim is well-supported by multiple reliable sources or a single authoritative primary source.

**Criteria (must meet ALL):**
- Source is Tier 1-3
- Methodology is appropriate for the claim
- Data is current (within 2 years for fast-moving markets)
- No significant conflicting data from comparable sources
- OR: Corroborated by 2+ independent Tier 3-4 sources

**Language:** State as fact. "The market is $2.1B" not "The market may be $2.1B"

**Example:**
> Market size: $2.16B in 2024 (Gartner, n=500 enterprises, survey methodology documented)

---

### MEDIUM Confidence

**Definition:** Claim is supported but with limitations - single source, older data, or minor conflicts.

**Criteria (any of):**
- Source is Tier 4-5 with clear reasoning
- Source is Tier 1-3 but data is 2-3 years old
- Two sources give similar but not identical numbers
- Methodology is partial or unclear
- Single Tier 3 source without corroboration

**Language:** State with appropriate hedging. "Research suggests" or "According to [source]"

**Example:**
> Industry analysts estimate 15-20% annual growth (Forrester 2024, methodology not fully disclosed)

---

### LOW Confidence

**Definition:** Claim exists but cannot be adequately verified. May be directionally useful.

**Criteria (any of):**
- Source is Tier 6-7
- Data is >3 years old for fast-moving markets
- Significant conflicts between sources
- Methodology is absent or inappropriate
- Single source with no corroboration and limited credentials

**Language:** Explicit uncertainty. "Unverified reports suggest" or "One source claims"

**Example:**
> Some aggregator sites cite $850M market size, but no primary source with methodology could be located (LOW confidence, treat as unverified)

---

### UNVERIFIED

**Definition:** Claim appears in sources but cannot be traced to any credible origin. Should not be used in recommendations.

**Criteria:**
- No Tier 1-5 source found despite searching
- Echo chamber detected (multiple sites, same number, no primary source)
- Source has clear conflict of interest with no independent verification
- Methodology would be required but is completely absent

**Language:** Explicit flag. "UNVERIFIED: [claim]. Multiple aggregator sites cite this but no primary source found."

**Example:**
> UNVERIFIED: "$850M market size" appears on multiple sites but all trace to a single aggregator with no methodology. Do not use for decisions.

---

### Confidence Propagation

When claims build on other claims, confidence can only decrease, never increase.

| Base Claim Confidence | Derived Claim Maximum |
|-----------------------|-----------------------|
| HIGH | HIGH |
| MEDIUM | MEDIUM |
| LOW | LOW |
| UNVERIFIED | UNVERIFIED |

**Example:**
> If market size is MEDIUM confidence and growth rate is HIGH confidence, the projected future market size is MEDIUM confidence (limited by weakest input).

---

## 3. Pitfall Catalog

These patterns produce unreliable data. Agents must detect and flag them.

### 3.1 Source Echo Chamber

**Pattern:** The same number appears across multiple sites, all citing each other or no primary source.

**How to detect:**
- Search for the specific number in quotes
- Check if sites cite each other circularly
- Look for a primary source with methodology
- If 3+ sites have identical numbers with no methodology trail → echo chamber

**Example:**
```
Site A: "The market is $850M"
Site B: "According to research, the market is $850M" (links to Site A)
Site C: "The $850M market..." (no citation)
Site D: "Studies show an $850M market" (links to Site B)
```

**Action:** Flag as UNVERIFIED. Note: "Echo chamber detected. Number appears on X sites but no primary source with methodology found."

---

### 3.2 Vendor Marketing as Research

**Pattern:** A company makes claims about their own market, product efficacy, or customer results.

**How to detect:**
- Source is the company's own website, blog, or press release
- Claims favor the company's product or market position
- Case studies without independent verification
- "Our customers see X% improvement"

**Example:**
```
"Acme Corp's platform increases engagement by 300%"
- Source: Acme Corp blog post
```

**Action:** Tag as [VENDOR CLAIM]. Do not treat as independent verification. Note the conflict of interest. May still be useful for understanding vendor positioning.

---

### 3.3 Precision Without Methodology

**Pattern:** Suspiciously specific numbers with no explanation of how they were derived.

**How to detect:**
- Very precise numbers ($384.7M, 23.7% growth)
- No sample size, survey method, or calculation basis
- No research firm or methodology citation
- Number appears in aggregator or SEO content

**Example:**
```
"The global market opportunity is $384.7 billion by 2030"
- No research firm named
- No methodology
- No sample size
- Found on SEO-optimized aggregator site
```

**Action:** Flag as LOW confidence or UNVERIFIED. The precision is false confidence. Seek primary source or downgrade.

---

### 3.4 Outdated Data Presented as Current

**Pattern:** Old statistics used without date context, especially in fast-moving markets.

**How to detect:**
- Claims about market size, adoption rates, or technology usage
- No publication date on the source
- Date found but data is >2-3 years old
- Market conditions have materially changed since data collection

**Example:**
```
"78% of enterprises have adopted cloud computing"
- Study from 2019
- Presented in 2024 article without date context
```

**Action:** Always include publication date. Flag if >2 years old for fast-moving markets. Note: "Data from [year]. Market conditions may have changed."

---

### 3.5 Survivorship Bias

**Pattern:** Examples only include successes, ignoring failures that would change the conclusion.

**How to detect:**
- "Companies like X, Y, Z did this and succeeded"
- No mention of companies that tried and failed
- Success rate not mentioned
- Cherry-picked case studies

**Example:**
```
"Dropbox, Slack, and Zoom all used product-led growth to reach $1B"
- Ignores hundreds of PLG companies that failed
- Implies PLG → success when correlation is weak
```

**Action:** Note survivorship bias. Seek data on failure rates. Adjust confidence. "Examples show success cases but base rate of success unknown."

---

### 3.6 Conflation of Correlation and Causation

**Pattern:** Two things happening together presented as one causing the other.

**How to detect:**
- "Companies that do X have Y% better outcomes"
- No controlled study
- Plausible alternative explanations not addressed
- Direction of causation unclear

**Example:**
```
"Companies with strong employer brands have 50% lower turnover"
- Are strong brands causing lower turnover?
- Or do successful companies have both?
- No controlled experiment
```

**Action:** Note correlation vs causation issue. Rephrase as correlation. "Companies with X correlate with Y (causation not established)."

---

### 3.7 Sample Bias / Non-Representative Data

**Pattern:** Data collected from a non-representative sample presented as general truth.

**How to detect:**
- Survey of "industry leaders" (selection bias)
- Data from single geography presented as global
- Self-selected respondents (people who chose to respond)
- Platform-specific data (LinkedIn data ≠ all professionals)

**Example:**
```
"90% of marketers plan to increase AI spending"
- Survey of attendees at AI marketing conference
- Sample is pre-selected for AI enthusiasm
```

**Action:** Note sample limitations. Adjust generalizability. "Among [specific sample], X%. May not represent broader population."

---

### 3.8 Misaligned Definitions

**Pattern:** Different sources use different definitions for the same term, making comparison invalid.

**How to detect:**
- Market size estimates vary wildly (2x or more)
- Terms like "AI market" or "SaaS market" without scope definition
- Includes/excludes different segments
- Different methodologies (TAM vs SAM vs SOM)

**Example:**
```
Source A: "AI market is $150B" (includes all software with any ML)
Source B: "AI market is $50B" (only pure-play AI companies)
Source C: "AI market is $500B" (includes hardware, services, everything)
```

**Action:** Note definition differences. Do not average incompatible numbers. Report range with definitions. "Market size ranges from $50B to $500B depending on definition. [Definition used by each source]."

---

## 4. Verification Requirements

When and how to verify claims before including them in research output.

### Claims That Require Verification

| Claim Type | Verification Requirement |
|------------|--------------------------|
| Market size / TAM | Must have Tier 1-3 source with methodology, or flag as UNVERIFIED |
| Growth rates | Must have source with time period and methodology |
| Company revenue / metrics | Must be from company filings, official releases, or Tier 1-3 research |
| User/customer counts | Official source or Tier 1-3 research |
| Percentages / adoption rates | Must have sample size and methodology |
| "Studies show" claims | Must name the study with citation |
| Competitive positioning | Multiple sources recommended |

### Claims That Can Use Lower-Tier Sources

| Claim Type | Acceptable Sources |
|------------|-------------------|
| Company exists and does X | Tier 5-6 acceptable |
| Feature comparisons | Official docs (Tier 2) + reviews (Tier 5-6) |
| General trends | Tier 4-5 with multiple sources |
| Historical events | Tier 5 journalism acceptable |
| Definitions / explanations | Tier 4-6 acceptable if consistent |

### Verification Methods

**Method 1: Source Trail**
- Follow citations back to primary source
- If trail ends at aggregator with no methodology → UNVERIFIED

**Method 2: Triangulation**
- Find 2-3 independent sources for the same claim
- If sources agree and are Tier 3-5 → upgrade confidence
- If sources conflict → note tension, report range

**Method 3: Primary Source Search**
- Search for the research firm + topic directly
- Search for SEC filings, official releases
- Search academic databases (Google Scholar)

**Method 4: Recency Check**
- Verify publication date
- Check if newer data exists
- Note if data is >2 years old for fast-moving markets

---

## 5. Domain Adaptations

Evidence standards shift based on research domain. The Planner agent uses this section to set scope-specific quality criteria.

### Market Research

**Priority sources:** Research firms (Gartner, Forrester, IDC), industry associations, company filings
**Minimum tier for sizing claims:** Tier 1-3
**Key pitfalls:** Echo chambers, precision without methodology, definition misalignment
**Special rules:**
- Market size requires methodology or flag as UNVERIFIED
- Vendor TAM claims are [VENDOR CLAIM], not independent data
- Distinguish TAM / SAM / SOM explicitly

### Technical / Product Research

**Priority sources:** Official documentation, GitHub, RFCs, academic papers, technical blogs from practitioners
**Minimum tier for core claims:** Tier 2-4
**Key pitfalls:** Outdated documentation, version mismatches, vendor marketing
**Special rules:**
- Stack Overflow answers are Tier 6 (starting point, not authority)
- Documentation version must match claim context
- Benchmarks require methodology and environment details

### Competitive Analysis

**Priority sources:** Company official sites, product documentation, analyst reports, quality journalism
**Minimum tier for positioning claims:** Tier 2-5
**Key pitfalls:** Vendor marketing, outdated comparisons, cherry-picked features
**Special rules:**
- Competitor self-reported metrics are [VENDOR CLAIM]
- Feature comparisons need official docs, not review sites
- Pricing requires official source or recent journalism

### Medical / Health Research

**Priority sources:** Peer-reviewed journals, clinical trials, regulatory filings, medical associations
**Minimum tier for health claims:** Tier 1-2 only
**Key pitfalls:** Blog health advice, supplement marketing, single studies overgeneralized
**Special rules:**
- No Tier 6-7 sources for health claims
- Single studies are not definitive
- Meta-analyses and systematic reviews preferred

### Financial / Investment Research

**Priority sources:** SEC filings, company financials, regulated analyst reports
**Minimum tier for financial claims:** Tier 1-3
**Key pitfalls:** Forward-looking statements, non-GAAP metrics, promotional material
**Special rules:**
- Distinguish reported vs adjusted metrics
- Note forward-looking statement caveats
- Historical data must include time period

### User Behavior / UX Research

**Priority sources:** Academic studies, controlled experiments, platform analytics reports
**Minimum tier for behavioral claims:** Tier 1-4
**Key pitfalls:** Self-reported behavior, small samples, single-platform data
**Special rules:**
- Self-reported surveys are not behavioral data
- Platform-specific data may not generalize
- A/B test results need sample size and statistical significance

---

## 6. Quick Reference Tables

### Tier Summary

| Tier | Name | Trust | Use For |
|------|------|-------|---------|
| 1 | Primary Research | Highest | Facts, citing as definitive |
| 2 | Official Documentation | High | Facts about the entity |
| 3 | Research with Methodology | High | Data with appropriate caveats |
| 4 | Expert Analysis | Medium-High | Interpretation, context |
| 5 | Quality Journalism | Medium | Events, quotes, leads |
| 6 | Aggregators | Low | Discovery only |
| 7 | Unverified / Biased | Lowest | Signals only, never cite |

### Confidence Quick Check

| Situation | Confidence |
|-----------|------------|
| Tier 1-3, methodology present, current data, no conflicts | HIGH |
| Tier 3-4, single source or minor limitations | MEDIUM |
| Tier 5-6, or conflicts, or old data | LOW |
| Echo chamber, no primary source, or Tier 7 only | UNVERIFIED |

### Pitfall Quick Check

| Signal | Pitfall | Action |
|--------|---------|--------|
| Same number, multiple sites, no methodology | Echo chamber | UNVERIFIED |
| Company claims about own product/market | Vendor marketing | [VENDOR CLAIM] |
| Precise number, no methodology | False precision | LOW / UNVERIFIED |
| No date or >2 years old | Outdated | Note date, flag if stale |
| Only success stories | Survivorship bias | Note bias, seek base rates |
| "X causes Y" without experiment | Correlation ≠ causation | Rephrase as correlation |

---

## 7. Changelog

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2024-01-27 | Initial framework |

