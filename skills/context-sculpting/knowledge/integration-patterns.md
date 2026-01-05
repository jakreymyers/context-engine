# Integration Patterns

> **Purpose:** Decision framework for where information belongs and how to integrate across files.
>
> **Load when:** Adding new information that might affect multiple documents.

---

## The Core Problem

When new information arrives, you must decide:
1. **Where does it belong?** (primary location)
2. **What else needs updating?** (related documents)
3. **How do I keep everything coherent?** (integration process)

This guide provides the decision framework.

---

## Information Placement Decision Tree

```
New information arrives
        │
        ▼
┌───────────────────────────────────┐
│ What domain does this belong to?  │
│ identity / offerings / customers  │
│ market / operations / strategy    │
└───────────────────────────────────┘
        │
        ▼
┌───────────────────────────────────┐
│ Is there an existing document     │
│ for this type of information?     │
└───────────────────────────────────┘
        │
    ┌───┴───┐
   Yes      No
    │        │
    ▼        ▼
Update   Create new doc
existing (follow document-standards.md)
    │
    ▼
┌───────────────────────────────────┐
│ Does this information affect      │
│ other documents?                  │
└───────────────────────────────────┘
        │
    ┌───┴───┐
   Yes      No
    │        │
    ▼        ▼
Update   Done (update
related  architecture if
docs     new doc created)
```

---

## Domain Routing Guide

| Information Type | Primary Domain | Primary Document |
|------------------|----------------|------------------|
| Mission, vision, why we exist | identity | company-brief.md |
| Values, principles | identity | company-brief.md |
| Voice, tone, communication style | identity | company-brief.md (or brand-voice.md if expanded) |
| What we won't do (guardrails) | identity | company-brief.md |
| Product features, capabilities | offerings | [product]-product-brief.md |
| Pricing, packaging | offerings | offerings-overview.md (or pricing-guide.md if expanded) |
| Value propositions | offerings | offerings-overview.md or product brief |
| Product roadmap | offerings | roadmap.md (when created) |
| Who buys/uses | customers | customer-personas.md |
| Customer journey stages | customers | journey-map.md (when created) |
| How to communicate with customers | customers | communication-guide.md (when created) |
| Pain points, goals | customers | customer-personas.md |
| Competitors, alternatives | market | competitors.md (or product brief temporarily) |
| Industry trends | market | landscape.md (when created) |
| Our positioning | market | positioning-matrix.md (or identity/positioning.md) |
| Team structure | operations | team-structure.md (when created) |
| Processes, workflows | operations | processes.md (when created) |
| Tools, tech stack | operations | tools-stack.md (when created) |
| Goals, OKRs | strategy | goals.md (when created) |
| Current initiatives | strategy | initiatives.md (when created) |
| Strategic decisions | strategy | decisions.md (when created) |

---

## Multi-Document Updates

### When One Change Affects Multiple Documents

**Scenario:** User says "Our target customer is now enterprise teams, not solo founders."

**Affected documents:**
1. **customer-personas.md** - Primary update (personas change)
2. **product-brief.md** - Target user section needs update
3. **company-brief.md** - Mission/scope may need adjustment
4. **offerings-overview.md** - Value props may shift

**Process:**
1. Identify all affected documents (check architecture map)
2. Update the primary document first
3. Update related documents for consistency
4. Verify cross-links still make sense
5. Update Open Questions if new unknowns arise

### The Coherence Check

After any update, verify:

| Check | Question |
|-------|----------|
| **Consistency** | Does the same fact appear the same way everywhere? |
| **No contradictions** | Are there conflicting statements across documents? |
| **Links valid** | Do all cross-references still make sense? |
| **Open questions** | Are new unknowns captured? |

---

## Primary vs. Secondary Location

### Primary Location

Where the full, authoritative information lives.

**Characteristics:**
- Complete detail
- Single source of truth
- Where updates happen
- Linked TO from secondary locations

