# Brainstorm: Indira.ro Customer Care Agent System

**Date:** 2026-02-16
**Status:** Draft

## What We're Building

A self-improving customer care AI agent for [indira.ro](https://www.indira.ro) (Shopify jewelry store), built as a Claude Desktop Cowork plugin. The system enables a care person to:

1. **Answer tickets** by pasting customer messages and getting drafted responses via `/draft-response`
2. **Improve the agent** on the fly via `/agent-improve` when responses are wrong or incomplete
3. **Track all changes in git** so the knowledge base and behaviors are versioned

## How Cowork Plugins Work (Research Findings)

- Cowork plugins are **file-based** (markdown + JSON, no code)
- Installed as `.plugin` files (zipped directories) into Cowork
- Components: **skills** (auto-loaded domain knowledge), **commands** (explicit `/slash-commands`), **connectors** (MCP tool integrations)
- "Work in a folder" provides **folder-level context/instructions** but does NOT load commands or skills from arbitrary directories
- To update a plugin, you **re-package and reinstall** the `.plugin` file
- Source: [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins)

## Architecture: Single Plugin, Git-Backed

```
indira-customer-care/
├── .claude-plugin/
│   └── plugin.json
├── .mcp.json                          # Shopify connector (future)
│
├── knowledge/                         # Layer 1: Knowledge Base
│   ├── brand-voice.md                 # Tone, style, personality
│   ├── policies/
│   │   ├── returns-exchanges.md
│   │   ├── shipping.md
│   │   ├── warranty.md
│   │   └── payments.md
│   ├── processes/
│   │   ├── order-issues.md
│   │   ├── escalation.md
│   │   └── complaints.md
│   └── products/
│       └── collections-overview.md    # Product categories, materials, care
│
├── skills/                            # Layer 2: Domain Skills
│   ├── response-drafting/
│   │   └── SKILL.md                   # How to draft responses using knowledge/
│   ├── ticket-triage/
│   │   └── SKILL.md                   # How to classify and prioritize
│   └── product-knowledge/
│       └── SKILL.md                   # Jewelry expertise, materials, care
│
├── commands/                          # Layer 3: Actions
│   ├── draft-response.md              # /draft-response - answer a customer ticket
│   ├── triage.md                      # /triage - classify urgency and topic
│   ├── kb-article.md                  # /kb-article - create knowledge base article
│   └── agent-improve.md              # /agent-improve - update knowledge/skills
│
└── README.md
```

### Layer Responsibilities

**Knowledge (knowledge/):** Pure content. Brand voice, policies, processes, product info. These are reference documents that skills and commands point to. The care person edits these most often.

**Skills (skills/):** Instructions for Claude on HOW to use the knowledge. Triggered automatically based on context. E.g., "when drafting a response, always check knowledge/policies/ first."

**Commands (commands/):** Explicit user actions. The care person types `/draft-response` with a pasted ticket. Claude follows the command instructions, leveraging skills and knowledge.

### The Self-Improvement Loop

1. Care person pastes a ticket, runs `/draft-response`
2. Claude drafts a response using knowledge base
3. If the response is wrong/incomplete, care person runs `/agent-improve`
4. `/agent-improve` asks: "What was wrong?" and "What should the correct answer be?"
5. Claude updates the relevant knowledge file, skill, or command
6. Changes are committed to git
7. Plugin is re-packaged and reinstalled

### Deployment Flow

```
Git repo (source of truth)
    ↓ /agent-improve commits changes
    ↓ re-package as .plugin
    ↓ reinstall in Cowork
Cowork picks up updated plugin
```

**Open question:** Can the `/agent-improve` command automate the re-packaging and reinstall? Need to test if Cowork commands can run `zip` and trigger plugin reload.

**Simpler alternative:** Use "Work in a folder" pointed at the git repo for the knowledge base context, and only package commands/skills as a plugin. This hybrid approach means knowledge updates are instant (folder instructions) while structural changes (new commands) require re-packaging.

## Key Decisions

1. **Single plugin** — start simple, split later if needed
2. **Knowledge as plain markdown** — easy for non-technical person to edit
3. **Git-backed** — all changes versioned, auditable
4. **Copy-paste workflow** — no direct Shopify integration initially (future MCP connector)
5. **Romanian language** — responses will be in Romanian for indira.ro customers

## Refined: Hybrid Approach

**Knowledge files** live in the git repo folder (loaded via "Work in a folder"). Updates are **instant** — no re-packaging needed.

**Commands and skills** are packaged as a `.plugin` file. Only need re-packaging when adding NEW commands or skills (structural changes).

This means the daily `/agent-improve` workflow (fixing policies, adding product info) is frictionless — just edit and commit.

## Refined: /agent-improve Structured Learning Flow

1. **Extract learning** from conversation context (ticket, draft, what was wrong)
2. **Classify learning type:**
   - Policy correction → `knowledge/policies/`
   - Process gap → `knowledge/processes/`
   - Tone/voice issue → `knowledge/brand-voice.md`
   - Product info → `knowledge/products/`
   - Response pattern → `skills/` SKILL.md
   - New scenario → may need new knowledge file
3. **Find the right file** by searching existing knowledge for related content
4. **Propose the change** — show file, specific edit, and reasoning
5. **Confirm** — care person approves or adjusts
6. **Save and commit** to git

## Refined: Knowledge Base Structure

```
knowledge/
├── brand-voice.md                 # Tone, personality, language (Romanian)
├── policies/
│   ├── returns-exchanges.md
│   ├── shipping.md
│   ├── payments.md
│   ├── warranty.md
│   └── privacy-gdpr.md
├── processes/
│   ├── order-issues.md
│   ├── escalation.md
│   ├── complaints.md
│   ├── custom-orders.md
│   └── gifting.md
└── products/
    ├── materials-care.md
    ├── sizing-guide.md
    └── collections.md
```

## Open Questions

1. What Shopify data would be useful via MCP connector? (Order status, tracking, customer history)
2. Should we scrape indira.ro for initial product catalog data?
3. How many care people will use this? (Affects plugin distribution)

## Next Steps

1. Run `/workflows:plan` to create implementation plan
2. Scrape indira.ro for product/policy content
3. Create plugin structure
4. Write initial knowledge documents
5. Build `/draft-response` and `/agent-improve` commands
6. Test the loop in Cowork
