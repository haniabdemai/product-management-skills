# Persona Creation Reference

Guide for building user and buyer personas using the Pragmatic Institute framework. Produces structured, evidence-grounded persona documents with explicit validation status, anti-personas, and product implications.

## Contents
- Process (6 steps: context check, inputs, persona profiles, anti-personas, comparison, save)
- Persona Profile Template (overview, use scenarios, JTBD, goals/frustrations, behaviours, buying process, evidence, product implications, quotes)
- Anti-Persona Template
- Persona Comparison Template
- Output Document Structure
- Cross-References

---

## Process

### Step 1: Check Your Context

Read the following project context files if they exist:
- `context/personas.md`: any existing persona work
- `context/product.md`: product definition, value proposition, positioning
- `context/company.md`: company stage, market, business model

Tell the user what you found. If files are missing or sparse, note what gaps exist and how that affects the persona work. Do not silently skip missing context.

### Step 2: Gather Persona Inputs

Present the user with what you need. Separate critical from nice-to-have so they can move quickly if they want to.

**Critical inputs (cannot proceed without these):**
1. Who are the users and/or buyers? (Roles, titles, segments)
2. What problem does the product solve for them?

**Nice-to-have inputs (improve accuracy and depth):**
3. User research: interview transcripts, survey data, ethnographic notes
4. Analytics data: usage patterns, demographics, cohort behaviour
5. Support ticket themes: common complaints, feature requests, confusion points
6. Sales call notes: objections, buying triggers, deal blockers
7. Competitor context: who else are these people evaluating or using?

If the user provides research data, extract persona-relevant details from it rather than asking them to summarise. Do the analytical work.

### Step 3: Build Persona Profiles

For each persona, produce every section below. If data is insufficient for a section, write it using your best inference and mark every inferred item as **Assumed** in the evidence matrix.

---

#### 3a. Overview

A short narrative paragraph covering:
- Role and title (or consumer archetype)
- Organisation type and size (if B2B)
- Day-to-day context: what does their working life or relevant life domain look like?
- Key characteristics that make them distinct from other personas
- Relationship to the product: are they a user, a buyer, both, or an influencer?

#### 3b. Use Scenarios (Pragmatic Format)

Present as a table. Each row captures one concrete scenario in which this persona interacts with the product or the problem space.

| Persona | Goal | Problem | Frequency |
|---|---|---|---|
| [Name/Role] | What they are trying to accomplish | What gets in the way today | How often this occurs |

Include 3-5 scenarios per persona minimum. Scenarios should span the range from routine use to edge cases.

#### 3c. Jobs-to-be-Done

Structure JTBD statements in three categories:

**Functional Jobs**: the practical task they need to complete.
Format: "When [situation], I want to [motivation], so I can [expected outcome]."

**Emotional Jobs**: how they want to feel (or avoid feeling).
Format: "Avoid feeling [negative emotion] when [situation]" or "Feel [positive emotion] when [situation]."

**Social Jobs**: how they want to be perceived by others.
Format: "Be seen as [perception] by [audience]."

List 2-4 jobs per category.

#### 3d. Goals and Frustrations

**Goals**: what success looks like for this persona in the relevant domain. Not product goals; life/work goals that the product serves.

**Frustrations**: specific pain points, not generic complaints. Each frustration should be traceable to a scenario or JTBD.

#### 3e. Behaviours

| Dimension | Detail |
|---|---|
| **Triggers** | What events or situations cause them to seek a solution? |
| **Current workflow** | How do they handle the problem today, step by step? |
| **Frequency** | How often do they encounter the problem or use the product category? |
| **Tools used** | What tools, systems, or workarounds are currently in their stack? |
| **Information sources** | Where do they go to learn, evaluate, or get help? |
| **Decision style** | Do they decide quickly or deliberate? Solo or committee? |

#### 3f. Buying Process (B2B)

Only include this section for B2B personas where buying behaviour is relevant.

