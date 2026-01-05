# Context Engine

A structured system for giving AI agents instant, accurate knowledge of your business.

**Stop re-explaining yourself every conversation.**

## What This Is

The Context Engine is a folder structure and maintenance system that lets any AI agent instantly understand your business. Instead of briefing your AI every time, you maintain structured markdown files that agents can load and operate against.

**The result:** Your AI outputs sound like you. First try.

**FULL INSTRUCTIONS:** https://myrs.notion.site/context-engine

## See It Work (2 Minutes)

Before setting anything up, try this:

**Without context:**
```
Write a tagline for a productivity app.
```
*Result: Generic output like "Work Smarter, Not Harder"*

**With context:**
```
Context: We're building an AI co-founder for solo founders. Our mission is to help
first-time founders validate ideas before wasting months building the wrong thing.
Our voice is direct, practical, and encouraging - like a mentor who's been there.

Write a tagline for our product.
```
*Result: Output that sounds like YOUR business*

That's the Context Engine in action. The rest of this system just makes it organized and maintainable.

## What's Included

```
context-engine/
├── context/                     # Starter context files (copy and customize)
│   ├── identity/                # Who you are
│   ├── offerings/               # What you sell
│   ├── customers/               # Who you serve
│   ├── market/                  # Where you compete
│   ├── operations/              # How you work
│   ├── strategy/                # Where you're going
│   └── .archive/                # Deprecated documents
│
├── skills/
│   └── context-sculpting/       # Maintenance skill (Claude Code / advanced)
│       ├── SKILL.md             # Main skill instructions
│       ├── workflow/            # Update, interview, audit workflows
│       └── knowledge/           # Architecture, standards, patterns
│
└── templates/                   # Reference templates (same as context/ files)
    ├── company-brief.template.md
    ├── customer-personas.template.md
    ├── offerings-overview.template.md
    └── context-architecture.template.md
```

## Quick Start

### 1. Copy the structure

```bash
# Clone this repo
git clone https://github.com/jakreymyers/context-engine.git

# Copy context folder to your project
cp -r context-engine/context ./context

# Optional: Copy the skill (for Claude Code users)
cp -r context-engine/skills/context-sculpting ./.claude/skills/
```

### 2. Fill in your first document

Start with `context/identity/company-brief.md`. This is your foundation.

Give your AI this prompt:

```
I want to create my company brief. Interview me to gather the information.

Ask me about:
- Company name and what we do
- Our mission (the change we seek to create)
- Our core values (3-5 principles)
- Our voice and tone (how we communicate)

After the interview, generate the complete document content for me.
```

*Copy the AI's output into your company-brief.md file.*

### 3. Load context for tasks

Before any task, give your AI the relevant context.

**How to "load" context depends on your AI tool:**

| Tool | How to Load Context |
|------|---------------------|
| **ChatGPT** | Copy file contents and paste at the start of your prompt |
| **Claude.ai** | Copy file contents and paste, or upload .md files |
| **Claude Code** | Files are automatically accessible - just reference paths |
| **Cursor/Copilot** | Add files to your project; they're in context automatically |

**Example prompt:**
```
Here's my business context:

[Paste contents of company-brief.md]
[Paste contents of customer-personas.md]

Now write a landing page headline for our product.
```

## The Six Domains

| Domain | Purpose | Start Here |
|--------|---------|------------|
| **identity/** | Who you are | `company-brief.md` |
| **offerings/** | What you sell | `offerings-overview.md` |
| **customers/** | Who you serve | `customer-personas.md` |
| **market/** | Where you compete | Add when needed |
| **operations/** | How you work | Add when needed |
| **strategy/** | Where you're going | Add when needed |

**Minimum viable setup:** identity + customers + offerings (3 files)

## Core Principles

1. **One source of truth** - Each fact lives in exactly one place
2. **Progressive disclosure** - Overview docs link to detail docs
3. **Self-maintaining** - The Context Sculpting skill keeps everything current
4. **Agent-readable** - Structured for AI consumption, not just humans

## Context Sculpting Skill

The skill automates context maintenance with three workflows:

| Workflow | Purpose | When to Use |
|----------|---------|-------------|
| **Update Context** | Add new information | After strategy conversations |
| **Interview & Elicit** | Gather context through questions | Filling in new documents |
| **Audit Context** | Check for inconsistencies | Monthly maintenance |

### Using the Skill

**For Claude Code users:**
```
Load: skills/context-sculpting/SKILL.md

Then help me update my context after our strategy discussion.
```

**For other AI tools:**

Copy the relevant workflow file contents into your conversation:
- `workflow/update-context.md` - For adding new information
- `workflow/interview-elicit.md` - For gathering context through questions
- `workflow/audit-context.md` - For checking consistency (advanced)

*Note: The audit workflow includes advanced multi-agent patterns designed for Claude Code. For simpler tools, use the basic prompts in the "Using the System" section below.*

## Using the System

### After Conversations

When you discuss strategy or make decisions, capture it:

```
We just discussed [topic]. What information from our conversation
should I add to my context files? Identify which file it belongs in
and what specifically to add.
```

### Monthly Maintenance

Run a simple audit:

```
Review these context files for any contradictions or outdated information:

[Paste your context files]

List any issues you find.
```

## Customization

### Changing paths

The default examples use `./context/`. Use whatever path works for your project:
- `./.claude/context/` - For Claude Code projects
- `./docs/context/` - For documentation-focused projects
- `./ai/context/` - Whatever you prefer

Update the `related_documents` paths in YAML front matter to match your structure.

### Scaling up

Start minimal. Add documents as you need them:

- **Minimal:** company-brief + customer-personas + offerings-overview
- **Standard:** Add brand-voice, product briefs, competitors
- **Expanded:** Add journey maps, processes, goals, initiatives

## Reference Documentation

- [Document Standards](./skills/context-sculpting/knowledge/document-standards.md) - Formatting conventions
- [Integration Patterns](./skills/context-sculpting/knowledge/integration-patterns.md) - Where information belongs
- [Cross-Linking Guide](./skills/context-sculpting/knowledge/cross-linking-guide.md) - How to connect documents

## License

MIT License. Use it, modify it, share it.

## Credits

Created by [Jak Myers](https://linkedin.com/in/jakreymyers) as part of building [MYRS.ai](https://myrs.ai) in public.

Questions? Reach out on LinkedIn.
