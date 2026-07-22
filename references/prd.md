# PRD: Product Requirements Document

Reference loaded by the orchestrator when the user needs the PRD capability.

A PRD is a **product vision document**, not a feature spec. It articulates the big picture: what the product is, why it matters, how capabilities combine to deliver value, and what success looks like. Individual feature details, user stories, and acceptance criteria belong downstream.

---

## When to Use

- Defining a new product or a significant new product area.
- Formalising something that has been discussed verbally into a document that can get stakeholder sign-off.
- Getting alignment across product, design, and engineering before detailed work begins.

## What You Need From the User

- A description of the problem or opportunity.
- Evidence that it is real (research, data, user feedback), or an acknowledgement that validation is still needed.
- Initial thoughts on approach (optional; you can explore together).

---

## Process

### Step 1: Read Context Files

Before asking any questions, read the user's context files to understand what is already known.

| File | What to look for |
|---|---|
| `context/product.md` | Current product state, roadmap, existing capabilities. Is this already planned? |
| `context/personas.md` | Who experiences this problem? What do we know about their needs and pain? |
| `context/company.md` | Strategic priorities. Does this align? |
| `context/competitors.md` | Competitive landscape. Table stakes vs differentiator? |

Tell the user what you found. Reference personas by name rather than reproducing their full profiles: the reader can consult `context/personas.md` for detail.

If `context/personas.md` is empty or stale, tell the user and suggest using the Persona capability first: read `references/persona.md` and follow it.

### Step 2: Problem Clarification

With context in hand, ask only what is missing. Do not re-ask things already covered in context files.

**Must have (ask if missing):**

1. What problem or opportunity are you addressing?
2. Who experiences it? (Map to existing personas where possible.)

**Generate with stated assumptions if missing:**

3. What evidence exists that this is a real problem? (Data, research, user quotes, support tickets.)
4. Why is it important to solve now? (Strategic urgency, competitive pressure, user churn, enabling future work.)

### Step 3: Vision and Product Framing

This is the step that distinguishes a PRD from a feature brief. Before jumping to features, articulate:

- **What is this product/experience?** A one-paragraph statement of what the user will be able to do and why it matters.
- **How do the pieces fit together?** If there are multiple features or capabilities, describe the holistic experience: the whole should be greater than the sum of its parts.
- **What is the value proposition?** Not a marketing tagline but a clear statement of the value delivered, grounded in the problem and the personas.

Work with the user to get this right. The vision section anchors everything else in the PRD.

### Step 4: Key Features and Capabilities

Describe each feature or capability at a **high level**. The goal is stakeholder alignment and a shared mental model, not a detailed specification.

For each feature:
- What it does (one to two sentences).
- Why it matters (how it connects to the vision and the problem).
- How it relates to other features in the PRD (dependencies, complementary value, sequencing).

Do NOT include:
- Detailed user flows (push to the Feature Decomposition capability: `references/feature-breakdown.md`).
- Acceptance criteria (push to the User Stories capability: `references/user-stories.md`).
- Technical implementation details (push to technical spec if one exists).
- Wireframes or mockups (if a diagramming skill is installed, use it for flow diagrams that complement the PRD; otherwise describe the flows in text).

### Step 5: Success Criteria

Define what success looks like using **both** lagging and leading indicators.

**Lagging indicators (post-launch outcomes):**
- What user behaviour or business metric should change?
- How will it be measured?
- What is the target and over what timeframe?

**Leading indicators (pre-launch and early signals):**
- What early signals predict success before full adoption?
- Examples: activation rate in first week, qualitative feedback from beta users, task-completion rate in usability testing.

If actual baselines or targets are not available, mark them as `[PLACEHOLDER: need actual baseline from <source>]`. Do not invent numbers.

### Step 6: Dependencies

Identify what this work depends on and what depends on it.

| Category | What to capture |
|---|---|
| Feature dependencies | Other features or capabilities that must exist first. |
| Team dependencies | Other teams whose work this requires or blocks. |
| External dependencies | Third-party services, APIs, regulatory approvals, partnerships. |
| Data dependencies | Data sources, pipelines, or instrumentation needed. |

Flag the **critical path**: the dependencies that, if delayed, would delay the entire initiative.

### Step 7: Risk Assessment

Use the Value / Usability / Feasibility / Business Viability framework (Marty Cagan, Inspired/Empowered).

| Risk type | Question | How to validate |
|---|---|---|
| **Value** | Will users choose to use this? Will it solve their problem? | User interviews, prototype testing, demand signals. |
| **Usability** | Can users figure out how to use it? | Usability testing, design review, prototype walkthroughs. |
| **Feasibility** | Can engineering build it within acceptable time and cost? | Technical spike, architecture review, proof of concept. |
| **Business viability** | Does it work for the business? (Legal, financial, strategic.) | Stakeholder review, legal check, business case analysis. |

For each identified risk, note:
- Severity (High / Medium / Low).
- Current status (Validated / Assumed / Unknown).
- Proposed validation approach.

### Step 8: Generate the PRD

Assemble the document using the template below. Before finalising, apply the size guardrails (see below).

---

## PRD Template

