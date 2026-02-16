---
title: "feat: Build Indira Customer Care Cowork Plugin"
type: feat
date: 2026-02-16
---

# Build Indira Customer Care Cowork Plugin

## Overview

Build a Claude Desktop Cowork plugin for indira.ro (Shopify jewelry store) that enables a customer care person to answer tickets, triage issues, and continuously improve the AI agent's knowledge base. The plugin is git-backed and self-improving.

## Problem Statement / Motivation

The care team at indira.ro currently handles tickets manually via Delight Chat. There's no structured knowledge base, no consistent brand voice, and no way to build institutional knowledge from resolved tickets. A Cowork plugin would let the care person leverage AI for drafting responses while building a growing, version-controlled knowledge base.

## Proposed Solution

A single Cowork plugin (`indira-customer-care`) with three layers:

1. **Knowledge Base** (`knowledge/`) — brand voice, policies, processes, product info as markdown
2. **Skills** (`skills/`) — domain expertise Claude draws on automatically
3. **Commands** (`commands/`) — explicit actions: `/draft-response`, `/triage`, `/agent-improve`

### Architecture

```
indira-customer-care/
├── .claude-plugin/
│   └── plugin.json
├── knowledge/                         # Layer 1: Knowledge Base
│   ├── brand-voice.md
│   ├── policies/
│   │   ├── returns-exchanges.md
│   │   ├── shipping.md
│   │   ├── payments.md
│   │   ├── warranty.md
│   │   └── privacy-gdpr.md
│   ├── processes/
│   │   ├── order-issues.md
│   │   ├── escalation.md
│   │   ├── complaints.md
│   │   ├── custom-orders.md
│   │   └── gifting.md
│   └── products/
│       ├── materials-care.md
│       ├── sizing-guide.md
│       └── collections.md
├── skills/
│   ├── response-drafting/
│   │   └── SKILL.md
│   ├── ticket-triage/
│   │   └── SKILL.md
│   └── product-knowledge/
│       └── SKILL.md
├── commands/
│   ├── draft-response.md
│   ├── triage.md
│   ├── kb-article.md
│   └── agent-improve.md
└── README.md
```

## Implementation Phases

### Phase 1: Initial Setup & Website Scraping

**Goal:** Create the plugin scaffold and populate knowledge base from indira.ro.

**Tasks:**

- [ ] Initialize git repo at `customer_care/`
- [ ] Create plugin structure: `.claude-plugin/plugin.json`, `commands/`, `skills/`, `knowledge/`
- [ ] **Scrape indira.ro** using browser automation to extract:
  - Product collections, categories, materials, price ranges → `knowledge/products/collections.md`
  - Materials and care instructions → `knowledge/products/materials-care.md`
  - Size guides (rings, bracelets) → `knowledge/products/sizing-guide.md`
  - Shipping policy page → `knowledge/policies/shipping.md`
  - Return/refund policy page → `knowledge/policies/returns-exchanges.md`
  - Terms and conditions → `knowledge/policies/payments.md`
  - About page / brand story → `knowledge/brand-voice.md`
  - FAQ if available → distribute across relevant knowledge files
- [ ] Review and clean up scraped content (remove HTML artifacts, format as clean markdown)
- [ ] Write `knowledge/brand-voice.md` — extract tone from website copy, define Romanian response style

**Files created:**
```
.claude-plugin/plugin.json
knowledge/brand-voice.md
knowledge/policies/returns-exchanges.md
knowledge/policies/shipping.md
knowledge/policies/payments.md
knowledge/policies/warranty.md
knowledge/policies/privacy-gdpr.md
knowledge/products/collections.md
knowledge/products/materials-care.md
knowledge/products/sizing-guide.md
```

### Phase 2: Core Skills

**Goal:** Create skills that teach Claude how to use the knowledge base.

**Tasks:**

- [ ] Create `skills/response-drafting/SKILL.md`
  - Must reference `knowledge/` files for policies and brand voice
  - Romanian language output by default
  - Follow Anthropic's response-drafting skill pattern but customized for jewelry e-commerce
  - Include jewelry-specific response templates: order status, returns, product questions, sizing help
  - Reference `knowledge/brand-voice.md` for tone

- [ ] Create `skills/ticket-triage/SKILL.md`
  - Category taxonomy specific to jewelry e-commerce: order issues, returns, product questions, sizing, payments, shipping, complaints, custom orders, gifting
  - Priority framework: P1 (lost package, wrong item), P2 (return request, payment issue), P3 (product question, sizing), P4 (general inquiry)

- [ ] Create `skills/product-knowledge/SKILL.md`
  - Jewelry materials expertise (argint/silver, aur/gold, pietre/stones)
  - Care and maintenance guidance
  - Sizing guidance
  - References `knowledge/products/` files

**Files created:**
```
skills/response-drafting/SKILL.md
skills/ticket-triage/SKILL.md
skills/product-knowledge/SKILL.md
```

### Phase 3: Commands

**Goal:** Build the slash commands the care person uses daily.

**Tasks:**

- [ ] Create `commands/draft-response.md`
  - Input: pasted customer message (Romanian or English)
  - Workflow: parse → check knowledge base → draft response in Romanian
  - Output: formatted draft with internal notes
  - Must read relevant `knowledge/` files based on topic
  - Follow Anthropic's draft-response command pattern (see reference below)