### Secondary Location

Where brief references or summaries appear.

**Characteristics:**
- One-line to one-paragraph summary
- Links to primary location
- Updated only when primary changes significantly
- Never contradicts primary

**Example:**

| Information | Primary | Secondary |
|-------------|---------|-----------|
| Mission statement | company-brief.md | — (no duplication needed) |
| Full persona details | customer-personas.md | product-brief.md (summary + link) |
| Product capabilities | product-brief.md | offerings-overview.md (table summary) |
| Competitive positioning | product-brief.md | — (keep in one place until market/ expands) |

---

## Open Questions Propagation

When information is incomplete or uncertain:

1. **Add to source document's Open Questions section**
2. **Add to `knowledge/context-architecture.md` if cross-cutting**
3. **Consider if the question affects other documents**

**Example:**
```
User: "We're thinking about targeting enterprise but haven't decided."

Actions:
1. Add to customer-personas.md Open Questions:
   - [ ] Enterprise vs. solo founder focus: Decision pending

2. Note in product-brief.md if target user section mentions this uncertainty
```

---

## Integration Scenarios

### Scenario 1: Interview Produces New Information

**Source:** User interview about values

**Process:**
1. Primary update: company-brief.md Core Values section
2. Check: Do values affect product principles? → Update product-brief.md if so
3. Check: Do values affect customer communication? → Note for communication-guide.md when created
4. Update Change History in modified documents
5. Update Open Questions if partial answers

### Scenario 2: Research Produces Market Insights

**Source:** Competitive research

**Process:**
1. Primary update: market/competitors.md (create if needed)
2. Secondary update: product-brief.md competitive positioning
3. Check: Does this change our differentiation story? → Update identity docs if so
4. Update architecture map if new document created

### Scenario 3: Strategic Decision Made

**Source:** User decides to focus on validation over ideation

**Process:**
1. Primary update: strategy/decisions.md (create if needed) or company-brief.md
2. Check impact on: product-brief.md (positioning), offerings-overview.md (value props), customer-personas.md (if ICP shifts)
3. Update all affected documents
4. Close related Open Questions

### Scenario 4: Correcting Inconsistency

**Source:** Audit finds conflicting information

**Process:**
1. Identify the source of truth (usually the most specific document)
2. Verify with user if uncertain
3. Update the incorrect document(s)
4. Add to Change History: "Corrected inconsistency with [source document]"

---

## Information Hierarchy

When in doubt about where information belongs, follow this hierarchy:

```
Most Specific → Least Specific

Product-specific docs     → Domain overview docs    → Company brief
(product-brief)             (offerings-overview)      (company-brief)

Detailed personas         → Customer overview       → Company brief
(customer-personas)         (if created)              (company-brief)
```

**Rule:** Information lives at the most specific appropriate level, with summaries/links at higher levels.

---

## Quick Decision Matrix

| New information is about... | Goes in... | Also update... |
|----------------------------|------------|----------------|
| What the product does | product-brief | offerings-overview |
| Who uses the product | customer-personas | product-brief (target user) |
| Why we exist | company-brief | — |
| How we talk | company-brief (or brand-voice) | — |
| What we charge | offerings-overview | product-brief (if detailed) |
| Who competes with us | market/competitors (or product-brief) | — |
| What we're building next | roadmap (or product-brief open questions) | — |
| A decision we made | strategy/decisions (or relevant doc) | Affected docs |

---

## Anti-Patterns

| Wrong | Right |
|-------|-------|
| Same paragraph copied to 3 documents | Primary location + links from others |
| Update one doc, forget related ones | Check architecture map for relationships |
| No record of where info came from | Note source in Change History |
| Ignore contradictions | Resolve immediately, note correction |
| Put everything in company-brief | Use domain-appropriate documents |
| Create new doc for every piece of info | Add to existing docs when appropriate |
