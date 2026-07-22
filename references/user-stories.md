# User Stories

Turn features into sprint-ready stories that are Independent, Negotiable, Valuable, Estimable, Small, and Testable.

## Cross-References

| Direction | Detail |
|---|---|
| **Upstream** | Takes feature or epic as input: from Decomposition output (`references/feature-breakdown.md`), a PRD, or a direct request. |
| **Downstream** | Stories feed sprint planning and backlog grooming. |
| **Personas** | References `context/personas.md` throughout. If that file is empty or missing, advise the user to use the Persona capability first (`references/persona.md`). |
| **Visual** | If a diagramming skill is installed, use it for user flow diagrams that support story writing; otherwise describe the flows in text. |

## Output

Save to `context/user-stories-[feature]-[YYYY-MM-DD].md`

---

## When to Use

- Writing stories during backlog grooming
- Translating PRD requirements into sprint-ready stories
- Fleshing out story outlines from a feature decomposition
- The user says "write user stories", "user stories for this", "I need backlog items", "make this sprint-ready", "acceptance criteria for..."

---

## Process

### Step 1: Check context

Read `context/personas.md` and `context/product.md`. You need specific personas to write proper user stories.

Tell the user what you found so they know what you are working with. For example:

> "I found your Jordan persona (PM) in personas.md. Their main frustration is 'spending 5+ hours/week updating spreadsheets.' I'll write the user story from Jordan's perspective."

If personas are missing, tell the user explicitly and advise using the Persona capability first (read `references/persona.md` and follow it). Do not silently skip this: personas are essential for well-written stories.

### Step 2: Understand the scope

Confirm what feature or epic the stories are for.

- If coming from Decomposition mode, you already have story outlines: now you are fleshing them out with full acceptance criteria, edge cases, and technical notes.
- If coming fresh, identify the stories first. Ask:

> "I need to understand the capability before writing stories:
> 1. What feature or capability are we writing stories for?
> 2. Which persona is this for? (I found [X] in your personas.md)
> 3. What's the user trying to accomplish?
>
> Or point me to a PRD or decomposition output if you have one."

### Step 3: Write each story

For each story, produce the full template shown below. Every story must include:

**The story itself**, in standard format:

> As a [persona from `context/personas.md`],
> I want to [action or capability],
> So that [benefit or outcome: connect to persona goals/frustrations].

**INVEST validation.** Check the story against all six criteria:

- **Independent:** Can this story be delivered without completing other stories first? If not, note the dependency explicitly.
- **Negotiable:** Are the implementation details flexible, or is the story over-specified? The story should describe *what* and *why*, not *how*.
- **Valuable:** Does this deliver something the user or business cares about? If it is purely technical, reframe it in terms of the value it enables.
- **Estimable:** Can the team give this a point estimate? If not, it needs a spike first.
- **Small:** Does this fit in a sprint? If it feels like more than 3 days of work, split it.
- **Testable:** Can someone write a test (manual or automated) that definitively passes or fails? If not, the acceptance criteria need tightening.

**Acceptance criteria** in BDD format (Given/When/Then). Include at minimum:

- One happy-path scenario.
- One alternate-path scenario (valid but non-default behaviour).
- One error-state scenario.

**Edge cases**: things that could go wrong or behave unexpectedly. Think about:

- Empty states, null values, missing data.
- Boundary conditions (max lengths, zero quantities, concurrent access).
- Permission and access control.
- Performance under load.
- Internationalisation and localisation.

**Technical notes**: anything the engineering team needs to know that is not captured in the acceptance criteria. Integration points, API contracts, data model changes, migration needs, performance requirements.

**Out of scope**: what this story explicitly does not cover, to prevent scope creep during implementation.

### Step 4: Review the set

Once all stories are written, review them as a set:

- Do they cover the full scope of the feature or epic?
- Are there gaps: user flows that no story addresses?
- Are there overlaps: two stories that cover the same ground?
- Is the ordering sensible given dependencies?

---

## Output Template

```markdown
## User Stories: [Feature or Epic Name]

**Date:** [date]
**Source:** [Decomposition output, PRD, or direct request]
**Personas referenced:** [list persona names from context/personas.md]

---

### Story [ID]: [Story Title]

**Context**
- **Persona:** [Name]: [one-line persona summary]
- **Job to be done:** [the underlying need this story serves]
- **Related feature/epic:** [name and ID if applicable]

**Story**

> As a [persona name],
> I want to [action],
> So that [outcome].

**INVEST Checklist**

| Criterion | Pass? | Notes |
|---|---|---|
| Independent | Yes / No | [If No, state dependency] |
| Negotiable | Yes / No | [Notes] |
| Valuable | Yes / No | [What value it delivers] |
| Estimable | Yes / No | [If No, what needs clarifying] |
| Small | Yes / No | [Estimated effort] |
| Testable | Yes / No | [How it would be tested] |

**Acceptance Criteria**

*Happy path:*

> Given [precondition],
> When [action],
> Then [expected outcome].

*Alternate path:*

> Given [different precondition],
> When [action],
> Then [different expected outcome].

*Error state:*

> Given [precondition leading to failure],
> When [action],
> Then [error handling behaviour].

**Edge Cases**

- [Edge case 1: description and expected behaviour]
- [Edge case 2: description and expected behaviour]
- ...

**Technical Notes**

- [Note 1]
- [Note 2]
- ...

**Out of Scope**

- [Thing this story does not cover]
- ...

**Related Context**

- Persona detail: `context/personas.md`
- Product context: `context/product.md`
- [Any other relevant references]

---

[Repeat for each story.]

---

### Story Set Review

| Check | Result |
|---|---|
| Full scope covered? | [Yes / No: note gaps] |
| Overlaps between stories? | [Yes / No: note overlaps] |
| Dependencies clear? | [Yes / No: note issues] |
| All stories INVEST-valid? | [Yes / No: note failures] |
| Estimated total points | [n] |
```

---

## Tips for Best Results

1. **Use your personas**: stories written from a real persona's perspective with their language are far more useful than generic "As a user" stories.
2. **Connect to JTBD**: the "So that" clause should link directly to persona goals or frustrations, not restate the action.
3. **Be specific on edge cases**: these often become bugs later if not captured upfront.
4. **Keep stories small**: if it cannot be done in a sprint, decompose it further. Use the Decomposition capability in `references/feature-breakdown.md` if needed.

---

## Decision Logging

After writing stories, log significant decisions to `context/decisions.md`:

- Scope or acceptance criteria debates that resolved in a particular direction.
- Stories that were considered but deferred, and why.
- Assumptions made about user behaviour or technical constraints.
