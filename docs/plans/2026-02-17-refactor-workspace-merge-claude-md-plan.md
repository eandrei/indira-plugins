---
title: Merge workspace into plugin dir + create CLAUDE.md
type: refactor
date: 2026-02-17
---

# Merge workspace/ into indira-customer-care/ + Create CLAUDE.md

## Overview

Cowork sandboxes the agent to the "Work in a folder" directory. Currently workspace/ and indira-customer-care/ are separate — the agent can't edit skills/commands. Fix: merge everything into indira-customer-care/ so it becomes both the plugin source AND the workspace.

## Steps

### 1. Move workspace content into indira-customer-care/

```bash
mv workspace/knowledge/ indira-customer-care/knowledge/
mv workspace/drafts/ indira-customer-care/drafts/
mv workspace/tickets/ indira-customer-care/tickets/
mv workspace/research/ indira-customer-care/research/
rm -rf workspace/
```

### 2. Create indira-customer-care/CLAUDE.md

Full conventions file covering:

- **Rolul agentului** — customer care indira.ro, limba română cu diacritice
- **Reguli de comunicare** — no emojis, semnătura "Elena", ton conform knowledge/brand-voice.md
- **Structura fișierelor** — 3 layers: knowledge/ (date), skills/ (comportament), commands/ (workflow) + working dirs (drafts/, tickets/, research/)
- **Cum se editează KB** — NEVER auto-save, always confirm, verify consistency across all 3 layers, run `./commit` after
- **Referință rapidă** — link-uri către brand-voice.md, fiecare skill, fiecare comandă

### 3. Update commands/agent-improve.md

- Reference CLAUDE.md as source of truth for conventions
- All paths are now relative to workspace root (knowledge/, skills/, commands/) — no `../` needed
- Add step: "Citește CLAUDE.md înainte de orice modificare"

### 4. Update README.md (root)

- Setup step 4: "Work in a folder" → select `indira-customer-care/` (not workspace/)
- Update structure diagram — no more workspace/ directory
- Note that plugin dir IS the workspace

### 5. Update indira-customer-care/README.md

- Remove references to workspace/ being separate
- Update structure diagram to show knowledge/, drafts/, etc. inside plugin dir

### 6. Update .gitignore

- Add drafts/, tickets/, research/ content exclusions if needed (keep .gitkeep)

## Acceptance Criteria

- [ ] `ls indira-customer-care/knowledge/` shows all KB files
- [ ] `workspace/` directory no longer exists
- [ ] `indira-customer-care/CLAUDE.md` exists with full conventions
- [ ] `commands/agent-improve.md` references CLAUDE.md
- [ ] Both READMEs updated with new structure
- [ ] `grep -r "workspace/" indira-customer-care/` returns nothing
- [ ] All existing `knowledge/` relative paths in commands/skills still work (unchanged)

## Risks

- **Plugin marketplace sync**: If Cowork expects plugin dir to only contain plugin files, having knowledge/ etc. might confuse it. Low risk — .claude-plugin/plugin.json is what defines the plugin.
- **Git history**: Moving files loses git blame. Acceptable tradeoff.

## References

- Brainstorm: `docs/brainstorms/2026-02-17-claude-md-workspace-merge-brainstorm.md`
- Current structure: `README.md` (root)
