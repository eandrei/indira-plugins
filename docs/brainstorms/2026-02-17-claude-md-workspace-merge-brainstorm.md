# Brainstorm: CLAUDE.md + Workspace Merge

**Date:** 2026-02-17
**Status:** Ready for planning

## What We're Building

1. **Merge workspace/ into indira-customer-care/** — the plugin directory becomes the Cowork workspace. Agent gets access to knowledge, skills, commands, and working dirs all in one place.

2. **Create CLAUDE.md** inside indira-customer-care/ (now the workspace root) with full conventions: brand voice rules, file structure, 3-layer consistency, editing guidelines.

3. **Update agent-improve** to reference CLAUDE.md as the source of truth for conventions. No more need for `../` paths — everything is relative to workspace root.

## Why This Approach

- Cowork sandboxes the agent to the "Work in a folder" directory — it cannot access files outside it
- The previous structure (workspace/ separate from plugin/) meant the agent couldn't edit skills/commands via agent-improve
- Merging solves this: one directory, full access, simple relative paths

## Key Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| Workspace location | `indira-customer-care/` IS the workspace | Cowork can't access files outside workspace |
| Structure | All-in-one | Agent needs to edit knowledge + skills + commands |
| CLAUDE.md scope | Full conventions | Brand voice, file structure, 3-layer consistency, editing rules |
| Path references | All relative to workspace root | `knowledge/`, `skills/`, `commands/` — no `../` |

## Target Structure

```
indira-customer-care/          ← Cowork "Work in a folder" points here
├── CLAUDE.md                  ← Agent conventions & rules
├── .claude-plugin/
│   └── plugin.json
├── commands/
├── skills/
├── knowledge/                 ← moved from workspace/
│   ├── brand-voice.md
│   ├── policies/
│   ├── processes/
│   └── products/
├── drafts/                    ← moved from workspace/
├── tickets/                   ← moved from workspace/
├── research/                  ← moved from workspace/
├── CONNECTORS.md
└── README.md
```

## CLAUDE.md Content Plan

1. **Rolul agentului** — customer care pentru indira.ro
2. **Reguli de comunicare** — Romanian, diacritice, no emojis, semnătura "Elena", ton conform brand-voice.md
3. **Structura fișierelor** — 3 layers (knowledge, skills, commands) + working dirs (drafts, tickets, research)
4. **Cum editezi KB** — always confirm, verify consistency across layers, use `./commit`
5. **Referințe** — point to brand-voice.md for detailed tone, link to each skill

## Changes Needed

1. `mv workspace/knowledge/ indira-customer-care/knowledge/`
2. `mv workspace/{drafts,tickets,research}/ indira-customer-care/`
3. Create `indira-customer-care/CLAUDE.md`
4. Update `commands/agent-improve.md` — reference CLAUDE.md, remove old path assumptions
5. Update `README.md` — new setup instructions (point to indira-customer-care/)
6. Remove empty `workspace/` directory

## Open Questions

- Does the plugin marketplace sync still work when the plugin dir is also the workspace?
- Do .gitkeep files in drafts/tickets/research need updating?
