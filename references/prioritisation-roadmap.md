# Prioritisation & Roadmap Reference

This reference is loaded by the orchestrator skill when a user needs to prioritise features or build a roadmap. It covers two capabilities that share a common foundation: prioritisation scores and ranks items; roadmapping runs prioritisation internally as its first step, then places items into a structured plan.

---

## Cross-References

- **Upstream inputs:** Feature lists from discovery mode or PRDs feed into prioritisation/roadmapping as raw input.
- **Downstream outputs:** Ranked and roadmapped items feed into the Feature Decomposition capability (`references/feature-breakdown.md`).
- **Visual:** If a diagramming skill is installed, use it for roadmap timeline visualisation (Gantt-style, dependency graphs, Now/Next/Later swim lanes); otherwise present the roadmap in text or ASCII.
- **Research:** If a deep-research skill is installed, use it for competitive pressure analysis or market validation before scoring; otherwise research manually and cite sources.

---

## Part 1: Prioritisation

### Purpose

Score and rank a set of features or initiatives so the team can make defensible trade-off decisions. Produce a transparent, auditable output that shows how each score was derived and what assumptions underpin it.

### Process

#### Step 1: Load Context

Read all available context files before scoring:

- `context/goals.md`: current objectives, OKRs, success metrics
- `context/product.md`: product vision, current state, constraints
- `context/company.md`: company strategy, stage, resources
- `context/personas.md`: target users, segments, jobs to be done
- `context/competitors.md`: competitive landscape, differentiation

If any context file is missing, note it as a data gap in the output. Do not guess at missing context; flag it explicitly.

#### Step 2: Gather Items to Prioritise

Obtain the list of features, initiatives, or opportunities to score. Sources may include:

- A user-provided list (typed or pasted)
- Output from a discovery session or PRD
- An existing backlog export
- Items surfaced by prior research (e.g. a deep-research skill, if one is installed)

For each item, confirm or establish: a short name, a one-line description, and the target persona/segment. If any item is too vague to score, ask the user to clarify before proceeding.

#### Step 3: Select Framework

**Default: RICE.** Use alternatives only when there is a clear reason.

| Framework | When to Use |
|---|---|
| RICE | Default. Works well for most product teams with quantifiable reach and effort data. |
| ICE | Quick-and-dirty scoring for early-stage ideas, hackathon-style triage, or when data is sparse. |
| Weighted Scoring | When standard frameworks do not capture the dimensions that matter (e.g., strategic alignment, regulatory risk, technical debt reduction). Build a custom scorecard. |

**RICE Calculation:**

```
RICE Score = (Reach x Impact x Confidence) / Effort
```

| Dimension | Definition | Scale |
|---|---|---|
| Reach | Number of users/customers affected per quarter | Concrete number (e.g., 5,000 users/quarter) |
| Impact | Contribution to the target goal per user reached | 3 = massive, 2 = high, 1 = medium, 0.5 = low, 0.25 = minimal |
| Confidence | How sure we are about the estimates | 100% = data-backed, 80% = some evidence, 50% = gut feel, 20% = pure speculation |
| Effort | Total work required across all teams | Person-months (e.g., 2 = two person-months) |

Confidence guidance:
- 100%: backed by analytics, user research, or A/B test results
- 80%: directional data exists (surveys, competitor benchmarks, support ticket volume)
- 50%: informed intuition, no hard data
- 20%: speculative, no evidence; flag for validation

**ICE Calculation:**

```
ICE Score = Impact x Confidence x Ease
```

All three dimensions scored 1-10. Faster to apply but less rigorous. Best for initial filtering before a deeper RICE pass.

**Weighted Scoring:**

Define custom dimensions with explicit weights. Example:

| Dimension | Weight |
|---|---|
| Strategic alignment | 30% |
| User value | 25% |
| Revenue impact | 20% |
| Feasibility | 15% |
| Risk reduction | 10% |

Score each dimension 1-5, multiply by weight, sum for total. Always state the weights and rationale before scoring.

#### Step 4: Score Each Item

Score every item transparently. Show the reasoning behind each dimension, not just the number. Where estimates are uncertain, say so and record the confidence level.

#### Step 5: Build Value/Effort Matrix

Plot items on a 2x2 quadrant:

