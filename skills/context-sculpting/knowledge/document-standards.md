# Context Document Standards

> **Purpose:** Defines all conventions for context documents—metadata, naming, structure, versioning.
>
> **Load when:** Creating or modifying any context document.

---

## File Naming Convention

**Pattern:** `{descriptive-name}.md`

Context documents use simple, descriptive lowercase names with hyphens:
- `company-brief.md`
- `customer-personas.md`
- `offerings-overview.md`
- `[product]-product-brief.md`

**Note:** Unlike artifacts (which include dates and versions in filenames like `IDEA-BRIEF-name-24DEC2025-v1.0.md`), context documents use simple names because they represent **current state**, not point-in-time snapshots.

---

## Storage Paths

```
context/
├── identity/       # company-brief.md, brand-voice.md, positioning.md
├── offerings/      # offerings-overview.md, [product]-product-brief.md
├── customers/      # customer-personas.md, journey-map.md
├── market/         # landscape.md, competitors.md
├── operations/     # operations-overview.md, processes.md
├── strategy/       # strategy-overview.md, goals.md
└── .archive/       # Deprecated documents (don't delete, archive)
```

---

## Document Structure

Every context document follows this structure:

```
┌─────────────────────────────────────┐
│  YAML Front Matter (machine-read)   │
├─────────────────────────────────────┤
│  Title (H1)                         │
├─────────────────────────────────────┤
│  Metadata Table (human-read)        │
├─────────────────────────────────────┤
│  Change History                     │
├─────────────────────────────────────┤
│  Purpose & When to Load (blockquote)│
├─────────────────────────────────────┤
│  Table of Contents (if needed)      │
├─────────────────────────────────────┤
│  Content Sections                   │
├─────────────────────────────────────┤
│  Open Questions                     │
├─────────────────────────────────────┤
│  See Also (cross-references)        │
└─────────────────────────────────────┘
```

---

## YAML Front Matter

Machine-readable metadata at the top of every document. Used by tooling and agents for document discovery and relationship mapping.

```yaml
---
domain: "customers"
type: "profile"
tags: ["personas", "buyers", "icp", "founders"]
related_documents:
  - "../identity/company-brief.md"
  - "../offerings/offerings-overview.md"
---
```

| Field | Required | Description |
|-------|----------|-------------|
| `domain` | Yes | Which domain: identity, offerings, customers, market, operations, strategy |
| `type` | Yes | Document type: profile, map, guide, catalog, playbook, signals, brief |
| `tags` | Yes | Keywords for discovery and search (3-8 tags) |
| `related_documents` | No | Documents that provide related context |

### Document Types

| Type | Purpose | Example |
|------|---------|---------|
| `brief` | Describes an entity comprehensively | company-brief.md, product-brief.md |
| `profile` | Describes people or segments | customer-personas.md |
| `catalog` | Lists things with descriptions | offerings-overview.md |
| `map` | Shows relationships or flows | journey-map.md |
| `guide` | How to do something | communication-guide.md |
| `playbook` | Repeatable process | campaign-playbook.md |
| `signals` | Indicators to watch | buying-signals.md |

---

## Metadata Table

Human-readable metadata displayed immediately after the H1 title.

```markdown
# Document Title

| Field | Value |
|-------|-------|
| **Type** | Customer Personas |
| **Version** | 1.2 |
| **Status** | Active |
| **Created** | [DATE] |
| **Modified** | [DATE] |
| **Author** | [Name] |
```

| Field | Description | Example Values |
|-------|-------------|----------------|
| **Type** | Human-readable document type | Company Brief, Customer Personas, Product Brief |
| **Version** | MAJOR.MINOR format | 1.0, 1.1, 2.0 |
| **Status** | Document lifecycle state | Draft, Active, Under Review, Deprecated |
| **Created** | Original creation date | DDMMMYYYY (e.g., 24DEC2025) |
| **Modified** | Last modification date | DDMMMYYYY |
| **Author** | Who created/owns the document | Name |

### Status Definitions

| Status | Meaning |
|--------|---------|
| **Draft** | Initial creation, not yet validated |
| **Template** | Blank template to be filled in |
| **Active** | Current, validated, ready for use |
| **Under Review** | Being updated or validated |
| **Deprecated** | No longer current; see superseding document |

