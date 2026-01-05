---
name: context-sculpting
description:
  Maintain and curate the business context system for LLM-assisted operations.
  Use when updating context documents, interviewing for new information, auditing
  context health, or integrating new insights across the context architecture.
  Ensures coherent institutional knowledge across all context files.
purpose: Sculpt and maintain coherent business context for LLM operations
tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
model: inherit
---

# Context Sculpting Skill

## Overview

The Context Sculpting skill maintains the business context system—a composable set of documents that provide LLMs with the information needed to perform tasks well. This skill ensures coherent, high-quality institutional knowledge across all context files.

### Why This Skill Exists

LLMs produce expert-quality work when given sufficient context. Without context, they produce generic output. This skill solves the maintenance problem: **how do we keep context accurate, coherent, and well-organized as the business evolves?**

### Core Principles

1. **One source of truth** - Each fact lives in exactly one place; cross-reference, don't duplicate
2. **Progressive disclosure** - Overview documents link to detail documents for depth
3. **Coherence across files** - Changes in one document may require updates in related documents
4. **Open questions captured** - Unknown items are explicitly tracked, not glossed over
5. **Architecture awareness** - Every change must consider the broader context structure
6. **Agent continuity** - Any agent without prior history can understand and maintain the system

### Capabilities

- Update context documents with new information from interviews or research
- Maintain cross-links and relationships between documents
- Track open questions requiring follow-up
- Audit context health and identify gaps or inconsistencies
- Integrate new insights across multiple related documents
- Keep the architecture mapping current with any structural changes

---

## Critical Knowledge Files

**ALWAYS load these files before ANY context operation:**

| File | Purpose | Load When |
|------|---------|-----------|
| `knowledge/context-architecture.md` | **REQUIRED** - Complete map of all context files, their purposes, and relationships | EVERY operation |
| `knowledge/document-standards.md` | Metadata, naming, and structural conventions | Creating or modifying documents |
| `knowledge/cross-linking-guide.md` | How to create and maintain links between documents | Any multi-document operation |
| `knowledge/integration-patterns.md` | How to decide where information belongs and how to integrate across files | Adding new information |

---

## Workflows

This skill has three workflows. Load the appropriate workflow based on intent.

### workflow/update-context.md

**Purpose:** Add new information to the context system from any source (interview, research, observation).

**Load when:**
- New information needs to be captured in context
- User provides updates to business information
- Research or discovery produces insights to integrate
- Corrections or refinements to existing context

**Triggers (examples):**
- "Update the company brief with..."
- "Add this to our context"
- "Our target customer has changed"
- "Record this decision"

**Required dependencies - load BEFORE executing:**
- `knowledge/context-architecture.md` - To identify affected documents
- `knowledge/document-standards.md` - For formatting
- `knowledge/integration-patterns.md` - For multi-document updates
- `knowledge/cross-linking-guide.md` - For relationship maintenance

---

### workflow/interview-elicit.md

**Purpose:** Conduct structured interviews to extract business context from stakeholders.

**Load when:**
- Gathering initial context for a new domain
- Filling gaps identified in existing context
- Validating or updating stale information
- User initiates context-building conversation

**Triggers (examples):**
- "Let's fill out the company brief"
- "Interview me about our customers"
- "Help me document our values"
- "I want to capture context about..."

**Required dependencies - load BEFORE executing:**
- `knowledge/context-architecture.md` - To identify target documents
- `knowledge/document-standards.md` - For output formatting
- Target document(s) to populate - To see existing content and open questions

---

### workflow/audit-context.md

**Purpose:** Review context health—identify gaps, stale information, broken links, or inconsistencies.

**Load when:**
- Periodic maintenance review
- Before major business decisions
- After significant business changes
- User requests context health check

**Triggers (examples):**
- "Audit the context system"
- "What's missing from our context?"
- "Review context health"
- "Check for stale information"

**Required dependencies - load BEFORE executing:**
- `knowledge/context-architecture.md` - As the source of truth for expected structure

---

## Knowledge

### knowledge/context-architecture.md

**Purpose:** The master map of the entire context system. Documents all folders, files, their purposes, relationships, and the overall architecture.

**CRITICAL:** This file MUST be updated whenever:
- A new context document is created
- A context document is renamed, moved, or deleted
- The folder structure changes
- Relationships between documents change

**Contains:**
- Complete folder structure with descriptions
- Every document with its purpose and key contents
- Relationship map showing how documents connect
- Domain summaries (identity, offerings, customers, market, operations, strategy)

---

### knowledge/document-standards.md

**Purpose:** Defines all conventions for context documents—metadata, naming, structure, versioning.

**Load when:** ANY operation that creates or modifies documents

