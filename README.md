# product-management-skills

**A product-management operating system for AI assistants: PRDs, feature
discovery, user stories, prioritisation, roadmaps and personas, built as
composable skills that work together rather than six disconnected
templates.**

PM templates are everywhere. What they don't give you is a system an AI
can actually *drive*: one entry point that recognises what stage of
product work you're in, routes to the right method, keeps shared context
files so each artefact builds on the last, and maintains a decision log
so the "why" survives the conversation it happened in. That integration
is the point of this repo.

## What's inside

| File | Covers |
|---|---|
| [SKILL.md](SKILL.md) | The orchestrator: intent → method routing, the shared `context/` file convention, the decision log, the pipeline between artefacts |
| [references/prd.md](references/prd.md) | Writing PRDs: vision, requirements, competitive landscape, context management |
| [references/feature-breakdown.md](references/feature-breakdown.md) | Feature discovery and decomposition into epics, tasks, dependencies and delivery streams |
| [references/user-stories.md](references/user-stories.md) | Sprint-ready user stories with acceptance criteria |
| [references/prioritisation-roadmap.md](references/prioritisation-roadmap.md) | Scoring frameworks (RICE, weighted), Now/Next/Later, OKR and timeline roadmaps |
| [references/persona.md](references/persona.md) | User and buyer personas with validation status and buying-process mapping |

The artefacts chain deliberately: personas and feature discovery feed the
PRD, the PRD feeds prioritisation and the roadmap, prioritised work is
decomposed into epics, and the decomposition feeds user stories. And the
orchestrator knows the chain, so "help me plan this product" walks the
whole path instead of producing one orphaned document.

## Use it

Built for Claude Code's skill format (see Anthropic's
[Agent Skills documentation](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview));
works with any assistant that can follow a routed instruction set.

```bash
git clone https://github.com/haniabdemai/product-management-skills
cp -r product-management-skills ~/.claude/skills/product-management
```

The destination folder must be named `product-management` so that it
matches the `name` field in SKILL.md's frontmatter.

Then just talk product. Say "I want to build X", "scope this", "write the
PRD", or "what should we build first", and the orchestrator routes.

## Licence

[MIT](LICENSE)