| Stage | Behaviour | Key Criteria | Influencers |
|---|---|---|---|
| **Awareness** | How they discover they have a problem worth solving. What triggers the search. | What makes them recognise the problem is urgent enough to act on? | Who or what brings the problem to their attention? |
| **Consideration** | How they research and evaluate solution categories. | What criteria do they use to build a shortlist? What do they compare? | Who do they consult? What content do they consume? |
| **Decision** | How they choose between shortlisted options and get approval. | What are the deal-breakers? What must be proven? | Who signs off? What internal politics matter? |
| **Implementation** | How they onboard, adopt, and measure success. | What does "working" look like? What would make them churn? | Who is responsible for rollout? Who judges success? |

#### 3g. Evidence Matrix

Every major claim in the persona must appear here, categorised by validation status.

| Claim | Status | Source | Confidence |
|---|---|---|---|
| [Specific claim from the persona] | **Validated** or **Assumed** | [Research source, data point, or "Inference from X"] | High / Medium / Low |

Rules:
- **Validated** means there is direct evidence: interview quotes, survey data, analytics, support tickets.
- **Assumed** means it is inferred from indirect evidence, pattern matching, or domain knowledge.
- Every **Assumed** item is a research gap. The persona document should make it obvious what still needs validation.

#### 3h. Product Implications

Map this persona's needs to concrete product decisions.

| Persona Need | Product Implication | Priority |
|---|---|---|
| [Need derived from JTBD, scenario, or frustration] | [What the product must do, support, or avoid] | Must-have / Should-have / Nice-to-have |

This table bridges persona work to PRD and feature breakdown work downstream.

#### 3i. Representative Quotes

Include 2-4 quotes that capture this persona's voice. If working from real research, use actual quotes (attributed or anonymised). If working from inference, write realistic constructed quotes and label them as **Constructed** so they are not mistaken for real data.