**Contains:**
- File naming conventions (simple names for context docs, dated names for artifacts)
- YAML front matter specification
- Metadata table format
- Document structure template
- Version increment rules
- Change history requirements
- Open Questions section format

---

### knowledge/cross-linking-guide.md

**Purpose:** How to create and maintain links between context documents for progressive disclosure.

**Load when:** Any operation that touches multiple documents or creates new documents

**Contains:**
- Link syntax and formatting
- "See Also" section structure
- When to link vs. when to duplicate
- Bidirectional linking patterns
- Link maintenance on document changes

---

### knowledge/integration-patterns.md

**Purpose:** Decision framework for where information belongs and how to integrate across files.

**Load when:** Adding new information that might affect multiple documents

**Contains:**
- Information placement decision tree
- Primary vs. secondary location rules
- When to update vs. when to link
- Coherence checking process
- Open questions propagation

---

## Tools

| Tool | Purpose | When Used |
|------|---------|-----------|
| `Read` | Load context documents | All workflows |
| `Write` | Create new context documents | New document creation |
| `Edit` | Modify existing documents | Updates, corrections |
| `Glob` | Discover all context files | Audit workflow, architecture sync |
| `Grep` | Search across context | Finding related content, checking consistency |

---

## The Context Architecture

The context system uses six core domains:

```
context/
├── identity/       # Who we are (mission, values, voice)
├── offerings/      # What we sell (products, pricing, value props)
├── customers/      # Who we serve (personas, journey, signals)
├── market/         # Where we compete (landscape, competitors)
├── operations/     # How we work (team, processes, tools)
└── strategy/       # Where we're going (goals, initiatives, risks)
```

**See `knowledge/context-architecture.md` for the complete current state.**

---

## Execution Rules

**These rules are mandatory. Deviations will cause coherence failures.**

### Before ANY Context Operation

1. **Load `knowledge/context-architecture.md` FIRST** - You must understand the current state
2. **Identify ALL affected documents** - Changes often ripple across multiple files
3. **Load required workflow** - Don't improvise; follow the documented process
4. **Load all workflow dependencies** - As listed in the workflow section above

### During Execution

1. **Follow the workflow steps in order** - No skipping, no optimization
2. **Update ALL affected documents** - Don't leave related documents inconsistent
3. **Maintain cross-links** - Add links to new content; update links if content moves
4. **Capture open questions** - Unknown items go in the Open Questions section
5. **Update the architecture map** - If structure changes, update `context-architecture.md`
6. **Use the document standards** - Correct metadata, versioning, formatting

### Information Placement Rules

1. **Facts live in ONE place** - Choose the primary document; link from secondary locations
2. **Overview before detail** - Brief mentions in overview docs; full detail in specialized docs
3. **Domain determines home** - Information goes in its natural domain first
4. **Cross-link for discovery** - Related content should be findable via links

### Quality Standards

1. **No orphan documents** - Every document must be linked from at least one other document
2. **No broken links** - All links must point to existing documents
3. **No stale Open Questions** - Regularly review and resolve or update open questions
4. **Consistent voice** - Match the established voice/tone across documents

### If Uncertain

- Re-read the relevant workflow and knowledge files
- Check `context-architecture.md` for guidance on where things belong
- Ask the user for clarification using numbered response options
- Do NOT improvise document structure or placement

---

## Integration with Primary Agent

This skill should be invoked proactively during conversations:

| Situation | Action |
|-----------|--------|
| User shares business information | Consider if it should update context |
| Strategic decisions are made | Record in relevant context documents |
| New insights from research | Integrate into context via update workflow |
| User asks about the business | Load relevant context; note if gaps exist |
| Periodic check-ins | Suggest context audit if not done recently |

**The goal is continuous improvement of institutional knowledge quality.**

---

## Anti-Patterns

| Wrong | Right |
|-------|-------|
| Duplicate information across files | Single source of truth + cross-links |
| Update one doc, leave related docs stale | Update all affected documents |
| Add new doc without architecture update | Always update `context-architecture.md` |
| Gloss over unknowns | Capture in Open Questions section |
| Improvise document structure | Follow document standards exactly |
| Skip loading knowledge files | Always load required dependencies first |

---

## Failure Modes

If these occur, stop and correct:

1. **Architecture drift** - Actual files don't match `context-architecture.md` → Run audit workflow
2. **Broken links** - Links point to non-existent documents → Fix links or restore documents
3. **Inconsistent information** - Same fact differs across documents → Identify source of truth, correct others
4. **Orphan documents** - Files exist but aren't linked from anywhere → Add links or archive
5. **Stale open questions** - Questions unchanged for extended periods → Review and resolve

**FAILURE TO FOLLOW THESE RULES WILL DEGRADE CONTEXT QUALITY.**
