# Context Architecture Map

> **This file is the single source of truth for the context system structure.**
>
> **CRITICAL:** Update this file whenever the context structure changes—new files, renames, moves, deletions, or relationship changes.

---

## Last Updated

| Date | Author | Change |
|------|--------|--------|
| [DATE] | [Name] | Initial architecture map creation |

---

## Overview

The context system provides LLMs with business information needed for task execution. It follows a domain-based architecture with six core domains, each containing documents at varying levels of detail.

**Location:** `context/`

**Design principles:**
- One source of truth per fact
- Progressive disclosure via cross-links
- Open questions explicitly tracked
- Architecture map always current

---

## Folder Structure

```
context/
├── identity/                       # Who we are
│   └── company-brief.md            # Mission, values, origin, voice
├── offerings/                      # What we sell
│   └── offerings-overview.md       # Summary of all products/services
├── customers/                      # Who we serve
│   └── customer-personas.md        # Target users, goals, pain points
├── market/                         # Where we compete
│   └── (to be populated)           # Competitors, landscape
├── operations/                     # How we work
│   └── (to be populated)           # Team, processes
├── strategy/                       # Where we're going
│   └── (to be populated)           # Goals, initiatives
├── README.md                       # System design documentation
└── .archive/                       # Deprecated documents
```

---

## Domain Summaries

### Identity (`/identity/`)

**Purpose:** Establish who we are, what we stand for, how we communicate.

**Core question:** If an LLM had to represent us authentically, what would it need to know?

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| `company-brief.md` | brief | Template | Company overview, mission, values, voice |

**Planned documents:** brand-voice.md, messaging-framework.md (as needed)

---

### Offerings (`/offerings/`)

**Purpose:** Define what we sell, the value it provides, and how it's structured.

**Core question:** What would an LLM need to accurately describe and sell what we offer?

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| `offerings-overview.md` | catalog | Template | Summary of all offerings, pricing |

**Planned documents:** [product]-product-brief.md (for each major product)

---

### Customers (`/customers/`)

**Purpose:** Understand who buys, why they buy, and how to reach them.

**Core question:** What would an LLM need to identify, engage, and serve customers effectively?

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| `customer-personas.md` | profile | Template | Target users, goals, pain points, objections |

**Planned documents:** journey-map.md, communication-guide.md (as needed)

---

### Market (`/market/`)

**Purpose:** Understand the competitive landscape and where we fit.

**Core question:** What would an LLM need to position us accurately and respond to competitive situations?

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| (none yet) | — | — | — |

**Planned documents:** market-overview.md, competitors.md

---

### Operations (`/operations/`)

**Purpose:** Understand how work gets done—teams, processes, tools.

**Core question:** What would an LLM need to help with operational tasks and understand constraints?

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| (none yet) | — | — | — |

**Planned documents:** operations-overview.md, team.md, processes.md

---

### Strategy (`/strategy/`)

**Purpose:** Understand where we're going and what we're prioritizing.

**Core question:** What would an LLM need to align its work with company direction?

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| (none yet) | — | — | — |

**Planned documents:** strategy-overview.md, goals.md, initiatives.md

---

## Document Relationship Map

```
IDENTITY DOMAIN
───────────────
company-brief.md [PRIMARY IDENTITY DOCUMENT]
├── Links to: offerings-overview.md, customer-personas.md
├── Contains: Mission, values, voice, core narrative
└── Foundation for all other documents

OFFERINGS DOMAIN
────────────────
offerings-overview.md
├── Links to: company-brief.md, customer-personas.md
├── Contains: Product/service summary, pricing
└── Links to product-specific briefs (when created)

CUSTOMERS DOMAIN
────────────────
customer-personas.md
├── Links to: company-brief.md, offerings-overview.md
├── Contains: Target users, goals, pain points, objections
└── Foundation for marketing and product decisions
```

---

## Cross-Reference Index

Find documents by topic:

| Topic | Primary Document | Also Mentioned In |
|-------|------------------|-------------------|
| **Mission** | company-brief.md | — |
| **Values** | company-brief.md | — |
| **Voice/Tone** | company-brief.md | — |
| **Products/Services** | offerings-overview.md | company-brief.md (summary) |
| **Pricing** | offerings-overview.md | — |
| **Target Users** | customer-personas.md | offerings-overview.md |
| **Pain Points** | customer-personas.md | — |

---

## Maintenance Rules

1. **When adding a new document:**
   - Add entry to appropriate domain table above
   - Update relationship map
   - Add to cross-reference index
   - Update folder structure diagram

2. **When renaming/moving a document:**
   - Update all references in this file
   - Update all cross-links in affected documents
   - Check relationship map

3. **When deleting a document:**
   - Move to `.archive/` (don't delete)
   - Remove from domain table
   - Update relationship map
   - Fix any broken links in other documents

4. **When adding open questions:**
   - Add to the document's own Open Questions section
   - Consider adding to this file if cross-cutting

5. **When resolving open questions:**
   - Remove from the source document
   - Update related documents if the answer affects them

---

## Related Files

- **System design:** `context/README.md`
- **Document standards:** `skills/context-sculpting/knowledge/document-standards.md`
- **Templates:** `templates/` folder
