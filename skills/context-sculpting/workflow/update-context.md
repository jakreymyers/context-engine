# Workflow: Update Context

> **Purpose:** Add new information to the context system from any source.
>
> **Use when:** New information needs to be captured, corrections needed, or insights from research/interviews need integration.

---

## Prerequisites

**Load these files BEFORE starting:**

1. `knowledge/context-architecture.md` - To understand current structure
2. `knowledge/document-standards.md` - For formatting requirements
3. `knowledge/integration-patterns.md` - For placement decisions
4. `knowledge/cross-linking-guide.md` - For relationship maintenance

---

## Workflow Steps

### Step 1: Understand the Information

Identify what information is being added or changed.

**Ask yourself:**
- What is the new information?
- Where did it come from? (interview, research, decision, observation)
- Is this a new fact, a correction, or an update to existing information?

---

### Step 2: Determine Primary Location

Use `knowledge/integration-patterns.md` decision tree.

**Questions:**
1. What domain does this belong to? (identity, offerings, customers, market, operations, strategy)
2. Is there an existing document for this type of information?
3. If new document needed, does it warrant creation or should info go in an overview doc?

**Consult:** `knowledge/context-architecture.md` for current document inventory.

---

### Step 3: Identify All Affected Documents

**Check the architecture map for:**
- Documents that link to the primary document
- Documents that contain related information
- Documents that might become inconsistent if not updated

**Common ripple patterns:**
| Primary Change | Often Also Affects |
|----------------|-------------------|
| customer-personas.md | product-brief.md (target user) |
| company-brief.md (mission) | product-brief.md (alignment) |
| product-brief.md (positioning) | offerings-overview.md (summary) |

---

### Step 4: Update Primary Document

1. **Read the current document** - Understand existing content
2. **Locate the appropriate section** - Don't add to wrong place
3. **Make the update:**
   - Add new content in appropriate section
   - Or correct existing content
   - Or expand existing content
4. **Update metadata:**
   - Increment version (minor for content changes)
   - Update Modified date
   - Add Change History entry with specific summary
5. **Update Open Questions:**
   - Add new questions if information is partial
   - Close questions if answered
   - Strike through resolved items with answer summary

---

### Step 5: Update Related Documents

For each affected document identified in Step 3:

1. **Read the document**
2. **Identify what needs updating:**
   - Summary that references changed information
   - Cross-links that might need adjustment
   - Consistency with primary update
3. **Make updates:**
   - Keep summaries brief; link to primary for detail
   - Ensure no contradictions
4. **Update metadata:**
   - Version, Modified date, Change History

---

### Step 6: Verify Cross-Links

**Check:**
- [ ] All updated documents have appropriate See Also links
- [ ] Bidirectional links exist where appropriate
- [ ] `related_documents` in YAML matches actual content links
- [ ] No broken links created

**If new document created:**
- Add links TO it from related documents
- Add links FROM it to related documents

---

### Step 7: Update Architecture Map

**Always update `knowledge/context-architecture.md` if:**
- New document was created
- Document was renamed or moved
- Relationships between documents changed
- Open Questions were added or resolved

**Update:**
- Folder structure (if changed)
- Domain tables (if documents added)
- Relationship map (if connections changed)
- Open Questions index (add new, remove resolved)

---

### Step 8: Final Coherence Check

Before completing, verify:

| Check | Status |
|-------|--------|
| Primary document updated correctly | [ ] |
| All related documents updated | [ ] |
| No contradictions across documents | [ ] |
| Cross-links valid and bidirectional | [ ] |
| Open Questions captured (if any) | [ ] |
| Architecture map current | [ ] |
| Change History entries added | [ ] |

---

## Example: Updating Target Customer

**Information:** "We're now targeting small teams (2-5 people), not just solo founders."

**Step 2 - Primary location:** customer-personas.md

**Step 3 - Affected documents:**
- product-brief.md (target user section)
- offerings-overview.md (if mentions solo founders)
- company-brief.md (if mission references solo founders)

**Step 4 - Primary update:**
- Update customer-personas.md primary persona section
- Change "Solo founder" to "Solo founders and small teams (2-5)"
- Update related goals, pain points if they differ
- Increment version, update Change History

**Step 5 - Related updates:**
- product-brief.md: Update "Target User" section
- offerings-overview.md: Update "Target user" in offerings table
- company-brief.md: Check mission statement wording

**Step 6 - Cross-links:** Verify all links still valid

**Step 7 - Architecture:** Update Open Questions if this resolves any

**Step 8 - Verify:** All documents consistent, no contradictions

---

## Quick Reference: Update Checklist

```markdown
## Context Update Checklist

**Information:** [What's being added/changed]
**Source:** [Interview/Research/Decision/Observation]

### Documents Affected
- [ ] Primary: [document name]
- [ ] Related: [document name]
- [ ] Related: [document name]

### Updates Made
- [ ] Primary document updated
- [ ] Version incremented
- [ ] Change History added
- [ ] Related documents updated
- [ ] Cross-links verified
- [ ] Architecture map updated
- [ ] Open Questions updated

### Coherence Verified
- [ ] No contradictions
- [ ] No broken links
- [ ] All related docs consistent
```