```
                    HIGH VALUE
                        |
         Big Bets       |      Quick Wins
        (high value,    |     (high value,
         high effort)   |      low effort)
                        |
   HIGH EFFORT ---------+---------- LOW EFFORT
                        |
         Money Pits     |      Fill-Ins
        (low value,     |     (low value,
         high effort)   |      low effort)
                        |
                    LOW VALUE
```

- **Quick Wins**: high value, low effort. Do these first.
- **Big Bets**: high value, high effort. Commit deliberately; these define the roadmap.
- **Fill-Ins**: low value, low effort. Slot in when capacity allows; do not plan around them.
- **Money Pits**: low value, high effort. Deprioritise unless there is a compelling strategic reason.

Use ASCII for the matrix. For a richer visual, use a diagramming skill if one is installed.

#### Step 6: Sensitivity Analysis

For the top 3 ranked items, test robustness:

- What happens if confidence drops by one tier (e.g., 80% to 50%)?
- What happens if effort increases by 50%?
- Does the ranking change?

If a small shift in assumptions changes the ranking, flag that item as sensitive and recommend validation before committing.

#### Step 7: Categorise Recommendations

Sort all items into action categories:

| Category | Criteria |
|---|---|
| Do Now | Top-ranked, high confidence, aligns with current objectives |
| Do Next | Strong score but blocked, needs sequencing, or depends on a Do Now item |
| Quick Win | High value, low effort: can be done in parallel or between larger initiatives |
| Defer | Moderate score, not urgent, revisit next planning cycle |
| Deprioritise | Low score, poor strategic fit, or Money Pit quadrant: explicitly set aside |

#### Step 8: Surface Gaps

List:

- **Assumptions to validate**: what did we assume that we should test? (e.g., "Assumed 5,000 users affected based on current MAU; validate with analytics")
- **Data gaps**: what information was missing that would change scores if known? (e.g., "No churn data available; Impact score for retention features is low-confidence")

---

### Prioritisation Output Template

```markdown
## Prioritisation: [Title]

**Date:** [date]
**Framework:** [RICE / ICE / Weighted Scoring]
**Context loaded:** [list which context files were read, or note gaps]

### Rankings

| Rank | Initiative | Reach | Impact | Confidence | Effort | RICE Score |
|------|-----------|-------|--------|------------|--------|------------|
| 1    | [name]    | [n]   | [n]    | [n%]       | [n]    | [n]        |
| 2    | [name]    | [n]   | [n]    | [n%]       | [n]    | [n]        |
| ...  | ...       | ...   | ...    | ...        | ...    | ...        |

### Value/Effort Matrix

[ASCII 2x2 quadrant with items placed]

### Sensitivity Analysis

| Initiative | Base Score | If Confidence -1 Tier | If Effort +50% | Ranking Stable? |
|-----------|-----------|----------------------|----------------|-----------------|
| [top 1]   | [n]       | [n]                  | [n]            | Yes / No        |
| [top 2]   | [n]       | [n]                  | [n]            | Yes / No        |
| [top 3]   | [n]       | [n]                  | [n]            | Yes / No        |

### Recommendations

**Do Now**
- [item]: [one-line rationale]

**Do Next**
- [item]: [one-line rationale]

**Quick Wins**
- [item]: [one-line rationale]

**Defer**
- [item]: [one-line rationale]

**Deprioritise**
- [item]: [one-line rationale]

### Assumptions to Validate
- [assumption and how to validate it]

### Data Gaps
- [what's missing and what it would affect]
```

---

## Part 2: Roadmap

### Purpose

Place prioritised initiatives into a structured, communicable roadmap. The roadmap is outcome-driven (organised around what we want to achieve) rather than feature-driven (organised around what we want to build).

### Process

#### Step 1: Load Context

Same as prioritisation Step 1. Read all context files. Additionally, look for:

- Existing OKRs or strategic objectives
- Capacity constraints and team structure
- External deadlines (regulatory, contractual, seasonal)

#### Step 2: Run Prioritisation

Execute the full prioritisation process (Part 1) on all candidate items. This produces the ranked list, recommendations, and sensitivity analysis that inform placement.

#### Step 3: Define Business Objectives

Establish what the business is trying to achieve this period. Each objective must map to a source (OKR, strategy document, leadership directive). If the user has not provided objectives, derive them from context files and confirm.

#### Step 4: Define Leading Product Outcomes

For each business objective, define the measurable product outcomes that drive it. These are leading indicators, not lagging business metrics.

