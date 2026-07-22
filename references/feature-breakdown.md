# Feature Breakdown

This reference file supports two modes of work: **Discovery** and **Decomposition**. The orchestrator SKILL.md loads this file when the user needs to identify features or break a feature into shippable pieces.

Read this file top to bottom. Determine which mode applies based on what the user has brought you. If unclear, ask.

---

## Cross-References

| Direction | Detail |
|---|---|
| **Upstream** | Takes PRD output as input for Decomposition mode. Takes vague ideas, problem spaces, or exploratory briefs as input for Discovery mode. |
| **Downstream** | Discovery outputs feed PRD or Decomposition. Decomposition story outlines feed `references/user-stories.md` for full story writing. |
| **Visual** | If a diagramming skill is installed, use it for concept maps (Discovery) and dependency graphs (Decomposition); otherwise describe them in text or ASCII. |
| **Personas** | References `context/personas.md` throughout. If that file is empty or missing, advise the user to use the Persona capability first (`references/persona.md`). |

---

## Mode 1: Discovery

### When to use

The user arrives with a vague idea, a problem space, or simply wants to think aloud. They do not yet have a well-defined feature. Your job is to listen, identify the distinct capabilities hiding inside what they describe, and help them decide which to pursue.

### Process

#### Step 1: Check context

Read `context/product.md`, `context/personas.md`, and `context/company.md`. Tell the user what you found and how it relates to what they are describing. If any file is missing or empty, note it explicitly: do not silently skip it.

#### Step 2: Listen and clarify

Let the user describe the idea in their own words. Ask clarifying questions if the problem space is ambiguous. Do not rush to structure things. Understand:

- What problem or opportunity they see.
- Who it affects (map to personas if possible).
- What success would look like, even loosely.
- Any constraints they already know about.

#### Step 3: Identify features

From the description, extract distinct features or capabilities. For each one:

- **Name**: a short, memorable label (2-4 words).
- **One-line description**: what it does and why it matters.
- **Relationship to other identified features**: does it depend on, enable, or complement another?
- **Prerequisite status**: flag anything that feels like a foundation other features rely on.

#### Step 4: Recommend a path forward

Based on prerequisites, user value, and feasibility signals, recommend which features to take forward first. Each selected feature becomes a candidate for PRD work or can proceed directly into Decomposition mode.

If the landscape is complex (more than five features, or tangled dependencies), produce a concept map of the feature landscape with a diagramming skill if one is installed; otherwise sketch it in ASCII.

### Output Template: Discovery

```
## Feature Discovery: [Topic / Problem Space]

**Date:** [date]
**Context loaded:** [list which context files were read and key takeaways]

### Problem Space

[1-2 paragraph summary of what the user described and the core problem or opportunity.]

### Identified Features

| # | Feature Name | Description | Depends On | Prerequisite For |
|---|---|---|---|---|
| 1 | [Name] | [One-line description] | None | 2, 3 |
| 2 | [Name] | [One-line description] | 1 | 4 |
| ... | ... | ... | ... | ... |

### Relationships

[Prose explanation of how the features relate, which clusters emerge, where the natural boundaries are, what the dependency chains look like.]

### Recommendation

**Start with:** [Feature name(s)]: [reason]
**Defer:** [Feature name(s)]: [reason]
**Investigate further:** [Feature name(s)]: [what needs answering before committing]

### Next Steps

- [ ] Write PRD for [feature] → use the PRD capability (`references/prd.md`)
- [ ] Decompose [feature] → use Decomposition mode in this reference
- [ ] Map feature landscape visually → use a diagramming skill, if one is installed
```

---

## Mode 2: Decomposition

### When to use

The user arrives with a defined feature: possibly output from a PRD, possibly from Discovery mode, possibly brought directly. The feature is understood well enough to break into buildable pieces. Your job is to produce a full decomposition: epics, stories, dependencies, parallelisation plan, and ship milestones.

### Process

#### Step 1: Check context

Read `context/product.md`, `context/personas.md`, and `context/company.md`. Tell the user what you found. If a PRD exists for this feature, read that too.

#### Step 2: Gather feature details

If you do not have enough context to decompose the feature confidently, ask. Do NOT decompose a feature you do not understand. You need to know:

- The core problem it solves.
- Who it serves (specific personas).
- What "done" looks like.
- Known constraints (technical, regulatory, timeline, team capacity).

#### Step 3: Define MVP scope

Produce three lists:

- **In scope (MVP):** The minimum set of capabilities needed to solve the core problem. Be ruthless: if it is not essential to the first usable version, it does not belong here.
- **Out of scope (Future):** Capabilities that add clear value but are not required for the initial release. These become future epics or features.
- **Non-goals:** Things this feature is explicitly not trying to do. Write these down to prevent scope creep and alignment disputes later.

#### Step 4: Identify epics (3-7)

Break the MVP scope into 3-7 epics. Each epic should:

- Be completable in 1-2 sprints.
- Have clear boundaries: you can explain where one ends and the next begins.
- Deliver user value on its own or form a necessary foundation for something that does.
- Have a name and a one-paragraph description.

#### Step 5: Decompose into stories

For each epic, produce stories that are:

