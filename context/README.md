# Context System

A composable system of context artifacts for AI-assisted operations.

## Purpose

This folder contains structured business context that AI agents can load to perform tasks with precision. Instead of re-explaining your business every conversation, agents load the relevant context files and operate with full knowledge.

## Folder Structure

```
context/
├── identity/       # Who we are (mission, values, voice)
├── offerings/      # What we sell (products, pricing)
├── customers/      # Who we serve (personas, journey)
├── market/         # Where we compete (landscape, competitors)
├── operations/     # How we work (team, processes)
├── strategy/       # Where we're going (goals, initiatives)
└── .archive/       # Deprecated documents
```

## How to Use

### Loading Context

Before any task, load the relevant context files:

```
Load these context files:
- context/identity/company-brief.md
- context/customers/customer-personas.md

Then [your task].
```

### Common Combinations

| Task | Load These |
|------|------------|
| Marketing copy | identity + customers + offerings |
| Product decisions | customers + offerings + strategy |
| Competitive response | market + offerings + identity |
| Sales messaging | customers + offerings |

## Document Structure

Every context document includes:

1. **YAML front matter** - Machine-readable metadata
2. **Metadata table** - Human-readable summary
3. **Change history** - Version tracking
4. **Purpose & when to load** - Usage guidance
5. **Content sections** - The actual context
6. **Open questions** - Unresolved items
7. **See also** - Cross-references

## Maintenance

Use the Context Sculpting skill to:
- Update documents after conversations
- Run audits to catch inconsistencies
- Interview to fill in gaps

See: `../skills/context-sculpting/SKILL.md`