---

## Change History

Required in all context documents. Place immediately after the metadata table.

```markdown
## Change History

| Version | Date | Author | Summary of Changes |
|---------|------|--------|-------------------|
| 1.0 | [DATE] | [Name] | Initial creation |
| 1.1 | [DATE] | [Name] | Added secondary persona |
| 1.2 | [DATE] | [Name] | Updated pain points from research |
```

---

## Version Control Rules

### Minor Increments (1.0 → 1.1)

Use for: Content additions, refinements, corrections, clarifications.

**Process:**
1. Make changes to the existing file
2. Update `Version` in metadata table
3. Update `Modified` date
4. Add entry to Change History with specific summary

### Major Increments (1.x → 2.0)

Use for: Significant restructuring, fundamental changes to content, complete rewrites.

**Process:**
1. Consider whether old version should be archived
2. Update version number
3. Update metadata
4. Add Change History entry explaining the major change

---

## Purpose & When to Load

Place as a blockquote after the Change History section.

```markdown
> **Purpose:** One sentence describing what this document provides.
>
> **When to load:** Comma-separated list of task types or situations.
```

**Example:**
```markdown
> **Purpose:** Define who buys and uses our products—their goals, pain points, and decision criteria.
>
> **When to load:** Marketing content, sales messaging, product decisions, feature prioritization
```

---

## Table of Contents

**Required when:**
- Document exceeds 150 lines, OR
- Document contains 8+ headers

**Format:**
```markdown
## Table of Contents

- [Section 1](#section-1)
  - [Subsection 1.1](#subsection-11)
- [Section 2](#section-2)
```

---

## Open Questions Section

**Required in all documents.** Tracks unresolved items needing follow-up.

```markdown
## Open Questions

*Items requiring follow-up or clarification.*

- [ ] Question or unknown item
- [ ] Another question
- [x] ~~Resolved question~~ → **Answer summary**
```

**Rules:**
1. Use checkboxes for tracking
2. When resolved, strike through and add answer summary
3. Also update `knowledge/context-architecture.md` if cross-cutting

---

## See Also Section

**Required in all documents.** Enables progressive disclosure.

```markdown
## See Also

- [Document Name](relative/path.md) - Brief description of what you'll find
- [Another Document](relative/path.md) - Brief description
```

**Example:**
```markdown
## See Also

- [Company Brief](../identity/company-brief.md) - Who we are
- [Offerings Overview](../offerings/offerings-overview.md) - What we sell
```

---

## Complete Template

```markdown
---
domain: "[domain]"
type: "[type]"
tags: ["tag1", "tag2", "tag3"]
related_documents:
  - "../folder/document.md"
---

# [Document Title]

| Field | Value |
|-------|-------|
| **Type** | [Human-readable type] |
| **Version** | 1.0 |
| **Status** | Draft |
| **Created** | [DATE] |
| **Modified** | [DATE] |
| **Author** | [Name] |

## Change History

| Version | Date | Author | Summary of Changes |
|---------|------|--------|-------------------|
| 1.0 | [DATE] | [Name] | Initial creation |

---

> **Purpose:** [One sentence on what this document provides]
>
> **When to load:** [Comma-separated list of task types]

---

## [Content Section 1]

[Content]

---

## [Content Section 2]

[Content]

---

## Open Questions

*Items requiring follow-up or clarification.*

- [ ] [Question]

---

## See Also

- [Related document](path) - [What you'll find there]
```

---

## Formatting Conventions

### Headers
- H1: Document title only (one per document)
- H2: Major sections
- H3: Subsections
- H4: Use sparingly for deep nesting

### Lists
- Use numbered lists (1, 2, 3) for ordered/prioritized items
- Use bullet points for unordered items
- Never use letters (a, b, c) for lists

### Tables
- Use tables for structured data
- Include header row
- Align columns for readability

### Emphasis
- **Bold** for key terms, field names, important callouts
- *Italics* for definitions, explanations, notes
- `Code` for paths, file names, technical terms

### Separators
- Use `---` between major sections for visual clarity
