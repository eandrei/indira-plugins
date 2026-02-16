# Indira Plugins

Claude Cowork plugin marketplace for [indira.ro](https://www.indira.ro).

## Plugins

| Plugin | Descriere |
|--------|-----------|
| [indira-customer-care](./indira-customer-care/) | Customer care agent — draft responses, triage tickets, escalate, research, and improve the knowledge base |

## Structură

```
indira-plugins/
├── workspace/                ← Cowork "Work in a folder" pointează aici
│   ├── knowledge/            ← baza de cunoștințe (brand, produse, politici, procese)
│   ├── drafts/               ← draft-uri de răspunsuri în lucru
│   ├── tickets/              ← note și context per ticket
│   └── research/             ← cercetări și investigații
├── indira-customer-care/     ← plugin source (instalat separat în Cowork)
│   ├── commands/
│   ├── skills/
│   └── .claude-plugin/
├── docs/
└── README.md
```

## Setup

### Ca Marketplace (recomandat — auto-update)

1. În Claude Code / Cowork, rulează:
   ```
   /plugin marketplace add eandrei/indira-plugins
   /plugin install indira-customer-care@indira-plugins
   ```
2. **Work in a folder** → selectează directorul `workspace/`

Plugin-ul se actualizează automat la fiecare `git push`.

> **Notă:** Repo-ul e privat. Trebuie acces la `eandrei/indira-plugins` pe GitHub. Pentru auto-update în background, setează `GITHUB_TOKEN` în shell config.

### Ca Upload Manual

1. Rulează: `cd indira-customer-care && zip -r ../indira-customer-care.plugin . -x "*.DS_Store"`
2. În Cowork, **Plugins** → **Upload plugin** → selectează `.plugin`
3. **Work in a folder** → selectează directorul `workspace/`
4. Necesită re-upload la fiecare modificare de commands/skills

## Workflow de Actualizare

### Knowledge base (instant)
Editezi fișierele din `workspace/knowledge/` → disponibil imediat (via "Work in a folder")

### Commands & Skills (via git push)
Editezi commands/skills → `git commit && git push` → Cowork detectează update-ul automat

### Self-improvement loop
1. `/draft-response` → răspuns greșit
2. `/agent-improve` → propune modificare knowledge
3. Confirmă → salvat local (instant)
4. `git push` → disponibil permanent
