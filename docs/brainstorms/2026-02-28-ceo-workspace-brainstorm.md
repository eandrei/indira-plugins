# CEO Workspace — Brainstorm

**Data:** 2026-02-28
**Status:** Definitivat

## Ce construim

Un mono-repo care servește dublu:
1. **Plugin marketplace** — plugin-uri partajabile (customer care, interview analysis, marketing, etc.) care se îmbunătățesc continuu
2. **CEO workspace** — spațiu personal de lucru cu context despre cine ești, cum lucrezi, și acces la toate plugin-urile

Interacțiunea e flexibilă: un agent CEO la root pentru overview/routing, sau intrare directă în plugin-ul relevant.

## De ce această abordare

**Mono-repo cu separare prin .gitignore** câștigă pentru că:
- Totul e într-un loc — nu trebuie să sari între directoare
- CLAUDE.md la root = context personal disponibil automat
- Plugin-urile rămân curate și partajabile (au propriul `.claude-plugin/`)
- Fișierele personale (about-me, working-style) stau în `.gitignore`
- Brand-voice e partajabil — e al business-ului, nu personal

## Decizii cheie

### 1. Structura directorului

```
indira-plugins/
├── CLAUDE.md                      ← instrucțiuni CEO: routing + personal context
├── .gitignore                     ← exclude personal files
│
├── about-me.md                    ← PERSONAL (gitignored)
├── working-style.md               ← PERSONAL (gitignored)
├── brand-voice.md                 ← SHARED (business context)
│
├── indira-customer-care/          ← plugin: customer care
│   ├── .claude-plugin/plugin.json
│   ├── CLAUDE.md
│   ├── knowledge/
│   ├── commands/
│   ├── skills/
│   └── ...
│
├── interview-analysis/            ← plugin: JTBD analysis
│   ├── .claude-plugin/plugin.json
│   └── ...
│
├── marketing/                     ← plugin: marketing & content (VIITOR)
├── operations/                    ← plugin: operațiuni & finanțe (VIITOR)
├── strategy/                      ← plugin: strategie & cercetare (VIITOR)
│
├── workspace/                     ← CEO working area
│   ├── drafts/
│   ├── research/
│   └── tickets/
│
└── docs/
    └── brainstorms/
```

### 2. Separare personal vs shared

| Fișier | Tip | .gitignore | Cine citește |
|--------|-----|------------|--------------|
| about-me.md | Personal | DA | CLAUDE.md la root (orice sesiune) |
| working-style.md | Personal | DA | CLAUDE.md la root (orice sesiune) |
| brand-voice.md | Business | NU | Plugin-uri customer-facing |

### 3. CLAUDE.md la root = Agent CEO

CLAUDE.md la root va funcționa ca "brain" central:
- Citește about-me.md și working-style.md pentru context personal
- Știe ce plugin-uri există și când să le folosească
- Rutează task-uri: "mesaj de la clientă" → customer-care, "analizează interviu" → interview-analysis
- Oferă overview de business când e nevoie

### 4. Conectori / MCP-uri

**Existente:**
- Shopify (Prism + Shop MCP) — comenzi, clienți, produse
- Google Analytics — traffic, conversii
- Chrome browser — browsing, tracking

**De adăugat:**
- Google Workspace (Gmail, Calendar, Drive) — email, programare, documente

MCP-urile se configurează la nivel de root (`.mcp.json`) sau per-plugin.

### 5. Plugin-uri viitoare (nu acum, doar direcție)

- **marketing/** — calendar editorial, drafturi social media, newsletter
- **operations/** — rapoarte stocuri, fulfillment, analytics
- **strategy/** — competitive analysis, product roadmap, planning

Se construiesc pe măsură ce apar nevoi concrete — nu în avans.

## Întrebări deschise

- Cum se va sincroniza brand-voice.md de la root cu cel din `indira-customer-care/knowledge/`? (duplicat vs symlink vs referință)
- Ce comenzi ar trebui să aibă agentul CEO? (ex: /daily-briefing, /priorities, /delegate)
- Google Workspace MCP — se configurează global sau per-plugin?
