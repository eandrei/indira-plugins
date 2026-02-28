# Indira Plugins

Plugin-uri și workspace CEO pentru [indira.ro](https://www.indira.ro) — bijuterii demi-fine din argint și aur.

## Setup cu Claude Cowork

1. **Work in a folder** → selectează `indira-plugins/` pentru CEO workspace
2. Sau selectează un plugin specific (ex: `indira-customer-care/`) pentru lucru focusat

## Plugin-uri disponibile

| Plugin | Descriere |
|--------|-----------|
| `indira-customer-care/` | Customer care agent — răspunsuri, triaj, cercetare, KB |
| `interview-analysis/` | Analiza interviuri JTBD |

## Structura

```
indira-plugins/
├── CLAUDE.md                  ← agent CEO: routing + context
├── about-me.md                ← personal (gitignored)
├── working-style.md           ← personal (gitignored)
├── brand-voice.md             ← vocea brandului (shared)
│
├── indira-customer-care/      ← plugin: customer care
│   ├── .claude-plugin/
│   ├── CLAUDE.md
│   ├── knowledge/
│   ├── commands/
│   ├── skills/
│   └── ...
│
├── interview-analysis/        ← plugin: analiza interviuri
│   ├── .claude-plugin/
│   ├── commands/
│   └── skills/
│
├── workspace/                 ← fișiere de lucru CEO
│   ├── drafts/
│   ├── research/
│   └── tickets/
│
└── docs/
    ├── brainstorms/
    └── plans/
```

## Cum se actualizează

| Ce se schimbă | Cum | Când e disponibil |
|---------------|-----|-------------------|
| Knowledge base | Editezi fișierele din `knowledge/` | Instant |
| Commands & Skills | `git commit && git push` | La push |
| Self-improvement | `/agent-improve` → confirmă → push | Instant local |