Example:
- Business Objective: "Increase ARR by 30%"
- Leading Outcome: "Improve trial-to-paid conversion from 8% to 14%"

Each outcome needs a current state and a target state.

#### Step 5: Place Initiatives (Now / Next / Later)

Use the Now/Next/Later framework. This is deliberately time-ambiguous to avoid false precision.

| Horizon | Meaning | Confidence Level | Commitment Level |
|---------|---------|-------------------|------------------|
| Now | Currently in progress or about to start | High: scoped, resourced, committed | Committed. Changing these has a real cost. |
| Next | Planned for after current work completes | Medium: directionally clear, details flexible | Planned. Sequencing may shift. |
| Later | On the radar, not yet committed | Low: intentionally vague, may change significantly | Directional. May be dropped entirely. |

Placement rules:
- **Do Now** items from prioritisation go into Now or Next (depending on capacity).
- **Quick Wins** go into Now if they can run in parallel, otherwise Next.
- **Do Next** items go into Next.
- **Defer** items go into Later or Not This Period.
- **Deprioritise** items go into Not This Period with an explicit reason.

#### Step 6: Capacity Check

Apply the 70/20/10 guideline as a sanity check:

| Category | Allocation | Purpose |
|----------|-----------|---------|
| Planned features | ~70% | New value delivery: the initiatives in Now/Next |
| Technical health | ~20% | Infrastructure, performance, security, tech debt |
| Unplanned | ~10% | Buffer for bugs, urgent requests, opportunities |

If the roadmap consumes more than ~70% of estimated capacity on planned features, it is overloaded. Either move items to Next/Later or flag that the plan requires more capacity than available.

This is a guideline, not a rigid rule. The actual split depends on product maturity, technical debt load, and team health. But if the ratio is wildly off (e.g., 95% features, 0% tech health), raise it.

#### Step 7: Map Dependencies

Categorise dependencies explicitly:

| Type | Description | Example |
|------|------------|---------|
| Technical | Requires infrastructure or platform work first | "Needs new event pipeline before analytics features" |
| Team | Requires another team's contribution | "Design team capacity needed for onboarding redesign" |
| External | Depends on third party, partner, or vendor | "Payment provider API v3 launches Q2" |
| Knowledge | Requires research or validation before committing | "Need user research on pricing sensitivity" |
| Sequential | Must happen in order | "Feature B builds on Feature A's data model" |

For each dependency, note: what depends on what, who owns the dependency, and what happens if it slips.

#### Step 8: Communicate the Roadmap

The roadmap must be understandable by different audiences. Tailor the level of detail:

| Audience | Focus | Level of Detail |
|----------|-------|----------------|
| Leadership / Board | Business objectives, outcomes, strategic bets | High-level themes, confidence levels |
| Cross-functional teams | What's coming, when, and what they need to do | Initiative-level, dependencies, timelines |
| Engineering | What to build, in what order, with what constraints | Detailed scope, technical dependencies, sequencing |

When communicating changes to a published roadmap:
- State what changed and why.
- Explain the impact on other items.
- Restate what has not changed (anchoring).
- Never just silently shuffle items.

#### Step 9: Document Deferrals

Explicitly list what is NOT on the roadmap and why. This is as important as what is on it. Reasons to defer:

- Lower priority than competing items
- Insufficient data to commit (needs research first)
- Blocked by unresolved dependencies
- Does not align with current objectives
- Capacity constraints

### Alternative Roadmap Formats

The Now/Next/Later framework is the default. Two alternatives are available when the context demands them:

**Quarterly Themes Format**

Organise by quarter, each with a theme that ties initiatives together.

```
Q2 2026: Theme: "Activate the Mid-Market"
  - Initiative A (drives outcome X)
  - Initiative B (drives outcome Y)

Q3 2026: Theme: "Platform Reliability"
  - Initiative C (drives outcome Z)
```

Use this when stakeholders need calendar-aligned planning (e.g., for budgeting, hiring, or external commitments). Be honest about the confidence decay: Q2 is high confidence, Q3 is medium, Q4 is low.

**OKR-Aligned Format**

Organise directly under OKRs, showing which initiatives drive which key results.

```
Objective: Become the default tool for mid-market teams
  KR1: 200 mid-market accounts (currently 80)
    - Initiative A
    - Initiative B
  KR2: NPS > 50 in mid-market segment (currently 32)
    - Initiative C
```

Use this when the organisation runs on OKRs and stakeholders think in that structure.

