# Workflow: Audit Context

> **Purpose:** Comprehensive context health review using parallel agent analysis to identify gaps, inconsistencies, and refinement opportunities.
>
> **Use when:** Periodic maintenance, before major decisions, after business changes, messaging refinement, or user requests health check.

---

## Prerequisites

**Load these files BEFORE starting:**

1. `knowledge/context-architecture.md` - The source of truth for expected structure
2. All context documents in the system (for subagent distribution)

---

## Workflow Overview

This workflow uses **3 parallel subagents** to analyze the context system from different perspectives, then synthesizes findings into prioritized recommendations.

```
Phase 1: Structural Health Check (orchestrator)
    ↓
Phase 2: Multi-Agent Deep Analysis (3 parallel subagents)
    ↓
Phase 3: Synthesis & Prioritization (orchestrator)
    ↓
Phase 4: Implementation (orchestrator, with user approval)
```

---

## Phase 1: Structural Health Check

*Performed by the orchestrating agent before launching subagents.*

### Step 1.1: Inventory Actual Files

Discover all files currently in the context system.

**Run:**
```bash
find context -name "*.md" -not -path "*/.archive/*"
```

Or use Glob to find all markdown files in context folders.

### Step 1.2: Compare to Architecture Map

Compare actual files against `knowledge/context-architecture.md`.

**Check for:**

| Issue | Description |
|-------|-------------|
| **Missing files** | Documented in architecture but file doesn't exist |
| **Undocumented files** | File exists but not in architecture map |
| **Wrong location** | File in different folder than documented |
| **Naming issues** | Filename doesn't match conventions |

### Step 1.3: Verify Cross-Links

1. Find all relative links:
```bash
grep -r --exclude-dir=.archive "](../" context/ | grep ".md)"
```

2. For each link found, verify the target exists in the Step 1.1 inventory.

3. Report any links where target file is not found.

**Also check for orphan documents** - files with no incoming links from other documents.

### Step 1.4: Fix Critical Structural Issues

Before proceeding to deep analysis, immediately fix:
- Broken links (update or remove)
- Architecture map mismatches (sync with reality)
- Missing required sections in documents

**Document fixes made** for the audit report.

---

## Phase 2: Multi-Agent Deep Analysis

*Launch 3 parallel subagents with identical instructions to get independent perspectives.*

### Why 3 Identical Agents?

- **Independent analysis** - Each agent reviews without knowing what others found
- **Overlap = signal** - When 2-3 agents flag the same issue independently, it's high priority
- **Scalable instructions** - No need to update prompts as content changes

### Subagent Prompt

Use the Task tool to launch 3 agents. Each receives the same prompt:

```markdown
## Context System Audit

You are one of 3 independent agents reviewing the business context system. Your goal is to identify the most impactful opportunities for improvement.

### Your Task

1. Read ALL context documents listed below
2. Analyze for any issues: gaps, inconsistencies, unclear messaging, structural problems, misalignment between documents
3. Return your TOP 3 findings, prioritized by impact
4. Be specific and actionable

### Documents to Review

[List all context document paths from Step 1.1]

### What to Look For

- **Consistency** - Do documents align with each other? Are facts stated the same way?
- **Clarity** - Is messaging clear and concrete? Would a reader understand what we do and why?
- **Completeness** - Are there gaps, thin sections, or unresolved questions?
- **Coherence** - Is information in the right place? Is cross-referencing effective?
- **Quality** - Is the writing sharp? Are value props differentiated? Does the problem resonate?

### Output Format

Return exactly 3 findings in this format:

#### Finding 1: [Title]
- **File:** [exact file path]
- **Section:** [section name]
- **Current Text:** "[quote the problematic text]"
- **Problem:** [what's wrong and why it matters]
- **Recommendation:** "[specific suggested fix or action]"

#### Finding 2: [Title]
[Same format]

#### Finding 3: [Title]
[Same format]

### Final Assessment
[2-3 sentence overall assessment of context health]
```

### Launching Subagents

**CRITICAL:** Launch all 3 subagents in a single message using parallel Task tool calls.

```
[Task tool call 1: Context Audit Agent A]
[Task tool call 2: Context Audit Agent B]
[Task tool call 3: Context Audit Agent C]
```

Wait for all 3 agents to complete before proceeding to synthesis.

---

## Phase 3: Synthesis & Prioritization

*Orchestrator aggregates findings and creates prioritized recommendations.*

### Step 3.1: Collect All Findings

Compile all 9 findings (3 from each agent) into a single list.

### Step 3.2: Identify Overlaps

**High-signal issues:** When 2+ agents independently flag the same issue, it's a strong signal.

| Overlap Pattern | Priority |
|-----------------|----------|
| All 3 agents flag same issue | Critical - address first |
| 2 agents flag same issue | High - likely real problem |
| Single agent flags issue | Normal - evaluate on merits |

### Step 3.3: Create Priority Matrix

Score each finding:

| Criteria | Weight | Scale |
|----------|--------|-------|
| Impact on user understanding | 40% | 1-5 |
| Number of agents flagging | 30% | 1-3 |
| Effort to fix | 30% | 1-5 (inverse: 5=easy) |

### Step 3.4: Generate Recommendations Summary

Present to user in this format:

```markdown
## Audit Findings Summary

**Structural Issues Fixed:** [N items]
**Deep Analysis Findings:** [N items from 9 total]

### Priority 1: [Title]
- **Flagged by:** Agent(s) [1/2/3]
- **Impact:** [High/Medium/Low]
- **Effort:** [Low/Medium/High]
- **Summary:** [1-2 sentences]
- **Action:** [Specific change to make]

### Priority 2: [Title]
[Same format]

[Continue for all actionable findings]

### Findings Requiring Discussion
[Any items that need user input before action]

---

**Recommended implementation order:** [List priority numbers]

Approve implementation? [Y/N/Modify]
```

---

## Phase 4: Implementation

*Execute approved changes with proper versioning.*

### Step 4.1: Get User Approval

**Do NOT proceed without explicit user approval.**

Present the prioritized list and wait for:
- Approval of all items
- Approval of subset
- Modifications to recommendations
- Request for clarification

### Step 4.2: Implement in Priority Order

For each approved change:

1. **Make the edit** to the target file
2. **Update metadata:**
   - Increment version (minor for refinements)
   - Update Modified date
   - Add Change History entry
3. **Check cascade effects:**
   - Does this change affect other documents?
   - Are cross-links still accurate?
   - Does architecture map need updating?
4. **Update related documents** if needed

### Step 4.3: Update Architecture Map

After all changes:

1. Update `knowledge/context-architecture.md`:
   - Last Updated table
   - Any structural changes
   - Open Questions section (resolved/new)
2. Verify all cross-references are current

### Step 4.4: Generate Final Audit Report

```markdown
## Context Audit Report

**Date:** [Date]
**Auditor:** Claude (orchestrator + 3 subagents)

### Phase 1: Structural Health
- Files inventoried: [N]
- Architecture mismatches fixed: [N]
- Broken links fixed: [N]

### Phase 2: Deep Analysis
- Findings from Agent A: [N]
- Findings from Agent B: [N]
- Findings from Agent C: [N]
- Overlapping findings: [N]

### Phase 3: Prioritization
- Critical issues: [N]
- High priority: [N]
- Medium priority: [N]
- Deferred/discussed: [N]

### Phase 4: Implementation
- Changes implemented: [N]
- Documents updated: [list]
- Version increments: [list]

### Remaining Open Items
- [Any items deferred or requiring future action]

### Next Audit
- Recommended: [Date based on audit frequency]
- Focus areas: [Based on patterns found]
```
