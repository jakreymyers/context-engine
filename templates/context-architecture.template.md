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
│   └── [documents as needed]
├── operations/                     # How we work
│   └── [documents as needed]
├── strategy/                       # Where we're going
│   └── [documents as needed]
├── README.md                       # System documentation
└── .archive/                       # Deprecated documents
```

---

## Domain Summaries

### Identity (`/identity/`)

**Purpose:** Establish who we are, what we stand for, how we communicate.

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| `company-brief.md` | brief | [Status] | Company overview, mission, values, voice |
| [Add as created] | | | |

---

### Offerings (`/offerings/`)

**Purpose:** Define what we sell, the value it provides, and how it's structured.

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| `offerings-overview.md` | catalog | [Status] | Summary of all offerings, pricing |
| [Add as created] | | | |

---

### Customers (`/customers/`)

**Purpose:** Understand who buys, why they buy, and how to reach them.

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| `customer-personas.md` | profile | [Status] | Target users, goals, pain points |
| [Add as created] | | | |

---

### Market (`/market/`)

**Purpose:** Understand the competitive landscape and where we fit.

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| [Add as created] | | | |

---

### Operations (`/operations/`)

**Purpose:** Understand how work gets done—teams, processes, tools.

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| [Add as created] | | | |

---

### Strategy (`/strategy/`)

**Purpose:** Understand where we're going and what we're prioritizing.

| Document | Type | Status | Purpose |
|----------|------|--------|---------|
| [Add as created] | | | |

---

## Document Relationship Map

```
IDENTITY DOMAIN
───────────────
company-brief.md [PRIMARY IDENTITY DOCUMENT]
├── Links to: [list linked documents]
└── Contains: [list key contents]

OFFERINGS DOMAIN
────────────────
offerings-overview.md
├── Links to: [list linked documents]
└── Contains: [list key contents]

CUSTOMERS DOMAIN
────────────────
customer-personas.md
├── Links to: [list linked documents]
└── Contains: [list key contents]
```

---

## Cross-Reference Index

| Topic | Primary Document | Also Mentioned In |
|-------|------------------|-------------------|
| **Mission** | company-brief.md | |
| **Values** | company-brief.md | |
| **Products/Services** | offerings-overview.md | company-brief.md |
| **Target Users** | customer-personas.md | offerings-overview.md |
| [Add topics as content grows] | | |

---

## Open Questions Index

*Cross-cutting questions that affect multiple documents.*

- [ ] [Question] - Affects: [doc1], [doc2]
- [ ] [Question] - Affects: [doc1]

---

## Maintenance Rules

1. **When adding a new document:**
   - Add entry to appropriate domain table
   - Update relationship map
   - Add to cross-reference index
   - Update folder structure diagram

2. **When renaming/moving a document:**
   - Update all references in this file
   - Update all cross-links in affected documents

3. **When deleting a document:**
   - Move to `.archive/` (don't delete)
   - Remove from domain table
   - Update relationship map
   - Fix any broken links

4. **When resolving open questions:**
   - Remove from source document
   - Remove from this index
   - Update related documents if affected