- **1-3 days of work each.** If it feels bigger, split it.
- **Independently testable.** You can verify the story works without completing the rest of the epic.
- **Clear on acceptance criteria.** Someone could read the story and know whether it passes or fails.
- **Estimable.** The team can give it a point estimate without needing extensive investigation.

Use the story table format shown in the output template below.

#### Step 6: Map dependencies

Answer these questions:

- Which stories block other stories?
- Which epics must complete before others can begin?
- Are there external dependencies (other teams, third-party services, data migrations, approvals)?

Produce a dependency graph. ASCII format is fine; for complex graphs, use a diagramming skill if one is installed.

#### Step 7: Plan parallelisation

Identify:

- Which stories have no dependencies and can start immediately.
- Where frontend and backend work can proceed in parallel.
- What can be stubbed or mocked to unblock downstream work.
- Where multiple developers can work simultaneously without stepping on each other.

#### Step 8: Define ship milestones

Map the work to progressive release stages:

- **Alpha:** Internal only. Core flow works end-to-end, rough edges acceptable.
- **Beta:** Limited external users. Feature-complete for MVP scope, known issues documented.
- **GA (General Availability):** Full rollout. Polished, monitored, documented.

For each milestone, state which epics and stories must be complete.

### Output Template: Decomposition

```
## Feature Decomposition: [Feature Name]

**Date:** [date]
**Source:** [PRD title/link, or "Discovery output", or "Direct request"]
**Context loaded:** [list which context files were read and key takeaways]

---

### Scope Definition

**In Scope (MVP)**
- [Capability 1]
- [Capability 2]
- ...

**Out of Scope (Future)**
- [Capability]: [why deferred]
- ...

**Non-Goals**
- [Thing we are explicitly not doing]: [why]
- ...

---

### Epic Breakdown

#### Epic 1: [Epic Name]

[One-paragraph description of what this epic delivers and why it matters.]

| Story ID | Story | Points | Owner | Dependencies |
|---|---|---|---|---|
| E1-S1 | [Story title] | [pts] | [role/name] | None |
| E1-S2 | [Story title] | [pts] | [role/name] | E1-S1 |
| E1-S3 | [Story title] | [pts] | [role/name] | None |

#### Epic 2: [Epic Name]

[One-paragraph description.]

| Story ID | Story | Points | Owner | Dependencies |
|---|---|---|---|---|
| E2-S1 | [Story title] | [pts] | [role/name] | E1-S2 |
| ... | ... | ... | ... | ... |

[Repeat for all epics.]

---

### Dependency Graph

```
E1-S1 ──► E1-S2 ──► E2-S1 ──► E3-S1
                         │
E1-S3 ─────────────────►│
                         ▼
                      E2-S2 ──► E3-S2
```

[Prose summary of the critical path and where bottlenecks sit.]

---

### Parallelisation Plan

| Sprint / Phase | Stream A (e.g. Backend) | Stream B (e.g. Frontend) | Stream C (e.g. Data) |
|---|---|---|---|
| Phase 1 | E1-S1, E1-S3 | E1-S2 (stub backend) | None |
| Phase 2 | E2-S1 | E2-S2 | E2-S3 |
| ... | ... | ... | ... |

[Notes on stubbing, mocking, or interface contracts needed to enable parallel work.]

---

### Ship Milestones

| Milestone | Epics Complete | Stories Complete | What Users Get |
|---|---|---|---|
| Alpha | Epic 1 | E1-S1 through E1-S3 | [Description of state] |
| Beta | Epics 1-2 | All of above + E2-S1 through E2-Sn | [Description of state] |
| GA | All | All | [Description of state] |

---

### Risks and Mitigations

| Risk | Impact | Likelihood | Mitigation |
|---|---|---|---|
| [Risk description] | High / Medium / Low | High / Medium / Low | [What to do about it] |
| ... | ... | ... | ... |

---

### Open Questions

- [ ] [Question that needs answering before work begins or during early sprints]
- [ ] ...

---

### Summary

| Metric | Value |
|---|---|
| Total epics | [n] |
| Total stories | [n] |
| Total points | [n] |
| Estimated sprints | [n] |
| Critical path length | [n stories / n sprints] |
| Parallel streams | [n] |
```

---

## Choosing Between Modes

If the user's intent is ambiguous, use these heuristics:

| Signal | Mode |
|---|---|
| "I have an idea for..." / "What if we..." / "I'm thinking about..." | Discovery |
| "Break down [feature]" / "Decompose this" / "Plan the build for..." | Decomposition |

When in doubt, ask: "It sounds like you're at the [Discovery / Decomposition] stage: is that right?"

Modes chain naturally. Discovery produces feature candidates. Decomposition takes a feature and produces epics and story outlines. Once story outlines exist, hand off to `references/user-stories.md` to flesh them into sprint-ready items. Offer to continue into the next stage when the current one completes.


## Decision Logging

After completing any mode, log significant decisions to `context/decisions.md`:

- **Discovery:** which features were identified, which were taken forward vs deferred, and why.
- **Decomposition:** scope decisions (what went into MVP vs future), dependency trade-offs, sequencing choices.

This creates a trail that makes future iterations faster: you can see what was already considered and why.
