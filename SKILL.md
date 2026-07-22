---
name: product-management
description: >
  Product management toolkit: PRDs, feature discovery and decomposition, user
  stories, prioritisation, roadmaps, and personas. TRIGGER when: the user is
  planning, scoping, or designing a new product, app, or tool with multiple
  features; discussing what to build, how it should work, or who it's for;
  exploring ideas for a complex project; figuring out features, capabilities,
  or requirements; writing PRDs, user stories, or acceptance criteria;
  prioritising what to build first; creating roadmaps or personas. Natural
  language triggers: "let's build [app/tool/product]", "I want to create...",
  "figure out the features", "what should this do", "how should this work",
  "plan this out", "scope this", "what do we need to build", "who is this for",
  "let's think through this", "I have an idea for...", "help me design this
  product", "what are the requirements", as well as PM-specific terms like
  "write a PRD", "decompose this feature", "user stories", "prioritise",
  "roadmap", "personas", "backlog", "sprint planning", "acceptance criteria",
  "MVP scope". DO NOT trigger for pure UI/UX visual design, pure technical
  architecture, or marketing copy.
---

# Product Management

This skill covers the full product management pipeline. It routes you to the
right reference based on what the user needs.

**Do not start generating anything until you have read the relevant reference.**


## Step 1: Assess what the user needs

Determine the capability required based on what the user has said and what
state the project is in. Check whether context files exist (`context/product.md`,
`context/personas.md`, etc.) to understand the current state.

| If the user wants to... | Capability | Reference to read |
|---|---|---|
| Explore a vague idea, identify what features exist in it | **Feature Discovery** | `references/feature-breakdown.md` |
| Write a PRD, define requirements, articulate the product vision | **PRD** | `references/prd.md` |
| Break a defined feature into epics, tasks, and dependencies | **Feature Decomposition** | `references/feature-breakdown.md` |
| Write sprint-ready user stories with acceptance criteria | **User Stories** | `references/user-stories.md` |
| Score and rank features or initiatives | **Prioritisation** | `references/prioritisation-roadmap.md` |
| Build a roadmap (Now/Next/Later, OKR-aligned, or timeline) | **Roadmap** | `references/prioritisation-roadmap.md` |
| Create or update user/buyer personas | **Personas** | `references/persona.md` |

Read **only** the reference file needed. Do not load all references at once.


## Step 2: Read the reference and follow its process

Each reference file contains the full process, output template, and
cross-references for that capability. Follow it directly.


## Step 3: Manage context files

This skill maintains a project-level `context/` directory. Each capability
reads from and writes to these files:

| File | Contains | Written by | Read by |
|---|---|---|---|
| `context/product.md` | Product overview, current state, known features | PRD, Roadmap | All capabilities |
| `context/personas.md` | Persona profiles | Persona capability | PRD, Feature Breakdown, Stories |
| `context/company.md` | Strategic priorities, team structure, capacity | User (manual) | PRD, Feature Breakdown, Persona, Prioritisation |
| `context/competitors.md` | Competitive landscape | PRD (or a deep-research skill, if installed) | PRD, Prioritisation, Roadmap |
| `context/goals.md` | OKRs, quarterly goals, success metrics | User (manual) | Prioritisation, Roadmap |
| `context/decisions.md` | Decision log | All capabilities | All capabilities |

When a context file does not exist and is needed, offer to create it. When a
capability produces output that belongs in a context file (e.g., persona
profiles → `context/personas.md`), save it there for future reference.


## Step 4: Maintain the decision log

Whenever a significant choice is made during any capability, log it in
`context/decisions.md`:

```markdown
## [Date]: [Context, e.g. "PRD: Meal Planner"]
**Decision:** [What was decided]
**Alternatives considered:** [What else was on the table]
**Rationale:** [Why this choice]
**Impact:** [What this changes downstream]
```

This captures: features considered but deferred (and why), scope changes,
prioritisation decisions, discovery outputs (all features identified, which
were taken forward). It is a lightweight log, not version control.


## The product pipeline

These capabilities chain naturally. Each one's output feeds the next:

```
Feature Discovery → PRD → Prioritisation/Roadmap → Feature Decomposition → User Stories
```

But each capability also works independently. You can write stories without a
PRD, prioritise without a roadmap, or discover features without decomposing
them. The pipeline is a guide, not a constraint.

At any stage, optional companion skills can support the work. They are not
part of this skill; use them only if they are installed, and otherwise
produce the equivalent in text:
- A diagramming skill: concept maps (discovery), architecture diagrams (PRD),
  dependency graphs (decomposition), roadmap visualisations. If none is
  installed, describe the diagram in text or ASCII.
- A mood-board skill: visual direction during early exploration.
- The Persona capability in this skill produces context a diagramming skill
  can use for journey maps.
- A deep-research skill: competitive analysis, market validation, buyer
  behaviour research. If none is installed, research manually and cite
  sources.