---

### Roadmap Output Template

```markdown
## Roadmap: [Title]

**Date:** [date]
**Period:** [e.g., Q2-Q4 2026]
**Context loaded:** [list which context files were read, or note gaps]

### Business Objectives

| # | Objective | Source | Confidence |
|---|----------|--------|------------|
| 1 | [objective] | [OKR / strategy doc / leadership directive] | [High/Medium/Low] |
| 2 | [objective] | [source] | [confidence] |

### Leading Product Outcomes

| Outcome | Drives Objective | Current | Target | Measurement |
|---------|-----------------|---------|--------|-------------|
| [outcome] | [#] | [current state] | [target state] | [how measured] |

### Now: [Theme or summary phrase]

**Why Now:** [rationale: why these items are committed and sequenced first]

| Initiative | Drives Outcome | Owner | Dependencies | Status |
|-----------|---------------|-------|--------------|--------|
| [name] | [outcome] | [team/person] | [deps or "None"] | [Not started / In progress / Blocked] |

### Next: [Theme or summary phrase]

**Why Next:** [rationale: why these follow, what needs to happen first]

| Initiative | Drives Outcome | Owner | Dependencies | Est. Readiness |
|-----------|---------------|-------|--------------|----------------|
| [name] | [outcome] | [team/person] | [deps or "None"] | [when expected to start] |

### Later: [Theme or summary phrase]

**Why Later:** [rationale: why these are deferred but retained]

| Initiative | Drives Outcome | Dependencies | Open Questions |
|-----------|---------------|--------------|----------------|
| [name] | [outcome] | [deps or "None"] | [what needs answering before committing] |

### Capacity Check

| Category | Planned Allocation | Guideline |
|----------|-------------------|-----------|
| New features | [n%] | ~70% |
| Technical health | [n%] | ~20% |
| Unplanned buffer | [n%] | ~10% |

[Note any capacity concerns or overload warnings]

### Dependencies & Risks

| Dependency | Type | Owner | Items Affected | Mitigation |
|-----------|------|-------|----------------|------------|
| [description] | [Technical/Team/External/Knowledge/Sequential] | [who] | [which initiatives] | [plan if it slips] |

### Not This Period

| Initiative | Reason Deferred | Revisit When |
|-----------|----------------|--------------|
| [name] | [reason] | [trigger or date] |

### Assumptions to Validate

- [assumption]: [how to validate, by when]

### Data Gaps

- [what's missing]: [impact on roadmap confidence]
```

---

## Behavioural Rules

1. **Always show your working.** Every score must have a visible calculation. Every placement must have a stated rationale. The value of this process is transparency, not just the output.

2. **Never fabricate data.** If a number is an estimate, label it as such with the confidence tier. If data is unavailable, say so and record it as a gap.

3. **Challenge weak assumptions.** If the user provides reach or impact estimates that seem implausible, push back. Ask for the source. A prioritisation built on fantasy numbers is worse than no prioritisation at all.

4. **Prefer fewer, better-scoped items.** A roadmap with 30 items in Now is not a roadmap; it is a wishlist. Push for focus. Three to five items in Now is typical. If the user insists on more, flag the capacity risk explicitly.

5. **Separate confidence from commitment.** Now items are committed. Next items are planned but flexible. Later items are directional. Never present Later items with the same certainty as Now items.

6. **State what is excluded.** The Not This Period section is mandatory. Stakeholders need to see what was considered and rejected, not just what made the cut.

7. **Flag when prioritisation is premature.** If there are too many data gaps or the items are too vaguely defined to score meaningfully, say so. Recommend a discovery or research step first (using a deep-research skill if one is installed, or manual research otherwise) rather than producing a false-precision ranking.

8. **Adapt the framework to the context.** RICE is the default, but do not force it when it does not fit. If the user's items are all internal tooling with no meaningful "reach" metric, suggest weighted scoring instead.

9. **Keep the roadmap alive.** A roadmap is a living document. When producing one, note when it should be reviewed (typically every 4-6 weeks or at the start of each planning cycle) and what would trigger an earlier revision (e.g., major market shift, key dependency slipping, new strategic direction).

10. **Log decisions.** After completing a prioritisation or roadmap, log significant decisions to `context/decisions.md`: which items were deprioritised and why, what trade-offs were made, and what assumptions drove the ranking. This creates an audit trail that makes future re-prioritisations faster and more informed.