Format:
> "Quote text here."
> Source: [Interview #3 / Constructed / Survey response]

---

### Step 4: Anti-Personas

For each anti-persona, explain:

**Who they are**: describe the person or segment clearly enough that someone could recognise them.

**Why they are not your customer:**
- **Mismatch reason**: what fundamental mismatch exists? (Wrong problem, wrong scale, wrong budget, wrong values, wrong stage, etc.)
- **Signals**: what observable behaviours or attributes identify them?
- **Cost of serving them**: what happens if you try? (Support burden, feature bloat, brand dilution, negative unit economics, etc.)

**What to do when they show up:**
- Do you redirect them elsewhere?
- Do you let them self-serve but deprioritise their feedback?
- Do you actively filter them out of the funnel?

Anti-personas are not hypothetical. If the user has no data, ask them: "Who have you seen try to use the product and fail, or whom have you deliberately turned away?" Ground it in reality.

### Step 5: Persona Comparison

Produce a comparison table across all personas:

| Dimension | Persona A | Persona B | Persona C |
|---|---|---|---|
| **Primary JTBD** | | | |
| **Key frustration** | | | |
| **Buying trigger** | | | |
| **Decision speed** | | | |
| **Technical sophistication** | | | |
| **Price sensitivity** | | | |
| **Shared needs** | Needs shared across all or multiple personas | | |
| **Unique needs** | Needs specific to this persona only | | |
| **Priority ranking** | [1st / 2nd / 3rd: with reasoning] | | |

Follow the table with a short narrative answering three questions. Which persona is the primary target and why? Where do personas conflict (a feature that helps one may hurt another)? What does the priority ranking mean for product decisions?

### Step 6: Save to Context

Save the completed persona document to `context/personas.md` so that other skills can reference it.

Confirm to the user:
- What was saved
- Where it was saved
- What other capabilities reference it

---

## Output Document Structure

The final document saved to `context/personas.md` should follow this structure exactly:

```markdown
# Personas

**Product:** [from context/product.md or user input]
**Date:** [date of creation]
**Data sources:** [list all inputs used: interviews, surveys, analytics, assumptions, etc.]
**Validation status:** [e.g., "60% validated, 40% assumed: see evidence matrices"]

## Context Summary
[Brief summary of what was found in context/product.md and context/company.md.
Note any gaps that affected persona quality.]

---

## Persona 1: [Name]

### Overview
[Narrative paragraph]

### Use Scenarios
| Persona | Goal | Problem | Frequency |
|---|---|---|---|
| | | | |

### Jobs-to-be-Done
**Functional:** ...
**Emotional:** ...
**Social:** ...

### Goals
- ...

### Frustrations
- ...

### Behaviours
| Dimension | Detail |
|---|---|
| Triggers | |
| Current workflow | |
| Frequency | |
| Tools used | |
| Information sources | |
| Decision style | |

### Buying Process
| Stage | Behaviour | Key Criteria | Influencers |
|---|---|---|---|
| Awareness | | | |
| Consideration | | | |
| Decision | | | |
| Implementation | | | |

### Evidence Matrix
| Claim | Status | Source | Confidence |
|---|---|---|---|
| | | | |

### Product Implications
| Persona Need | Product Implication | Priority |
|---|---|---|
| | | |

### Representative Quotes
> "..."
> Source: [...]

---

## Persona 2: [Name]
[Repeat all sections]

---

## Anti-Personas

### Anti-Persona 1: [Name]
**Who they are:** ...
**Why they are not your customer:**
- Mismatch reason: ...
- Signals: ...
- Cost of serving them: ...

**What to do when they show up:** ...

---

## Persona Comparison

| Dimension | Persona 1 | Persona 2 |
|---|---|---|
| Primary JTBD | | |
| Key frustration | | |
| Buying trigger | | |
| Decision speed | | |
| Technical sophistication | | |
| Price sensitivity | | |
| Shared needs | | |
| Unique needs | | |
| Priority ranking | | |

[Narrative comparison paragraph]

---

## Suggested Next Steps
- [ ] Validate assumed claims (see evidence matrices)
- [ ] [Specific research recommendations based on gaps]
- [ ] Create journey maps for each persona (with a diagramming skill, if one is installed)
- [ ] Feed personas into PRD creation
- [ ] Review and update quarterly
```

---

## Cross-References

**Downstream usage:**
Output saved to `context/personas.md`: referenced by PRD, Feature Breakdown, and User Story capabilities. Personas inform prioritisation, acceptance criteria, and feature scoping in all downstream product work.

**Visual work:**
If a diagramming skill is installed, use it to create journey maps for each persona; otherwise describe the journeys in text. Journey maps visualise the buying process and use scenarios spatially, making them easier to share with stakeholders.

**Research:**
If a deep-research skill is installed, use it for market segmentation or buyer behaviour research when the evidence matrix shows too many **Assumed** items; otherwise research manually and cite sources. Deep research can validate or challenge persona assumptions with external data.

---

## Guidance Notes

**On persona count:** Aim for 2-4 personas maximum. More than that usually means the segmentation is too fine-grained or the product is trying to serve too many masters. If you end up with more than 4, ask whether some should be merged or deprioritised.

**On naming:** Give personas human names (e.g., "Sarah the Sales Lead") rather than abstract labels. It makes them easier to reference in conversation. But always include the role descriptor alongside the name.

**On assumptions:** The point of marking things as **Assumed** is not to discredit the persona. It is to create a clear research backlog. Every assumed claim is a question that can be answered with targeted research. The persona is still useful in the meantime.

**On anti-personas:** Teams resist writing anti-personas because it feels like turning away revenue. Frame it as focus: knowing who you are not for makes every product decision sharper. Anti-personas are especially valuable when the product team is under pressure to say yes to every feature request.

**On updates:** Personas are living documents. Set a review cadence (quarterly is typical). When new research data arrives (interviews, analytics shifts, market changes), update the persona and re-validate the evidence matrix. Stale personas are worse than no personas because they create false confidence.

**On B2C vs B2B:** The buying process table is optional for B2C products, but consider including a simplified version if the purchase decision involves deliberation (e.g., SaaS, subscription services, high-ticket consumer products). For pure impulse-purchase consumer products, skip it and focus more on the behavioural and emotional sections.
