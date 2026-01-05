# Workflow: Interview & Elicit

> **Purpose:** Conduct structured interviews to extract business context from stakeholders.
>
> **Use when:** Gathering initial context, filling gaps, validating information, or user initiates context-building conversation.

---

## Prerequisites

**Load these files BEFORE starting:**

1. `knowledge/context-architecture.md` - To identify target documents and gaps
2. `knowledge/document-standards.md` - For output formatting
3. Target document(s) to populate - To see existing content and open questions

---

## Workflow Steps

### Step 1: Identify Interview Focus

Determine what context needs to be gathered.

**Options:**
1. **Specific document** - User wants to populate a particular document
2. **Open questions** - Address unresolved items from existing documents
3. **Domain gap** - Fill missing context in a domain area
4. **Validation** - Verify existing information is still accurate

**Check `knowledge/context-architecture.md`:**
- Open Questions index for unresolved items
- Domain tables for empty or draft documents
- Relationship map for gaps in coverage

---

### Step 2: Load Target Document(s)

Read the document(s) that will be updated.

**Note:**
- Current content (to avoid re-asking known information)
- Open Questions (prioritize these)
- Section structure (to know where answers will go)
- Related documents (for context on what's already known)

---

### Step 3: Prepare Interview Questions

Based on the target document and gaps identified:

**Use discovery questions from:**
- The document's own Discovery Questions section (if template)
- Open Questions section (if populated document)
- Domain-specific question banks (see below)

**Structure questions to be:**
- Open-ended (not yes/no)
- Specific enough to be actionable
- Grouped by topic/section

---

### Step 4: Conduct the Interview

**For each question or topic:**

1. **Ask the question** - Present clearly
2. **Provide response options** - Offer 5-8 numbered options ranked by likelihood
3. **Allow free response** - User can choose options, combine, or respond freely
4. **Clarify if needed** - Follow up on ambiguous responses
5. **Confirm understanding** - Summarize back what you heard

**Response Option Format:**
```
**Question:** [The question]

Select, combine, or respond freely:

1. [Most likely response]
2. [Second most likely]
3. [Third option]
4. [Fourth option]
5. [Fifth option]
6. [Sixth option] (optional)
7. [Seventh option] (optional)
8. [Eighth option] (optional)
```

**Important:**
- Options should cover the likely answer space
- Include substantively different options, not just variations
- Rank by probability of selection
- Always allow free-form response

---

### Step 5: Document Responses

As information is gathered:

1. **Update the target document in real-time**
   - Add content to appropriate sections
   - Update metadata (version, modified date)
   - Add to Change History

2. **Track new open questions**
   - If response raises new questions, add to Open Questions
   - If response is partial, note what's still unknown

3. **Check for cross-document impact**
   - Does this answer affect other documents?
   - Note for later update if so

---

### Step 6: Update Related Documents

After the interview:

1. **Identify affected documents** (from Step 5 notes)
2. **Update each with relevant information**
   - Brief summaries in related docs
   - Links to primary content
3. **Maintain consistency** across all updates

---

### Step 7: Update Architecture Map

Update `knowledge/context-architecture.md`:

- Open Questions index (add new, remove resolved)
- Document status (Draft → Active if substantially complete)
- Any structural changes

---

### Step 8: Summarize & Confirm

Present to the user:

1. **Summary of what was captured**
2. **Documents updated**
3. **Remaining open questions** (if any)
4. **Suggested next topics** (based on gaps)

---

## Interview Best Practices

### Creating Good Response Options

**Do:**
- Cover the likely answer space
- Make options meaningfully different
- Include options from different perspectives
- Rank by probability

**Don't:**
- Offer only slight variations of same answer
- Lead toward a particular answer
- Make options so specific user can't relate
- Forget to allow free response

### Handling Ambiguous Responses

If user's response is unclear:

1. Summarize your understanding
2. Ask a targeted clarifying question
3. Offer refined options if helpful

### Handling "I Don't Know"

If user doesn't know:

1. Acknowledge it's okay not to know
2. Add to Open Questions for later
3. Ask if there's related information they do know
4. Move to next topic

### Maintaining Conversation Flow

- Don't interrogate—maintain natural dialogue
- Group related questions
- Acknowledge and build on previous answers
- Take breaks if covering a lot of ground

---

## Interview Question Banks by Domain

### Identity Questions

1. What is the company's mission—the change it seeks to create?
2. What values guide decision-making when trade-offs arise?
3. What's the origin story—why does this company exist?
4. What tone and voice should represent the company?
5. What should the company NEVER say or do?

### Offerings Questions

1. What products or services are offered?
2. What primary problem does each offering solve?
3. Who is each offering designed for?
4. How is pricing structured?
5. What differentiates each offering from alternatives?

### Customer Questions

1. Who is the primary buyer?
2. What problem are they solving when they find us?
3. What does their buying process look like?
4. What are their main objections or concerns?
5. What makes a customer successful vs. unsuccessful?

### Market Questions

1. What industry/category do we compete in?
2. Who are the top competitors?
3. What is our primary competitive advantage?
4. What market opportunities exist?

### Strategy Questions

1. What are the top 3-5 priorities right now?
2. What major initiatives are underway?
3. What strategic decisions have been made recently?
4. What is explicitly NOT a priority?

---

## Example Interview Session

**Focus:** Company Brief - Origin Story

**Step 3 - Questions prepared:**
- What's your personal connection to this problem?
- What was the "aha moment" when this idea clicked?
- Why are you the right person to build this?
- Why is now the right time?

**Step 4 - Interview:**

```
**Question: What's your personal connection to this problem?**

Select, combine, or respond freely:

1. **Lived experience:** "I've been that person struggling with this exact problem."
2. **Professional background:** "My background gave me unique perspective."
3. **Pattern recognition:** "I kept seeing people fail the same way."
4. **Technology timing:** "I realized the technology is now capable enough."
5. **Building for myself:** "This started as solving my own problem."
6. **Mission-driven:** "Everyone deserves access to this."
7. **Skills convergence:** "My skills uniquely position me for this."
8. **Market timing:** "The market is ready for this now."
```

**User responds:** "Combination of 3 and 5 - I saw patterns in my own experience and others around me."

**Step 5 - Document:**
- Update company-brief.md Origin Story section
- Note follow-up: Specific examples of the pattern?
- Add to Open Questions if details needed

---

## Quick Reference: Interview Checklist

```markdown
## Interview Session Checklist

**Focus:** [Document/Domain/Topic]
**Date:** [Date]

### Preparation
- [ ] Loaded context-architecture.md
- [ ] Loaded target document(s)
- [ ] Identified open questions to address
- [ ] Prepared interview questions

### During Interview
- [ ] Asked open-ended questions
- [ ] Provided 5-8 ranked response options
- [ ] Allowed free-form responses
- [ ] Clarified ambiguous answers
- [ ] Documented responses in real-time

### After Interview
- [ ] Updated target document(s)
- [ ] Updated related documents
- [ ] Updated architecture map
- [ ] Captured new open questions
- [ ] Summarized to user
```