```yaml
# commands/draft-response.md frontmatter
---
description: Scrie un răspuns profesional pentru un mesaj de la client
argument-hint: "<mesajul clientului>"
---
```

- [ ] Create `commands/triage.md`
  - Input: pasted ticket text
  - Workflow: categorize → prioritize → suggest response
  - Output: structured triage assessment

```yaml
---
description: Triază și prioritizează un ticket de suport
argument-hint: "<textul ticketului>"
---
```

- [ ] Create `commands/kb-article.md`
  - Input: resolved issue description
  - Workflow: extract knowledge → find right file → draft update
  - Output: knowledge base article or update to existing file

- [ ] Create `commands/agent-improve.md` (the self-improvement command)
  - Input: description of what was wrong + correct answer
  - Workflow:
    1. Extract learning from conversation context
    2. Classify: policy correction | process gap | tone issue | product info | response pattern
    3. Search existing `knowledge/` files for the right location
    4. Propose specific edit to the right file
    5. Show diff and ask for confirmation
    6. Save the change (care person commits via git)
  - Must NEVER auto-save — always confirm first

```yaml
---
description: Îmbunătățește baza de cunoștințe pe baza feedback-ului
argument-hint: "<ce a fost greșit și care e răspunsul corect>"
---
```

**Files created:**
```
commands/draft-response.md
commands/triage.md
commands/kb-article.md
commands/agent-improve.md
```

### Phase 4: Placeholder Knowledge (Manual)

**Goal:** Fill in knowledge files that can't be scraped — policies that need human input.

**Tasks:**

- [ ] `knowledge/policies/warranty.md` — needs input from care person about warranty terms
- [ ] `knowledge/policies/privacy-gdpr.md` — GDPR compliance text
- [ ] `knowledge/processes/order-issues.md` — internal process for handling wrong/missing/damaged items
- [ ] `knowledge/processes/escalation.md` — when and how to escalate
- [ ] `knowledge/processes/complaints.md` — complaint handling procedures
- [ ] `knowledge/processes/custom-orders.md` — custom order process
- [ ] `knowledge/processes/gifting.md` — gift wrapping, gift cards

These files should be created as **templates with TODO markers** that the care person fills in via `/agent-improve` during daily use. Example:

```markdown
# Politica de Garanție

<!-- TODO: completați cu termenii de garanție specifici Indira -->

## Perioadă de garanție
- Bijuterii din argint: [perioadă]
- Bijuterii din aur: [perioadă]

## Ce acoperă garanția
- [de completat]

## Ce NU acoperă garanția
- [de completat]
```

### Phase 5: Package, Test & Git

**Goal:** Package as `.plugin`, install in Cowork, test the loop.

**Tasks:**

- [ ] Write `README.md` with plugin overview and usage instructions
- [ ] Initialize git repo, create `.gitignore`
- [ ] Package plugin:
  ```bash
  cd indira-customer-care && zip -r /tmp/indira-customer-care.plugin . -x "*.DS_Store" "*.git*"
  ```
- [ ] Install in Cowork and test:
  - Test `/draft-response` with a sample return request
  - Test `/triage` with a sample order complaint
  - Test `/agent-improve` to update a policy
  - Verify the knowledge base update is reflected in subsequent `/draft-response` calls
- [ ] First commit to git

## Technical Considerations

- **Language:** All knowledge base content and command outputs in Romanian. Command metadata (frontmatter) can be in Romanian or English.
- **Plugin packaging:** Commands and skills must be in the `.plugin` file. Knowledge files can also be in the plugin OR accessed via "Work in a folder" (hybrid). Start with everything in the plugin for simplicity.
- **No code required:** Everything is markdown + JSON. No build steps.
- **Cowork command format:** Follow the Anthropic convention — YAML frontmatter with `description` and `argument-hint`, markdown body with instructions for Claude.

## Acceptance Criteria

- [ ] Plugin installs in Claude Desktop Cowork without errors
- [ ] `/draft-response` produces Romanian responses that reference correct policies
- [ ] `/triage` categorizes tickets with jewelry-specific taxonomy
- [ ] `/agent-improve` can update knowledge files and show confirmation before saving
- [ ] All files tracked in git
- [ ] Knowledge base contains real content from indira.ro (not just placeholders)

## Dependencies & Risks

- **Website scraping:** indira.ro renders client-side (Shopify), so browser automation needed (not simple HTTP fetch). Risk: content may be dynamically loaded.
- **Policy accuracy:** Scraped policies need human review. Risk: outdated or incomplete info on website.
- **Plugin reload:** After `/agent-improve` edits files, the plugin may need re-packaging to pick up changes to commands/skills (not knowledge). Need to test.
- **Delight Chat integration:** Not in scope for MVP. Copy-paste workflow for now.

## References

- Brainstorm: `docs/brainstorms/2026-02-16-indira-customer-care-agent-brainstorm.md`
- Anthropic's customer-support plugin: used as reference for command/skill patterns
- Cowork plugin structure: [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins)
- Create plugin skill: `references/component-schemas.md` in cowork-plugin-management