```markdown
# [Product/Initiative Name]: PRD

| Field | Value |
|---|---|
| Status | Draft / In Review / Approved |
| Owner | [Name] |
| Last updated | [Date] |
| Target release | [Quarter or date] |

---

## Context

[Summary of relevant context drawn from context files. Reference personas by
name: do not reproduce full profiles. Link to context/personas.md,
context/product.md, context/competitors.md as appropriate.]

## Vision and Product Overview

[One to three paragraphs. What is this product or experience? What is the
holistic value proposition? How do the capabilities combine to deliver
something greater than the sum of its parts? Ground this in the problem
and the personas.]

## Problem

[Clear statement of the problem or opportunity. Who experiences it and how.
Reference personas by name.]

## Evidence

[What evidence supports this problem being real and worth solving?]

Mark each piece of evidence:
- **Validated**: backed by data, research, or direct user feedback.
- **Assumed**: believed to be true but not yet validated. Note the
  proposed validation approach.

## Key Features and Capabilities

[High-level description of each feature. For each one: what it does, why it
matters, how it connects to the vision and to other features. Show the
relationships between capabilities.]

[If this section grows beyond a few paragraphs per feature, push detail
downstream: see Size Guardrails.]

## Success Criteria

### Lagging Indicators
| Indicator | Metric | Target | Timeframe |
|---|---|---|---|
| [Outcome] | [How measured] | [Target or PLACEHOLDER] | [When] |

### Leading Indicators
| Signal | What it predicts | How measured |
|---|---|---|
| [Early signal] | [What it tells us] | [Measurement approach] |

## Non-Goals

[What is explicitly out of scope for this initiative and why. Be specific:
vague non-goals do not prevent scope creep.]

## Dependencies

| Category | Dependency | Owner | Status | Critical path? |
|---|---|---|---|---|
| Feature | [Description] | [Team/person] | [Status] | Yes/No |
| Team | [Description] | [Team/person] | [Status] | Yes/No |
| External | [Description] | [Provider] | [Status] | Yes/No |
| Data | [Description] | [Team/person] | [Status] | Yes/No |

## Risks

| Risk | Type | Severity | Status | Validation approach |
|---|---|---|---|---|
| [Description] | Value/Usability/Feasibility/Viability | H/M/L | Validated/Assumed/Unknown | [How to validate] |

## Open Questions

| # | Question | Owner | Validation approach | Status |
|---|---|---|---|---|
| 1 | [Question] | [Who will answer] | [How] | Open/Resolved |

## Sign-off Checklist

- [ ] Product owner has reviewed and approved the vision and scope.
- [ ] Engineering lead has reviewed feasibility and dependencies.
- [ ] Design lead has reviewed usability risks and user experience framing.
- [ ] Key stakeholders have reviewed and provided feedback.
- [ ] All "Assumed" evidence items have a validation plan.
- [ ] Success criteria have real baselines or are marked as PLACEHOLDER.
- [ ] Non-goals are specific enough to prevent scope creep.
- [ ] Open questions have owners and validation approaches.
```

---

## Size Guardrails

A PRD should stay around **300 lines or fewer**. If the document grows beyond this, it is a signal that detail is creeping in that belongs downstream.

**What to push downstream:**

| Content type | Where it goes | How |
|---|---|---|
| Detailed user flows and interaction sequences | Feature breakdown | Use the Feature Decomposition capability (`references/feature-breakdown.md`) to break features into buildable chunks. |
| Acceptance criteria and edge cases | User stories | Use the User Stories capability (`references/user-stories.md`) to generate sprint-ready backlog items. |
| Architecture decisions and technical constraints | Technical specification | Separate document owned by engineering. |
| Lengthy competitive analysis | `context/competitors.md` | Save the analysis as a context file and reference it in the PRD. |
| Flow diagrams and visual architecture | Diagrams | Use a diagramming skill if one is installed; otherwise describe the visuals in text. |

**What stays in the PRD:**

- Vision and product overview.
- Problem statement and evidence.
- Scope: high-level features and how they connect.
- Success criteria.
- Dependencies and critical path.
- Risks and open questions.
- Sign-off checklist.

**Context file management:** When a section grows large enough to be a reference document in its own right (e.g., a detailed competitive landscape), extract it to the appropriate context file and replace the inline content with a summary and a reference: "See `context/competitors.md` for the full analysis."

---

## Cross-References to Other Capabilities

| Capability | When to use | How to invoke |
|---|---|---|
| Feature Breakdown | Break PRD features into buildable, estimable chunks. | Read `references/feature-breakdown.md` and follow it. |
| User Stories | Generate sprint-ready backlog items with acceptance criteria from a feature breakdown. | Read `references/user-stories.md` and follow it. |
| Persona Development | Create or refresh personas before writing a PRD. | Read `references/persona.md` and follow it. |
| Deep Research | Conduct competitive analysis, market validation, or literature review to support PRD evidence. | Optional companion: use a deep-research skill if one is installed; otherwise research manually and cite sources. |
| Diagramming | Create architecture diagrams, user flow diagrams, or system maps that complement the PRD. | Optional companion: use a diagramming skill if one is installed; otherwise describe the diagram in text. |

**Typical workflow:** Personas (if needed), then PRD, then Feature Decomposition, then User Stories.

---

## Notes for the Agent

- Always read context files before asking questions. Do not ask the user to repeat information that is already documented.
- Reference personas by name. Do not reproduce persona profiles in the PRD: link to `context/personas.md`.
- When evidence is missing or weak, say so explicitly. Mark items as Assumed and note validation approaches. Do not fabricate data points.
- If the user provides a problem statement that maps to multiple features, frame the PRD as a product vision document, not a collection of independent feature specs.
- The PRD is a living document. Note in the Status field whether it is Draft, In Review, or Approved.
- When generating the PRD, apply size guardrails before presenting it to the user. If you notice it exceeding ~300 lines, proactively suggest pushing detail downstream and explain which capability to use.
