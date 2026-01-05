# Cross-Linking Guide

> **Purpose:** How to create and maintain links between context documents for progressive disclosure.
>
> **Load when:** Any operation that touches multiple documents or creates new documents.

---

## Why Cross-Linking Matters

Cross-links enable **progressive disclosure**—readers (human or LLM) can:
1. Get an overview from high-level documents
2. Go deeper by following links to specialized documents
3. Navigate related content without searching

**Without cross-links:** Documents become isolated silos; related information is hard to find.

**With cross-links:** The context system becomes a navigable knowledge graph.

---

## Link Syntax

### Markdown Links

```markdown
[Display Text](relative/path/to/document.md)
```

**Examples:**
```markdown
[Company Brief](../identity/company-brief.md)
[Product Brief](./product-brief.md)
[Customer Personas](../customers/customer-personas.md)
```

### Always Use Relative Paths

| Context | Path Format |
|---------|-------------|
| Same folder | `./document.md` |
| Parent folder | `../folder/document.md` |
| Sibling folder | `../sibling/document.md` |

**Never use absolute paths** - they break if the repository moves.

---

## Where to Place Links

### 1. See Also Section (Required)

Every document must have a See Also section at the end with links to related documents.

```markdown
## See Also

- [Company Brief](../identity/company-brief.md) - Who we are
- [Customer Personas](../customers/customer-personas.md) - Who we serve
```

**Structure:** List links with descriptions of what readers will find.

### 2. Inline Contextual Links

Link within content when referencing information that lives elsewhere.

```markdown
Our primary users are first-time founders (see [Customer Personas](../customers/customer-personas.md) for detailed profiles).
```

### 3. Purpose/When to Load Section

Link to detail documents from overview documents.

```markdown
> **For product-specific context:** See [Product Brief](../offerings/product-brief.md)
```

### 4. YAML Front Matter

Machine-readable links for tooling and discovery.

```yaml
related_documents:
  - "../identity/company-brief.md"
  - "./product-brief.md"
```

---

## Linking Patterns

### Pattern 1: Overview → Detail

Overview documents (briefs, overviews) link to specialized documents for depth.

```
company-brief.md
├── "See [Product Brief] for full details"
└── Links in See Also to product-brief, personas

offerings-overview.md
├── Product table with summary
└── "Go deeper: [Product Brief]"
```

### Pattern 2: Detail → Context

Specialized documents link back to higher-level context.

```
product-brief.md
├── "Part of [Company Name](../identity/company-brief.md)"
└── Links in See Also to company-brief, personas
```

### Pattern 3: Lateral Links

Documents in the same tier link to related peers.

```
customer-personas.md ←→ product-brief.md
│                       │
├── "What we build for them"  ├── "Who we build for"
└── Link to product brief     └── Link to personas
```

### Pattern 4: Bidirectional Links

When A links to B, B should link back to A (in See Also at minimum).

```
company-brief.md ──→ customer-personas.md
                 ←──
```

---

## When to Link vs. When to Duplicate

### Link When:
- Information has a clear primary home
- The detail is substantial (more than a sentence)
- The reader might want to go deeper
- The information might change (single source of truth)

### Duplicate (briefly) When:
- A one-line summary is sufficient
- The information is critical context for understanding the current document
- Linking would interrupt flow too much

**Example of brief duplication with link:**
```markdown
**Target user:** First-time founders building on nights and weekends.
See [Customer Personas](../customers/customer-personas.md) for detailed profiles.
```

---

## Maintaining Links

### When Creating a New Document

1. Add links in the new document's See Also to related documents
2. Update related documents' See Also to link back
3. Update `related_documents` in YAML front matter (both directions)
4. Update `knowledge/context-architecture.md` relationship map

### When Renaming or Moving a Document

1. Find all documents that link to it: `grep -r "old-name.md" context/`
2. Update all links to use new path
3. Update `knowledge/context-architecture.md`

### When Deleting a Document

1. Move to `.archive/` instead of deleting
2. Find all links: `grep -r "document-name.md" context/`
3. Either:
   - Remove the links, or
   - Redirect to appropriate replacement document
4. Update `knowledge/context-architecture.md`

---

## Link Quality Checklist

Before completing any context update, verify:

- [ ] All new documents have See Also sections
- [ ] Bidirectional links exist (if A links to B, B links to A)
- [ ] `related_documents` in YAML matches actual links
- [ ] No broken links (all paths resolve to existing files)
- [ ] `knowledge/context-architecture.md` reflects current relationships

---

## Anti-Patterns

| Wrong | Right |
|-------|-------|
| Absolute paths `/Users/name/...` | Relative paths `../folder/file.md` |
| Links with no description | Links with brief description of what's there |
| One-way links only | Bidirectional linking |
| Deep duplication of content | Brief summary + link to source |
| Links in random places | Consistent See Also section + contextual inline |
| Orphan documents (no incoming links) | Every document linked from at least one other |

---

## Quick Reference

### Adding a link in See Also:
```markdown
- [Document Name](relative/path.md) - What the reader will find there
```

### Adding an inline link:
```markdown
See [Document Name](relative/path.md) for more details.
```

### Finding what links to a document:
```bash
grep -r "document-name.md" context/
```

### Checking for broken links:
Review `knowledge/context-architecture.md` relationship map against actual files.
